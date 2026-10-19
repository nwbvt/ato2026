# AI Agents in Production
## What is an AI agent?
- Systems that indepently accomplish tasks on behalf of users
- Systems where LLMS dynamically change their own processes and tool usage
- Agents use AI to demonstrate any level of agency
### Deterministic vs probablistic
- old software is deterministric, agents are probalistic
### handling unstructured data
- content generation
- classification
- transformation of data
 - summarization
 - extraction
- role playing
- anaysis
- decision making
## REACT
- goal directed
 - working torwards an objective
- multi-step
 - plans and sequences actions across turns
## Levels of autonomy
### Level 1 Tool
- deterministric
### Level 2 AI Assistant
### Level 3 AI Copilot
- AI assistant on training wheels
### Level 4 AI Agent
### Level 5 Autonomous Agent
- Runs independently, can choose own goals
- More risk
## Harnesses
- LLMs are stateless
- Harness powers agentic loop
- Put guardrails around flow
 - Limit number of turns
- Manage boundaries between LLM and outside world
- MCP and skills
- Context engineering
- RAG
- Observability & training
### Engineering
- Prompt engineering
 - Less important, models getting better
- Context engineering
 - Still matters improve signal to noise ratio
- Harness engineering
### MCP
- Protocol for invoking tools
- Third party systems
- Tool descriptions should be descriptive
- OAuth to authenticate
 - Don't share api keys
#### A2A
- MCP has surpassed A2A
- More complex
- Difficult to govern
### Observability
- Monitor a log trace data
- OTel
- Send to telemetry server
 - Grafana
 - Datadog
 - Langfuse (open source)
- Useful for detecting drift and debugging
### Skills
- Loaded on demand
- File level
- Scripts
### Memory systems
Memory poisoning
- Memory should not be shared between users
- inaccurate memories
 - old memories
- Prompt injection
- Handle untrusted content
- Even if prompt injection is found, can still influence
 - Needs to be discarded
- Consider deactivating memories if not needed
### Personal Agents at work
- Incubators for enterprise agents
- Can stay as personal agent
- Or graduate to enterprise
### Enterprise Harness
- Optimize for scaling
- saftey/security
- principle of least privilege
- make powered by service account
### Consumer vs Enterprise
- Turnkey
- DIY frameworks
- Spectrum from personal to enterprise
## Loops
- Loop engineering
- goal based loop continues iterating until a goal is judged as achieved
- Ralph Wiggum loop
 - iterating with a fresh context each time
 - brute force
- Karpathy loop
 - Continues modifying an asset,
 - tests against rigid metric,
 - saves or rejects the change based on score
- Can be expensive
- Chronological loop
 - triggers at a particular time of day
### Judging
- Need a reliable judge for when they are done
- Don't let it change the scoring rubric
## Graphs
- Combining deterministic flows and ReACT agentic nodes
- Much of what is needed can be done with deterministic flows
### System One models
- Jev
- Outputs choices, not raw text
- Classifier model
- Unstructured input, Structured output
- Much cheaper than LLMs
- For decisions
- Already open weight versions for Ollama
 - d1, nimble
- Fit in graph
## Multi agent Orchestration
### Subagents
- Coordinator agent that delegates to subagents
- Subagents parallelize work
- Enforce through graph
- Subagents isolate tool use, permissions/access specific to subtasks
- Can use simpler models
### Agent Swarms
- Agents with diverse skills and capabilities
- Harder to govern
- Can debate
- Very expensive
- Too many cooks in the kitchen
## Choosing the Right Use Case
- Pair business need with AI superpower
 - Volume
  - Same thing happens over and over again
 - Assembly
  - People spend more time preparing than executing
  - i.e. Getting prepared for the meeting, looking for data
  - Scavenger hunt for data
 - Orchestration/Classification
  - People act as a router, directing things to the right place
 - Vigilance
  - People get tired, AI doesn't
 - Speed
  - Something done in minutes is much more valuable than something done in days
 - Access to Experise
