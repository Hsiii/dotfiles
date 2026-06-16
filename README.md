# dotfiles

Small Vim-focused dotfiles setup for a terminal editor that feels closer to a modern code editor while staying lightweight.

## Layout

- `vim/vimrc` is the tracked Vim config.
- `~/.vimrc` symlinks to `~/dotfiles/vim/vimrc`.
- `~/.vim` symlinks to `~/dotfiles/vim` so Vim native packages load from this repo.
- Plugins and themes are Git submodules under `vim/pack/**/start`.

## Restore

```sh
git clone --recurse-submodules https://github.com/Hsiii/dotfiles.git ~/dotfiles
ln -s ~/dotfiles/vim/vimrc ~/.vimrc
ln -s ~/dotfiles/vim ~/.vim
mkdir -p ~/.local/state/vim/undo ~/.local/state/vim/backup ~/.local/state/vim/swap
```

## Vim Config Coverage

### UI

Shows line numbers, the current line, matching brackets, command feedback, a stable sign column, and a compact status line. This keeps editing context visible without turning Vim into a full IDE.

### Theme

Uses true-color terminal rendering with Rose Pine Moon. The theme is managed as a native Vim package submodule instead of a plugin-manager-specific setup.

### Editing

Enables mouse support, system clipboard integration, modern Backspace behavior, line-boundary cursor wrapping, visual-block selection past short lines, and completion menu behavior without preselecting items. These settings reduce old Vim rough edges during plain text editing.

### Indentation

Uses real tab characters displayed at four columns, preserves previous-line indentation, and enables filetype-specific indentation rules. This matches the chosen tab policy while still letting Vim adapt by language.

### Windows And Buffers

Opens splits to the right/below, allows switching away from modified buffers, confirms before discarding edits, and reloads external file changes when safe. This makes buffer handling closer to modern editors.

### Files And State

Stores undo, backup, and swap files under `~/.local/state/vim` instead of project folders or the dotfiles repo. Persistent undo survives restarts without polluting Git worktrees.

### Search

Enables highlighted, incremental, smart-case search. Lowercase searches are case-insensitive; searches containing uppercase become case-sensitive.

### Display

Wraps long visual lines at word boundaries, keeps wrapped indentation readable, and leaves scroll context around the cursor.

### Plugins

- `rose-pine/vim`: Rose Pine Moon colorscheme.
- `matze/vim-move`: plugin-backed line and selection movement.
- `airblade/vim-gitgutter`: Git change signs in the gutter.

### Mappings

- `Alt-Up` / `Alt-Down`: move the current line or selected block in normal, visual, and insert mode.
- `Ctrl-s`: save in normal, insert, and visual mode.

## Intentionally Skipped

This setup skips file explorer, fuzzy finding, heavy LSP/autocomplete, broad Git UI, visible whitespace, folding, and comment plugins. Those are useful in some Vim setups, but this repo is focused on being a clean place to edit while leaving project navigation and broader workflows to external tools.
