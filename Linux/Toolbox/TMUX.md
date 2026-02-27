#windowmanager

Terminal Multiplexer (TMUX) is a command line tool that runs a server as a local service that can manage multiple terminal sessions and processes.

https://github.com/tmux/tmux/wiki

The use cases for TMUX are

1. Handle and keep alive local and remote sessions created via SSH. When a connection is closed TMUX can keep the session and attached processes alive for future re-connection and use.
2. Access the same user session from multiple remote machines.
3. Window manager, work on multiple tasks at once (tabs and windows).

Usage

	tmux

Starts tmux with a default window

	tmux new -t <name>

Starts tmux with a new named window, where the name is `<name>` 

To detach a session from inside tmux: `ctrl+b d`

To list all running windows: `tmux ls`

To return to detached session: `tmux attach -t <name>`

or `tmux a -t <name>`