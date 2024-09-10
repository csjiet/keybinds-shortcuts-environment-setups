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

**(Go to begining of the console line)** - `ctrl + a`
**(Go to end of the console line)** - `ctrl + e`
(**Move cursor forward**) - `ctrl + f`
(**Move cursor backward**) - `ctrl + b`
**(Reverse delete/ delete to the right)** - `ctrl + d`
**(Delete from the cursor to the beginning of the line)**: `ctrl + u` (Uplift)
**(Delete from the cursor to the end of the line)**: `ctrl + k` (Knockdown)

**(Cancel the current command line command) - ctrl + c**

(Cycle through historical commands entered in terminal) - (instead of up arrow) - `ctrl + p`


# tmux

(general)
(RE-Source tmux config): `tmux source ~/.tmux.conf`
(Install plugins stored in `.tmux/` directory): `ctrl+b shift i`

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

(Swap windows with index n and index m) 
1) tmux-command prompt: `ctrl + b + :`, 
2) Specify swap-window command and its source and target windows: `swap-window -s {window-index-n} -t {window-index-m}`


  
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

### tmux-vi
More info: [YT, Tmux has forever changed the way I write code](https://www.youtube.com/watch?v=DzNmUNvnB04&t=691s), [Medium, bindings](https://medium.com/@bertrandoubida/tmux-vim-vi-and-basic-cli-commands-a87092fb2d49#:~:text=To%20enter%20Append%20Mode%3A%20Press,Command%20Mode%3A%20Press%20Esc%20key.****) 
First: (Enter Scroll mode): `ctrl+b [`, then:
- (Enter NORMAL visual mode): `v<space>`
- (Enter LINE visual mode): `shift+v`
- (Enter BLOCK visual mode): `ctrl+v<space>`
- (Esc vi mode): `Esc`  (Ctrl+c will close the scroll mode)
  

  

# Vim
**General**

- (temporarily put vim in the background to use the terminal) - `ctrl+z ; fg`

- (Check path to the file opened in the current buffer) - `ctrl +g` 
	- "g" --- "get" file path

- (Delete next word) - `dw`

- (Delete previous word) - `db`

- (Delete from cursor to end of line) - `shift + d`

- (Delete sentence): [source](https://francopasut.medium.com/vim-delete-sentences-and-paragraphs-via-text-objects-21d55a883e7b#:~:text=A%20sentence%20is%20defined%20as,by%20a%20space%20or%20tab.)
	- (Delete inside sentence): `dis` 
	- (Delete around sentence): `das`
- (Delete paragraph): 
	- (Delete inside paragraph) `dip` 
	- (Delete around paragraph) `dap`
> `w`: word
> `s`: sentence
> `p`: paragraph

> - Sentence: A sequence of text terminated by a punctuation mark `.`/ `!`/ `?` + two spaces.
> - Paragraph: A block  of text delimited by 2 or more newlines (newline) or lines containing only whitespace.
> - Around: Outside the delimiter
> - Inside: Within the delimiter.

- (Repeat prev command) - `.` 
	- E.g., in you use `ciw` and press `.` on cursored word, the same command will be executed.


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

**(Marking a vim buffer with a specific opened file to a capital letter key, and allow quick switching/ jumping to the specific vim buffer)** --- [YT, Use THIS to Level Up Your Vim Navigation Game](https://www.youtube.com/watch?v=R_VxVuR1X6Y)

> **Jumplists**: A historical list of file lines associated with an opened buffer that we have visited.
- (Check jumplist): `:jumps`

> **Marks**: A **mark** allows you to record your current position so you can return to it later, stored in a jumplist. ([source](https://vim.fandom.com/wiki/Using_marks))
- (Mark line in a file (can be the same file)): `m` `shift + {alphabet-key}`
- (Jump to mark): `' + shift + {stored-alphabet-key}`
- (Clear jumplist): `:clearjumps`






  

**OPENING AND QUITTING FILES FROM WITHIN VIM**

(Open file ANOTHER from within vim) - `:e {filename}`
> **Vim Buffers**: Buffers are containers that hold the content of files or text that you are editing. An in-memory representation of a file or text that you are currently editing in Vim.
> - Resources: [YT, Vim Buffers](https://www.youtube.com/watch?v=Dt1d2_IcR1Q)
- (List all Vim Buffers) - `:ls` or `:buffers`
- (Navigating Vim Buffers, the next buffer) - `:bn`
- (Navigating Vim Buffers, the previous buffer) - `:bp`
- (Navigate to Specific Vim Buffer) - `:b {n}` (n - buffer number)
- (Delete Vim Buffer number) - `:bd {n}`

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

(Run terminal command from within vim) - : `!<command>`
(Open terminal within vim): `:term`
  

**OPENING AND SPLITTING MULTIPLE FILES FROM OUTSIDE VIM**

(Open and split file horizontally) - vim -o {file1}{file2}

(Open and split file vertically) - vim -O {file1} {file2}


### Windows in vim
**OPENING AND SPLITTING MULTIPLE WINDOWS FROM WITHIN VIM**

Vim split window prefix: `ctrl+w`
- (Split file horizontall) -`ctrl+w s` or  `:sp <old/new_filename>` 
- (Split file vertically)  -  `ctrl+w v` or  `:vs <old/new_filename>`
- Operation after split(s)
	- (Jump to split window using direction) - `ctrl+w {h/j/k/l}`
	- (Jump to next split window) - `ctrl + w w`
	- (Open file name at current cursored window) - `:e {filename}`
	- (Look at files in current directory to open in netrw) - `:Ex`
	- (View all opened vim buffers/ windows): `:buffers`
	- (Increase/ decrease width of buffers): `ctrl+w >/<`
	- (Increase/ decrease height of buffers): `ctrl+w +/-`
	- (Maximize buffer that was split vertically): `ctrl+w |`
	- (Maximize buffer that was split horizontally): `ctrl+w _`
	- (Reset all buffer/ window size so that they are ALL EQUAL dimensions): `ctrl+w =`
	- (Exit pane): `ctrl+w q`
- Vim split windows orientation change:
	- (Move current window to the most left) - `ctrl+w H`
	- (Move to most right) - `ctrl+w L`
	- (Move to most top) - `ctrl+w K`
	- (Move to most left) - `ctrl+w J`
  

**(insert at the END of the line) -** A

**(insert at the START of the line) -** I

**(horizontal split) -** :sp {filename}

**(vertical split) - :**vs {filename}

(Insert at the start of the highlighted columns across all highlighted lines): `ctrl+v`, `(highlight column and lines)` , `shift+i`, `(type away)`

### Tabs in vim

`:tabnew` - opens new tab

`gt`/ `:tabnext` - switches to next tab

`gT`/ `:tabprev` - switches to previous tab

`n`+`gt` - switches to nth tab

`:q`/ `:tabclose` - closes current tab


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

HIGHLIGHTING IN VISUAL MODE

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
(auto-indenting lines) =  "`=`"


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

### Edit words in vim

Search and replace:
Source: [YT](https://www.youtube.com/watch?v=9Sodnanx_yI)
1) `:{% / {start-line}, {stop}}s/word2replace/replace/{g}{i/I}{c}` --- replace for the whole file 
- `g`: all occurence
- `i`: case insensitive (doesn't care about capitalization); `I`: case sensitive.
- `c`: confirmation (ask before replace)
2) `:{start-line},{stop}s/word2replace/replace/{g}{i/I}{c}` --- replace occurances in specific lines

## VIMRC
- **:map**: See all keybinds in vimrc 
- `:unmap {keybind}`: unmap the specified keybind in vimrc.
- `:nnoremap {keybind} {command}`: Remap key to execute the command in normal mode.
- `:vnoremap {keybind} {command}`: Remap key to execute the comamnd in visual mode.
- `:inoremap {keybind} {command}`: Remap key to execute the command in insert mode.

vimcal plugin

**Open event list**: `shift+e`
**Open task list**: `shift+t`
**Add/ Edit event/ task**: `a`/ `i`
**Mark task as "done"**: `dd`
**Undo marked "done" task**: `shift+u`



# neovim (nvim)
> Installation:
> - I installed nvim using `brew install neovim`
> Config:
> - To ease first time use: I copied config from [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim), it is supposed to contain the most basic config to get neovim started. 
> - The image below shows the output generated after copying and pasting it into `.config/nvim/init.lua`, and restarting nvim by typing `nvim`. (Basically a list of plugins that are installed, as recommended by kickstart.nvim)
![[neovim_kickstart_initlua.png|1000]]

### vim diff tool (neovim)
Source: [neovim doc](https://neovim.io/doc/user/diff.html#:~:text=Vim%20will%20then%20append%20the,diff%22%20command%20will%20be%20used.)
> Checks the differences between >1 files.

```
nvim -d file1 file2 [file3 [file4]]
```

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
> **After installing `Telescope` + `LSP` plugin for neovim:**
 
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
(Goto Definition (after placing your cursor on text)) 
- `<leader>gd`
(Goto References)(see all files that use the text) 
- `<leader>gr`
(Goto Implementation) 
- `<leader>gI`



# PLUGINs in neovim

## OSC52
(Allow osc52 to link with local connection): `set -s set-clipboard external`

---
Git fugitive

- **Diff the file in your working directory vs remote upstream**: Go to the file $\to$`:Gdiffsplit upstream/main`

-----
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

  

  

## Markdown

### Table of contents

- Sources: [Table of contents, how to](https://gist.github.com/jonschlinkert/ac5d8122bfaaa394f896#sub-heading)
```
<!-- link -->
- [Identifier 1](#identifier-1)

<!-- content -->
# Identifier 1
```

```
- [Heading](#heading)
  * [Sub-heading](#sub-heading)
    + [Sub-sub-heading](#sub-sub-heading)
- [Heading](#heading-1)
  * [Sub-heading](#sub-heading-1)
    + [Sub-sub-heading](#sub-sub-heading-1)


## Heading
This is an h1 heading

### Sub-heading
This is an h2 heading

#### Sub-sub-heading
This is an h3 heading


## Heading
This is an h1 heading

### Sub-heading
This is an h2 heading

#### Sub-sub-heading
This is an h3 heading
```

### Text formatting

**(header)**

`# This is an H1`

`## This is an H2`

`##### This is an H5`

**Color text**
```html
<span style="color:red">
Text_content
</style>
```

Text bolding: `**{text}**`

Text italic: `__text__`, `*text*`, `_text_`

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

  
## Image
**(links)** 
```
\[Text\](http://exampleLinkHere.net/)
```

**(image)**  
```
!\[text\](attachment:{<file_name}) 
```
OR 
```
!\[text\]({relative_path})
```
OR
```
<img src="drawing.jpg" alt="drawing" width="200"/>
```
  

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

**Connect jupyter notebook to a REMOTE server/ ssh** --- [Stackoverflow, source!](https://stackoverflow.com/questions/69244218/how-to-run-a-jupyter-notebook-through-a-remote-server-on-local-machine)
1. In your local terminal: ssh to your remote machine; Run jupyter lab server in your remote machine
2. `jupyter lab --no-browser --port={r-port}`
3. Copy URL generated by the jupyter server. 
4. In your local terminal:
- `ssh -L {l-port}:localhost:{r-port} {user}@{ip}`
6. Paste the URL in your browser.

Details: 
In **remote host**: Start server and allow a port 
`jupyter lab --no-browser --port={r-port}`
- `jupyter lab`: 
- `--no-browser`: don't launch on local browser
- `--port={r-port}`: specify remote server port

In **local host**: Connect local port that listens to remote port
- `ssh -L`: to expect "local port forwarding" syntax
- `{l-port}:localhost`: Local port 
- `:`: TO
- `{r-port} {user}@{ip}`: Remote port

> **(Since we are using jupyter-vim-bindings for jupyter notebook, and jupyterlab-vim for jupyter lab, we have an additional "VIM mode", which we will enter, allowing normal insert, normal, visual mode in vim. To use vanilla jupyter notebook commands, we must exit VIM MODE: SHIFT + ESC)**

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
- `{function_identifier}??`: It will display the source code and docstring directly within the notebook interface - (if you are interested to read the documentation for that function/ how to use it).


	

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

Navigation
- Explorer (file directory)
	- (Hide explorer pane/ directory view pane): `cmd + b`
	- (Move cursor to Explorer): `cmd + shift + e`
- Pane
	- {==View Vim bindings above==}


# SCP (Secure CoPy)
> Command line tool in Unix and Linux systems; Uses SSH (Secure Shell) to securely transfer files between two hosts. 

Syntax:
```
scp {-option} {source} {destination}
```
- `-r`: Recursively copy 

**"Send to":**
- In local terminal:
```
scp -r -P {remote-port} {./local_path_to_dir} usr@{i.p.address}:~/{path}
```
- (specifying destination port)
```
scp -P {destination_port} {./local_path_to_dir} usr@{i.p.address}:~/{path}
```

> Running the `scp` command to copy a directory to a remote location will overwrite any existing files in the destination if they have the same name and are in the same location.


**"Receive from":**
- In local terminal:
```
scp -r -P {remote-port} usr@{i.p.address}:~/{path} {./local_path_to_dir}
```

> The ip address changes depending on the network your device is connected to.
> 
> Who allocates the ip address?
> - The Wi-Fi network.
> - When you connect a device to a Wi-Fi network, the Wi-Fi network assigns an IP address to that device. This assignment is done dynamically using a protocol called DHCP (Dynamic Host Configuration Protocol), to manage resources efficiently and avoid conflicts. (Wi-Fi networks can use DHCP to assign IP addresses to connected devices)
> - So, whenever you connect your computer to a different Wi-Fi network (such as at home, at a cafe, or at work), it will receive a different IP address assigned by that network's router or DHCP server. (different wifi provider modem, different ip)

Find your current wifi network ip:
```
ipconfig getifaddr en0
```
- `getifaddr`: command to retrieve ip address of subsequently specified network interface.
- `en0`: network interface

----

# rsync (remote synchronization/ remote sync)
> How is rsync different from scp?
> - rsync: Used to maintain a mirror copy or backup of a source directory to a destination directory. It does so differently compared to scp by **only minimally transferring the differences or portion of changes (addition or deletions) made to the files** rather than the entire file every time.

> Benefits:
> - Does not require separate commits, when splitting workload across computers. 
> 	- (e.g., pushing changes from machine 1, pulling from pushed changes to machine 2, and then pushing changes from machine 2 as 2nd commit)
> - Fault tolerant (A system continues to operate properly despite a failure). 
> 	- Fault: Failure.
> 	- Tolerant: Resistant.

Setup --- [source](https://www.digitalocean.com/community/tutorials/how-to-copy-files-with-rsync-over-ssh)
### 1. Establish trust between two machines (optional: usually, rsync should work out of the box)
In source machine:
- Generate public SSH keys with no password
```
ssh-keygen -f ~/.ssh/id_rsa -q -P ""
```

- Get public SSH key that can be placed on other hosts to give us access
```
cat ~/.ssh/id_rsa.pub
```
In destination machine:
- Copy the public key and login to your destination server.
- Place this SSH key into your ~/.ssh/authorized_keys file
```
# If not created
mkdir ~/.ssh 
chmod 0700 ~/.ssh 

# If not created
touch ~/.ssh/authorized_keys 
chmod 0644 ~/.ssh/authorized_keys
```

### 2. Rsync! 
Syntax:
```
rsync -uvrP -e "ssh -p {port}" {usr}@{ip-address}:{source~/code/} {destination}
```

#### (Push: Send synced files to remote): 
- **Trailing slash)): Means sync "contents in" source directory to destination_path_dir
```
rsync -uvrP -e "ssh -p {port}" {usr}@{ip-address}:{source}/ {destination}
```
Or
- **No trailing slash**: Means sync source directory to destination_path_dir
```
rsync -uvrP -e "ssh -p {port}" {usr}@{ip-address}:{source} {destination}
```
> `-e`: specifies the remote shell to use for communication
> `-u` : Update. This forces rsync to skip any files which exist on the destination and have a modified time that is newer than the source file. (If an existing destination file has a modification time equal to the source file’s, it will be updated if the sizes  are different.)
> `-v`: Verbose. This option increases the amount of information you are given during the transfer.
> `-r`: Recursive. This tells rsync to copy directories recursively
> `-P`: Partial progress. For a long transfer that may be interrupted.
> `--delete`: Make target an identical copy of the source, purging files in the destination that is not found in the source. (default: if there are files in the target destination that are not present at the source, they will be left alone and not touched)
> `--ignore-existing`: tells rsync to skip updating files that already exist on the destination. (default:  If the file contents differ then the file will be overwritten)

#### (Pull: Receive synced files from remote): 
```
rsync -uvrP username@remote_host:destination_path local_path
```


Make it perform like `scp` 
```
rsync -aurvP --ignore-existing --force --checksum --ignore-times -e "ssh -p 3333" {source} {destination} 
```

----
# Aerospace 
Tile manager

> Config: `.config/aerospace/aerospace.toml`

- Reload: `alt + shift + ;` + `esc`

- Layout accordion: `alt + ,`
- Layout tiles: `alt + /` 
- Fullscreen & retype to unfull: `alt + shift + f` 
- Float the window & retype to unfloat: `alt + shift + ;` (service mode) + `f`
- Make tile smaller in size: `alt + shift + -`
- Make tile bigger in size: `alt + shift + =`
``

----
# Obsidian

(Resize images) \!\[\{image_name\} \| \{size_int\}\]

(Move current file to another folder): ctrl + shift + m


# LaTEX 
Setup: [Youtube](https://www.youtube.com/watch?v=CmagZthwhaY)
Downloads: [miktex](https://miktex.org/download)

Boilerplate
```
\documentclass{article} %
\usepackage[utf8]{inputenc}

\title{youtube get started}
\author{Federi Tartarini}
\date{April 2020}

\usepackage{natbib}
\usepackage{graphicx}

\begin{document}
\maketitle

\bibliography{references}
\end{document}
```

### Packages
```
\usepackage{name_of_package}
```
- `natbib`: 
- `graphicx`: 
- `multicol`: For multiple columns in a page
```
\begin{document}
\begin{multicol}[num_of_col]

\end{multicol}
\end{document}
```


## Tensorboard

In Remote machine
```bash
tensorboard --logdir={path_to_dir}  --port=6006
```

In Local machine
> use the option `-L` to transfer the port `6006` of the remote server into the port `16006` of my machine. everything on the port `6006` of the server (in `127.0.0.1:6006`) will be **forwarded** to my machine on the port `16006`.
```bash
ssh -L 16006:127.0.0.1:6006 olivier@my_server_ip
```

> Go to link
```
http://127.0.0.1:16006/
```


