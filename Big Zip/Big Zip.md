![Alt](assets/pcioctf_BigZip.png)
Attached file: `big-zip-files.zip`

Presented with the above zip file, the first thing I did was unzip it using `unzip`. This created a subfolder called `big-zip-files` with various files and subfolders contained within.

grep can be used to search recursively with using `-r`, which means it will search within the current directory. So I `cd` into `big-zip-files` and execute the command `grep -r pico` to recursively search for “pico”. This was the output:

![Alt](assets/picoctf-BigZip_flag.png)
It searched through all the files and subfolders until it identified the string. `picoCTF{gr3p_15_m4g1c_ef8790dc}`
![Alt](assets/picoctf_BigZip-win.png)
