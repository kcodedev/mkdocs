# FZF - Command-Line Fuzzy Finder

## Overview

FZF (Fuzzy Finder) is an interactive command-line filter that reads a list of items from stdin and allows you to select items using fuzzy matching. It's a powerful tool for enhancing command-line workflows with interactive selection capabilities.

## Features

- **Fuzzy Matching**: Find items even with partial or incorrect input
- **Interactive Selection**: Real-time filtering as you type
- **Multiple Selection**: Select multiple items with tab/shift-tab
- **Preview Window**: Preview file contents or command output
- **Scriptable**: Easy integration with shell scripts and other tools
- **Customizable**: Extensive configuration options
- **Fast Performance**: Optimized for speed with large datasets

## Basic Usage

### Interactive Selection

```bash
# Basic usage - select from a list
echo -e "apple\nbanana\norange\npear" | fzf

# Select from command history
history | fzf

# Select from files in current directory
find . -type f | fzf

# Select from processes
ps aux | fzf
```

### Key Bindings

- **Enter**: Confirm selection
- **Ctrl-C / Esc**: Cancel
- **Tab / Shift-Tab**: Toggle selection (multi-select mode)
- **Ctrl-K / Ctrl-J**: Move cursor up/down
- **Ctrl-Q**: Select all items
- **Alt-Enter**: Toggle preview window

## Integration with Shell

### Bash Integration

Add to `~/.bashrc`:

```bash
# Use fd instead of find for faster file search
export FZF_DEFAULT_COMMAND='fd --type f'

# Use ripgrep for faster content search
export FZF_DEFAULT_OPTS='--bind ctrl-k:kill-line'

# Custom key bindings
source /usr/share/fzf/key-bindings.bash
source /usr/share/fzf/completion.bash
```

### Zsh Integration

Add to `~/.zshrc`:

```zsh
# Enable fzf completion and key bindings
source /usr/share/fzf/key-bindings.zsh
source /usr/share/fzf/completion.zsh

# Custom options
export FZF_COMPLETION_OPTS='--border --info=inline'
```

## Advanced Usage

### File and Directory Search

```bash
# Find files with preview
fzf --preview 'cat {}' --preview-window right:60%

# Find directories only
find . -type d | fzf

# Find files with specific extension
find . -name "*.md" | fzf

# Find files and open with editor
find . -type f | fzf --bind "enter:execute(nvim {})"
```

### Process Management

```bash
# Kill process interactively
ps aux | fzf --bind "enter:execute(kill {2})"

# Kill multiple processes
ps aux | fzf --multi --bind "enter:execute(kill {+2})"
```

### Git Integration

```bash
# Select files to add to git
git status --short | fzf --multi --preview 'git diff {2}' | cut -c4- | tr '\n' ' ' | xargs git add

# Select commits to cherry-pick
git log --oneline | fzf --multi --preview 'git show {1}' | cut -d' ' -f1 | xargs git cherry-pick

# Interactive branch switching
git branch | fzf --preview 'git log {1} --oneline -10' | xargs git checkout
```

### Command History Search

```bash
# Search through command history
fzf-history() {
    local cmd
    cmd=$(history | fzf --tac | cut -d' ' -f4-)
    echo "$cmd"
    eval "$cmd"
}

# Bind to Ctrl-R
bind '"\C-r": "\C-e \C-u\C-y\ey\C-u`fzf-history`\e\C-e\er"'
```

## Configuration

### Environment Variables

```bash
# Default command for finding files
export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'

# Default options
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border --inline-info'

# Ctrl-T options (file selection)
export FZF_CTRL_T_OPTS='--preview "bat --color=always --style=numbers --line-range=:500 {}"'

# Alt-C options (directory selection)
export FZF_ALT_C_OPTS='--preview "tree -C {} | head -50"'
```

### Configuration File

Create `~/.fzf/config`:

