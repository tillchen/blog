---
layout: post
title: "Bash tips"
---

## Basics

1. `cd` alone goes to the home directory.

2. `ls -lt` gives the long format and sorted by modification time.

3. `file foo.txt` gives the file type.

4. `less foo.txt` gives the content of the file.

5. We can double click a filename to copy it.

6. `cp` copies the files.

7. `mv` moves the files or renames the files.

8. `ln` creates links.

9. Use `|` to combine commands.

10. Control A goes to the beginning.

11. Control R goes to revere searching in the history.

12. `zip -r foo.zip foo` zips the file/directory. `unzip foo.zip` unzips.

13. `grep regex foo.txt` searches in foo.txt

## Writing scripts

1. Put `#!/bin/bash` at the beginning of the script.

2. Use `chmod 755 foo.sh` to make the script executable for everyone. (700 for the owner only.)
