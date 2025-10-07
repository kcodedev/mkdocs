# Yazi - Modern Terminal File Manager

## Overview

Yazi (Yet Another Zen Index) is a modern, blazingly fast terminal file manager written in Rust. It provides a visually appealing and highly customizable interface for navigating and managing files directly from the terminal.

## Features

- **Fast Performance**: Written in Rust for optimal speed
- **Modern Interface**: Clean, modern UI with image previews
- **Highly Customizable**: Extensive configuration options
- **Plugin System**: Support for custom plugins and scripts
- **Image Previews**: Built-in image preview support
- **Fuzzy Finding**: Integrated fuzzy search capabilities
- **Multiple Tabs**: Support for multiple tabs and panes

## Basic Usage

### Launching Yazi

Simply run `yazi` in your terminal to start the file manager:

```bash
yazi
```

### Navigation

- **Arrow Keys** or **hjkl**: Navigate through files and directories
- **Enter**: Enter directory or open file
- **Backspace**: Go to parent directory
- **Tab**: Switch between panes (if multiple panes are open)

### File Operations

- **y**: Yank (copy) selected files
- **d**: Delete selected files
- **p**: Paste yanked files
- **c**: Create new file/directory
- **r**: Rename selected file/directory
- **/**: Search files
- **n**: Create new file
- **N**: Create new directory

### Visual Modes

- **v**: Enter visual mode for selecting multiple files
- **V**: Enter visual line mode
- **Ctrl+v**: Enter visual block mode

## Configuration

Yazi can be extensively configured through its configuration files located in `~/.config/yazi/`.

### Key Configuration (`keymap.toml`)

```toml
# ~/.config/yazi/keymap.toml
[manager]
keymap = [
    { on = "<C-n>", exec = "plugin smart-new", desc = "Create new file" },
    { on = "<C-t>", exec = "tab_create", desc = "Create new tab" },
]
```

### Theme Configuration (`theme.toml`)

```toml
# ~/.config/yazi/theme.toml
[flavor]
base = "dark"
```

## Plugins

Yazi supports a plugin system for extending functionality:

### Popular Plugins

- **smart-new**: Enhanced file creation
- **git**: Git integration
- **mime**: Better MIME type handling
- **video**: Video thumbnail generation

### Installing Plugins

Plugins are typically installed through package managers or manually placed in the appropriate directories.

## Tips and Tricks

### Quick Navigation

- Use bookmarks to quickly jump to frequently accessed directories
- Utilize the jump feature to navigate to recently visited locations
- Take advantage of the integrated fuzzy finder for quick file searching

### Customization

- Customize keybindings to match your workflow
- Modify themes to suit your visual preferences
- Create custom scripts for frequently performed tasks

### Integration

Yazi works well with other command-line tools:
- Use with `zoxide` for intelligent directory jumping
- Integrate with `fzf` for enhanced searching
- Combine with `tmux` for advanced terminal workflows

## Troubleshooting

### Common Issues

1. **Display Issues**: Ensure your terminal supports modern features
2. **Performance**: For large directories, consider using filters or search
3. **Plugin Issues**: Check plugin compatibility and installation

### Getting Help

- Run `yazi --help` for command-line options
- Check the official documentation for detailed guides
- Join the community for support and discussions

## See Also

- [Official Yazi Repository](https://github.com/sxyazi/yazi)
- [Yazi Documentation](https://yazi-rs.github.io/)
- [Community Plugins](https://github.com/yazi-rs/plugins)