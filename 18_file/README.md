**file():** file read write etc. used for transactions.

- GLOB: to get list of files in current directory.
- GLOB_RECURSE: to get a list of files in the current directory and all its subdirectories.

```
file(GLOB_RECURSE myfiles  ${PROJECT_SOURCE_DIR}/src/*.cpp ${PROJECT_SOURCE_DIR}/inc/*.h)
```