# Zoxide - Smart Directory Navigation

## Overview

Zoxide is a blazingly fast replacement for your `cd` command, inspired by `z` and `autojump`. It learns from your directory visits and allows you to jump to frequently used directories with minimal typing.

## Features

- **Intelligent Learning**: Tracks your most visited directories
- **Fuzzy Matching**: Find directories even with partial matches
- **Fast Performance**: Written in Rust for optimal speed
- **Multiple Interfaces**: Works with `cd`, `cdi`, and interactive search
- **Cross-Shell Compatibility**: Works with bash, zsh, fish, and more
- **Query Scoring**: Ranks results based on frecency (frequency + recency)

## Installation

### Using Package Manager

#### Arch Linux
```bash
sudo pacman -S zoxide
```

#### Ubuntu/Debian
```bash
# Using cargo (recommended)
cargo install zoxide

# Or using the official binary releases
curl -sS https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | bash
```

#### Fedora
```bash
sudo dnf install zoxide
```

#### macOS (Homebrew)
```bash
brew install zoxide
```

#### Nix
```bash
nix-env -iA nixpkgs.zoxide
```

### Manual Installation

```bash
# Download the latest release
wget https://github.com/ajeetdsouza/zoxide/releases/download/v0.9.2/zoxide-v0.9.2-x86_64-unknown-linux-gnu.tar.gz

# Extract and install
tar -xzf zoxide-v0.9.2-x86_64-unknown-linux-gnu.tar.gz
sudo cp zoxide /usr/local/bin/
```

## Shell Integration

### Bash

Add the following to your `~/.bashrc`:

```bash
# Initialize zoxide
eval "$(zoxide init bash)"

# Optional: Replace cd with zi
alias cd='z'
```

### Zsh

Add to your `~/.zshrc`:

```zsh
# Initialize zoxide
eval "$(zoxide init zsh)"

# Optional: Replace cd with zi
alias cd='z'
```

### Fish

Add to your `~/.config/fish/config.fish`:

```fish
# Initialize zoxide
zoxide init fish | source

# Optional: Replace cd with zi
alias cd='z'
```

## Basic Usage

### Adding Directories to Database

Zoxide automatically tracks directories as you navigate:

```bash
# Navigate to a directory (adds it to the database)
cd /path/to/some/deeply/nested/directory

# Or use zoxide to add without navigating
zoxide add /path/to/directory
```

### Jumping to Directories

#### Using `z` command

```bash
# Jump to directory with interactive selection
z

# Jump to best match for pattern
z pattern

# Jump to directory with substring match
z doc  # matches /home/user/documents

# Jump to directory with fuzzy matching
z prog  # might match /home/user/projects
```

#### Using `zi` command

```bash
# Interactive mode - shows all matches with scores
zi pattern
```

#### Using `cd` replacement

If you've aliased `cd` to `z`:

```bash
# These work like normal cd but with zoxide's intelligence
cd documents
cd prog/python
cd ~/down
```

## Advanced Usage

### Query Options

#### Multiple Patterns

```bash
# Jump to directory matching both patterns
z src python  # finds /home/user/projects/python/src
```

#### Query Types

```bash
# Exact match (if exists)
z 'exact/path'

# Fuzzy match (default)
z fuzzypath

# Substring match
z 'substring'
```

### Database Management

#### Viewing Database

```bash
# Show all tracked directories with scores
zoxide query -l

# Show top 10 most visited directories
zoxide query -l | head -10
```

#### Removing Entries

```bash
# Remove a specific directory from database
zoxide remove /path/to/unwanted/directory

# Remove multiple entries
zoxide remove /path/one /path/two
```

#### Importing/Exporting

```bash
# Export database
zoxide query -l > ~/.config/zoxide/db.txt

# Import database (after exporting)
zoxide import ~/.config/zoxide/db.txt
```

## Configuration

### Environment Variables

```bash
# Set custom database path
export _ZO_DATA_DIR="$HOME/.config/zoxide"

# Set maximum number of entries
export _ZO_MAXAGE="10000"

# Set frecency algorithm parameters
export _ZO_FRECENCY="0.3"
```

### Configuration File

Create `~/.config/zoxide/config.toml`:

```toml
# Zoxide configuration
[data]
dir = "~/.local/share/zoxide"

[options]
maxage = 10000
frecency = 0.3
```

## Integration with Other Tools

### Integration with FZF

```bash
# Use fzf for interactive selection
function zf() {
    local dir
    dir=$(zoxide query -l | fzf)
    cd "$dir"
}

# Bind to key combination in bash
bind '"\C-g":"zf\C-m"'
```

### Integration with Yazi

```bash
# Jump to directory in yazi and open it
function zy() {
    local dir
    dir=$(zoxide query -i)
    yazi "$dir"
}
```

### Integration with Tmux

```bash
# Smart tmux session naming based on current directory
function tmux-smart-session() {
    local dir
    dir=$(basename "$(zoxide query -i)")
    tmux new-session -s "$dir"
}
```

## Tips and Tricks

### Efficient Workflow

1. **Use short aliases**: `z docs` instead of `cd ~/Documents`
2. **Combine with fuzzy finders**: Use `z` with `fzf` for interactive selection
3. **Leverage frecency**: Zoxide learns from your habits automatically
4. **Use with file managers**: Jump to directories before opening GUI file managers

### Performance Optimization

- Zoxide is already very fast, but you can:
  - Reduce database size with `export _ZO_MAXAGE=5000`
  - Use SSD storage for the database
  - Regularly clean unused entries

### Troubleshooting

#### Common Issues

1. **No matches found**: Ensure you've visited directories recently
2. **Slow performance**: Check database size and consider cleanup
3. **Shell integration not working**: Verify initialization code in shell config

#### Debug Mode

```bash
# Enable debug output
export _ZO_DEBUG=1

# Check database status
zoxide query --help
```

## Comparison with Alternatives

| Feature | Zoxide | Autojump | Z (bash) | Fasd |
|---------|--------|----------|---------|------|
| Performance | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| Fuzzy Matching | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Cross-Platform | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐ |
| Ease of Use | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Maintenance | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐ |

## See Also

- [Official Zoxide Repository](https://github.com/ajeetdsouza/zoxide)
- [Zoxide Documentation](https://github.com/ajeetdsouza/zoxide/wiki)
- [Autojump Alternative](https://github.com/wting/autojump)
- [Z (bash) Alternative](https://github.com/rupa/z)