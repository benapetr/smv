smv
==========

Smart move utility for linux OS allows you to move (similar to mv) whole directory
infrastructure, basically a workaround utility that allows you to solve issues
like this one:
http://unix.stackexchange.com/questions/59112/preserve-directory-structure-when-moving-files-using-find

## Example use:
```
# This example assumes that smv is installed in some folder that is in your $PATH variable
# Move files older than 10 days while preserving hierarchy
# -vf = verbose + force (doesn't stop on errors)
smv -vf `find some_folder -type f -mtime "-10"` target_folder

# You can additionally run it in dry mode so that it doesn't do anything but print what it would do
smv -rvf `find some_folder -type f -mtime "-10"` target_folder

# Or in case that list of files is too long to fit into argument line and you don't mind
# executing python for every single file, then
find "$soure" -type f -mtime "-2" -exec smv {} "$destination" \;
```
