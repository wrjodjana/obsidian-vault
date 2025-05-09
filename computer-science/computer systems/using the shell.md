### Shells

**Shells:** programs you interact with when working on the command line. Expects to provide strings to them, most of which runs a process. Common interaction with the GUI called the **terminal emulator**.

**Variables:** accessed by preceding `$`, like `$var = "new value"`

**stdout, stderr and stdin**
- Running `ls` , the stdout and stderr display to the terminal emulator and its stdin reads from the terminal emulator, read from keyboard
- To interact with file:
	- `ls > /tmp/dump` redirects stdout to file `/tmp/dump`
	- `ls 2> /tmp/dump` redirects stderr to file `/tmp/dump`
	- `ls < /tmp/dump` redirects stdin to read from file `/tmp/dump`
- One process's stdout mapped to another process's stdin:
	- `ls | shuf` redirects `ls` stdout to `shuf`' stdin

**Global variables:**
- `$PWD` is the present working directory, `cd` changes the value of `PWD`
- `$PATH` is a colon-separated list of paths to look for applications in. `$PATH` is often (`/usr/bin')
- `$USER` is the currently logged-in user
- `$HOME` is the home directory of the currently-logged-in user. `~` is shorthand for `$HOME`. `cd` with no arguments is equivalent to `cd "$HOME"`

**Most important commands**
- `man term` shows manual page for `term`
- `ls` shows contents of current directory
	- `ls -l` shows more info about each file
	- `ls -A` shows "hidden" files too
- `cd` changes the value of `PWD`
- `cp` copies files
	- `cp -r` copies directories with all their contents recursively
- `mv` moves or rename files/directories
- `rm` removes files
	- `rm -r` removes files and directories with all of the directories' contents
- `mkdir` makes directories
- `echo` copies its arguments to its stdout; mostly used for assembling pipelines
- `cat` dumps contents of its arguments to stdout
- `less` shows contents of argument file, or its stdin if none
- `nano` is a self-documenting text editor
- `grep` searches for things
	- `grep -n term filename` searches for `term` in `filename` and shows each line where it occurs
	- `grep -rl term directory` searches all files in `directory` recursively for ones that contain `term` somewhere inside and lists the files it finds



