# An Agent is Just a Directory
Eve agent framework
## Model vs Agent
### Model is like a function
- needs handholding
### Agent wraps model in loop
- gives instructions
- gives tools
- gives memories
- triggers
    - start work on its own
Model is like a brilliant new hire, agent is him after knows what he is doing
## Difficulties
- Lots of wiring things together
- Lots of glue code
## Eve
- Open source framework
- File locations
    - tools/* assumed to be tools
    - skills/* assumed to skills
- durable sessions
- Two files make an agent
    - agent.ts
        - tells what model
    - instructions.md
        - what it should be doing
### Tools
- tools folder
- filename is name of tool
- description
    - is the interface
    - model determines what to use based on this
- input schema
### Skills
- markdown
- only description is always loaded
- tools are abilities, skills are know-how
### Channels
- Front door for agent
- check who is accessing
### Connections
- Let agent reach other systems
### Schedules
- Start work on its own
- cron job
- platform rules still shape agent design
### Get for free
- Durability
- Sandboxing
- Tracing
- Evals