- Not human connections
- Measuring impact
- Data and Context
 - Do you have sufficient data
 - Is the data too dirty?
 - Are edge cases documented?
- Integration/Complexity
 - How many systems must this touch?
- Risk and reversibility
 - Whats the worst that could happen if it goes wrong?
 - Can you roll back the damage?
## Enterprising
### Evals
- Run your agent through a number of evaluations
- Consider like unit tests
- Make as deterministic as possible
- Can use LLM as a judge
- Run mutliple times for statistical significance
- Reduce change of failure to as close to zero as possible
## Drift
- People start asking different questions
- Change in meanings
### Detecting Drift
- Evals
- Logging traces
 - OpenTelemetry
  - spans
  - status + events
  - model + token costs
  - tool calls
  - agent and conversation ids
  - prompts
## Secruity
### Principle of Least Privilege
- Scope down privileges on a per subtask basis
- Subagents get access to specific tools
### Workload identity
- SPIFFE
 - Secure Production Identity Framework for Everyone
 - SPIRE
 - short lived tokens
 - avoid giving api keys to agents
### Compromised Agents
Lethal Trifecta
- If agent has access to private data
- Ability to read untrusted content
- Can externally communicate
### Additional guardrails
- Input guardrails
 - Prompt injection
 - Strip out PII
- Output guardrails
 - Verify for hallucination/factual accuracy
- Tool guardrails
 - hooks, deterministic trigger
 - enforce policies
 - LLM-as-judge steering
## Agent tokenomics
### Cost per agent run
- average cost per agent run vs token
- number of loops can vary
- ensure KV cache is utilized
 - if cache lasts 10 minutes, make sure agent runs are within that window
### Right model
- Haiku for high volume simple tasks
- Sonnet for everyday stuff
- Opus judgement heavy tasks
- Fable save for when actually needed
 - 30 day retention
### Context management
- Sub agent delegation
 - doesn't send tokens for each subagent in main agent calls
### SLMs for scaling volume
- Most tasks don't actually need frontier models
- Classification, extraction, summarization
- Hybrid architecture
 - LLM Orchestrator
 - SLMs for tasks
 - System One for triaging
- Can be fine tuned
 - LoRA/QLoRA
  - train adapters, not full model weights
- Agentic (tool invoking) SLMs
 - Qwen 3.8, Gemma 4, Muse Glimmer, Nemotron 3.5
- Open Source Personal Agent Harnesses
 - Goose, OpenCode, OpenHands
- inference servers
 - Ollama, vLLM, LiteLLM
- Strata inference engine
 - use GPU + CPU
## Agent Governance
### Accountability
- Is there a named individual would own performance and decisions
- Orphaned agents, what happens when the owner leaves?
### Constraints and Boundaries
Do we have clear policies on what they can do?
### Liability
Is it clear what the risks are, and who has authority to sign off?
### Human Element
- Is the person who thought it up close enough to understand whats changing?
- Trust problem
- Need buy in
## AI Sovereignty
Controlling your AI future
### Are frontier companies deserving of trust?
- Increasingly trying to break into new markets
 - Are they using user's data for this?
 - Companies being hesitant to share their "secret sauce"
- Commodization of frontier models
 - Open weights models getting better
- Vendor lock-in
- Keep harness IP portable
 - skills, graphs
- Dial, not switch
- Backup plan if vendor breaks
### Models you control
Keep sensitive work on models you control
## AI Ethics
Essential for Human Adoption
### Trust eroding
- many concerned about AI
- creates resistance
- people sensing something wrong
### Clarifies Responsibility
- be responsible for errors made by your AI
- AIs cannot claim responsibility, only humans can
### Engenders Trust
- don't let the AI generate fake news
- safey issues break trust
- Deceptive uses
### Unlocks Human Potential
Better quality comes from humans and AI working together
### AI Fatalism
- people presurred to go faster
- fear induced statements
- speed alone causes bad problems

