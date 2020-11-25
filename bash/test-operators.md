# Test operators
In Bash, the `test` command is expressed as 
```
test EXPRESSION
[ EXPRESSION ]       <- old POSIX shells
[[ EXPRESSION ]]     <- New version in Bash, Zsh, Ksh
```

## Commonly used operators
* `-n VAR`  :: True if length of `VAR` is greater then zero
* `-z VAR`  :: True if VAR is empty
* `STRING1 = STRING1`  :: True if `STRING2` and `STRING2` are equal
* `STRING1 != STRING2`
* `INTEGER1 -eq INTEGER2`  :: True if integers are equal
* `INTEGER1 -ne INTEGER2`  :: True if integers are not equal
* `INTEGER1 -gt INTEGER2`  :: True if `INTEGER1` is greater than `INTEGER2`
* `INTEGER1 -lt INTEGER2`  :: True if `INTEGER1` is less than `INTEGER2`
* `INTEGER1 -ge INTEGER2`  :: True if `INTEGER1` is equal or greater than `INTEGER2`
* `INTEGER1 -le INTEGER2`  :: True if `INTEGER1` is equal or less than `INTEGER2`
* `-h FILE`  :: True if `FILE` exists and is a symbolic link
* `-r FILE`  :: True if `FILE` exists and is readable
* `-w FILE`  :: True if `FILE` exists and is writable
* `-x FILE`  :: True if `FILE` exists and is executable
* `-d FILE`  :: True if `FILE` exists and is a directory
* `-e FILE`  :: True if `FILE` exists and is a file, regardless of type (node, directory, socket, etc.)
* `-f FILE`  :: True if `FILE` exists and is a regular file (not a directory or device)

## Uncommon but useful operators
* `-k FILE`  :: True if `FILE` exists and has its sticky bit set
* `-s FILE`  :: True if `FILE` exists and has a size greater than zero
* `FILE1 -nt FILE2`  :: True if `FILE1` is newer (modification date) than `FILE2`
* `FILE1 -ot FILE2`  :: True if `FILE1` is older (modification date) than `FILE2`

Other tests exist and can be found with `$ man test`

