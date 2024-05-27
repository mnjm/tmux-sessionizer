# tmux-sessionizer

TMUX Sessionizer is a fzf-based tmux session and project switcher written in Bash.

![Demo.gif](https://github.com/mnjm/github-media-repo/blob/main/tmux-sessionizer/demo.gif?raw=true)

This is heavily based upon [ThePrimeagen](https://www.youtube.com/channel/UC8ENHE5xdFSwx71u3fDH5Xw)'s [tmux-sessionizer](https://github.com/ThePrimeagen/.dotfiles/blob/master/bin/.local/scripts/tmux-sessionizer) which I found a little non flexible.

1. Sometimes, I open Tmux sessions for general use outside of specific projects and wanted a script that lists these one-off sessions alongside projects.
2. My project organization is a bit haphazard, with entirely different directory structures for my work and personal projects.
3. I've integrated `git worktree` into my projects, so was looking for a script that can handle such worktree branchs as well.

**How does this tmux-sessionizer work?**

This script first lists Tmux sessions in FZF, then projects from a file (Default: `$HOME/.tmux-sessionizer.list`). You can add or edit entries with `tmux-sessionizer add` or `tmux-sessionizer edit`.

<details>

   <summary>Some other similar alternatives.</summary>

- [jrmoulton/tmux-sessionizer](https://github.com/jrmoulton/tmux-sessionizer) - more "feature reach" and built using rust
- [joshmedeski/t-smart-tmux-session-manager](https://github.com/joshmedeski/t-smart-tmux-session-manager) - uses [zoxide](https://github.com/ajeetdsouza/zoxide)
- [joshmedeski/sesh](https://github.com/joshmedeski/sesh) - from t-smart-tmux-session-manager's dev built using go

</details>

## Commands

- `tmux-sessionizer switch`: Fuzzy search through Tmux sessions and projects and switch/create a session for the selected entry.
- `tmux-sessionizer add [path] [name]`: Add a new entry to the list file with the specified path and session name. If no name is provided, it defaults to the basename of the path. If neither name nor path is provided, it uses the current directory, setting the session name as the current directory's name.
- `tmux-sessionizer edit`: Opens the sessionizer list file in editor. Refers `$EDITOR`, if not provided defaults to `vi`.
- `tmux-sessionizer sanitize`: Remove duplicate and non-reachable entries from the list file.

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

### Configuration

Environment variables

- `TMUX_SEZ_LIST_FILE`: Path to the list file. Default: `$HOME/.tmux-sessionizer.list`
- `TMUX_SEZ_FZF_COMMAND`: Custom fzf command. Default: `fzf --height 100% --reverse`


## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request

## License

This project is licensed under the MIT License.
