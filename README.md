# 📋⚡ clip2path

> :rocket: **Blazingly safe** clipboard handling for Kitty terminal warriors

[![Made with Bash](https://img.shields.io/badge/Made%20with-Bash-1f425f.svg)](https://www.gnu.org/software/bash/)
[![Powered by Kitty](https://img.shields.io/badge/Powered%20by-Kitty-ff6b35.svg)](https://sw.kovidgoyal.net/kitty/)
[![Wayland Ready](https://img.shields.io/badge/Wayland-Ready-blue.svg)](https://wayland.freedesktop.org/)
[![Zero Config](https://img.shields.io/badge/Zero-Config-brightgreen.svg)](#)

## 🔥 What is this sorcery?

**clip2path** is a :zap: **lightning-fast** hybrid clipboard injector designed to paste images seamlessly into **Claude Code CLI** and other terminal applications. It brings your clipboard content directly into your Kitty terminal with **enterprise-grade safety** and **zero configuration**.

### :sparkles: **The Magic**

- :framed_picture: **Images** → Instantly saved as temp files with paths injected
- :memo: **Text** → Delegated to Kitty's built-in paste with military-grade safety
- :shield: **Control codes?** → Neutralized before they can execute
- :warning: **Malicious payloads?** → Blocked by Kitty's advanced filtering
- :globe_with_meridians: **URLs?** → Auto-quoted when pasted at shell prompts

## :rocket: Features That Will Blow Your Mind

- **:zap: Blazing Performance**: Near-zero latency clipboard detection
- **:shield: Fort Knox Security**: Leverages Kitty's enterprise clipboard safety
- **:framed_picture: Smart Image Handling**: PNG, JPEG, SVG → instant file paths
- **:gear: Zero Configuration**: Works out of the box with Kitty remote control
- **:ocean: Wayland Native**: Built for the future of Linux desktop
- **:crystal_ball: Intelligent Detection**: Knows exactly what's in your clipboard

## :fire: Installation

### The One-Liner That Changes Everything

```bash
# Place the script in your Kitty config
chmod +x ~/.config/kitty/clip2path
```

### Kitty Configuration

Add this **game-changing** line to your `kitty.conf`:

```conf
# :rocket: The future of clipboard handling
map ctrl+v launch --type=background --allow-remote-control --keep-focus ~/.config/kitty/clip2path
```

## :zap: Usage

**It just works.** Copy anything, hit `Ctrl+V`, and watch the magic happen:

### :framed_picture: Images
```bash
# Screenshot copied → Instant file path
/tmp/clip2path_Ac3X9k.png

# Ready to use in any command
eog '/tmp/clip2path_Ac3X9k.png'
```

### :memo: Text & URLs
```bash
# Text copied → Safe paste with Kitty's protection
echo "Hello, World!"

# URLs → Auto-quoted at shell prompts
'https://github.com/your-amazing-repo'
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

- **Kitty Terminal** (with `allow_remote_control`)
- **Wayland** (because we live in 2024)
- **wl-clipboard** (`wl-paste`)
- **Bash** 4.0+ (for the advanced parameter expansion magic)

## :computer: Compatibility

| Feature | Support | Notes |
|---------|---------|-------|
| :framed_picture: PNG Images | :white_check_mark: | Perfect quality preservation |
| :framed_picture: JPEG Images | :white_check_mark: | Maintains original compression |
| :framed_picture: SVG Images | :white_check_mark: | Vector graphics ready |
| :memo: Plain Text | :white_check_mark: | With Kitty safety features |
| :link: URLs | :white_check_mark: | Auto-quoted at shell prompts |
| :file_folder: File Lists | :construction: | Coming soon™ |

## :building_construction: Architecture

```
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│   Clipboard     │───▶│  clip2path   │───▶│  Kitty Terminal │
│   (Wayland)     │    │   (Hybrid)   │    │   (Secure)      │
└─────────────────┘    └──────────────┘    └─────────────────┘
         │                      │                      │
    ┌────▼────┐          ┌─────▼─────┐          ┌─────▼─────┐
    │ Images  │          │   Route   │          │   Paste   │
    │ Text    │          │  & Save   │          │  & Filter │
    │ URLs    │          │           │          │           │
    └─────────┘          └───────────┘          └───────────┘
```

## :handshake: Contributing

We welcome contributions that make this tool even more :fire: **blazingly awesome**!

### :pray: Hall of Fame
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