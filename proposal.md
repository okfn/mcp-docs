## MCP Technical Documentation – Proposed Restructure

* [Home](#home)  
* [Introduction](#introduction)  
  * [Project context](#project-context:-connecting-ai-to-public-open-data)  
  * [Why MCP?](#why-mcp?-–-an-open-model-for-public-data)  
* [Developer Guide](#developer-guide)  
  * [Architecture & Design Principles](#architecture-&-design-principles)  
    * [System Architecture](#system-architecture)  
    * [Architectural constraints](#architectural-constraints)  
    * [Design Pattern](#design-pattern-–-modular-plugins)  
  * [Getting Started (Quickstart)](#getting-started-\(quickstart\))  
    * [Repositories overview](#repositories-overview)  
    * [Run the MCP server](#run-the-mcp-server)  
    * [Run the chat gateway](#run-the-chat-gateway)  
    * [Test with MCP Inspector](#test-with-mcp-inspector)  
  * [Building Plugins & Datasets](#building-plugins-&-datasets)  
    * [Describing your plugin](#describing-your-plugin)  
    * [Building YAML Datasets](#building-yaml-datasets)  
    * [Python Tools](#python-tools)  
    * [Tool Results](#tool-results)  
    * [Connecting plugins to a server](#connecting-plugins-to-a-server)  
    * [Implementing domain glossaries](#implementing-domain-glossaries)  
* [Use Cases](#use-cases)  
  * [Uruguay implementation](#uruguay-implementation)  
  * [Brazil implementation](#brazil-implementation)  
* [Operations](#operations)  
  * [Deployment](#deployment)  
* [Contributing](#contributing)

### Home {#home}

Welcome to the MCP Technical Documentation – a practical guide to connecting open public data to AI models using the Model Context Protocol (MCP).

This manual provides the architecture specifications, code patterns, and configuration templates needed to build plugins, run the server, and deploy data tools.

**Looking for non-technical context or project strategy?** Check out the \[Field Guide to Connecting AI to Public Information\]. It covers lessons from our Brazil and Uruguay pilots, guidance on working with domain experts, and real-world user feedback.

For more information, please visit the official project page “Traceable AI Answers for Public Data” at the [Open Knowledge Foundation (OKFN) website](https://okfn.org/en/projects/ai-learning-labs/mcp-open-government-data/).

### Introduction {#introduction}

#### Project context: Connecting AI to Public Open Data {#project-context:-connecting-ai-to-public-open-data}

Public open data is essential for transparency, accountability, and informed decision-making. However, extracting answers from official portals often requires navigating complex interfaces, writing technical queries, and spending significant time interpreting raw files.

Integrating AI allows users to query data using natural language, but standard AI models also introduce a major risk: hallucinations, miscalculated figures, and plausible-sounding errors that undermine trust in official information. 

To solve this, the Open Knowledge Foundation’s AI Learning Labs built an open technical bridge using the Model Context Protocol (MCP). We tested this approach across two live public datasets:

* Brazil: Parliamentary amendments (tracking public funds).  
* Uruguay: National Energy Balance (monitoring energy transition).

**Core technical principles:** 

* Accuracy and Traceability: Answers must be grounded strictly in official datasets, and every response must link to its source. The server enforces this rule in code.  
* Plain Code Over Custom Languages: Tools are written as small, standard Python functions. Simple datasets can be declared in YAML without writing code.  
* Simple & Proven Tech Stack: Built on open-source, standard, reliable technologies (Python, CSV, SQLite, plain HTML/JS). The entire system can run locally on a laptop without complex infrastructure.   
* Local Ownership: Each team maintains its own plugin repository independently, using their preferred language and release schedule. 

#### Why MCP? – An open model for public data {#why-mcp?-–-an-open-model-for-public-data}

The Model Context Protocol (MCP) provides an open, standardized architecture for connecting AI models directly to public open data. Instead of building custom, proprietary integrations for every dataset, MCP establishes an open and reusable method for responsible data retrieval.

**Key reasons for choosing MCP include:**

* Standardization and Plug-and-Play Design: MCP embeds good practices directly into the server architecture. If datasets follow standard structures, developers can connect new data sources using templates without rebuilding the AI interface from scratch.  
* Open, Replicable Framework: Developed as part of the OKFN AI Learning Labs, the stack is fully open source, avoiding vendor lock-in or proprietary "black box" solutions.  
* Proven Local Autonomy: The architecture allows technical teams to extend the system independently. During the pilots, partner technicians successfully built an MCP server over a new data source unprompted.  
* A Growing Reusable Toolkit: Deploying a new data assistant starts from a template rather than from scratch, making it easier for less experienced technical teams to adopt and scale.

### Developer Guide {#developer-guide}

#### Architecture & Design Principles {#architecture-&-design-principles}

##### System Architecture {#system-architecture}

The platform consists of three core components coordinated by a central orchestrator:

* Chat Gateway: The central initiator that handles user input and orchestrates calls between the LLM and the MCP server.  
* LLM: Generates natural language prose and determines which tools to invoke based on user prompts.  
* MCP Server & Plugins: Receives tool calls from the Gateway and dispatches them to domain-specific plugin code to read raw data.

The LLM and MCP server never talk to each other directly; the Gateway acts as the sole intermediary and initiator.

**Execution Flow**  
Before processing user questions, the Gateway requests the tool catalog `(tools/list)` from the MCP server and caches it. This step requires no AI.

When a user submits a question, the runtime cycle proceeds as follows:

1. Tool Request: The Gateway sends the user prompt and the cached tool catalog to the LLM. The LLM selects an appropriate tool and returns the required arguments.  
2. Data Retrieval: The Gateway calls the tool via the MCP server `(tools/call)`. The plugin executes Python code or reads YAML data to fetch raw records.  
3. Data Division: The plugin splits its output into two parts:  
   * Plain text summaries sent back to the LLM via the Gateway.  
   * Structured data (tables, charts, and source links) sent directly to the Gateway UI.  
4. Final Response: The LLM receives the plain text data and generates a natural language answer. The Gateway combines this prose with the structured tables and charts to render the final response to the user.

\[Insert Sequence Diagram Here\]

**Key Technical Rules**

* Structured Data Bypasses the LLM: Tables and charts flow directly from the plugin to the user interface. They never pass through the model context, which reduces token overhead and prevents the LLM from misrendering UI elements.  
* Generic Core, Domain-Specific Plugins: The Gateway, LLM, and MCP server are dataset-agnostic. All domain knowledge and data retrieval logic live entirely inside the plugin.  
* Strict Source Contract: Tools must include a `structuredContent` payload declaring the exact data source. The MCP server enforces this contract at startup and rejects any tool that fails to declare its source.  
* Direct Messaging (`Force` Message): A plugin can send a message directly to the user's screen over the model's head, allowing tools to display strict system limits or warnings without LLM interference.  
* Transports: The server supports stdio for local debugging (e.g., Claude Desktop) and HTTP for production deployment.

##### Architectural constraints {#architectural-constraints}

Stateless Gateway (No Accounts, No Database):

* Design Choice: The system operates without user accounts, session registration, or a central database. Users can download individual outputs (tables, charts, or text blocks), but whole conversations are not saved or shared server-side.  
* Trade-off: This eliminates database administration, data retention compliance, and user management overhead, keeping the server lightweight and easy to deploy. While missing chat history is a known limitation compared to general commercial chat products, the MCP server follows standard protocols and can be plugged into existing third-party chat clients that handle account management and history if needed.

Structured Presentation (Tables and Charts):

* Design Choice: Tools return structured data (tables and charts) alongside text responses to ensure answers are auditable and verifiable.  
* UI Mitigation: Structured outputs are rendered minimized by default in the interface to prevent large data tables from cluttering the conversation flow while keeping full source records one click away.

##### Design Pattern – Modular Plugins {#design-pattern-–-modular-plugins}

Scope Plugins by Domain, Not by Portal:

* Design Choice: Plugins must be scoped to a single specific dataset or domain (e.g., Uruguay’s National Energy Balance repo, mcp-datos-uruguay-ben) rather than attempting to cover an entire government open data portal in one repository.  
* Rationale: Portal-wide plugins become shallow generalists. Narrowing plugin boundaries to a single domain provides key technical advantages:  
  * Sharper Tool Descriptions: Prompts and tool parameters are written specifically for the dataset's actual query patterns.  
  * Manageable Glossaries: Domain terminology and data dictionaries remain precise and feasible to maintain.  
  * Independent Lifecycle: Repositories stay small, clean, and able to evolve at their own pace without breaking unrelated dataset tools.

#### Getting Started (Quickstart) {#getting-started-(quickstart)}

##### Repositories overview  {#repositories-overview}

\[Moved to Getting Started section. No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/dev/repositories/)\]

##### Run the MCP server  {#run-the-mcp-server}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/getting-started/mcp-server/)\]

##### Run the chat gateway  {#run-the-chat-gateway}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/getting-started/chat-gateway/)\]

##### Test with MCP Inspector  {#test-with-mcp-inspector}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/getting-started/inspector/)\]

#### Building Plugins & Datasets {#building-plugins-&-datasets}

##### Describing your plugin {#describing-your-plugin}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/plugins/plugin-info/)\]

##### Building YAML Datasets {#building-yaml-datasets}

*NOTE: Just this lesson at the at of the page:*  
**Developer Trade-Off: When to Use YAML vs. Python**  
Declaring datasets in YAML works well for basic cases, but declarative YAML can easily turn into a bespoke query language if stretched too far. Every new filter type, join, or calculated column requires expanding the YAML parser engine.  
Rule of Thumb:

* Use YAML: For genuinely simple CSV files with standard aggregation or top-N questions.  
* Use Python: As soon as a dataset requires custom calculations, date transformations, multi-table joins, or complex filtering logic. Writing a few lines of standard Python code is clearer and easier to maintain than extending custom YAML rules.

##### Python Tools {#python-tools}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/plugins/python-tools/)\]

##### Tool Results {#tool-results}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/plugins/tool-results/)\]

##### Connecting plugins to a server {#connecting-plugins-to-a-server}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/plugins/connect/)\]

##### Implementing domain glossaries {#implementing-domain-glossaries}

Public datasets often rely on domain-specific administrative terms, legal taxonomy, or specialized units (such as energy balance figures or budget codes) that non-experts – and general LLMs – may misinterpret.  
To ensure accurate responses, plugins should include a domain glossary that injects term definitions directly into the tool context.

**How Glossary Injection Works**  
Glossary definitions serve a dual purpose in the MCP architecture:

1. LLM Context Injection: Terms and definitions are included in the tool’s system prompt or description. When the LLM receives data results, it uses these definitions to interpret raw figures and write accurate prose.  
2. User Clarity: Terms can be exposed directly in the interface so users can consult official definitions alongside their query results.

**Implementation Guidelines for Developers**

* Map Terms to Specific Tools: Avoid dumping an entire portal dictionary into every prompt. Manually curate and attach only the relevant terms to the specific tool that uses them. This conserves context window space and prevents prompt confusion.  
* Bridge Everyday Language and Bureaucratic Terms: Include alias mappings in your tool descriptions (e.g., mapping informal user terms like "pix" or "fuel tax" to their official administrative category names in the dataset).  
* Treat Glossaries as Code: Budget development time for glossary mapping during plugin creation. Defining terminology is a core technical requirement for retrieval accuracy, not post-launch documentation polish.

### Use Cases {#use-cases}

The platform includes two live reference plugins in production. Each is maintained in its own repository, in its native language, and serves as an official blueprint for building new domain plugins:

* Uruguay – National Energy Balance (mcp-datos-uruguay-ben)  
  * Source Data: Energy balance figures from catalogodatos.gub.uy (Spanish).  
  * Technical Highlights: Demonstrates domain-specific Python tools, custom parameter filters, and injected domain glossaries for specialized energy terminology.  
  * Best Used As: Template for complex datasets requiring custom python logic and term definitions.  
* Brazil – Parliamentary Amendments (mcp-datos-brasil-emendas)  
  * Source Data: High-demand budget allocation data from dados.gov.br (Portuguese).  
  * Technical Highlights: Demonstrates querying high-frequency financial records and handling informal user terminology ("emendas pix") via term mappings.  
  * Best Used As: Template for tracking structured financial allocations and public expenditure.

**Development Status:** Both implementations are currently in Alpha. Developers starting a new country or domain plugin should fork one of these repositories as a starting baseline.

#### Uruguay implementation {#uruguay-implementation}

\[Just rename the title. No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/catalogs/uruguay/)\]

#### Brazil implementation {#brazil-implementation}

\[Just rename the title. No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/catalogs/brasil/)\]

### Operations {#operations}

#### Deployment {#deployment}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/operations/deployment/)\]

### Contributing {#contributing}

\[No content adjustment – [keep as it is](https://okfnlabs.org/mcp-docs/contributing/)\]