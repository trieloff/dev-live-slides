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

```banner:graceful
aem.live
```

---

# AGENTS.md

```banner:mini +animate:scanner +loop
AGENTS.md
```

---

```ascii
┌────────────────────────────────────────────────────────┐
│                     .claude/                           │
│                   AGENTS.md                            │
│  ┌──────────────────────────────────────────────────┐ │
│  │ ## Custom Agents                                 │ │
│  │                                                  │ │
│  │ ### Research Agent                               │ │
│  │ Searches docs, analyzes patterns                │ │
│  │                                                  │ │
│  │ ### Refactor Agent                               │ │
│  │ Restructures code, updates dependencies         │ │
│  └──────────────────────────────────────────────────┘ │
└─────────────────┬──────────────────────────────────────┘
                  │
                  │ extends capabilities
                  ▼
          ┌───────────────┐
          │  Claude Code  │
          │    Agent      │
          └───────────────┘
```

- Define custom agent behaviors and workflows
- Extend Claude Code with specialized capabilities
- Agents can invoke tools, chain tasks, and maintain context
- Stored in `.claude/AGENTS.md` in your project

---

# SKILLS.md

```banner:mini +animate:neon +loop
SKILLS.md
```

---

```ascii
┌────────────────────────────────────────────────────┐
│              SKILLS.md Definition                  │
│                                                    │
│  ┌──────────────────────────────────────────────┐ │
│  │ name: pdf                                    │ │
│  │ description: Extract text from PDF files     │ │
│  │ prompt: "Use pdftotext to extract..."        │ │
│  └────────────────────┬─────────────────────────┘ │
└───────────────────────┼────────────────────────────┘
                        │
                        │ Agent invokes skill
                        ▼
        ┌───────────────────────────────┐
        │      Agent Execution          │
        │                               │
        │  1. Loads skill definition    │
        │  2. Injects prompt context    │
        │  3. Executes with tools       │
        │  4. Returns results           │
        └───────────────────────────────┘

  Reusable capabilities • Shared across projects
  Custom tools • Domain-specific workflows
```

---

# --dangerously-skip-permissions

```banner:shadow +animate:glitch
YOLO
```

---

```ascii
  /\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\
  ////////////////////////// DANGER ZONE ////////////////////////
  /\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\
                                /\
                               /!!\
                              /!!!!\
                             /!!!!!!\
                            /!!!!!!!!\
                            \!!!!!!!!/
                             \!!!!!!/
                              \!!!!/
                               \!!/
                                \/
  /\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\
  ///////////////////////////////////////////////////////////////
```

Skips all permission prompts for file operations

---

**Use when:**
- You trust the code/agent completely
- Working in a sandboxed environment
- Time-sensitive demos (like this one!)

**Don't use when:**
- Working with production code
- Unsure about the agent's actions
- Your code isn't version controlled

---

# Herzblut

```banner +animate:fire +loop
HERZBLUT
```

---

```ascii +animate:breathe
       ♥♥♥♥♥       ♥♥♥♥♥
     ♥♥     ♥♥   ♥♥     ♥♥
    ♥♥       ♥♥ ♥♥       ♥♥
    ♥♥                   ♥♥
     ♥♥                 ♥♥
      ♥♥               ♥♥
       ♥♥             ♥♥
         ♥♥         ♥♥
           ♥♥     ♥♥
             ♥♥ ♥♥
               ♥
```

**Herzblut** (German): *lifeblood, passion, heart and soul*

When you code with an AI agent, you're not just writing code—you're infusing it with your vision, your standards, your *Herzblut*.

The agent amplifies your passion by handling the mechanics while you focus on the craft.

---

# Multitasking/Multi-Clauding

```banner:ogre +animate:prism +loop
PARALLEL
```

---

