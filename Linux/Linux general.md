
- /dev/null sends data to a special file that immediately discards all data written to it but reports a successful write operation. it provides no data to any process that reads from it, yielding an immediate End Of File
	- End Of File (EOF) means no more data can be read from data. it signals the end of input

- pasted input prepended with `"^[[200~"`
	- https://askubuntu.com/questions/1396132/when-i-paste-in-the-terminal-sometimes-the-contents-are-prefixed-with-the-charac#1396240
	- these are called paste brackets, with the above text being **control codes**
	- there is a **readline** library in Bash that reads pasted content differently than say a normal text editor
	- you need to use ctrl + shift + v to to paste text into the terminal, where just the pasted text is seen by the readline library