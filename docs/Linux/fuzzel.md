# Fuzzel - Wayland Application Launcher

## Overview

Fuzzel is a fast, Wayland-native application launcher similar to `dmenu` but designed specifically for Wayland compositors using the `wlr-layer-shell` protocol. It provides a clean, efficient interface for launching applications and running commands.

## Features

- **Wayland Native**: Built specifically for Wayland compositors
- **Fast Performance**: Written in C for optimal speed
- **Fuzzy Matching**: Intelligent application and command matching
- **Customizable Interface**: Extensive theming and configuration options
- **Layer Shell Support**: Proper integration with wlroots compositors
- **Keyboard Driven**: Efficient keyboard-only navigation
- **Multiple Modes**: Application launcher and general command runner

## Basic Usage

### Launching Applications

```bash
# Launch fuzzel as application launcher
fuzzel

# Launch with custom prompt
fuzzel -p "Launch: "

# Show only desktop applications
fuzzel --show-actions=no
```

### Command Mode

```bash
# Run fuzzel in command mode (like dmenu)
echo | fuzzel -d

# Use with other commands
find . -type f | fuzzel -d
```

### Key Bindings

- **Enter**: Launch selected application/execute command
- **Ctrl+C / Esc**: Exit fuzzel
- **Tab**: Navigate through results
- **Ctrl+J / Ctrl+K**: Move up/down in results
- **Ctrl+U / Ctrl+D**: Page up/down

## Configuration

### Configuration File

Create `~/.config/fuzzel/fuzzel.ini`:

```ini
# Fuzzel Configuration
[main]
font=monospace:size=12
icon-theme=Papirus-Dark
dpi-aware=yes

[colors]
background=1e1e2eff
text=cdd6f4ff
match=89b4faff
selection=313244ff
selection-text=89b4faff
selection-match=89b4faff
border=89b4faff

[border]
width=2
radius=8

[key-bindings]
cancel=Control+c Escape
execute=Return KP_Enter
cursor-up=Up Control+k Control+p
cursor-down=Down Control+j Control+n
cursor-home=Home Control+a
cursor-end=End Control+e
delete-line-left=Control+u
delete-line-right=Control+k
```

### Theming

#### Dark Theme Example

```ini
[colors]
background=1a1b26ff
text=c0caf5ff
match=7aa2f7ff
selection=283457ff
selection-text=7aa2f7ff
selection-match=7aa2f7ff
border=7aa2f7ff
```

#### Light Theme Example

```ini
[colors]
background=f8f8f2ff
text=282a36ff
match=bd93f9ff
selection=6272a4ff
selection-text=bd93f9ff
selection-match=bd93f9ff
border=bd93f9ff
```

## Advanced Usage

### Desktop Integration

#### Desktop File Scanning

Fuzzel automatically scans standard desktop file locations:

```bash
# Standard locations checked:
/usr/share/applications/
/usr/local/share/applications/
~/.local/share/applications/
```

#### Custom Desktop Files

```bash
# Create custom desktop file
cat > ~/.local/share/applications/custom-app.desktop << EOF
[Desktop Entry]
Name=Custom Application
Exec=/path/to/custom-app
Icon=custom-icon
Categories=Utility
EOF
```

### Command Line Options

```bash
# Basic options
fuzzel --help                    # Show help
fuzzel --version                 # Show version
fuzzel --list-executables        # List available executables

# Display options
fuzzel --dpi-aware=yes           # Respect screen DPI
fuzzel --font="JetBrains Mono:size=11"  # Set font
fuzzel --icon-theme=Adapta-Nokto  # Set icon theme

# Behavior options
fuzzel --show-actions=no         # Hide desktop actions
fuzzel --fuzzy=yes               # Enable fuzzy matching
fuzzel --password=[CHARACTER]    # Password mode
fuzzel --prompt-separator=" > "   # Set prompt separator

# Layout options
fuzzel --lines=20                # Number of lines
fuzzel --width=30                # Minimum width in characters
fuzzel --horizontal-pad=20       # Horizontal padding
fuzzel --vertical-pad=10         # Vertical padding
fuzzel --inner-pad=5             # Inner padding

# Position options
fuzzel --anchor=top-left         # Anchor position
fuzzel --margin=10               # Margin from screen edge
```

### Integration with Window Managers

#### Sway Integration

Add to your Sway config (`~/.config/sway/config`):

```bash
# Application launcher keybinding
bindsym $mod+d exec fuzzel

# Terminal with fuzzel
bindsym $mod+Return exec $term

# Custom launcher for specific applications
bindsym $mod+Shift+d exec fuzzel --prompt="Run: "
```

#### Hyprland Integration

Add to your Hyprland config (`~/.config/hypr/hyprland.conf`):

