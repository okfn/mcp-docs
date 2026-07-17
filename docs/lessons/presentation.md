# Tables and charts

The MCP tools are built to always show tables and charts alongside the
answer. Users value this a lot, it is what makes an answer verifiable,
but several testers reported the flip side: the tables and charts were
sometimes **repeated or too verbose**.

## What we changed

Based on that feedback, tables and charts are now shown **minimised by
default**. The information is still there, one click away, but it no
longer floods the conversation.

## What is still open

A better future fix is to detect when the same table or chart is being
drawn a second time and simply not repeat it. That deduplication is not
built yet; for now, minimising by default is the mitigation.
