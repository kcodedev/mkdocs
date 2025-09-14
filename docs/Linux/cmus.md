# Cmus Tutorial

Cmus is a powerful command-line music player for Unix-like operating systems. It supports various audio formats and provides a text-based interface for managing and playing music collections.

## Installation

Install Cmus using your package manager:

```bash
# On Ubuntu/Debian
sudo apt install cmus

# On Fedora/CentOS
sudo dnf install cmus

# On macOS with Homebrew
brew install cmus

# On Arch Linux
sudo pacman -S cmus
```

## Basic Concepts

- **Library**: Your music collection
- **Playlists**: Custom lists of songs
- **Views**: Different ways to browse your music (library, playlists, queue)
- **Formats**: Supports MP3, OGG, FLAC, WAV, and more

## Getting Started

### Launch Cmus
```bash
cmus
```

### Add Music to Library

#### Add a Single File
```bash
:add ~/Music/song.mp3
```

#### Add Entire Directory
```bash
:add ~/Music/
```

#### Add Multiple Files
```bash
:add ~/Music/album1/ ~/Music/album2/
```

## Basic Playback Controls

| Action | Key |
|--------|-----|
| Play/Pause | `c` |
| Stop | `s` |
| Next Track | `b` |
| Previous Track | `z` |
| Seek Forward/Backward | Right/Left arrow (5 seconds) |
| Volume Up/Down | `+` / `-` |
| Mute/Unmute | `m` |

## Navigating the Interface

| Action | Key |
|--------|-----|
| Library View | `1` |
| Sorted Library View | `2` |
| Playlist View | `3` |
| Play Queue View | `4` |
| Browser View | `5` |
| Navigate Up/Down | Up/Down arrows |
| Page Up/Down | Page Up/Down |
| Jump to Top/Bottom | Home/End |
| Enter Directory (Browser) | Enter |
| Go Back (Browser) | Backspace |

## Managing Playlists

| Action | Command |
|--------|---------|
| Create Playlist | `:P create playlist_name` |
| Add Current Track | `y` |
| Add Selected Tracks | `Y` |
| Load Playlist | `:P load playlist_name` |
| Save Playlist | `:P save playlist_name` |
| Clear Playlist | `:P clear` |

## Searching and Filtering

| Action | Key |
|--------|-----|
| Search | `/search_term` |
| Filter Library | `f` |
| Clear Search/Filter | `/` (empty) |

## Queue Management

| Action | Key/Command |
|--------|-------------|
| Add to Queue | `e` |
| Remove from Queue | `D` (select track and press) |
| View Queue | `4` |
| Clear Queue | `:q clear` |
| Shuffle Queue | `:q shuffle` |

## Advanced Features

| Action | Key |
|--------|-----|
| Repeat Track | `r` |
| Repeat Playlist | `R` |
| Shuffle | `S` |
| Track Info | `i` |
| Update Library | `U` |
| Jump to Playing | `j` |

## Configuration

### Edit Configuration File
```bash
nano ~/.config/cmus/rc
```

### Common Settings
```
set output_plugin=pulse
set mixer.pulse.device=default
set lib_sort=artist
set show_hidden=true
```

### Key Bindings
```
bind common a add
bind common p toggle
```

## Remote Control

### Control Cmus from Another Terminal
```bash
cmus-remote -p  # play/pause
cmus-remote -n  # next
cmus-remote -r  # previous
cmus-remote -s  # stop
```

### Get Current Status
```bash
cmus-remote -Q
```

## Tips and Tricks

1. **Keyboard Shortcuts**: Learn the shortcuts for efficient navigation
2. **Multiple Views**: Use different views for different browsing needs
3. **Playlists**: Organize your music with custom playlists
4. **Search**: Use search to quickly find specific tracks
5. **Queue**: Build a queue for custom playback order
6. **Remote Control**: Control playback from scripts or other applications

## Common Workflows

### Building a Playlist
```
1. Switch to library view (1)
2. Search for artist (/artist_name)
3. Select tracks (space)
4. Add to playlist (Y)
5. Switch to playlist view (3)
6. Save playlist (:P save my_playlist)
```

### Quick Playback
```
1. Launch cmus
2. Add music directory (:add ~/Music/)
3. Start playing (c)
4. Skip tracks (b/z)
5. Adjust volume (+/-)
```

Cmus provides a lightweight yet powerful way to manage and enjoy your music collection from the command line. With its extensive keyboard shortcuts and features, it can be a very efficient music player for power users.