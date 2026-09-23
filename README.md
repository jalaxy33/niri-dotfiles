# My Niri dotfiles

我的 [niri](https://github.com/niri-wm/niri) 配置，使用 [chezmoi](https://www.chezmoi.io/) 管理。

## 使用的软件

niri 使用 [DMS](https://danklinux.com/) 预设。如果需要使用我的配置，请安装以下软件，或者自行调整相应的配置：

- `fish` 用户友好的交互式 shell
- `kitty` 终端模拟器
- `imv` 图片查看器
- `satty` 截图编辑
- `wl-clipboard` 提供更丰富的剪贴板功能，配合实现截图编辑
- `ttf-jetbrains-maple-mono-nf-xx-xx` 等宽字体，用于 kitty 的字体配置
- 浏览器：我用的是 brave，此配置也支持稳定版的 firefox、chrome 和 zen

## 使用方法

> 为了不包含与 niri 无关的配置，使用 `-S` 参数指定 chezmoi 管理目录为 `~/.local/share/chezmoi-niri/`，不干扰其他配置备份。

使用我的配置：

- 在新机器上从 Github 上拉取配置

  ```sh
  chezmoi init -S ~/.local/share/chezmoi-niri/ --apply https://github.com/jalaxy33/niri-dotfiles
  ```

  > <details><summary>如果你在国内</summary>
  >
  > ```sh
  > chezmoi init -S ~/.local/share/chezmoi-niri/ --apply https://gh-proxy.org/https://github.com/jalaxy33/niri-dotfiles
  > ```
  >
  > </details>

- 将所有配置与远程同步：

  ```sh
  chezmoi update -S ~/.local/share/chezmoi-niri/
  ```

- 只同步某个文件：

  ```sh
  chezmoi apply -S ~/.local/share/chezmoi-niri/ <path-to-file>
  ```

查看配置差异：

- 查看有哪些文件发生了变动：

  ```sh
  chezmoi status -S ~/.local/share/chezmoi-niri/
  ```

- 查看具体差异：

  ```sh
  chezmoi diff -S ~/.local/share/chezmoi-niri/
  ```

处理配置冲突：

- 进入 chezmoi 管理仓库后用 git 处理：

  ```sh
  nirichezmoi cd
  git <command>
  exit
  ```
