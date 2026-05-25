Platform MCP — Natural language operations across your entire platform stack
When something breaks, the investigation loop across Grafana, Kong, and Kafka costs you 25–40 minutes before you even have a working theory. You're writing LogQL under pressure, manually tracing request failures, and cross-referencing dashboards across three different tools. Platform MCP eliminates that loop — replacing it with a single question in plain English.

Connectors in this release
Platform MCP ships with two connectors in this early release:
🪵 Loki MCP
Connects your Grafana Loki instance to any MCP-compatible AI agent. Ask questions about your logs in plain English — no LogQL required. The model generates the query, executes it against live data, filters the noise, and returns a reasoned explanation of what it found.
"What errors did Kong report in the last 30 minutes?"
"Is there a spike in 5xx responses after the last deployment?"
"Show me all errors and warnings from the payment service in the last hour — are there any patterns that could explain the issue?"
🦍 Kong MCP
Connects your Kong API Gateway to the same agent interface. Query route health, upstream status, plugin behaviour, and proxy traffic patterns without touching the Kong Admin API directly.
"Which upstream is returning the most errors right now?"
"Are any rate limits being hit across active consumers?"
Together, they give the model a correlated view across your request layer and your logs — so a single question can span both.

🔧 More connectors are on the way. Kafka MCP and additional platform integrations are currently under development. Watch this space.


The investigation loop they replace
Without Platform MCP

Navigate to Loki, iterate on LogQL syntax, scroll thousands of lines for signal
Separately check Kong Admin API for upstream errors, rate limit hits, and plugin behaviour
Piece together a timeline manually from two disconnected tools
Form a hypothesis based on timestamp correlation and experience
Time to first actionable conclusion: 25–40 minutes

With Platform MCP

Ask once in natural language
Loki logs queried and Kong traffic analysed automatically against live data
Noise filtered — health checks, retries, and INFO spam stripped before reasoning
Cross-component context correlated in a single inference pass
Root cause returned with supporting evidence across both Loki and Kong
Time to first actionable conclusion: 15–30 seconds


Why LLMs are well-suited for platform triage
Platform incidents are rarely isolated. A Kong upstream timeout often leaves a trace in Loki before it surfaces as a 5xx spike. Correlating that chain manually — across two tools, under pressure — is exactly the kind of problem LLMs are built to handle.

Volume — thousands of log lines and Kong request traces processed in seconds
Cross-component correlation — failures across Loki and Kong identified in one pass, not multiple open tabs
Semantic understanding — extracts error types, affected routes, retry storms, and timeout chains rather than just pattern-matching strings
Explainability — doesn't just flag anomalies; narrates what changed, when, and what the likely blast radius is


What it doesn't replace
Platform MCP handles the investigation — reading logs, querying Kong traffic, and spotting patterns across your stack. But the decisions that follow still belong to the engineer: whether to roll back, how to communicate the impact, what the right fix is. That requires judgment the model doesn't have.
Platform MCP gets you to that decision point in seconds instead of 30 minutes.