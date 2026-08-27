Open Knowledge Foundation | AI Learning Labs 

# A Field Guide to Connecting AI to Public Information

**How governments and developers can increase accuracy and trust in AI responses**.

## Background

Public data is essential for accountability, participation, and informed decision-making. Yet, available data isn't always accessible data; users too often must navigate complex portals, master technical queries, and invest significant time simply to extract answers.

Over the course of four months in 2026, the Open Knowledge Foundation's AI Learning Labs tackled this challenge by connecting open-source AI to public open data portals in Brazil and Uruguay. The goal was to enable citizens to ask natural language questions to the data portals. The challenge was to create a process whereby the risk of false information (hallucinations) could be minimised, and responses could be verified. The last thing anyone wants to see is an AI system that misrepresents or entirely reinvents numbers or facts in open data portals. Together with our government partners, our pilots set out to find steps to minimise this risk.

We piloted a technical bridge using the Model Context Protocol (MCP), allowing an AI assistant to retrieve and verify answers directly from official datasets. To ensure this approach worked in the real world, we tested it on live, high-demand datasets chosen by our government partners:

* Brazil: Parliamentary amendments – a politically sensitive, high-demand dataset used constantly by citizens and journalists to track the allocation of public funds.  
* Uruguay: National Energy Balance – a critical dataset used to monitor the country's world-renowned renewable energy transition.

Being able to ask questions across years of data is a gift to any researcher, journalist, or citizen – but only if answers can be verified in a trustworthy way. Testing across these two contexts helped us move far beyond a technical proof-of-concept. The lessons we learned from these pilots are condensed below into a practical guide to help inform your own AI and open data development process.

## What you can do to make AI responses more trustworthy

### Access to data is not the same as understanding data

The MCP layer successfully helped the assistant connect to official datasets and retrieve information directly from the source. In that sense, the technical bridge worked: the model could read real numbers from official data instead of relying only on general training data. 

But the pilots confirmed that access alone is not enough. To answer responsibly, the system also needs context: what terms mean, what units values use, which time periods figures cover, what the dataset leaves out, and what assumptions were made when the data was compiled. These are not details that an AI system can safely infer from a column name or dataset title. They require people who understand the data and can explain what should – and should not – be inferred from it.

**What we recommend:** Build the technical setup alongside the people who understand the data, and keep them involved as the system is tested and refined. Ensure the system is built around the dataset's meaning, not just the dataset itself.

### Complex datasets are stress tests, not starting points

During our pilots, testing on a highly complex dataset proved that our architecture could handle difficult conditions. However, achieving reliable answers required far more fine-tuning, support tools, and expert time than expected, which significantly multiplied the cost and duration of testing. 

One valuable learning from our pilot teams is to start small. Prove your end-to-end workflow – including tool descriptions, glossaries, system prompts, and testing cycles – on a simple dataset first. Once your methodology is solid, applying it to a complex dataset becomes an intentional, controlled stress test rather than an unexpected bottleneck.

**What we recommend:**

* Run your first pilot on simple, easy-to-explain data.  
* Fix the system before scaling up. Ensure any early errors you encounter are problems with your methodology, not confusion over complex data.  
* Treat complex datasets as phase two. Introduce difficult, highly technical datasets only as a stress test after your base process is fully established.

### Traceability helps, but does not guarantee correctness

Traceability was one of the main reasons for testing MCP. If an AI assistant answers a question about public data, users should be able to see where the answer came from.

While the pilots confirmed this matters, they also showed that a source link does not prove the full answer is correct. In one Uruguay example, the system referred to “climate factors” when explaining changes in energy data. The answer sounded plausible, but the provided dataset did not actually contain climate data. 

Across 84 test questions, testers marked 32 answers as correct, while 21 were marked as partially correct or uncertain. The most visible recurring issue was a coverage or retrieval gap: the system could not provide an answer even though testers believed the information existed in the data. These numbers should be read as learning signals, not as a final accuracy benchmark. But they show why traceability needs to be tested carefully.

**What we recommend:** 

* Keep traceability at the centre of the design.  
* Test whether the source actually supports the full answer, rather than just verifying that a source link appears.

### Answers need to separate data from interpretation

Several testers noticed that the assistant sometimes mixed information from the datasets with its own model inferences or pre-trained data, without clearly indicating which was which.

This matters because users may not know whether a statement comes directly from the data, from the model’s underlying training, or from an interpretation of the data. The system prompt was updated to ask the model to make this distinction clearer, but this reduced the problem rather than removing the need for checking.

**What we recommend:**

* Require the assistant to distinguish between data-backed facts and interpretation.  
* Make that distinction visible in the answer itself, so users can see what the data supports and what it does not.

### Arithmetic calculations need extra safeguards

The pilots showed a clear difference between two kinds of questions. Questions asking the system to find an existing value (e.g., “What was the value in this year?”) were much more reliable. Questions asking the system to calculate a new value (e.g., percentages, shares, or year-on-year changes) were considerably riskier. In the pilots, this was one area where testers reported answers that were numerically wrong, even though they were presented as if they came from the data.

This matters because a wrong calculation can look very convincing. A table of percentages may seem authoritative, even if the numbers were calculated incorrectly during the conversation.

The safer approach is to prepare important calculated values in advance, document what they mean, and let the system read them from the data like any other field.

