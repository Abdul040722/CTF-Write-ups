![[picoctf-information.png]]
Attached file: `cat.jpg`

After uploading the image to my VM for analysis, the first thing I do is use `file` and `exiftool` to learn about the files metadata. In this process I noticed that the license is base64 encoded. Decoding the license key will output the following:

![[picoctf-Information_flag.png]]
`picoCTF{the_m3tadata_1s_modified}`
![[picoctf-information-win.png]]
