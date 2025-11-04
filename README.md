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

### Break a leg!
