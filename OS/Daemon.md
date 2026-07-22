A daemon process is a computer program that runs in the background, primarily on Unix-like operating systems. Unlike regular applications, daemons operate independently of user control and do not require direct interaction. They are essential for performing various system tasks without interrupting the user experience.

Daemons run silently in the background, they provide services to other programs, hardware, or the network. Common tasks include managing network connections, logging system events, and handling print queues.

- They do not have a graphical user interfaces (GUI).
- They remain dormant until triggered by specific events or requests.
- Daemons are initiated at system boot and continue running until the system shuts down.
- They do not depend on an active user session to function.

Daemons are similar to [[service|services]] found in Windows systems.

Some common Daemons in Linux systems are

`systemd` – the main purpose of this daemon is to unify service configuration and behavior across Linux distributions.

`rsyslogd` – used to log system messages. This is a newer version of `syslogd` having several additional features. It supports logging on local systems as well as on remote systems.

`udisksd` – handles operations such as querying, mounting, unmounting, formatting, or detaching storage devices such as hard disks or USB thumb drives

`logind` – a tiny daemon that manages user logins and seats in various ways

`httpd` – the HTTP service manager. This is normally run with Web server software such as Apache.

`sshd` – Daemon responsible for managing the SSH service. This is used on virtually any server that accepts SSH connections.

`ftpd` – manages the FTP service – FTP or File Transfer Protocol is a commonly-used protocol for transferring files between computers; one act as a client, the other act as a server.

`crond` – the scheduler daemon for time-based actions such as software updates or system checks.

(Source: https://itsfoss.com/linux-daemons/)

The `pstree` is a useful command to see what daemons are currently running.