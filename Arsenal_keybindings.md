# Mac
**(Fullscreen)** - cmd + ctrl + f

  

# Web
**In 1 tab**

**(Back a page)** - cmd + left key

**(previous page) -cmd + right key**

**Across multiple tabs**

**(Next tab) - shift + command + ]**

**(Previous tab) - shift + command + [**

**(Close tab) - cmd + w**

**(Reopen previously close tab) - shift + cmd + t**

  

# Terminal

**(Go to begining of the console line) - ctrl + a**

**(Go to end of the console line) - ctrl + e**

**(Reverse delete/ delete to the right) - ctrl + d**

**(Clear to the LEFT till the beginning line) - ctrl + u**

**(Cancel the current command line command) - ctrl + c**

(Scroll/ cycle through historical commands entered in terminal) - (instead of up arrow) - `ctrl + p`


# tmux

(general)
(RE-Source tmux config) `ctrl+b :`, `source-files ~/.tmux.conf`
(Install plugins stored in `.tmux/` directory) `ctrl+b shift i`

**(sessions)**
**(start tmux)** tmux

**(Create a new session)** tmux new/ :new

**(Create new named session)** tmux new -s [name of session]/ :new -s [name of session]

**(check running sessions)** tmux ls

**(ATTACH to a session)** tmux a -t [session_name/ session number]

**(DETACH session)** ctrl+b d

**(KILL A session)** tmux kill-ses  -t {name_of_session}

**(KILL ALL sessions)** tmux kill-server

**(Give a view of ALL tmux sessions without quiting tmux)** ctrl+b s
  
**(windows)**

(Help manual): `ctrl + b ?`

**(Create windows) ctrl + b c**
**(Close window)** `ctrl + d`

**(Move to previous window) ctrl + b p**

**(Move to next window) ctrl + b n**

**(Switch to the next pane)** ctrl + b o

**(Switch between the most recent pane) ctrl+ b ;**


  
**(Rename)**
(Rename a session) ctrl + b $
  
**(display)**
**(Split horizontally)** ctrl+b “
**(Split vertically)** ctrl + b %
**(move to pane)** ctrl + b [arrow key]
**(Expand pane)** ctrl + b:, then   ":resize-pane <-U/-D/-L/-R> {number of lines,moving the border}"

**(Close pane)** ctrl + b x


**(Navigation)**

**(Move to previous session)** ctrl + b (

**(Move to next session)** ctrl + b )

(Move to previous pane) ctrl + b ;

(Move to subsequent pane) ctrl + b o

(To allow scrolling in the tmux terminal pane) ctrl + b [

(Stop scrolling mode in tmux terminal pane) ctrl + c

  
  

  

# Vim
**General**

**- (temporarily put vim in the background to use the terminal) - ctrl+z ; fg**

**- In terminal, we can use ‘ps’ to check for processes in the background**

**- (Delete next word) - dw**

**- (Delete previous word) - db**

**- (Delete from cursor to end of line) - shift + d**
  

**NAVIGATION**

**(Pan 1/2 screen up) - ctrl + u**

**(Pan 1/2 screen down) - ctrl + d**

**(Pan 1 full screen forward) - ctrl + f (for forward)**

**(Pan 1 full screen backwards) - ctrl + b (for backwards)**

**(Go to the top of the screen): zt**

**(Go to the bottom of the screen): zb**

**(Jump back to** **previous line****): ctrl + o**

**(Jump to next word): w**

**(Jump to previous word): b**

**(find next nearest character)**: f {char}
  

**OPENING AND QUITTING FILES FROM WITHIN VIM**

(Open file ANOTHER from within vim) - :e {filename}

(Switch between files): ctrl + ^

(Switch to next file) - :bn

(Switch to previous file) - :bN

(switch to first file) - :bf

(swich to last file) - :bl

(switch to specific file name) - :b {filename}

(Quit the current open file) - :bw

(save all files) - :wall 

(quit all opened files) - :qall / :qall! (forcefull quit, discarding and disregarding any changes)

(save and exit file) - :wq! or :x!  (the exclamation mark is just to force change without confirmation)

  

RUN TERMINAL COMMAND FROM WITHIN VIM

(Run terminal command from within vim) - :!<command>

  

**OPENING AND SPLITTING MULTIPLE FILES FROM OUTSIDE VIM**

(Open and split file horizontally) - vim -o {file1}{file2}

(Open and split file vertically) - vim -O {file1} {file2}


**OPENING AND SPLITTING MULTIPLE FILES FROM WITHIN VIM**
Vim split prefix: `ctrl+w`
(Split file horizontall) -`ctrl+w s` or  `:sp <another_filename>` 

(Split file vertically)  -  `ctrl+w v` or  `:vs <another_filename>`

- Operation after split(s)
	- (Jump to split window using direction) - `ctrl+w {h/j/k/l}`
	- (Jump to next split window) - `ctrl + w w`
	- (Open file name at current cursored window) - `:e {filename}`
	- (Look at files in current directory to open in netrw) - `:Ex`
	- (View all opened vim buffers/ windows): `:buffers`
	- (Maximize current WIDTH of buffer/ window): `ctrl+w |`
	- (Maximize current HEIGHT of buffer/ window): `ctrl+w -`
	- (Reset all buffer/ window size so that they are ALL EQUAL dimensions): `ctrl+w =`
  

**(insert at the END of the line) -** A

**(insert at the START of the line) -** I

**(horizontal split) -** :sp {filename}

**(vertical split) - :**vs {filename}

(Insert at the start of the highlighted columns across all highlighted lines): `ctrl+v`, `(highlight column and lines)` , `shift+i`, `(type away)`


### (Horizontal movement) 
- https://www.youtube.com/watch?v=5JGVtttuDQA&list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R&index=2

###### General rule to use keybindings - 
{Command - `d`,`c`,`y`, `v`}{Count}{Motion} CCM

**f{char}** - find the closest matching char to the right (jump forward), and stop AT that character

**F{char}** - find the closest matching char to the left (jump back)

; (semicolon) - jumps to right next ‘f/F’-ed character

, (comma) - jumps to left previous ‘f/F’-ed character

t{char} - find the closest matching car to the right, but stop BEFORE that character

**r{char}** - replace

**ci{bounds}** - “change” “inside” <bounds: e.g., (, <, “, ‘, [, {> (deletes everything within the bounds, and goes into insert mode)

**w** - jump right by 1 word

**b** - jump left by 1 word
  
{action}{i/a}{w/W}

- {action}

- {i/a} - exclude/ include

- <w/W> - **w**: move word after “empty char”/,/./\//? while **W**: move to word after empty char only

**viw** - highlight cursored word

**viW** - highlight cursored word + 1 space to the right

**vi**( - highlight everything IN the nearest set of parenthesis

**va**( - highlight everything IN and including the nearest set of parenthesis

**yiw** - copy/ yank cursored word to the right

### (Vertical movement)
(Jump HALF page down)
	ctrl + d
(Jump HALF page up)
	ctrl + u

(Search next occurences of current word pointed by the cursor)
	\*
- n - to navigate to next instances
- shift + n - to navigate to previous instances

(Search previous occurences of current word pointed by the cursor)
	\!
- *Technically if you know \* you don't need this because you can get the same effect by using shift + n after using \**

(Search next occurence (starting from characters to the right of this line to the next))
	/{regex}
	
(Search previous occurence (starting from the characters to the left of this line to the lines before))
	?{regex}


**formatting**

**(format to proper indent) = [highlight] + =**

  

**selecting**

**(highlight everything within the brace): [highlight] + %**
(goto previously/ last highlighted): `gv`
  

**line numbers**

**- relative line numbers: cursor will be at position 0; other lines will be the relative position from the cursor**

**- absolute line numbers: cursor will be at the real line number; other lines will be also absolute/ real line numbers**

**- hybrid line numbers when turned on: cursor will show real line number; other lines will be the relative position from the cursor**

**(Turn on relative line numbers) - :set rnu**

**(Turn off relative line numbers) - :set nornu**

**(Turn on absolute line numbers) - :set nu**

**(Turn off absolute line numbers) - :set nonu**

**(Turn on hybrid <relative + absolute> line number - :set nu rnu**

**(Turn off hybrid <relative + absolute> line number: set nonu nornu**


## VIMRC
- **:map**: See all keybinds in vimrc 
- `:unmap {keybind}`: unmap the specified keybind in vimrc.
- `:nnoremap {keybind} {command}`: Remap key to execute the command in normal mode.
- `:vnoremap {keybind} {command}`: Remap key to execute the comamnd in visual mode.
- `:inoremap {keybind} {command}`: Remap key to execute the command in insert mode.

# neovim (nvim)
> Installation:
> - I installed nvim using `brew install neovim`
> Config:
> - To ease first time use: I copied config from [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim), it is supposed to contain the most basic config to get neovim started. 
> - The image below shows the output generated after copying and pasting it into `.config/nvim/init.lua`, and restarting nvim by typing `nvim`. (Basically a list of plugins that are installed, as recommended by kickstart.nvim)
![[neovim_kickstart_initlua.png|1000]]

## Help (find all shortcuts)
(Find keymaps in neovim) - `:Telescope keymaps`
(Learn how to install nvim plugins) - `:Telescope help_tags`

## General

## Plugin manager
(Mason plugin manager)
- `:Mason` - a search bar is provided to find the lsp (language server protocol) - (allows 1. code completion, 2. syntax highlighting, 3. warnings and errors) you want to use
	- `i` - to install

(Show recently opened files)
- `<leader><space>`

### Search neovim commands
(Search Filename across directory) 
- `<leader>sf`
(Search word)
- `<leader>sw`
(Search by grep)
- `<leader>sg`

(Search symbol within document) - search "document symbol"
- `<leader>ds`
(Search symbol within current directory (workspace dir)) - search "workspace symbol"
- `<leader>ws`
(Search keywords within file)
- `<leader>/`

### lsp commands 
(Goto Definition (after placing your cursor on text)) 
- `<leader>gd`
(Goto References)(see all files that use the text) 
- `<leader>gr`
(Goto Implementation) 
- `<leader>gI`






# Iterm2 shortcuts

**GENERAL**

**(delete to the start of line) ctrl + u**

**(delete to the end of line) ctrl + k**

**(delete previous word) ctrl + w**

**(delete IN REVERSE ORDER for next character) ctrl + d**

  

**TAB**

**(new tab) - command + T**

**(move between tabs) - command + {arrow keys}** 

**(close tab) - command + w**

  

  

**PANE**

**(switch between panes): option + command + {arrow keys}** 

**(maximize pane): command + shift + enter**

**(drag and move pane): command + option + shift + mouse drag and drop**

**(split window vertically): command + d**

**(split window horizontally): command + shift + d**

  

  

**Markdown**

**(Text formatting)**

  

**(header)**

# This is an H1

## This is an H2

##### This is an H5

**Color text**
```html
<span style="color:red">
Text_content
</style>
```

**(bold text)** 

**text**

  __text__

**(italic text)** 

*text*

  _text_

**(highlight text)** 

`very important words`

**(strikethrough text)** 

       ~~The world is flat.~~

  

**(Hyperlink with real link)**

\[{text}\][] at `<path_to_stuff>`

  

**(Hyperlink WITHOUT real link)**

\[{text}\[]

  
**(tast list)**

- \[x\]  Write the press release
- [x]  Write the press release

- \[ \] Update the website

- \[ \] Contact the media
- [ ] Contact the media

  

**(ordered list)** 
1.   Ready
2.   Steady
3.   Go

  

**(unordered list)** 
\*   Red
\*   Green
\*   Blue

OR

\+   Red
\+   Green
\+   Blue

OR

\-   Red
\-   Green
\-   Blue

  

**(links)** \[Text\](http://exampleLinkHere.net/)

**(image)**  
!\[text\](attachment:{<file_name}) 
OR 
!\[text\]({relative_path})

  

Nice formats

**(Definitions)** 

First Term
: This is the definition of the first term.

  

Second Term

: This is one definition of the second term.

: This is another definition of the second term.

  

**(Block quotes)** 

\> This is the first level of quoting.
> This is the first level of quoting.


\> > This is nested blockquote.
> > This is nested blockquote.


> Back to the first level.

**(Code)** 

\```<bash/javascript/python/c/css>
{code here}
\```

  

**(Alert box)**

\------

**NOTE**

It works with almost all markdown flavours (the below blank line matters).

\------

**(Table)** [website that descibes usage](https://www.markdownguide.org/extended-syntax/)
```
| Syntax | Description |
| --- | ----------- |
| Header | Title |
| Paragraph | Text |
```

Table alignment
```
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
```
- :--- (left alignment)
- :---: (center alignment)
- ---: (right alignment)
  

  

**MATH**

*** All math expressions within the block equation and inline equation should not contain space or unnecessary new line**

**(block equation)**

**$$**

**<the equation>**

**$$**

**(inline equation)**

\$
**{the equation}**
\$

**(dot product)**

\\cdot

**(subscript)** 

**\<sub\>[text]\<sub\>**

**OR**

\{text}\__{[text]}

  
**(superscript)** 

\<sup\>[text]\<sup\>

**OR**

{text}\^{[text]}

  

**(over a range of number)**

**$ \<text>_{<range_of_value>} $**

E.g., https://tex.stackexchange.com/questions/170281/how-put-minimize-in-place-of-min-in-a-typical-optimization-problem*

 
**(normal text within an equation)**
\\text{}

(underline) 
\\underline{}

**(text at the end of line of an equation)**

\&&\\text{}

**(hat)**  \$\hat{{data}}$  

**(fraction)** 
\$/frac{numerator}{denomenator}$

  

**(summation from i to m)** 
\$ \sum_{i}^{m}{<the_equation_which_is_summed>} $

  

**(partial derivative)** 
\$ \frac{\partial{func}}{/partial{w_respect_to}}

  

**(newline)** 
\\\\

**(vector/ magnitude)**

**E.g., put an arrow on top of the character “beta”**

\$\overrightarrow{\beta}$

\$\vec{\beta}$

\$\vv{\beta}$

  


**math alignment**

***All alignment should be wrapped in \begin{align} \end{align} tag FIRST**

**(align equals operator) All = that wants to be aligned in the equation should be &=**

**Examples: https://latex-programming.fandom.com/wiki/Align_(LaTeX_environment)**

# Jupyter notebooks (vanilla) commands
**(Since we are using jupyter-vim-bindings for jupyter notebook, and jupyterlab-vim for jupyter lab, we have an additional "VIM mode", which we will enter, allowing normal insert, normal, visual mode in vim. To use vanilla jupyter notebook commands, we must exit VIM MODE: SHIFT + ESC)**

**Insert cell above**: 
	A
**Insert cell below**: 
	B
Delete Cell:
	DD
Change cell to 'markdown':
	M
Change cell to 'code':
	Y

(Within cell):
**Run terminal command in jupy n cell**
	!{cli command in terminal}

**Time entire cell of code, to see how long it took to run the code in the cell**:
\##### cell \#####
	\%\%timeit
	{code}
	{code}
\#############

**Time line of the code within the cell, to see how long it took to run the code in the cell**
	\%timeit {code}

#### IPython MAGIC commands:
- Resources:
	- https://www.dataquest.io/blog/jupyter-notebook-tips-tricks-shortcuts/
	- https://ipython.readthedocs.io/en/stable/interactive/magics.html
-  `%run` can execute python code from .py files and .ipynb files
```python
# this will execute and show the output from
# all code cells of the specified notebook
%run ./two-histograms.ipynb
```

- `%cat {file_path}`: prints text in a file
- `%%writefile {file_path}`: Writes text written in the ipython prompt to the file

	

# Python Pdb (Python debugger)
> A helpful replacement to print statements

1. Place `breakpoint()` in your `.py` files - (introduced in Python 3.7) - across lines of code where the debugger stops execution to allow debugging operations.
2. Run your `.py` files like normal - `python {file-name}.py`
3. Debugger will start in the console:
- [Commands](https://docs.python.org/3/library/pdb.html#pdbcommand-step):
	- `h`: help
	- `w`: where
	- `n`: next
	- `s {func_name}`: step (step into function)
	- `c`: continue
	- `r`: return - Continue execution until the current function returns.
	- `p {variable_name}`: print
		- `p __return__` : prints value returned by the current function, which has just executed its `return` statement.
	- `pp {variable_name}`: pretty print, for better readability.
	- `l`: list
		- Subsequent entering of `l` / `list`, will show remaining code below. To reset list view, type `list .` (to return to the unexecuted line)
	- `ll`: longer list
	- `q`: quit
	- `''`: comment in pdb to add space for visibility
	- `ctrl + l`: clear pbd screen

# Jupyter-vim-bindings in jupyter notebooks

**Turn on line numbers**
- {C-o} + shift+L

# Jupyter lab

## Jupyter lab themes
- https://github.com/topics/jupyterlab-theme

## Jupyter lab vim
Resource: https://github.com/jupyterlab-contrib/jupyterlab-vim
**Escape VIM MODE** (so that you can use normal jupyter lab/ jupyter notebook commands)
	shift + esc
**Run current line and stay in current cell**: 
	ctrl + enter
**Run current line and jump to the next cell**: 
	shift + enter

Check jupyterlab extension
https://jupyterlab.readthedocs.io/en/stable/user/extensions.html

# VSCODE
> Edit the `keybindings.json` file in vscode
> 1. Open command pallete: `shift + cmd + p`
> 2. Search for `Preferences: Open Keyboard Shortcuts (JSON)`
> 3. Enter `key`, `command`, `when` identifiers. 
> 	1. `command`: can be found here: [link](https://code.visualstudio.com/docs/getstarted/keybindings#_basic-editing)
> 	2. `key, command` : can also be queried using ChatGPT

(close side panel): `cmd + b`


# Obsidian

(Resize images) \!\[\{image_name\} \| \{size_int\}\]

(Move current file to another folder): ctrl + shift + m

