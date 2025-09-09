# Linux Commands

## lsof
The command `lsof -i tcp:PORT_NUMBER` is a powerful Linux/Unix utility for diagnosing network-related issues, particularly port conflicts in development environments (e.g., when encountering "address already in use"). `lsof` stands for LiSt Open Files, and since network sockets (like TCP ports) are treated as "files" in Unix-like systems, it can list processes using specific network resources.