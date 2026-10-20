# Architecture of AI Agents
## Workflows vs Agents
- 2 types of agentic systems
### Workflows
- LLMs and tools that are orchastrated through predefined code paths
- Code is driving
#### Prompt Chaining
- fixed steps
- gates
    - deterministic
    - was the last response sufficient? If so exit
#### Routing
- Router LLM
    - chooses which path to take
- One path at a time
#### Parallelization
- Efficiency purposes
- Run multiple LLM calls at the same time
- Aggregator combines them
- Voting can choose between similar runs
#### Orchestrator workflows
- orchestrator chooses how many workers to generate
    - ie one per file needed to analyze
- synthesizer to combine results
#### Evaluator optimizer
- Loops
- Generator
    - generates draft
- Evaluator
    - decides if result passes
        - if not return with feedback
- maximum number of loops
#### Hybrid
- vocabulary, not recipe
- combine workflows
### Agents
- Model decides when to use tools, how many iterations, etc.
- LLMs using tools based on environmental feedback in a loop
- Model + Harness
- Model just takes in text and generates text
- Harness gives access to environment (sandbox)
    - model
    - tools (mcp)
    - memory
    - guardrails
    - loop control
- Types
    - coding agents
        - claude code
        - codex
#### Loops
- ReAct, Reasoning and Acting
    - prompting technique 
    - llm to get feedback on the world before acting
    - mitigates chain of thought hallucinations
- Ralph
    - while loop around call to agent
    - loop outside session
        - resets each time
    - memory not in context window, writes to disk
    - decides whether or not to run another session
    - needs tests it can't fake
    - max # of loops
### Connecting the pieces
#### MCP
- N x M problem
    - every agent needed its own integation
- MCP makes standard way, N+M
- sdk underneath
- mcp server wraps tool
#### - OKF (Open Knowledge Format)
durable knowledge
