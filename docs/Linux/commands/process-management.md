# Process Management

## ps
Display information about running processes.

- `ps` : Show processes for current user
- `ps aux` : Show all processes with detailed info

## top
Display real-time process information.

- `top` : Interactive process viewer

## htop
Enhanced version of top (if installed).

- `htop` : More user-friendly process viewer

## kill
Send signal to a process.

- `kill PID` : Terminate process by PID
- `kill -9 PID` : Force kill process

## pkill
Kill processes by name.

- `pkill processname` : Kill processes matching name

## bg
Resume suspended job in background.

- `bg %1` : Resume job 1 in background

## fg
Bring background job to foreground.

- `fg %1` : Bring job 1 to foreground

## jobs
List background jobs.

- `jobs` : Show current jobs

## nice
Run command with modified scheduling priority.

- `nice -n 10 command` : Run with lower priority

## renice
Change priority of running process.

- `renice -n 10 -p PID` : Change priority of process