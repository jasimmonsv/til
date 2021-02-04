# Remove a file via inode

A file is created with unprintable characters. To delete the file, you can try and copy and paste, or just
find and use the inode file number.

list files with inode number:
'''
$ ls -il
'''

use find command to delete the file by inode:
```
$ find . -inum ##### -exec rm -i {} \;
```