**What we recommend:** 

* Test questions that ask for both existing values and calculated values.  
* Make sure important percentages, shares, and changes are calculated in a controlled way before they are shown to users

### Real questions showed what the system needed to understand

Pilot partners helped provide questions that people actually ask about the datasets. These became test cases for the system and made the testing more useful than generic prompts.  Instead of asking whether the AI could answer questions about a dataset in general, we could test whether it could answer the questions that mattered in practice.

Real questions also improved the system itself. They showed where terms were missing, where user language did not match the language used in the data, where tool descriptions were unclear, and where the assistant needed stronger limits because it answered when it should have declined. For example, “What is an amendment?” showed the need to include core concepts in the glossary. A question about “emendas pix” showed the need for a dictionary that maps informal terms to dataset terminology.

**What we recommend:** 

* Use real user questions as test cases from the start.  
* Build the glossary and terminology dictionary earlier, and make them part of the system context – not only user-facing documentation.   
* Include edge cases and high-risk questions, especially where a wrong answer could mislead users or where the data cannot fully answer the question.

### Testing needs the right people, not just more questions

Checking AI-generated answers against public data is not a simple pass/fail exercise. It takes time and requires people who understand the dataset well enough to spot answers that sound plausible but are not actually supported by the data.

This kind of human review is a continuous requirement, as the most important failures may look correct until checked by a domain expert. The mix of testers also matters: government insiders were more likely to catch wrong figures, while external civil society testers noticed when answers were confusing or assumed too much background knowledge.

**What we recommend:**

* Involve both domain experts and external users in testing.  
* Budget enough time for human review, including time to trace unclear or questionable answers back to the source.

### The "Blank Chat" Problem: Communicating System Limits

A standard chat interface implies the AI knows everything. But in this pilot, the AI is tightly constrained to specific datasets.

Because an empty chat box doesn't tell users what filters apply, what categories exist, or what years are covered in the data, testers often didn't know what questions they were "allowed" to ask. Furthermore, when the system couldn't answer a prompt, users couldn't easily tell why: was the data missing, did the AI misunderstand, or was the question simply outside the system's scope?

**What we recommend:**

* Don't rely on the chat box to explain the data. Explicitly surface the system’s scope, available datasets, and limitations before the user starts typing.  
* Guide the user's queries by providing visible examples of what can and cannot be answered.  
* Test with real users from civil society and government to ensure system boundaries are easily understood by non-technical audiences.

### Conversation flow needs more systematic testing

We tested multi-question conversations, but have not yet analysed conversation flow in enough detail to draw strong conclusions across both pilots.

The Brazil overview suggests that answer quality can vary within a conversation, including accurate answers followed by inaccuracies or “No answer” results. But to understand why this happens, future evaluation should look more closely at the content of each exchange: whether the user asked a follow-up, changed topic, used different terminology, challenged the answer, or asked something the data could not support.

**What we recommend:** Evaluate conversation flow as its own test area, rather than merely treating it as a sequence of separate questions.

## Conclusion: Should Open Data Communities Adopt AI?

These pilots do not suggest that open data portals should be replaced by chatbots. Rather, they suggest open data needs to be ready for the ways people now ask questions.

For data providers and open data teams, this means thinking beyond publication documentation for people to find online. For civil society, researchers, and other users, it means asking not only whether an AI answer has a source, but whether the source actually supports the answer.

### Make data usable by AI, not only accessible

Publishing data is still essential, but availability alone is not enough. For AI systems to use public data responsibly, they need more than a file or API endpoint; AI readiness must be treated as part of open data readiness. Public data needs clear metadata, shared definitions, documented limitations, and traceable sources.  

### Guarantee accuracy, show the source

Users should not have to become domain experts to fact-check an official data portal. The system itself must guarantee that outputs are grounded strictly in source data. Iif an accurate answer cannot be retrieved, the system should decline to answer rather than guess.

Traceability should not be a "fact-checking task" passed on to the user. Instead, clear source links serve as transparent proof that the answer comes directly from an official record, allowing users to trust the result without needing to re-verify it.

### Bridge the gap between everyday language and data jargon

Testing with real questions revealed a common failure point: citizens ask questions using informal terms, shorthand, and industry slang, whereas public datasets use strict administrative taxonomy.

Ensure your system includes domain dictionaries or semantic mappings that translate everyday language into official data categories. Without this bridge, an AI will report that data is missing simply because the user didn't know the exact bureaucratic phrase to search for.

### Start small to build trust 

Do not attempt to make your most complex, high-demand dataset AI-ready on day one. Establish your workflow, glossaries, and testing cycles on simple data first. A working pipeline on a simple dataset builds institutional trust and creates a blueprint you can later scale to more difficult domains.

### Budget for meaning

Glossaries, metadata, and dataset limits are not documentation polish. They are part of the system. They help the AI understand the data, and they help users understand the answer.

For the next implementation, plan time for:

* definitions;  
* informal terminology;  
* units and time periods;  
* known data gaps;  
* questions the data cannot answer.

### Keep humans in the loop

Human review is not a final sign-off step. People who understand the data are needed throughout testing and refinement. External users are needed too, because they notice when an answer is hard to understand, assumes too much, or does not make the source trail clear.

Useful tester mix:

* domain experts;  
* government data teams;  
* civil society users;  
* non-technical users.