# grep
#linux 

Search resources using text and regular expressions 

Usage: `grep <content> <path>`

Example:

    grep -i 'text' /path/to/file

Recursive usage 

    grep -r 'text' /path/to/folder

Print files that contain results: `grep -L <content> <path>`
Example usage 

    grep -r -L "Network" /var/log/*

Parameters

`-i` case insensitive 
`-w` whole word
`-r` searches recursively

## Using regular expressions

You can search for text that matches regular expressions 

Parameters

`.` matches any single character
`*` matches zero or more times
`+` matches zero or more times
`{n}` matches exactly n times

Examples:

    grep 'c.r' testfile
    grep -E '[a-z]{11}' testfile