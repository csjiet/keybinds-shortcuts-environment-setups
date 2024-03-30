# Download NeoVim
[Build prerequisites](https://github.com/neovim/neovim/wiki/Building-Neovim)/ [Neovim git repo](https://github.com/neovim/neovim/blob/master/BUILD.md)

1. (Build prerequisites): 
**Ubuntu/ Debian:**
- 1. Run command below:
```
sudo apt-get install ninja-build gettext cmake unzip curl
```

**MacOS**
- 1. Install Xcode Command Line Tools: `xcode-select --install`
- 2. Install [Homebrew](http://brew.sh/)
- 3. Run command below
```
brew install ninja cmake gettext curl
```

2. Real installation
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
sudo make install
```

```
rm -r build/  # clear the CMake cache
make CMAKE_EXTRA_FLAGS="-DCMAKE_INSTALL_PREFIX=$HOME/neovim"
make install
export PATH="$HOME/neovim/bin:$PATH"
```
- copy `export PATH="$HOME/neovim/bin:$PATH"` to your shell rc file.

# Setup NeoVim
> We can now choose to `lua` programming language or the `vim` programming language to set things up.

NeoVim plugins: [awesome Neovim](https://github.com/rockerBOO/awesome-neovim#cursorline)
## Configs
1. Navigate to `/.config/nvim/{init.vim_or_init.lua_file}`
### `/init.lua`
Resource: [YT, Primegen nvim setup](https://www.youtube.com/watch?v=w7i4amO_zaE&t)
1. create `mkdir .config/nvim`
2. create `touch .config/nvim/init.lua` 
3. Copy [init.lua from kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) to `init.lua`.
> Bugs:
> Had to fix this: [init.lua error: no specs found for module custom.plugins](https://github.com/nvim-lua/kickstart.nvim/issues/204)

Plugins
**Lazy.nvim** (plugin manager)
- Paste lua code instructions from git repo. 

### `/init.vim`
Resource: [YT, NeuralNine nvim setup](https://www.youtube.com/watch?v=JWReY93Vl6g)
> ProTip: `:so` (source command) -  execute and load the contents of your current Vimscript file (a script written in Vim's scripting language) into the current Vim session. - we use this everytime when we include new keybindings or  plugins.
 
1. create `mkdir .config/nvim`
2. create `touch .config/nvim/init.vim` 

Plugins
**VimPlug**
- Install VimPlug: `https://github.com/junegunn/vim-plug` - vim plugin manager
- Place github repo signature within VimPlug block
- 1) `call plug#begin()` {within block} `call plug#end()`
- 2) Specify github repo signature: `Plug {gitrepo/signature}`
- 3) Commands:
	- `:PlugInstall` - checks your Vim/Neovim configuration for a list of plugins you've specified within the VimPlug block, specified using keyword `Plug`, and install these plugins from their respective sources, typically from Git repositories.
	- `:PlugClean` - ... and uninstall plugins that is install in the system but not specified in the VimPlug block.
> ProTip: To read manuals on how to use plugins, we can type in `:help <PlugInName>` to invoke the manual.

**NERDTree** 
> Rationale of usage: vs. "Vim's NetRW", it opens in another buffer that does not occupy the screen
1.  `Plug 'preservim/nerdtree'`, Run VimPlug commands. (Place github repo signature within VimPlug block)

**Telescope**
1. `Plug 'nvim-telescope/telescope.nvim'`, Run VimPlug commands. (Place github repo signature within VimPlug block) 
- Debugging
	- For `:Telescope grep_string` to work: Install `brew install ripgrep`

**TreeSitter**
> Use: parsing library and syntax tree generator that is used in Neovim to provide advanced code analysis and manipulation features. 
> 1) **Syntax Highlighting**: Highlights code elements from different languages.
> 2) **Code Folding**: automatically identify code blocks and structures in code, where we can fold and unfold sections of code with precision, making it easier to navigate and focus on specific parts of your codebase.
> 3) **Jump-to-Definition**: Creating an abstract syntax tree (AST), accurately locate function or variable definitions in the code, facilitating efficient code navigation.
> 4) **Code Analysis and Linting**: identify code issues, errors, or inconsistencies as you type, and provide suggestions for improving your code.
> 5) **Auto-Completion**: accurate and context-aware code suggestions.
> 6) Improve **Language Server Protocol (LSP)**: provide additional context and code analysis capabilities alongside language servers
> 7) **Custom Language Support**: allows the community to create parsers for new or less common programming languages. This enables Neovim to support a wide range of languages effectively.
> 8) **Plugin Development**: Plugin developers can utilize Tree-sitter to create advanced code manipulation and analysis plugins for Neovim, enhancing its extensibility.
1. `Plug 'nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'}`
2. `:TSInstall <language_to_install>`