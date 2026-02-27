# alias
#linux

manage command aliases 

Usage:

	alias

Prints all aliases set up for the current terminal user session

To create aliases

	alias command="some command with args"

aliases the name `command` to the `some command with args`

Example

	alias bashrc="vim ~/.bashrc"

Will open the current user's `.bashrc` file using vim

Pitfall !!

aliases are not persistent across system reboots, to persist them. write them inside a `.bashrc` file
