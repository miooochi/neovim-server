<h1 align="center"> ☁️ NeoVim  Server</h1>
<p align="center">
    <em>A containerized IDE-like text editor that runs on a web server</em>
</p>

<p align="center">
    <a href='https://github.com/yqlbu/neovim-server/actions?query=workflow%3A"Docker+CI+Builds"'>
        <img src='https://github.com/yqlbu/neovim-server/workflows/Docker%20CI%20Builds/badge.svg' alt="CICD"/>
    </a>
    <img src="https://img.shields.io/github/license/yqlbu/neovim-server" alt="License"/>
    <a href="https://hub.docker.com/repository/docker/hikariai/nvim-server">
        <img src="https://img.shields.io/badge/Docker-19.03-blue" alt="Version">
    </a>
    <a href="https://github.com/neovim/neovim">
        <img src="https://img.shields.io/badge/neovim-0.5.0-violet.svg" alt="NeoVim"/>
    </a>
    <a href="https://hub.docker.com/repository/docker/hikariai/nvim-servers">
        <img src="https://img.shields.io/badge/platform-%20Linux%20|%20OSX%20|%20ARM-red.svg" alt="Platform"/>
    </a>
</p>

This tool is for running NeoVim remotely and continuing the development process at 🚀 speed.
You can use it to implement an IDE-like web-based terminal text editor.

![screenshot](https://github.com/yqlbu/neovim-server/raw/master/demo.gif)

## ✨ Features

- Portable and light-weight
- Support popular languages
- Syntax highlight
- Intellisense autocomplete
- Markdown snippets and preview
- Easy to deploy
- Versatile and customizable
- Containerized
- Run on a web browser
- Build with multi-arch (ARM/x86)
- Supported platforms: `arm64`, `arm64`, `arm/v7`

## Prerequisites

- `Driod Sans Mono Nerd Font` is required to be downloaded since its the default font of the container. You may find the installation guide below. To use other fonts, please find the instructions on the [Nerd Font](https://github.com/ryanoasis/nerd-fonts) repository.
- Choose a web browser in your preference. Google Chrome, Microsoft Edge, and FireFox should work fine, whereas Safari does not work temporarily.

## Font Installation

Notes: `reboot` might be needed after the font installation

#### Linux

```bash
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts && curl -fLo "Droid Sans Mono for Powerline Nerd Font Complete.otf" https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf
```

#### macOS

```bash
cd ~/Library/Fonts && curl -fLo "Droid Sans Mono for Powerline Nerd Font Complete.otf" https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/DroidSansMono/complete/Droid%20Sans%20Mono%20Nerd%20Font%20Complete.otf
```

#### Arch User ONLY

```bash
yay -S nerd-fonts-droid-sans-mono
```

## 📥 Installation

#### Run with the pre-built image

```bash
docker run -d \
  --name nvim-server \
  --restart unless-stopped \
  -p 6080:3000 \
  -p 8090:8090 \
  -v ~/workspace:/workspace \
  -v /appdata/nvim-server:/config \
  -e UID=$UID \
  -e GId=$GID \
  -e TZ=Asia/Shanghai \
  -e USER=<USER> \
  -e SECRET=<PASSWORD> \
  hikariai/nvim-server:latest
```

Notes:

- Wait for a couple seconds until the container finishes its bootstrap process, then visit `http://localhost:6080/wetty`
- You may check the log by running `docker logs nvim-server`

|            Parameters             |                               Usage                               |
| :-------------------------------: | :---------------------------------------------------------------: |
|       `--name nvim-server`        |                Specify the name for the container                 |
|          `-p 6080:3000`           |               Map the port for accessing the Web UI               |
|          `-p 8090:8090`           |       Map the port for the Instant Markdown Preview Server        |
|    `-v ~/workspace:/workspace`    |                     Map the working directory                     |
| `-v /appdata/nvim-server:/config` |        Contain all relevant configuration config directory        |
|           `-e UID=$UID`           |                        Map current user ID                        |
|           `-e GID=$GID`           |                       Map current group ID                        |
|           `-e TZ=<TZ>`            |          Specify a timezone to use e.g. `Asia/Shanghai`           |
|         `-e USER=<USER>`          |  Specify the username for user login, default is set to `guest`   |
|       `-e SECRET=<SECRET>`        | Specify the password for user login, default is set to `password` |

#### Build the image manually

Follow the instruction [HERE](https://github.com/yqlbu/neovim-server/wiki/Installation#build-container-image-manually)

#### UNRAID User ONLY

`NeoVim Sever` is now available on `unRAID CA`. Search `nvim server` and install

Detailed installation guide is available [HERE](https://github.com/yqlbu/unraid-templates)

## 💡 Usage

- After logging in with `username` and `password` in the web console, type `vim` to finish the initial setup.

- For the first launch, NeoVim will install the coc-extensions defined in [coc.settings](https://github.com/yqlbu/neovim-server/blob/master/nvim/coc-settings.json). You may also download additional coc-extensions followed by the [instructions](https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions)

- All the functionalities and usage cases are written in the [Wiki Page](https://github.com/yqlbu/neovim-server/wiki), feel free to check it out.

- To get familiar with the default key mappings, please visit the [Cheat Sheet Page](https://github.com/yqlbu/neovim-server/wiki/Cheat-sheet)

## 📋 Wiki

- [Wiki (EN)](https://github.com/yqlbu/neovim-server/wiki)

## 💬F.A.Q

- [F.A.Q (EN)](https://github.com/yqlbu/neovim-server/wiki/F.A.Q)

## TODO

- Add a customizable base image
- Add more customizable features
- Add more advanced usage cases
- Add demo and usage guide for selection, registers, substitution, and macro
- Add SSL support
- Add relative number option

## Reference

- [wetty repository](https://github.com/butlerx/wetty)
- [neovim repository](https://github.com/neovim/neovim)
- [coc-nvim repository](https://github.com/neoclide/coc.nvim)

## License

[MIT (C) Kevin Yu](https://github.com/yqlbu/neovim-server/blob/master/LICENSE)
