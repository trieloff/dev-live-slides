---
title: Coding Agent Showdown
sub_title: The Good, the Bad, and the Ugly
author: Lars Trieloff (@trieloff)
theme:
  name: dark
options:
  end_slide_shorthand: true
---

# Say hi to AI

```banner
AI
```

---

# And AI says hi to you

```bash +exec
claude -p "Say hi to the Adobe Developers Live audience, but keep it short"
```

---
# Not just any kind of AI

```banner +animate:rainbow +loop
Agentic
```
---

# What

- Smarter autocomplete
- Chat with your code base, ask questions
- Agents in your IDE
- __Standalone agents in your CLI__ (we are here)
- Standalone agents in the cloud

---

# Architecture

```ascii
┌──────────────────────────────────────────────────────────┐
│                        CLOUD                             │
│                  ┌──────────────────┐                    │
│                  │   Claude Model   │                    │
│                  │   (Sonnet 4.5)   │                    │
│                  └────────▲─────────┘                    │
└───────────────────────────┼──────────────────────────────┘
                            │ API calls
┌───────────────────────────┼──────────────────────────────┐
│                  LOCAL ENVIRONMENT                       │
│                  ┌────────▼─────────┐                    │
│                  │  Agent Harness   │                    │
│                  │ (orchestration)  │                    │
│                  └────────┬─────────┘                    │
│        ┌─────────────────┼─────────────────┐             │
│        │                 │                 │             │
│   ┌────▼─────┐     ┌─────▼─────┐      ┌────▼─────┐       │
│   │ File I/O │     │   Bash    │      │   MCP    │       │
│   │  Tools   │     │   Tools   │      │ Servers  │       │
│   └────┬─────┘     └─────┬─────┘      └────┬─────┘       │
│        └─────────────────┼─────────────────┘             │
│                  ┌───────▼─────────┐                     │
│                  │  Your Codebase  │                     │
│                  │  & Environment  │                     │
│                  └─────────────────┘                     │
└──────────────────────────────────────────────────────────┘
```

---

# Edge Delivery Services

```banner:slant
AEM.live
```
