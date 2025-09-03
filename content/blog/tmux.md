---
title: "Tmux"
description: "Best way to manage terminal sessions"
draft: false
tags: ["tmux", "terminal", "session-management", "developer-tools"]
showToc: true
showReadingTime: true
weight: 2
---

# Tmux: Your Terminal Sessions, Perfected

Ever lost hours of work because your SSH connection dropped? Or wished you could keep multiple terminal tasks running while switching between projects? tmux solves these problems and transforms how you work with the terminal.

tmux (terminal multiplexer) lets you create persistent terminal sessions that survive disconnections, organize your workspace with windows and panes, and maintain multiple projects simultaneously. It's like having a desktop environment for your terminal.

## Why tmux Changes Everything

**Session Persistence**: Start a task, disconnect, reconnect hours later – everything's exactly where you left it.

**Organization**: Multiple projects, each with their own windows and panes, all manageable from one interface.

**Remote Work**: Essential for SSH sessions – never lose work due to network issues again.

**Productivity**: Switch contexts instantly, run background tasks, monitor multiple processes simultaneously.

## Installation & Basic Setup

### Install tmux:

```bash
# macOS
brew install tmux

# Ubuntu/Debian
sudo apt install tmux

# CentOS/RHEL
sudo yum install tmux
```

### Start your first session:

```bash
# Create a new session
tmux

# Create a named session
tmux new -s myproject

# List sessions
tmux ls

# Attach to existing session
tmux attach -t myproject
```

## Core Concepts

### Sessions

Think of sessions as separate workspaces. Each project gets its own session.

```bash
# Create session
tmux new -s frontend

# Detach (keep running)
# Press: Ctrl+B, then D

# Reattach later
tmux attach -t frontend
```

### Windows

Windows are like tabs – different tasks within a project.

```bash
# Create new window: Ctrl+B, then C
# Switch windows: Ctrl+B, then 0-9
# Rename window: Ctrl+B, then ,
```

### Panes

Split windows into multiple terminal panes for side-by-side work.

```bash
# Split horizontally: Ctrl+B, then "
# Split vertically: Ctrl+B, then %
# Navigate panes: Ctrl+B, then arrow keys
```

## Essential Configuration

The default tmux setup is functional but not optimal. Here's how to make it yours.

### Change the Prefix Key

The default `Ctrl+B` is awkward. Most users prefer `Ctrl+A`:

```bash
# ~/.tmux.conf
set -g prefix C-a
unbind C-b
bind-key C-a send-prefix
```

### Better Pane Splitting

Intuitive split commands that remember your current path:

```bash
# Horizontal split with 'v'
unbind %
bind v split-window -h -c "#{pane_current_path}"

# Vertical split with '-'
unbind '"'
bind - split-window -v -c "#{pane_current_path}"
```

### Vim-Style Pane Resizing

Resize panes with vim-like hjkl keys:

```bash
bind -r j resize-pane -D 5
bind -r k resize-pane -U 5
bind -r l resize-pane -R 5
bind -r h resize-pane -L 5

# Zoom pane toggle
bind -r m resize-pane -Z
```

### Enable Mouse Support

Modern terminals deserve mouse interaction:

```bash
set -g mouse on
```

### Configuration Reload

Quick config reloading without restarting tmux:

```bash
unbind r
bind r source-file ~/.tmux.conf \; display-message "Config reloaded!"
```

## Advanced Configuration Deep Dive

### Performance & Responsiveness

```bash
# Reduce delay for ESC key
set -s escape-time 10

# Faster repeat rate
set -sg repeat-time 200

# Better terminal support
set -sg terminal-overrides ",*:RGB"
set -g default-terminal "${TERM}"

# Large scrollback buffer
set-option -g history-limit 50000
```

### Window & Pane Management

```bash
# Start numbering at 1 (easier keyboard access)
set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1

# Renumber windows automatically
setw -g renumber-windows on
setw -g automatic-rename on

# Vi mode for copy/paste
set-window-option -g mode-keys vi
```

### Copy Mode Enhancements

Vim-style text selection and copying:

```bash
bind-key -T copy-mode-vi 'v' send -X begin-selection
bind-key -T copy-mode-vi 'y' send -X copy-selection

# System clipboard integration
set -g set-clipboard on

# Don't exit copy mode when dragging
unbind -T copy-mode-vi MouseDragEnd1Pane
```

### Status Bar Customization

Clean, informative status bar:

```bash
# Position and timing
set-option -g status-position bottom
set -g status-interval 10

# Center window list
set -g status-justify centre
set -g status-left-length 200
set -g status-right-length 200

# Color scheme
set-option -g status-style bg=colour0,fg=colour205
set-window-option -g window-status-style fg=colour123,bg=default,dim
set-window-option -g window-status-current-style fg=colour84,bg=default,bright
```

