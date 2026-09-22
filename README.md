# My Niri dotfiles

Dotfiles for [niri](https://github.com/niri-wm/niri), a scrollable-tiling Wayland compositor. Managed by [chezmoi](https://www.chezmoi.io/).

## Usage

Set a command alias for chezmoi environment specific for niri dotfiles:

```sh
alias nirichezmoi="chezmoi -S ~/.local/share/chezmoi-niri/"
```

### Load configs from this repo

- Load configs from my Github dotfiles repo on a new, empty machine:

  ```sh
  nirichezmoi init --apply https://github.com/jalaxy33/niri-dotfiles
  ```

  <details>
  <summary>Easier sync for CN user</summary>

  ```sh
  nirichezmoi init --apply https://gh-proxy.org/https://github.com/jalaxy33/niri-dotfiles
  ```
  </details>

- Updating configs on any machine:

  ```sh
  nirichezmoi update
  ```

- Update certain config file, for example:

  ```sh
  nirichezmoi apply ~/.bashrc
  ```

### Sync with local changes

- Manage new configs:

  ```sh
  nirichezmoi add </path/to/config_file>
  ```

- After editing local configs, update all chezmoi managed configs by:

  ```sh
  nirichezmoi re-add
  ```

- Commit and push changes

  ```sh
  nirichezmoi cd
  git add -A
  git commit -m "<commit messages>"
  git push
  exit
  ```

### Check difference with managed files

- Check changed files:

  ```sh
  nirichezmoi status
  ```

- Check differences

  ```sh
  nirichezmoi diff
  ```

### Ignore files

Edit `.chezmoiignore`:

```sh
nirichezmoi cd
vi .chezmoiignore
```

Add files you want to ignore:

```.gitignore
README.md
```

### Manage machine-to-machine differences

Use [template](https://www.chezmoi.io/user-guide/templating/#editing-a-template-file) to manage machine-to-machine differences.

- Add files as template, for example:

  ```sh
  nirichezmoi add --template ~/.zshrc
  ```

  If a file is already managed by chezmoi, but is not a template, you can make it a template by:

  ```sh
  nirichezmoi chattr +template ~/.zshrc
  ```

- Edit a template file:

  ```sh
  nirichezmoi edit ~/.zshrc
  ```

  Check [this tutorial](https://www.chezmoi.io/user-guide/manage-machine-to-machine-differences/) for use cases.

- Check template variables:

  ```sh
  nirichezmoi data
  ```

- Test templates:

  ```sh
  nirichezmoi execute-template '{{ .chezmoi.hostname }}'
  ```
