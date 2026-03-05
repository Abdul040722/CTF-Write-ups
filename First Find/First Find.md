![Alt](assets/picoctf_FirstFind.png)
Attached File: `files.zip`

Similar to `Big Zip` but this time we’re searching for a file. This can be done using `find . -name uber-secret.txt`, `find` is the command to search for a file, the `.` means to start in the current directory, and the `-name` option specifies the name of the file. The output is `./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt`

From here, instead of moving to that directory, I can just use `cat` to print it’s contents. This prints the following:
![Alt](assets/picoctf-FirstFind_flag.png)
The file contains the flag. `picoCTF{f1nd_15_f457_ab443fd1}`
![Alt](assets/picoctf_FirstFind-win.png)
