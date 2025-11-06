# Dev Live Slides

This repo contains the slides and code used in the Dev Live session.

# Prerequisites

- MacOS (Apple Silicon)
- [Ghostty Shell](https://ghostty.org)
- [Homebrew](https://brew.sh/) `curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh | bash`
- [figlet](https://www.figlet.org/) `brew install figlet`
- [Presenterm (Lars' fork)](https://github.com/trieloff/presenterm) `./bin/presenterm` (pre-installed)
- [ai-aligned-git](https://github.com/trieloff/ai-aligned-git) `curl -fsSL https://raw.githubusercontent.com/trieloff/ai-aligned-git/main/install.sh | sh`
- [ai-aligned-gh](https://github.com/trieloff/ai-aligned-gh) `curl -fsSL https://raw.githubusercontent.com/trieloff/ai-aligned-gh/main/install.sh | sh`
- [yolo](https://github.com/trieloff/yolo) `curl -fsSL https://raw.githubusercontent.com/trieloff/yolo/main/install.sh | sh`
- [Apple Shortcuts Yolo Shortcut](https://www.icloud.com/shortcuts/32970a55ba5c41538d8168dc48a83dd7) (bind this to `cmd+option+y`, it will broadcast a message to all Ghostty splits)
- [bat](https://github.com/sharkdp/bat) `brew install bat`

## Agent Setup

### Claude code

You can use an existing Claude Code subscription, or buy API credits (you'll need about $20 for dry-runs). Claude will ask you to authenticate upon first launch.

```bash
$ brew install claude-code
$ claude


 ▐▛███▜▌   Claude Code v2.0.32
▝▜█████▛▘  Opus 4.1 · Claude API
  ▘▘ ▝▝    /Users/trieloff/Developer/dev-live-slides

> /model

─────────────────────────────────────────────────────────────────────────────────────
 Select model
 Switch between Claude models. Applies to this session and future Claude Code
 sessions. For other/previous model names, specify with --model.

   1. Default (recommended)   Sonnet 4.5 · Smartest model for daily use
 ❯ 2. Opus                    Legacy: Opus 4.1 · Reaches usage limits faster ✔
   3. Haiku                   Haiku 4.5 · Fastest model for simple tasks

 Enter to confirm · Esc to exit
```

We will use `Opus 4.1` for Claude, as other coding agents will use Sonnet instead.

### Codex

```bash
$ brew install --cask codex
$ codex
╭────────────────────────────────────────────────╮
│ >_ OpenAI Codex (v0.53.0)                      │
│                                                │
│ model:     gpt-5-codex high   /model to change │
│ directory: ~/Developer/dev-live-slides         │
╰────────────────────────────────────────────────╯

  To get started, describe a task or try one of these commands:

  /init - create an AGENTS.md file with instructions for Codex
  /status - show current session configuration
  /approvals - choose what Codex can do without approval
  /model - choose what model and reasoning effort to use
  /review - review any changes and find issues


  Select Reasoning Level for gpt-5-codex

  1. Low               Fastest responses with limited reasoning
  2. Medium (default)  Dynamically adjusts reasoning based on the task
› 3. High (current)    Maximizes reasoning depth for complex or ambiguous problems
                       ⚠ High reasoning effort can quickly consume Plus plan rate
                       limits.

  Press enter to confirm or esc to go back

We use gpt-5-codex with high reasoning effort, as it is the only model that outcompetes Sonnet (albeit with a higher cost and slower reasoning).
```

### Gemini

```bash
$ brew install gemini-cli
$ nano -w ~/.gemini/settings.json
# add { "contextFileName": "AGENTS.md" }
$ gemini
```

You can use Gemini for free (within limits) if you have a Google account.

### GitHub Copilot

You can buy a Copilot subscription from GitHub for $20.

```bash
$ npm install -g @github/copilot
$ copilot
Copilot can write, test and debug code right from your terminal. Describe a task to
 get started or enter ? for help. Copilot uses AI, check for mistakes.

● Logged in with gh as user: trieloff

● Connected to GitHub MCP Server

~/Developer/dev-live-slides[⎇ main*]                      claude-haiku-4.5 (0.33x)
───────────────────────────────────────────────────────────────────────────────────
> /model claude-haiku-4.5
───────────────────────────────────────────────────────────────────────────────────
Ctrl+c Exit · Ctrl+r Expand recent
```

We are running Copilot with Claude Haiku 4.5, so that we get more variation.

### Cursor Agent (CLI)

You probably have an Adobe-sponsored Cursor Agent license, if not, the smallest plan is $20/month.

```bash
$ curl https://cursor.com/install -fsS | bash
$ cursor-agent

  Cursor Agent
  ~/Developer/dev-live-slides · main
 │ → /mode                                                                         │
 │ → /model composer-1                                                             │
 └─────────────────────────────────────────────────────────────────────────────────┘
 → /model composer-1  Composer 1
```

Composer 1 is Cursor's own model, likely based on GLM-4.6.

### Opencode

We use [Opencode Zen](https://opencode.ai/docs/zen/), which is the best tested open provider for OpenCode. Create an account, buy some credits. Minimum amount.

```bash
$ brew install opencode
$ opencode auth login
(select Opencode Zen, then paste your API key)
$ opencode
/models
```

Type `/models` and select Grok Code Fast 1, which is currently free.

### Qwen Coder

Qwen has a free account. Select Qwen as the provider upon first login.

```bash
$ npm install -g @qwen-code/qwen-code@latest
$ qwen
```

We use the default model.

### Aside: groq.com

Log in at [Groq Console](https://console.groq.com/home) and create an API key. You need to fund the account. $20 should be enough.

### Kimi-CLI

```bash
$ brew install kimi-cli
$ nano -w ~/.kimi/config.json
{
  "default_model": "groq-kimi",
  "models": {
    "groq-kimi": {
      "provider": "groq",
      "model": "moonshotai/kimi-k2-instruct-0905",
      "max_context_size": 131072
    }
  },
  "providers": {
    "groq": {
      "type": "openai_legacy",
      "base_url": "https://api.groq.com/openai/v1",
      "api_key": "<YOUR KEY HERE>",
      "custom_headers": {}
    }
  },
  "loop_control": {
    "max_steps_per_run": 100,
    "max_retries_per_step": 3
  },
  "services": {}
}
$ kimi
```

### Crush

For Crush, I am using the [GLM Coding Lite plan](https://z.ai/subscribe) at $9 per quarter.

```bash
$ brew install charmbracelet/tap/crush
$ crush
ctrl-p, Switch Model, Z.AI, GLM-4.6
```

Get your API Key from [Z.AI Console](https://z.ai/manage-apikey/apikey-list)

# On Presentation Day

Open two terminal windows, in the first one, run the presentation. Fiddle with the font size (`command+plus` or `command+minus`) until the presentation is readable.

```bash
# pre-cache the copresenter answers
$ ./copresenter --prepare
# show the presentation
$ ./bin/presenterm -x slides.md
```

In the second one, reduce the font size (`command+minus`) as you will have a number of splits running at the same time.

```bash
# launch all splits, one agent per split
$ yolo -a
```

Then press `cmd+option+y` to broadcast a message to all Ghostty splits.

## Prompts for Demo

### Blog Archive

```markdown
The blog under /blog currently lists only the most recent post and shows excepts for
the five most recent posts. As the list of blog posts has grown, we now need a proper
blog archive page that is grouped by year and month and lists posts.

I'd like to see a card for each post in the archive, including
- Title
- Date
- Author
- Hero Image
- One or two sentences

Do not attempt to change the index configuration, and instead use the existing index. If you need additional data, let the component fetch the blog post HTML, and parse it using the DOMParser API.

AEM has predictable HTML structure, so building that kind of parser is straightforward.

Analyze the project and the content of the live website to understand the code and content structure, then develop a plan to implement
this blog archive, and put it into action. Create descriptive commit messages for each
step along the way and finish by creating a PR.

Once you are done, open a new PR using gh CLI, and clearly identify yourself (tool and model) and add the ai-generated label to the PR
```

### Light/Dark Mode

```markdown
Use the light-dark() CSS color function to enable an automatic toggle between light and dark mode based on the user's system settings.

Watch out for following issues:
- use Adobe's spectrum colors
- make sure that colors in all blocks are light/dark enabled, we don't want single blocks to stick out
- some blocks like the hero block have background images, and using white text will not work well there
- ensure there is sufficient contrast between text and background, especially for image backgrounds

Analyze the project and the content of the live website to understand the code and content structure, then develop a plan to implement
this bug fix, and put it into action. Create descriptive commit messages for each
step along the way and finish by creating a PR.

Once you are done, open a new PR using gh CLI, and clearly identify yourself (tool and model) and add the ai-generated label to the PR. Provide plenty of test links, so that different parts of the site, with different blocks can be evaluated.
```

### Search Return Keypress Bug

```markdown
I've found a bug in the search functionality. When I enter search terms, multiple results are shown as cards. Pressing enter/return will open a page, but it is not the first result (which could be expected behavior), but the very last result.

Analyze the project and the content of the live website to understand the code and content structure, then develop a plan to implement
this bug fix, and put it into action. Create descriptive commit messages for each
step along the way and finish by creating a PR.

Once you are done, open a new PR using gh CLI, and clearly identify yourself (tool and model) and add the ai-generated label to the PR.
```

### Break a leg!