```bash
# FZF Configuration File
--height 40%
--layout=reverse
--border
--inline-info
--preview '([[ -f {} ]] && (bat --style=numbers --color=always {} || cat {})) || ([[ -d {} ]] && (tree -C {} | less)) || echo {} 2> /dev/null | head -200'
--preview-window 'right:60%:wrap'
--bind 'ctrl-/:toggle-preview'
--bind 'ctrl-y:execute-silent(echo -n {2..} | pbcopy)+abort'
--color 'fg:#bbccdd,fg+:#ddeeff,bg:#334455,preview-bg:#223344,border:#778899'
```

## Custom Scripts and Functions

### Enhanced File Search

```bash
# Search files with ripgrep and open in editor
frg() {
    local file
    file=$(fzf --preview 'bat --style=numbers --color=always {}' --preview-window 'right:60%' --bind 'enter:execute(nvim {1} +{2})' < <(rg --line-number --no-heading --color=never '' .))
    [[ -n "$file" ]] && nvim "$file"
}
```

### Interactive Directory Navigation

```bash
# Navigate directories with fzf
fcd() {
    local dir
    dir=$(find . -type d | fzf --preview 'tree -C {} | head -50')
    cd "$dir"
}
```

### Package Management

```bash
# Search and install packages (Ubuntu/Debian)
fapt() {
    local pkg
    pkg=$(apt-cache search . | fzf --preview 'apt-cache show {1}' | cut -d' ' -f1)
    [[ -n "$pkg" ]] && sudo apt install "$pkg"
}
```

## Integration with Other Tools

### Integration with Zoxide

```bash
# Jump to directory with fzf selection
fz() {
    local dir
    dir=$(zoxide query -l | fzf --preview 'tree -C {} | head -50')
    cd "$dir"
}
```

### Integration with Yazi

```bash
# Use fzf to select files and open in yazi
fy() {
    local files
    files=$(find . -type f | fzf --multi --preview 'bat --color=always {}')
    [[ -n "$files" ]] && yazi $files
}
```

### Integration with Tmux

```bash
# Switch tmux sessions with fzf
ftms() {
    local session
    session=$(tmux list-sessions | fzf | cut -d: -f1)
    tmux switch-client -t "$session"
}
```

## Tips and Tricks

### Performance Optimization

1. **Use `fd` instead of `find`**: Much faster file searching
2. **Use `ripgrep` instead of `grep`**: Faster text searching
3. **Limit search scope**: Use `--max-depth` for large directories
4. **Use preview caching**: Enable preview caching for better performance

### Custom Key Bindings

```bash
# In bashrc/zshrc
# Ctrl-T: Paste selected file path(s)
bind '"\C-t": "$(__fzf_select__)\e\C-e\er"'

# Alt-C: cd to selected directory
bind '"\M-c": "$(__fzf_cd__)\e\C-e\er"'
```

### Workflow Enhancements

- **Use with `bat`**: Better file previews with syntax highlighting
- **Combine with `tree`**: Better directory structure visualization
- **Use with `delta`**: Enhanced git diff previews
- **Integrate with editors**: Quick file opening in vim/nvim/emacs

## Troubleshooting

### Common Issues

1. **No preview window**: Install `bat` for better previews
2. **Slow performance**: Use `fd` and `ripgrep` instead of `find` and `grep`
3. **Key bindings not working**: Ensure proper shell integration
4. **Unicode issues**: Set proper locale settings

### Performance Tuning

```bash
# Use faster alternatives
export FZF_DEFAULT_COMMAND='fd --type f'
export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"

# Optimize for large codebases
export FZF_DEFAULT_OPTS='--height 40% --reverse --bind ctrl-k:kill-line'
```

## See Also

- [Official FZF Repository](https://github.com/junegunn/fzf)
- [FZF Wiki](https://github.com/junegunn/fzf/wiki)
- [FZF Vim Plugin](https://github.com/junegunn/fzf.vim)
- [FD (Find Alternative)](https://github.com/sharkdp/fd)
- [Ripgrep (Grep Alternative)](https://github.com/BurntSushi/ripgrep)
- [Bat (Cat Alternative)](https://github.com/sharkdp/bat)