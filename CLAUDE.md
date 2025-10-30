# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a presentation repository for "Coding Agent Showdown: The Good, the Bad, and the Ugly" - a live demo presentation about AI coding agents. The presentation uses **presenterm**, a terminal-based presentation tool that renders Markdown with extended features for live demos, ASCII art, and animations.

## File Structure

- `slides.md` - Main presentation file containing all slides in Markdown format with YAML frontmatter
- `*.cast` - Asciinema recordings (JSON format) that capture terminal sessions for embedding in slides

## Running the Presentation

```bash
# Standard presenterm (if installed)
presenterm slides.md

# With code execution enabled (allows +exec blocks to run)
presenterm -x slides.md

# With auto-reload (for editing)
presenterm --watch slides.md
```

## Presenterm Slide Structure

### Basic Syntax

Presenterm uses standard Markdown with slides separated by slide delimiters. Use either:
- `---` when `end_slide_shorthand: true` is set in frontmatter options
- `<!-- end_slide -->` as the standard delimiter

### Frontmatter

Every presentation starts with YAML frontmatter:

```yaml
---
title: Presentation Title
sub_title: Optional Subtitle
author: Your Name (@handle)
theme:
  name: dark
options:
  end_slide_shorthand: true  # Allows using --- as slide delimiter
---
```

### HTML Comment Commands

Presenterm supports HTML comment commands to control presentation behavior:

- `<!-- pause -->` - Pause before showing next content (creates builds)
- `<!-- incremental_lists: true -->` - Show list items one at a time
- `<!-- jump_to_middle -->` - Vertically center content on slide
- `<!-- column_layout: [3, 2] -->` - Create column layout with proportional widths
- `<!-- column: 0 -->` - Switch to specific column
- `<!-- reset_layout -->` - Exit column mode
- `<!-- alignment: center -->` - Set text alignment (left/center/right)
- `<!-- font_size: 2 -->` - Adjust font size (1-7 scale)
- `<!-- no_footer -->` - Hide footer on this slide
- `<!-- speaker_note: Your note here -->` - Add presenter notes

## Code Highlighting & Execution

### Syntax Highlighting

Presenterm supports 70+ languages with syntax highlighting:

```markdown
# Basic highlighting
```python
def hello():
    print("Hello World")
```

# With line numbers
```python +line_numbers
def hello():
    print("Hello World")
```

# Highlight specific lines (static)
```python {1,3,5-7}
line 1  # highlighted
line 2
line 3  # highlighted
```

# Dynamic highlighting (changes on advance)
```python {1,3|5-7}
# First view: lines 1,3 highlighted
# Second view: lines 5-7 highlighted
```
```

### Code Execution

Code blocks can execute live during presentations:

```markdown
# Execute on demand (Ctrl+E during presentation)
```bash +exec
echo "Hello from live code!"
```

# Execute and replace with output automatically
# Requires -X flag: presenterm -X slides.md
```bash +exec_replace
date
```

# Execute with terminal access (for interactive programs)
```python +exec +acquire_terminal
input("Press enter: ")
```
```

**Important**: Code execution requires the `-x` flag for `+exec` or `-X` flag for `+exec_replace`

## Custom Features: Banners & ASCII Art

This presentation uses a **custom build of presenterm** with additional features for ASCII art. These features are available in `../presentation/presenterm`.

### Banner Blocks (FIGlet ASCII Art)

Banners convert text into large ASCII art using FIGlet fonts:

```markdown
# Default font, static rainbow coloring
```banner
HELLO
```

# Specific font
```banner:slant
SLANTED
```

```banner:big
BIG TEXT
```

# Available fonts include: standard, slant, big, block, epic, doom, and more
# Install figlet for more fonts: brew install figlet (macOS) or apt install figlet (Linux)
```

### Banner Animation Styles

Banners support 17+ animation styles:

```markdown
# Static (default - no animation)
```banner
STATIC
```

# Animated once
```banner +once
ONCE
```

# Looping animation (continues forever)
```banner +loop
LOOP
```

# Specific animation styles
```banner +animate:rainbow +loop
RAINBOW
```

```banner +animate:wave
WAVE
```

```banner +animate:fire
FIRE
```

```banner +animate:matrix
MATRIX
```
```

**Available animation styles**: rainbow, flash, wave, iris, neon, matrix, plasma, fire, glitch, sepia, breathe, kaleidoscope, scanner, prism, aurora, crt, typewriter

### Multi-line Banners (Builds)

Multi-line banners create builds where each line replaces the previous:

```markdown
```banner
FIRST
SECOND
THIRD
```

# Behavior:
# - Initial view: Shows "FIRST" in ASCII art
# - Advance once: Screen clears, shows "SECOND" (FIRST disappears)
# - Advance again: Screen clears, shows "THIRD" (SECOND disappears)
```

### ASCII Art Blocks

For custom ASCII art that shouldn't be processed by FIGlet:

```markdown
# Static ASCII art (verbatim, centered)
```ascii
┌──────────────────┐
│  Architecture    │
└──────────────────┘
```

# With animation
```ascii +animate:wave
  /\   /\
 (  \_/  )
  >  _  <
```
```

ASCII blocks render content verbatim (no FIGlet processing) and center it on the slide. They support the same animation styles as banners.

## Images & Diagrams

### Images

Presenterm supports images via terminal graphics protocols (iterm2, kitty, sixel):

```markdown
![](path/to/image.png)

# With size control
![image:width:50%](image.png)
```

Images scale to preserve aspect ratio and won't overflow terminal bounds.

### D2 Diagrams

Create diagrams using D2 (requires `d2` to be installed):

```markdown
```d2 +render
server -> database: query
database -> server: results
```

# With scaling
```d2 +render +width:80%
architecture: {
  shape: rectangle
}
```
```

## Layouts

### Column Layouts

Create multi-column slides:

```markdown
<!-- column_layout: [3, 2] -->
<!-- column: 0 -->
This content appears in the left column (60% width)

<!-- column: 1 -->
This content appears in the right column (40% width)

<!-- reset_layout -->
Back to full width content
```

### Centering Content

```markdown
<!-- jump_to_middle -->
This content will be vertically centered on the slide
```

## Navigation

During presentation:
- **Space** / **→** / **l** - Next slide
- **←** / **h** - Previous slide
- **j** / **k** - Next/previous slide (vim-style)
- **gg** - Jump to first slide
- **G** - Jump to last slide
- **<number>G** - Jump to specific slide
- **Ctrl+P** - Open slide index modal
- **Ctrl+E** - Execute code in current block
- **?** - Show all keybindings
- **Ctrl+C** / **q** - Quit

## Content Guidelines

The presentation covers:
- AI agent capabilities progression (autocomplete → chat → IDE agents → CLI agents → cloud agents)
- Claude Code architecture (local tools + cloud model + MCP servers)
- Advanced features like AGENTS.md, SKILLS.md, and safety guardrails
- Practical demonstrations of agent-driven development

When adding new slides:
- Maintain the progression from basic concepts to advanced features
- Use banners for section headers and key concepts
- Use ASCII art for architecture diagrams
- Use `+exec` blocks sparingly and only for safe, quick commands
- Test live code execution before presenting
- Keep slide content focused (prefer multiple slides over dense content)
