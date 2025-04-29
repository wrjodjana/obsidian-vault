### Shells

**Shells:** programs you interact with when working on the command line. Expects to provide strings to them, most of which runs a process. Common interaction with the GUI called the **terminal emulator**.

**Variables:** accessed by preceding `$`, like `$var = "new value"`

**stdout, stderr and stdin**
- Running `ls` , the stdout and stderr display to the terminal emulator and its stdin reads from the terminal emulator, read from keyboard
- To interact with file:
	- `ls > /tmp/dump` redirects stdout to file `/tmp/dump`
	- `ls 2> /tmp/dump` redirects stderr to file `/tmp/dump`
	- `ls < /tmp/dump` redirects stdin to read from file `/tmp/dump`
- 