## Essential Plugin Ecosystem

tmux's plugin manager (TPM) extends functionality significantly.

### Plugin Manager Setup

```bash
# Add to ~/.tmux.conf
set -g @plugin 'tmux-plugins/tpm'

# Install TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# Reload config and install plugins: Prefix + I
```

### Must-Have Plugins

**Session Persistence** - Never lose sessions again:

```bash
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'

# Auto-restore sessions
set -g @resurrect-capture-pane-contents 'on'
set -g @continuum-restore 'on'
```

**Vim Integration** - Seamless vim/tmux navigation:

```bash
set -g @plugin 'christoomey/vim-tmux-navigator'
```

**Fuzzy Finding** - Quick session/window/pane switching:

```bash
set -g @plugin 'sainnhe/tmux-fzf'
# Use: Prefix + F
```

**Text Extraction** - Copy anything from your terminal:

```bash
set -g @plugin 'laktak/extrakto'
# Use: Prefix + Tab
```

**File Opening** - Open files/URLs directly:

```bash
set -g @plugin 'tmux-plugins/tmux-open'
# Use: Prefix + O
```

## Real-World Workflows

### Development Project Setup

```bash
# Start new project session
tmux new -s project-name

# Window 1: Code editor
nvim .

# Window 2: Development server (Ctrl+A, C)
npm run dev

# Window 3: Git operations (Ctrl+A, C)
# Keep this for commits, pushes, etc.

# Split for monitoring (Ctrl+A, -)
tail -f logs/app.log
```

### Multiple Project Management

```bash
# Frontend project
tmux new -s frontend -d 'cd ~/projects/frontend && nvim'

# Backend project
tmux new -s backend -d 'cd ~/projects/backend && nvim'

# Infrastructure
tmux new -s infra -d 'cd ~/terraform && nvim'

# Switch between projects instantly
tmux attach -t frontend  # or backend, infra
```

### Remote Server Management

```bash
# Connect to servers in separate windows
tmux new -s servers

# Window 1: Production
ssh prod-server

# Window 2: Staging (Ctrl+A, C)
ssh staging-server

# Window 3: Database (Ctrl+A, C)
ssh db-server

# Pane synchronization for bulk operations
# Ctrl+A, Q (toggles sync across panes)
```

## Pro Tips & Advanced Features

### Notes Integration

Quick note-taking without leaving your workflow:

```bash
# Custom notes menu (Ctrl+A, G)
bind g display-menu -T "#[align=centre]Notes" \
  "Create new note" n \
    "command-prompt -p 'Note:' 'new-window -n notes nvim ~/notes/%%.md'" \
  "Search notes" s \
    "new-window -n notes 'cd ~/notes && nvim \$(find * -type f | fzf)'" \
  "" \
  "Quit menu" q ""
```

### Session Templates

Create project templates for consistent setup:

```bash
# ~/.tmux/layouts/web-dev.sh
tmux new-session -d -s $1
tmux rename-window 'editor'
tmux send-keys 'nvim .' C-m
tmux new-window -n 'server'
tmux send-keys 'npm run dev' C-m
tmux new-window -n 'git'
tmux select-window -t 1

# Usage: ~/.tmux/layouts/web-dev.sh my-project
```

### Clipboard Integration

System clipboard that works everywhere:

```bash
# Copy to system clipboard
bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "pbcopy"

# Paste from system clipboard
bind-key p paste-buffer
```

### Activity Monitoring

Know when background tasks complete:

```bash
set -g monitor-activity on
set -g visual-activity off  # Use status bar instead of popup
```

## Troubleshooting Common Issues

**Colors look wrong?**

```bash
# Check terminal support
echo $TERM
# Should be "screen-256color" or "tmux-256color"

# Fix in ~/.tmux.conf
set -g default-terminal "screen-256color"
```

**Key bindings not working?**

```bash
# Reload config
tmux source-file ~/.tmux.conf

# Check current bindings
tmux list-keys
```

**Session not persisting?**

```bash
# Install resurrect plugin and ensure continuum is saving
tmux show -g @continuum-restore
# Should show "on"
```

**Mouse not working?**

```bash
# Enable mouse support
set -g mouse on

# May need terminal-specific settings for some terminals
```

## Wrapping Up

tmux transforms terminal work from chaotic to organized. With persistent sessions, you never lose work. With windows and panes, you stay organized. With plugins, you get superpowers.

The configuration here represents years of refinement – shortcuts that save hours, plugins that solve real problems, and workflows that scale from single projects to complex infrastructures.

Start with basic sessions and panes. Add the essential config options. Install a few plugins. Most importantly: use it daily. tmux becomes indispensable once it's part of your muscle memory.

Your terminal is your workspace. Make it work for you.
