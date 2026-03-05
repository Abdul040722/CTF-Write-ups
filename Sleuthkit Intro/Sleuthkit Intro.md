![[picoctf-Sleuthkit Intro.png]]
Attached file: `disk.img.gz`

Since it’s a `.gz` file, I decompress with `gunzip disk.img.gz` to get the unpacked image.
I then use `mmls` to reveal the partition table: size of the Linux partition is `0000202752`.
Once I start the instance, I connect to `nc saturn.picoctf.net 57871` and enter the partition size when prompted. This prints the following:

![[picoctf-SleuthkitIntro_flag.png]]
`picoCTF{mm15_f7w!}`
![[picoctf-SleuthkitIntro-win.png]]