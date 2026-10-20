# The Future of Apps is Open Source and Agentic
Dynamic UI
## Why
- today have to click through multiple screens
- users have to find where it is
- ideally app delivers what you want when you need it
- Smaller and focused
    - Autofills, but already done
    - combined into one page
- Finding things makes it easier to convert
## Example
1. user sends chat request
2. app responds with graph, visuals, next steps actions
3. display necessary information for user
## A2UI Protocol
- Harness has tools, model, mcp, etc
    - Add UI composition and state
- Protocol
### Client side
- Renderer recieves messages
- Renders things described by json
- style based on theme
### Messages
- createSurface
- updateComponents
- updateDataModel
- deleteSurface
### Core components
- Transport
    - send messages from agent to client
- Catalog
    - components the agent can use
    - don't let it just make anything
- Data Model
    - reactive data store
- Surface
    - place in app to display UI
- Surface Controller
- Conversation
#### Transport
- flutter
- genui
    - uses a2a
#### Catalog
- shadcn_ui
- shadalog
- libraries with components
- json describes component
- builder method to create component
#### Data Model
get for free
#### Conversation and Surfaces
- list of text events
- new surface added or removed
- conversational content
- surface controller handles creating surfaces
### Agent
#### a2a
- standard for talking to agents
- agent cards
#### a2ui
- a2ui catalog support
- add tool that validates json
- genai part converter
