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
./copresenter --new "Say hi to the Adobe Developers Live audience"
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
```bash +exec
./copresenter "Got anything to add?"
```

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
│         ┌─────────────────┼─────────────────┐            │
│         │                 │                 │            │
│    ┌────▼─────┐     ┌─────▼─────┐      ┌────▼─────┐      │
│    │ File I/O │     │   Bash    │      │   MCP    │      │
│    │  Tools   │     │   Tools   │      │ Servers  │      │
│    └────┬─────┘     └─────┬─────┘      └────┬─────┘      │
│         └─────────────────┼─────────────────┘            │
│                   ┌───────▼─────────┐                    │
│                   │  Your Codebase  │                    │
│                   │  & Environment  │                    │
│                   └─────────────────┘                    │
└──────────────────────────────────────────────────────────┘
```

---

```bash +exec
./copresenter "Remind me what MCP stands for"
```

---

# Edge Delivery Services

```banner:graceful
aem.live
```

---

https://www.aem.live/ai

---

# AGENTS.md

```banner:mini +animate:scanner +loop
AGENTS.md
```

---

```ascii
┌────────────────────┐          ┌────────────────────┐
│                    │          │                    │
│    ~/AGENTS.md     │          │    ./AGENTS.md     │
│~/.claude/CLAUDE.md │          │    ./CLAUDE.md     │
│                    │          │                    │
└────────────────────┘          └────────────────────┘
           │                               │
           │                               │
           └────injected into (almost) ────┘
                     every  prompt
                          │
                          ▼
                     ┌─────────┐
                     │ Coding  │
                     │  Agent  │
                     └─────────┘
```

---

# If you don't like repeating yourself

- default prompt for every project (~) or the current repository
- or even the current folder
- put all the things the agent should always follow here

https://github.com/adobe/helix-website/blob/main/AGENTS.md

(steal this)

---

```bash +exec
./copresenter "Hey, why does every agent but Claude respect AGENTS.md?"
```
---

# SKILLS.md

```banner:mini +animate:neon +loop
SKILLS.md
```

---

```ascii
         ┌────────────────────────────────────┐
     ┌───│  .claude/skills/search/SKILLS.md   │
     │   └────────────────────────────────────┘
     │       ┌────────────────────────────────────┐
     ├───────│   .claude/skills/test/SKILLS.md    │
     │       └────────────────────────────────────┘
     │           ┌────────────────────────────────────┐
     ├───────────│    .claude/skills/pr/SKILLS.md     │
     │           └────────────────────────────────────┘
     │
     ▼
┌─────────┐
│ Coding  │ list skills at start of
│  Agent  │ session, load on demand
└─────────┘
```

---

# What skills can do

- make your agent more __skilled__
- are used on-demand
- don't consume *context* by default

<!--

Note: context is the hard currency of coding agents. you want to preserve them,
protect them, and use them wisely.

-->
---

```bash +exec
./copresenter "Kudos to team Anthropic for inventing SKILLS.md. Do other agents respect SKILLS.md?"
```
---

# Upskill

```bash
$ gh ext install trieloff/gh-upskill
$ gh upskill adobe/helix-website
```

Install skills from another repository, for any agent that respects `AGENTS.md`

---

# `--dangerously-skip-permissions`

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

```banner +animate:glitch +once
COMPARE
```

---

| Agent | Model |
|-------|-------|
| `claude` | claude-opus-4.1 |
| `codex` | gpt-5-high |
| `gemini` | gemini-2.5-pro |
| `copilot` | claude-haiku-4.5 |
| `cursor-agent` | composer 1 |
| `opencode` | Grok Code Fast 1 |
| `qwen` | qwen3-coder-plus-2025-09-23 |
| `droid` | Droid Core (GLM 4.6) |
| `amp` | sonnet-4.5/gpt-5 |
| `kimi` | kimi-k2 |
| `crush` | GLM-4.6 |
| `goose` | gpt-oss-120b |