```ascii
┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
│   Terminal 1    │  │   Terminal 2    │  │   Terminal 3    │
│                 │  │                 │  │                 │
│  $ claude       │  │  $ claude       │  │  $ claude       │
│  Building...    │  │  Testing...     │  │  Documenting... │
│                 │  │                 │  │                 │
│  [████░░] 60%   │  │  ✓ 47 passed    │  │  Writing API    │
│                 │  │  ⚠ 2 warnings   │  │  docs...        │
└─────────────────┘  └─────────────────┘  └─────────────────┘
         │                    │                    │
         └────────────────────┼────────────────────┘
                              │
                    ┌─────────▼──────────┐
                    │   Same Codebase    │
                    │  Different Tasks   │
                    └────────────────────┘
```

---

**Why run multiple Claude instances?**

- **Different tasks in parallel**: Build, test, document simultaneously
- **Different branches**: Work on features while fixes run in main
- **Context isolation**: Each instance focuses on one specific task
- **Faster iteration**: Don't wait for one task to finish before starting another

---

# Git Worktrees

```banner:small +animate:matrix +loop
WORKTREE
```

---

```ascii
                    main repo (.git)
                          │
            ┌─────────────┼─────────────┐
            │             │             │
         worktree-1    worktree-2    worktree-3
         (main)        (feature-a)   (feature-b)
            │             │             │
         ┌──▼──┐       ┌──▼──┐       ┌──▼──┐
         │ 📁  │       │ 📁  │       │ 📁  │
         │ src │       │ src │       │ src │
         └─────┘       └─────┘       └─────┘
           │             │             │
        claude        claude        claude
       instance 1    instance 2    instance 3
```

---

**What are Git Worktrees?**

Multiple working directories attached to the same repository
- Each worktree can check out a different branch
- Share the same `.git` database (efficient!)
- Work on multiple features/branches simultaneously

---

**Why They're Perfect for Agents**

- Run multiple Claude instances on different branches
- No context switching or stashing required
- Agents can work in parallel without conflicts
- Test features independently while keeping main clean

---

# Seeing like an Agent

```banner:epic +animate:scanner +once
OBSERVE
```

---

```ascii
    .-"-._.-"-._.-"-._.-"-.
   /                       \
  |   .-----------------.   |
  |   |  .-----------. |   |
  |   | |    * * *   | |   |
  |   | |   /  |  \  | |   |
  |   | |  /___|___\ | |   |
  |   | '-----------' |   |
  |   '----------------'   |
   \    Agent Vision      /
    '-._.-"-._.-"-._.-"-'
```

## How Agents Perceive Code

- **File System**: Read, search, and navigate your entire codebase
- **Context**: Understand structure through grep, glob, and AST analysis
- **Memory**: Build mental models from multiple file reads
- **Tools**: Extend perception via MCP servers (web, docs, databases)

Agents don't see files like humans - they see patterns, relationships, and possibilities across the entire codebase simultaneously.

---

# Guardrails/Attribution/Transparency

```banner +animate:breathe +loop
SAFETY
```
---

```ascii +animate:aurora
    ╔════════════════════════════╗
    ║   🛡️  PROTECTED ZONE  🛡️   ║
    ╠════════════════════════════╣
    ║   ┌──────────────────┐     ║
    ║   │  Your Codebase   │     ║
    ║   │   + Data + Keys  │     ║
    ║   └──────────────────┘     ║
    ║         ▲      ▲           ║
    ║         │      │           ║
    ║    ┌────┴──┬───┴────┐      ║
    ║    │ Guard │ Guard  │      ║
    ║    │ Rails │ Rails  │      ║
    ║    └───────┴────────┘      ║
    ╚════════════════════════════╝
```

---

## Built-in Safety Features

- **Permission prompts** for file modifications and destructive operations
- **Attribution** - All model responses clearly sourced from Claude
- **Transparency** - Full audit trail of agent actions in conversation history
- **Data locality** - Code stays on your machine, only queries sent to cloud
- **Consent-based** - Agent asks before making changes

---

# Agent/Model table

```banner +animate:scanner +once
COMPARE
```

---

| Agent | Model |
|-------|-------|
| `claude` | Claude 4.5 Sonnet |
| `copilot` | GPT-4 / Codex |
| `cursor` | GPT-4 / Claude |
| `aider` | GPT-4 / Claude |
| `windsurf` | GPT-4 |