```bash
# Application launcher
bind = $mod, D, exec, fuzzel

# Command runner
bind = $mod, Return, exec, $term -e fuzzel -d

# Emoji picker
bind = $mod, E, exec, fuzzel --prompt="Emoji: " --show-actions=no
```

## Custom Scripts

### Application Launcher with Categories

```bash
#!/bin/bash
# launcher.sh - Enhanced application launcher

case $(echo -e "Applications\nCommands\nBookmarks\nRecent" | fuzzel -d -p "Category: ") in
    "Applications")
        fuzzel
        ;;
    "Commands")
        fuzzel -d -p "Command: "
        ;;
    "Bookmarks")
        cat ~/.config/bookmarks.txt | fuzzel -d
        ;;
    "Recent")
        cat ~/.local/share/recently-used.xbel | grep -o 'file://.*' | sed 's|file://||' | fuzzel -d
        ;;
esac
```

### Password Manager Integration

```bash
#!/bin/bash
# password-launcher.sh

PASSWORD=$(echo | fuzzel -d -p "Password: " --password="*")
ENTRY=$(gpg -d ~/.passwords.gpg 2>/dev/null | fuzzel -d)

# Type the password and entry
xdotool type "$PASSWORD"
xdotool key Tab
xdotool type "$ENTRY"
xdotool key Return
```

### Screenshot Tool

```bash
#!/bin/bash
# screenshot-tool.sh

ACTION=$(echo -e "Fullscreen\nSelection\nWindow\nDelay" | fuzzel -d -p "Screenshot: ")

case "$ACTION" in
    "Fullscreen")
        grim ~/Pictures/screenshot-$(date +%Y%m%d-%H%M%S).png
        ;;
    "Selection")
        grim -g "$(slurp)" ~/Pictures/screenshot-$(date +%Y%m%d-%H%M%S).png
        ;;
    "Window")
        grim -g "$(swaymsg -t get_tree | jq -r '.. | select(.focused==true).rect | "\(.x),\(.y) \(.width)x\(.height)"')" ~/Pictures/screenshot-$(date +%Y%m%d-%H%M%S).png
        ;;
    "Delay")
        sleep 3 && grim ~/Pictures/screenshot-$(date +%Y%m%d-%H%M%S).png
        ;;
esac
```

## Tips and Tricks

### Performance Optimization

1. **Icon Theme**: Use lightweight icon themes for faster loading
2. **Cache Management**: Fuzzel caches desktop files for better performance
3. **Fuzzy Matching**: Adjust fuzzy matching settings for your preferences

### Customization Tips

- **Custom Colors**: Use hex color codes for precise color matching
- **Font Selection**: Choose fonts that render well at small sizes
- **Icon Themes**: Test different icon themes for best visual results
- **Key Bindings**: Customize key bindings to match your workflow

### Troubleshooting

#### Common Issues

1. **No Applications Found**: Check desktop file locations and permissions
2. **Display Issues**: Ensure proper Wayland setup and DPI settings
3. **Font Problems**: Verify font installation and configuration
4. **Icon Issues**: Check icon theme installation and configuration

#### Debug Mode

```bash
# Run with debug output
FUZZEL_LOG_LEVEL=debug fuzzel

# Check desktop file parsing
fuzzel --list-executables | head -20
```

## Integration with Other Tools

### Integration with FZF

```bash
# Use fzf for additional filtering
find . -type f | fuzzel -d | xargs fzf | xargs xdg-open
```

### Integration with Zoxide

```bash
# Jump to directory and launch fuzzel there
function fcd() {
    local dir
    dir=$(zoxide query -l | fuzzel -d)
    cd "$dir" || return
    fuzzel
}
```

### Integration with Systemd

```bash
# Create a systemd user service for fuzzel
cat > ~/.config/systemd/user/fuzzel.service << EOF
[Unit]
Description=Fuzzel Application Launcher

[Service]
ExecStart=/usr/bin/fuzzel
Restart=always

[Install]
WantedBy=default.target
EOF

# Enable and start the service
systemctl --user enable fuzzel.service
systemctl --user start fuzzel.service
```

## Comparison with Alternatives

| Feature | Fuzzel | dmenu | rofi | wofi |
|---------|--------|-------|------|------|
| Wayland Native | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Performance | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Theming | ⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Fuzzy Matching | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Desktop Integration | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Configuration | ⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |

## See Also

- [Official Fuzzel Repository](https://git.sr.ht/~scoopta/fuzzel)
- [Fuzzel Documentation](https://man.archlinux.org/man/fuzzel.1)
- [Wayland Compositors](https://wiki.archlinux.org/title/Wayland)
- [Sway Window Manager](https://swaywm.org/)
- [Hyprland Window Manager](https://hyprland.org/)