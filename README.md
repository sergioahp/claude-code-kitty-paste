# 📋⚡ claude-code-kitty-paste

> :rocket: **Blazingly safe** clipboard handling for Claude Code CLI and Kitty terminal warriors

> :warning: **Disclaimer**: This project is not affiliated with Anthropic or Claude Code CLI. It's a community tool inspired by Claude Code's clipboard functionality.

[![Made with Bash](https://img.shields.io/badge/Made%20with-Bash-1f425f.svg)](https://www.gnu.org/software/bash/)
[![Powered by Kitty](https://img.shields.io/badge/Powered%20by-Kitty-ff6b35.svg)](https://sw.kovidgoyal.net/kitty/)
[![Wayland Ready](https://img.shields.io/badge/Wayland-Ready-blue.svg)](https://wayland.freedesktop.org/)
[![Zero Config](https://img.shields.io/badge/Zero-Config-brightgreen.svg)](#)

## 🔥 What is this sorcery?

**claude-code-kitty-paste** is a :zap: **lightning-fast** hybrid clipboard injector designed to paste images seamlessly into **Claude Code CLI** on **Linux systems**. It works on both **Wayland** and **X11** environments, bringing your clipboard content directly into your Kitty terminal with **enterprise-grade safety** and **zero configuration**.

> :information_source: **macOS users**: You don't need this script! macOS terminals already have built-in image paste support. Just use `Cmd+Ctrl+Shift+4` for screenshots and `Ctrl+V` (not `Cmd+V`) to paste images into Claude Code CLI.

### :sparkles: **The Magic**

- :framed_picture: **Images** → Instantly saved as temp files with paths injected
- :memo: **Text** → Delegated to Kitty's built-in paste with military-grade safety
- :shield: **Control codes?** → Neutralized before they can execute
- :warning: **Malicious payloads?** → Blocked by Kitty's advanced filtering
- :globe_with_meridians: **URLs?** → Auto-quoted when pasted at shell prompts

## :pray: Credits & Inspiration

This tool is built upon the community solutions from [GitHub Issue #834](https://github.com/anthropics/claude-code/issues/834) and related community contributions:

- **[@SamDc73](https://github.com/SamDc73)** - :bulb: Original Linux/Wayland/Kitty script implementation (May 2025)
- **[@lockmeister](https://github.com/lockmeister)** - :point_up: Original issue reporter who identified the clipboard challenge
- **[@Stewart86](https://github.com/Stewart86)** - :desktop_computer: Terminal compatibility insights  
- **[Shukebeta Blog Author](https://blog.shukebeta.com/)** - :memo: Independent [Linux terminal solution](https://blog.shukebeta.com/2025/07/11/quick-fix-claude-code-image-paste-in-linux-terminal/) and documentation (July 2025)

We've enhanced the original concept with:

- :shield: **Enhanced security** via `socket-only` remote control
- :gear: **Hybrid approach** leveraging Kitty's built-in paste safety  
- :sparkles: **Polish and documentation** for the community

Special thanks to the entire community for collaborating on this solution! :clap:

## :rocket: Features That Will Blow Your Mind

- **:zap: Blazing Performance**: Near-zero latency clipboard detection
- **:shield: Fort Knox Security**: Leverages Kitty's enterprise clipboard safety
- **:framed_picture: Smart Image Handling**: PNG, JPEG, SVG → instant file paths
- **:gear: Zero Configuration**: Works out of the box with Kitty remote control
- **:ocean: Cross-Platform**: Native support for both Wayland and X11 environments
- **:crystal_ball: Intelligent Detection**: Knows exactly what's in your clipboard

## :fire: Installation

### Step 1: Script Setup

```bash
# Place the script anywhere you like (doesn't need to be in kitty config)
curl -o ~/bin/clip2path https://raw.githubusercontent.com/your-repo/claude-code-kitty-paste/main/clip2path
chmod +x ~/bin/clip2path

# Or clone and symlink
git clone https://github.com/your-repo/claude-code-kitty-paste.git
ln -s $(pwd)/claude-code-kitty-paste/clip2path ~/bin/clip2path
```

### Step 2: Kitty Configuration

Add these **game-changing** lines to your `kitty.conf`:

```conf
# :shield: Enable socket-only remote control (SECURE!)
allow_remote_control socket-only

# :rocket: The future of clipboard handling  
map ctrl+v launch --type=background --allow-remote-control --keep-focus ~/bin/clip2path
```

> :warning: **Security Note**: We use `socket-only` instead of `yes` for maximum security!

## :zap: Usage

**It just works.** The script auto-detects your environment (Wayland/X11) and uses the appropriate clipboard tool. Copy anything, hit `Ctrl+V`, and watch the magic happen:

### :framed_picture: Images
```bash
# Screenshot copied → Instant file path pasted
/tmp/clip2path_Ac3X9k.png

# Claude Code CLI automatically detects and loads the image
# You'll see [Image #1] appear in your text entry box
# Now Claude can analyze, discuss, or help with the image!
```

> :magic_wand: **Claude Code Magic**: Once the image path is pasted, it displays as `[Image #1]` in your text input. Claude can read the image when asked or when the intention is clear - perfect for analyzing screenshots, explaining code in images, or getting help with visual content!

### :memo: Text & URLs
```bash
# Text copied → Safe paste with Kitty's protection
echo "Hello, World!"

# URLs → Auto-quoted at shell prompts
'https://github.com/your-amazing-repo'

# Text pasting uses Kitty's built-in safety features
# - Control code filtering prevents malicious payloads
# - Large paste warnings for 16KB+ content
# - URL auto-quoting at shell prompts
```

## :gear: Advanced Configuration

### :fire: Environment Variables

```bash
# Custom temp directory for images
export CLIP2PATH_TMPDIR="/your/custom/path"

# Enable debug mode for the full experience
export CLIP2PATH_DEBUG=1
```

### :shield: Security Features

- **Control Code Filtering**: Malicious terminal sequences = :no_entry_sign:
- **Large Paste Protection**: 16KB+ content gets confirmation prompts
- **URL Auto-Quoting**: Shell injection protection for URLs
- **Remote Control Security**: Uses Kitty's secure socket communication

## :construction_worker: Requirements

- **Kitty Terminal** (with `allow_remote_control socket-only`)
- **Display Server**: Wayland or X11
- **Clipboard Tools**:
  - **Wayland**: `wl-clipboard` (`wl-paste`)
  - **X11**: `xclip` or `xsel` (prefers xclip)
- **Bash** 4.0+ (script runtime only - your shell can be zsh, fish, etc.)

## :computer: Compatibility

| Feature | Wayland | X11 | Notes |
|---------|---------|-----|-------|
| :framed_picture: PNG Images | :white_check_mark: | :white_check_mark: | Perfect quality preservation |
| :framed_picture: JPEG Images | :white_check_mark: | :white_check_mark: | Maintains original compression |
| :framed_picture: SVG Images | :white_check_mark: | :white_check_mark: | Vector graphics ready |
| :memo: Plain Text | :white_check_mark: | :white_check_mark: | With Kitty safety features |
| :link: URLs | :white_check_mark: | :white_check_mark: | Auto-quoted at shell prompts |
| :file_folder: File Lists | :construction: | :construction: | Coming soon™ |

## :building_construction: Architecture

```
┌─────────────────────┐    ┌──────────────┐    ┌─────────────────┐
│     Clipboard       │───▶│  clip2path   │───▶│  Kitty Terminal │
│  (Wayland/X11)     │    │   (Hybrid)   │    │   (Secure)      │
└─────────────────────┘    └──────────────┘    └─────────────────┘
            │                      │                      │
       ┌────▼────┐          ┌─────▼─────┐          ┌─────▼─────┐
       │ wl-paste │          │   Route   │          │   Paste   │
       │   xclip   │          │  & Save   │          │  & Filter │
       │   xsel    │          │ Images   │          │   Text    │
       └─────────┘          └───────────┘          └───────────┘
```

## :handshake: Contributing

We welcome contributions that make this tool even more :fire: **blazingly awesome**!

### :pray: Hall of Fame
- **[@SamDc73](https://github.com/SamDc73)** - :bulb: Original Linux/Wayland/Kitty script implementation (May 2025)
- **[@lockmeister](https://github.com/lockmeister)** - :point_up: Identified the Linux clipboard pasting challenge  
- **[@Stewart86](https://github.com/Stewart86)** - :desktop_computer: Terminal compatibility expert
- **[Shukebeta Blog Author](https://blog.shukebeta.com/)** - :memo: Independent documentation and solution (July 2025)
- **[Claude (Anthropic)](https://claude.ai)** - :robot: Code enhancement, security improvements, and documentation
- Clipboard safety pioneers
- Wayland evangelists  
- Terminal productivity maximalists
- Security-first developers

## :scroll: License

MIT - Because sharing is caring and freedom is :rocket: **blazing**

## :warning: Disclaimer

This tool is so efficient it might spoil you for other clipboard managers. Use responsibly.

---

<div align="center">

**Made with :heart: and excessive amounts of :coffee:**

*Bringing the future of clipboard handling to your terminal, one paste at a time*

</div>