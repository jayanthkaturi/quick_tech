# Editing sudoers file

#### Allowing users run commands as sudo

  1. ```sudo visudo```
  2. Add ```username ALL=(ALL:ALL) ALL``` line and exit.
```bash
username -> username of the user who should be given sudo access
first ALL -> hostname (ALL implies any host)
second ALL -> as user (ALL implies as any user)
third ALL -> as group (ALL implies as any group)
fourth ALL -> command (ALL implies as any command). For multiple commands, use comma seperator
Example: joe ALL=(ALL:ALL) /path/to/cmd1, /path/to/cmd2
```

#### Changing default sudoers editor
```sudo update-alternatives --config editor``` and enter the number against your favourite editor.

#### Allow user to run sudo without entering passwd

```joe ALL=(ALL:ALL) NOPASSWD: /path/to/cmd1```.

Using ALL inplace of /path/to/cmd1 is bad idea, restricting privilage is always better.

#### Security
1. ```Defaults env_reset``` -> Resets the environment to run sudo commands
2. ```Defaults mail_badpass``` -> Mail non sudo users attempting to run sudo commands
3. ```Defaults secure_path``` -> $PATH to use while executing sudo commands, necessary for forbidding users to run their own scripts.
