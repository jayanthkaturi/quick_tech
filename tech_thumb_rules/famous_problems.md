### Technical
1. [c10k Problem](http://www.kegel.com/c10k.html)
```
Serve 10k parallel connections.
[nginx solution](https://murphyswork.wordpress.com/2014/05/04/solve-c-10k-problem-with-nginx/).
```

2. [16 Group Limit Problem](https://www.xkyle.com/solving-the-nfs-16-group-limit-problem/)
```
This problem occurs when a user, who is a member of more than 16 groups, tries to access a file or
directory on an nfs mount that depends on his group rights in order to be authorized to see it.
The default authorization mechanism for NFS (auth_sys) will take only a subset of your groups and
send it to the nfs server to check if you have rights to read a file. This leads to unpredicatable and
intermittent permission problems when it looks like you should have permission.
```

### Non Technical
1. [XY Problem](http://xyproblem.info/):
```
The XY problem is asking about your attempted solution rather than your actual problem.
This leads to enormous amounts of wasted time and energy, both on the part of people asking for help,
and on the part of those providing help.
```
