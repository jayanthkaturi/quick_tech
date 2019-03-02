### rsync
```
## a -> preseve permissions, symlinks, times (modification, update) etc. and recursive (-t + -r)
## z -> compress
## u -> update, -u --delete -> update + delete files that are deleted in src/
## --exclude-files '/path/to/file_or_folder'
rsync -az src/ username@host:/path/to/dst/
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
```
