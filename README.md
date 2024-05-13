# tmux-sessionizer

TMUX Sessionizer is a fzf-based tmux session and project switcher written in Bash.

<!-- TODO: add demo -->
<!-- Highlight some alternatives -->
<!-- and why I resorted to writing my own -->
<!-- https://github.com/edr3x/tmux-sessionizer -->
<!-- https://github.com/ThePrimeagen/.dotfiles/blob/master/bin/.local/scripts/tmux-sessionizer -->
<!-- https://github.com/jrmoulton/tmux-sessionizer -->

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/mnjm/tmux-sessionizer.git
   ```

2. Add the script directory to your `$PATH` environment variable. For example, if you cloned the repository to `~/tmux-sessionizer`, add the following line to your shell profile (e.g., `.bashrc`, `.zshrc`):

   ```bash
   export PATH="~/tmux-sessionizer:$PATH"
   ```

   (or) Copy / link `tmux-sessionizer` script in one of the entries directory in your `$PATH` For ex. `~/.local/bin`

   ```bash
   cd ./tmux-sessionizer
   cp ./tmux-sessionizer ~/.local/bin
   (or)
   ln -s $(realpath tmux-sessionizer) ~/.local/bin/
   ```

3. (Optional) you can add it as an alias in your shell config (.bashrc or .zshrc):

   ```bash
   alias tmuxs='tmux-sessionizer switch'
   alias tmuxs-add='tmux-sessionizer add'
   alias tmuxs-edit='tmux-sessionizer edit'
   ```

4. (Optional) you can add it as a binding in your tmux config (.tmux.conf):

   ```tmux
   bind s display-popup 'tmux-sessionizer switch'
   ```

### Commands

- `tmux-sessionizer switch`: Switch to an existing session or create a new session based on the selected entry from the list.
- `tmux-sessionizer add [path] [name]`: Add a new entry to the list file with the specified path and session name. If no name is provided, it defaults to the basename of the path. If neither name nor path is provided, it uses the current directory, setting the session name as the current directory's name.
- `tmux-sessionizer edit`: Opens the sessionizer list file in editor. Refers `$EDITOR`, if not provided defaults to `vi`.
- `tmux-sessionizer sanitize`: Remove duplicate and non-reachable entries from the list file.

## Configuration

Environment variables

- `TMUX_SEZ_LIST_FILE`: Path to the list file. Default: `$HOME/.projects-tmux-sessionizer.list`
- `TMUX_SEZ_FZF_COMMAND`: Custom fzf command. Default: `fzf --height 100%`

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request

## License

This project is licensed under the MIT License.
