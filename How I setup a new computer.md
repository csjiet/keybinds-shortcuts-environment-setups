
### Neovim

[Build prerequisites](https://github.com/neovim/neovim/wiki/Building-Neovim)
- (Build prerequisites): Ubuntu/ Debian: 
```
sudo apt-get install ninja-build gettext cmake unzip curl
```
```
git clone https://github.com/neovim/neovim
```
```
cd neovim && make CMAKE_BUILD_TYPE=RelWithDebInfo
```
Install neovim "from source"
- [neovim from source](https://github.com/neovim/neovim/wiki/Installing-Neovim#install-from-source), but with additional commands to make installation isolated at `$HOME` which is stated explicitly in the github readme.

> This one below might not need if we execute the next one. Try, and if so delete this.
```
make CMAKE_BUILD_TYPE=Release
sudo make install
```

```
rm -r build/  # clear the CMake cache
make CMAKE_EXTRA_FLAGS="-DCMAKE_INSTALL_PREFIX=$HOME/neovim"
make install
export PATH="$HOME/neovim/bin:$PATH"
```
- copy `export PATH="$HOME/neovim/bin:$PATH"` to your shell rc file.
- create `mkdir .config/nvim`
- create `touch .config/nvim/init.lua` 
- copy [init.lua from kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) to `init.lua`.

- bugs:
	- Had to fix this: [init.lua error: no specs found for module custom.plugins](https://github.com/nvim-lua/kickstart.nvim/issues/204)
	- [Ripgrep](https://github.com/BurntSushi/ripgrep) plugin for telescope not installed: `brew install ripgrep`

### tmux
- [legal nested sessions: ssh remote host tmux session, with local tmux already running](https://www.freecodecamp.org/news/tmux-in-practice-local-and-nested-remote-tmux-sessions-4f7ba5db8795/)
create`.tmux.conf`, and copy config
+ create `touch $HOME/.tmux.conf`
+ copy config to the file
Download tmux plugin manager, so that we can enable some plugin commands in `.tmux.conf` (must be done)
- `git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`
- This will create a new `~/.tmux` directory to store the plugins file

### Anaconda installation
- Go to [anaconda official website](https://repo.anaconda.com/archive/) (or [scroll to the bottom](https://www.anaconda.com/download)) and locate the download link for your operating system.
- Copy the link 
- Create a temp file in your intended destination directory, `cd` into it.
- In terminal, use wget to install `wget {copied_installer_link}`
- Run the shell script that is installed: e.g., `bash Anaconda3-5.2.0-Linux-x86_64.sh`
- [Follow remaining steps](https://clouds.eos.ubc.ca/~phil/docs/problem_solving/01-Orientation/01.05-Installing-Anaconda-on-Linux.html)
- In the end a `conda init` script will be appended to your terminal configuration file (e.g., `.bashrc`), which helps your terminal identify anaconda as default python to use/ run. 
	- Check if the correct "anaconda python" is used as default using: `which python`. 
	- If python path does not display the correct path e.g.,(`xxx/xxx/anaconda/bin/python`): then you need to copy the `export PATH="/xx/xx/anaconda3/bin:$PATH"` snippet from the appended script (usually nested within the if-else statement of the conda initialize script), and place it outside for a more visible scope.
> anaconda python affects: `python`, `python3`, `pip` commands and installation.
- Setup bash to be sourced whenever terminal opens: Create `nvim .bash_profile` -> copy into `source ~/.bashrc` 

> `.bash_profile` gets called first when a bash shell is initialize

## vscode
- Jupyter notebook extension
	- install 'Python: install the jupyter extension' to recognize kernel (because installed "python environment" - to run `.py` files cannot run jupyter notebooks that uses "Jupyter kernels")

## iterm
Install nerd fonts using bash for neovim: `https://gist.github.com/davidteren/898f2dcccd42d9f8680ec69a3a5d350e`
- e.g., `brew tap homebrew/cask-fonts && brew install --cask font-jetbrains-mono-nerd-font`

### No sudo permissions
> In shared machines, usually you do not have sudo permissions. Hence, we cannot install package managers like `homebrew` or use `apt-get`. In that case, we always do our builds from scratch.
1. Build from source
	- Git clone
2. Open directory, locate binary (usually linux highlights it in green)
3. Create a local binary directory: `mkdir ~/.local/bin`
4. Place binary into the local binary directory: `mv {bin} ~/.local/bin`
5. Add binary to PATH environment variable: `export PATH="$HOME/.local/bin:$PATH".

- Example problems I faced:
	- [Build ripgrep for neovim telescope from source](https://github.com/BurntSushi/ripgrep/discussions/2477)


`
