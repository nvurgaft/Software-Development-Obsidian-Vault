# cp
#linux 

Copy files, their contents and directories to other locations on the filesystem

Usage: `cp [options] <sources> <destination>`

Examples

Copy entire source file's content into the target file

    cp ./file_a ./file_b

Copy single file to target directory

    cp ./logfile.txt /var/log/

Copy multiple files to target directory

    cp log1.txt log2.txt log3.txt /var/log/

## Options

`-i` prompt the user for confirmation
`-u` update only is file is newer than the one in destination
`-v` verbose mode, will print actions to output

## Copy directories
When copying directories. their contents should also be copied, you can accomplish it using the `-R` flag
    
	cp -R logs logs_backup

Copy only sub-directories

    cp -RT src target 

