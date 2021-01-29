<h1 align="center"> ☁️ NeoVim  Server</h1>
<p align="center">
    <em>A containerized IDE-like text editor that runs on a web server</em>
</p>

<p align="center">
    <a href="https://github.com/wfxr/code-minimap/actions?query=workflow%3ACICD">
        <img src="https://github.com/wfxr/code-minimap/workflows/CICD/badge.svg" alt="CICD"/>
    </a>
    <img src="https://img.shields.io/github/license/yqlbu/neovim-server" alt="License"/>
    <a href="https://crates.io/crates/code-minimap">
        <img src="https://img.shields.io/badge/docker-19.03-blue" alt="Version">
    </a>
    <a href="https://github.com/wfxr/code-minimap/releases">
        <img src="https://img.shields.io/badge/platform-%20Linux%20|%20OSX%20|%20ARM-orange.svg" alt="Platform"/>
    </a>
</p>

This tool is for running NeoVim remotely, and continuing the developing process at 🚀 speed.
You can use it to implement an IDE-like web-based terminal text editor.

## ✨ Features

- Portable and light-weight
- Easy to deploy
- Versatile and customizable
- Containerized
- Run on a web browser

## Prerequisites

- Driod Sans Mono Nerd Font is required to be downloaded since its the default font of the container. You may find the installation guide below. To use other fonts, please find the instructions on the [Nerd Font](https://github.com/ryanoasis/nerd-fonts) repository.

## Font Installation

#### Linux

```bash
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts && curl -fLo "Droid Sans Mono for Powerline Nerd Font Complete.otf" https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf
```

#### macOS

```bash
cd ~/Library/Fonts && curl -fLo "Droid Sans Mono for Powerline Nerd Font Complete.otf" https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf
```

## 📥 Installation

#### Run with the pre-built image

```bash
docker run -d \
  --name nvim-server \
  -p 6080:3000 \
  -e TZ=Asia/Shanghai \
  -e USER=<USER> \
  -e SECRET=<PASSWORD> \
  hikariai/nvim-server:latest
```

Wait for a couple seconds until the container finishes its bootstrap process, then visit `http://localhost:6080/wetty`

You may check the log by running `docker logs nvim-server`

#### Build the image manually

Notes: `docker-compose` is required

```bash
docker-compose build nvim-server
```

#### UNRAID user only

## 💡 Usage

After logging in with `username` and `password` in the web console, type `vim` to finish the initial setup.

For the first launch, NeoVim will install the coc-extensions defined in [coc.settings](https://github.com/yqlbu/neovim-server/blob/master/nvim/coc-settings.json). You may also download additional coc-extensions followed by the [instructions](https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions)

## 📋 Wiki

## 💬F.A.Q

## TODO

- Prepare the Wiki
- Add more customizable feature

## Reference

- [wetty repository](https://github.com/butlerx/wetty)
- [neovim repository](https://github.com/neovim/neovim)
- [coc-nvim repository](https://github.com/neoclide/coc.nvim)
