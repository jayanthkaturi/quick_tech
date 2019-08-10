```
By default du reports the amount of disk space used by files/directories.
If a file contains any data at all (even a single byte), it will occupy one
block on the disk (which is typically 4k these days). One block cannot be shared between files.
This means that the space of that whole block will not be available for other files, so it is considered "used".

The GNU implementation of du includes an option --apparent-size which will change
the behaviour of the program to output the size of the file contents rather than the
amount of disk space used by the files. For example:

Code:
```bash
$ touch zerosize
$ for (( i=0; i<100; i++)); do echo -n "x" >> less_than_a_block; done
$ for (( i=0; i<5000; i++)); do echo -n "x" >> two_blocks; done
$ ls -l
total 12
-rw-r--r-- 1 matthew matthew  100 2007-12-03 17:31 less_than_a_block
-rw-r--r-- 1 matthew matthew 5000 2007-12-03 17:32 two_blocks
-rw-r--r-- 1 matthew matthew    0 2007-12-03 17:31 zerosize
[permis] [num dirs]         [size]
$ du -h *
4.0K    less_than_a_block
8.0K    two_blocks
0       zerosize
$ du --apparent-size -h *
100     less_than_a_block
4.9K    two_blocks
0       zerosize
```

Note that "total 12" refers to the total size, rounded up for block size: 8k + 4k = 12k
```
