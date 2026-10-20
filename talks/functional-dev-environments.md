# Building Function Dev Environments for Humans and Agents
## Most dev environments are bad
- Problems
    - docs are out of date
    - many steps
    - needs IT, secrets
    - devs write their own hacks
    - environments rarely mimics production
    - only works on one machine
- Agents have the same problems
- Dev environments
    - Code
        - only part cloned from git
    - Dependencies
    - Secrets
    - Context
    - Infrastructure
- Why stay broken
    - Tech debt, not prioritized
    - Easy to fix for yourself, hard to spread to everyone else
- More important now
    - Agents need to spin up environments
    - More people contributing
## Coder
- Lightweight
- Repo has most config
    - mise.toml
    - container
    - setup scripts
    - AGENTS.md
        - institutional knowledge
## mise
- Definte runtime, versions
