
### Neovim

[Build prerequisites](https://github.com/neovim/neovim/wiki/Building-Neovim)
- (Build prerequisites): Ubuntu/ Debian: `sudo apt-get install ninja-build gettext cmake unzip curl`
Install neovim "from source"
- [neovim from source](https://github.com/neovim/neovim/wiki/Installing-Neovim#install-from-source), but with additional commands to make installation isolated at `$HOME` which is stated explicitly in the github readme.
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

### tmux
- [legal nested sessions: ssh remote host tmux session, with local tmux already running](https://www.freecodecamp.org/news/tmux-in-practice-local-and-nested-remote-tmux-sessions-4f7ba5db8795/)
create`.tmux.conf`, and copy config
+ create `touch $HOME/.tmux.conf`
+ copy config to the file
Download tmux plugin manager, so that we can enable some plugin commands in `.tmux.conf` (must be done)
- `git clone git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`
- This will create a new `~/.tmux` directory to store the plugins file

### Anaconda installation
- https://clouds.eos.ubc.ca/~phil/docs/problem_solving/01-Orientation/01.05-Installing-Anaconda-on-Linux.html
- Go to anaconda official website and locate the download link for your operating system.
- Copy the link 
- Create a temp file in $HOME directory, `cd` into it.
- In terminal, use wget to install `wget {copied_installer_link}`
- Run the shell script that is installed: e.g., `bash Anaconda3-5.2.0-Linux-x86_64.sh`
- [Follow remaining steps](https://clouds.eos.ubc.ca/~phil/docs/problem_solving/01-Orientation/01.05-Installing-Anaconda-on-Linux.html)

## vscode
- Jupyter notebook extension
	- install 'Python: install the jupyter extension' to recognize kernel (because installed "python environment" - to run `.py` files cannot run jupyter notebooks that uses "Jupyter kernels")
