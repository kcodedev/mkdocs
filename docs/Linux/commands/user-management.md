# User Management

## useradd
Create a new user.

- `useradd username` : Create user
- `useradd -m username` : Create user with home directory

## userdel
Delete a user.

- `userdel username` : Delete user
- `userdel -r username` : Delete user and home directory

## usermod
Modify user account.

- `usermod -aG group username` : Add user to group
- `usermod -l newname oldname` : Change username

## groupadd
Create a new group.

- `groupadd groupname` : Create group

## groupdel
Delete a group.

- `groupdel groupname` : Delete group

## groups
Show user's groups.

- `groups username` : Show groups for user

## who
Show who is logged in.

- `who` : List logged in users

## w
Show who is logged in and what they are doing.

- `w` : Detailed user information

## last
Show last logged in users.

- `last` : Login history

## passwd
Change password (also in permissions).

- `passwd username` : Change password

## chage
Change user password expiry information.

- `chage -l username` : Show password expiry info
- `chage -m 7 username` : Set minimum days between password changes