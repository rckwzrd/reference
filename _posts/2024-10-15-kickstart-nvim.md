---
layout: post
ks-git: https://github.com/nvim-lua/kickstart.nvim
nv-git: https://github.com/neovim/neovim

---

Below is a psuedo script for intalling Neovim and applying a kick start configuration. The entire script can be ran by hand in less than two minutes and will yield a functional and lightweight editor. There is a language server, project wide fuzzy search, git integration, and all the wonders of modal text editing. There is also a plugin manager and module based configuration leaving the door open for further enhancement and customization.

The key piece in the script is the kick start configuration. This is a comprehensive Lua script that Neovim will run and reference after it is added to the Neovim configuration directory. The links below provide details on Neovim and the kick start configuration. Follow the directions closely.

[Kick start configuration source]({{page.ks-git}}).

[Latest Neovim build]({{page.nv-git}}).

```bash
# install latest stable neovim from source, put in opt software dir
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz
sudo rm -rf /opt/nvim
sudo tar -C /opt -xzf nvim-linux64.tar.gz

# add this to ~/.bashrc, source or restart terminal
export PATH="$PATH:/opt/nvim-linux64/bin"

# install ripgrep, telescope system dependancy
sudo apt install ripgrep

# clone kickstart fork into /.config/nvim
git clone https://github.com/rckwzrd/kickstart.nvim.git "${XDG_CONFIG_HOME:-$HOME/.config}"/nvim

# run nvim to apply kickstart
nvim

# look at kickstart
nvim ~/.config/nvim/init.lua
```
