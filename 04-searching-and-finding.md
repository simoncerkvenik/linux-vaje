# 04 - Searching and Finding

## Purpose
This file contains basic notes about searching text and finding files in Linux.

## Common commands

### `grep`
Searches for text inside files.

Example:
grep error file.txt

### `find`
Finds files and directories by name or location.

Example:
find . -name "file.txt"

### `grep -i`
Searches for text without case sensitivity.

Example:
grep -i error file.txt

### `grep -n`
Shows matching lines with line numbers.

Example:
grep -n error file.txt

### `find /home -name "*.txt"`
Finds all `.txt` files inside `/home`.

Example:
find /home -name "*.txt"
