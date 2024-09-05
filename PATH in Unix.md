> (`$PATH`: bin $\mapsto$ recognizable and invokable bin)


Table of contents:
1. Binaries ("bin")
2. $PATH environment variable 

# Binaries ("bin")
- Abbreviation: "/bin"
- Definition: A directory that stores all executable commands in the terminal.
- Binaries = OS executable programs (associated with a keyword command)
- Common locations of bin and its executable programs that we run on the terminal:
	- `/bin`: Essential system binaries (e.g., `ls`, `cp`, `mv`)
	- `/usr/bin`: User binaries (e.g., `python`)
	- `/usr/local/bin`: User's manually installed binaries, not managed by the OS (e.g., `racket` (Racket programming lang)) 
	- `~/bin`: User's personal bin within the home directory (for custom scripts)
	- `/opt`: Optional or additional software.

> Binaries exist in directories. 
> Binaries are not executed automatically. 
> :: We need to **explicitly "append" the binary directory** (`/opt`) to the PATH environment variable (`$PATH`) which is a variable that stores a list **containing "multiple absolute paths to the binaries directories" (e.g., `/bin`, `/opt`, `/usr/local/bin`). 
> 
> Note: Binaries/ executable programs can be installed in a directory location, but if binaries are not explicitly added to the PATH list, it cannot find the executable (usually same name as command) associated with the terminal command, hence it does not recognize it as a valid command, and is unable to invoke the associated binary (the executable file).

> Environment variables: 
> - A variable that holds the string path to prominent locations within the file system (E.g., `$HOME` --- Points to user's home directory, `$TEMP` --- Points to user's temporary files, `$PATH` --- Points to directories which store executable files associated with a terminal command)
### Adding binaries to PATH 
> (`$PATH`: bin $\mapsto$ recognizable and invokable bin)

# $PATH
- $PATH: a special "environment variable". It stores the string path to the binaries directory --- `"path/to/binaries_or_executable_files"`
- Use: Whenever you execute a terminal command, it will search for the executable corresponding to the command to run.
	- E.g., 
	- **In terminal** (type command): `raco`, 
	- **OS search all binary directories**: Traverse all string path in `$PATH`,
	- **IF BINARY FOUND** *Execute the binary associated with the command*; 
	- **ELSE** *Command not found Error*
