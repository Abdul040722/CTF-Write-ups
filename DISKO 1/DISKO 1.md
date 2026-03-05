![Alt](assets/picoctf_DISKO1.png)
Attached file: `disko-1.dd.gz`

The image is packed in gunzip format indicated by the `.gz` extension. so we use `gunzip disko-1.dd.gz` to unpack the file. We then get the raw `disko-1.dd` file.

picoCTF flags usually follow the format `picoCTF{...}` so I used the `strings` command to gauge what type of content is in the file, and narrowed it down with `grep -i pico`. `grep` being used to search for expressions and `-i` used to ignore case. This prints the following:
![Alt](assets/picoctf-DISKO1_flag.png)
Among the printed strings is the flag. `picoCTF{1t5_ju5t_4_5tr1n9_be6031da}`
![Alt](assets/pcioctf_DISKO1-win.png)
