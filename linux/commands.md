### Tips
```
1. Double space before command to not to add it to history.
```

### lsof
```bash
## list open files
lsof -U <user_name> ## Open files of user
lsof -i <host_name|optional>:<port_name> ## which ports are open
```

### tmux
```bash
## multiple terminals
tmux list-sessions
tmux ## to start
## <ESC> <:> <resize_pane> <-L|-R|-U|-D>
tmux attach -t <target_tmux_id>
tmux -S <path_to_tmux_socket> attach
tmux kill-session -a <except_tmux_session_id>
```

### Python Virtual ENV
```bash
virtualenv -p <python_executable|python3.6> /dir/path/to_virtual_envs/
source /dir/path/to_virtual_envs/bin/activate
deactivate ## to come out
```

### rsync
```
## a -> preseve permissions, symlinks, times (modification, update) etc. and recursive (-t + -r)
## z -> compress
## u -> update, -u --delete -> update + delete files that are deleted in src/
## --exclude-files '/path/to/file_or_folder'
rsync -auz src/ username@host:/path/to/dst/
```

### du - disk usage
```bash
## sort -h -> sort based on human redable strings
du -sh .[!.*]* * <LOCATION> | sort -h
```

### PS1 - Bash
```bash
export PS1="\e\[1,33m\e\[4,33m\h | \u | \d | \t | \w\n>>"
```

### awk
```
awk '/regex/ {print}' file_name

## NF -> number of fields
## s -> array, dynamically created
## NR -> number record
awk '
{
	for (i = 1; i <= NF ; i++) {
		if (NR == 1) {
			s[i] = $i;
		} else {
			s[i] = s[i]" "$i;
		}
	}
}
END {
	for (i=1; s[i] != "" ; i++) {
		print s[i];
	}
}'

## sed example
sed -n '/<regex>/g p' file.txt
```
