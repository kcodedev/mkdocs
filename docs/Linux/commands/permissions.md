# Permissions

## chmod
Change file permissions.

- `chmod 755 file.txt` : Set permissions to rwxr-xr-x
- `chmod +x script.sh` : Add execute permission
- `chmod -R 755 directory/` : Recursive permission change

## chown
Change file owner and group.

- `chown user file.txt` : Change owner
- `chown user:group file.txt` : Change owner and group
- `chown -R user directory/` : Recursive owner change

## chgrp
Change group ownership.

- `chgrp group file.txt` : Change group

## umask
Set default file permissions.

- `umask 022` : Set umask value

## ls -l
View permissions (also in file management).

- `ls -l file.txt` : Show permissions

## su
Switch user.

- `su username` : Switch to user
- `su - username` : Switch with environment

## sudo
Execute command as another user (usually root).

- `sudo command` : Run command as root
- `sudo -u username command` : Run as specific user

## passwd
Change user password.

- `passwd` : Change current user password
- `passwd username` : Change another user's password (root only)