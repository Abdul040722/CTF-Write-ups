![Alt](assets/picoCTF_Sleuthkit_Apprentice.png)
Attached File: `disk.flag.img.gz`

## Step 1 – Unpack the Disk Image

First, decompress the image.
```bash
gunzip disk.flag.img.gz
```

This leaves you with:
```bash
disk.flag.img
```
<div class="page-break" style="page-break-before: always;"></div>

## Step 2 – Inspect the Partition Table

Use `mmls` (Sleuth Kit) to view the disk layout:
```bash
mmls disk.flag.img
```

Output:
![Alt](assets/picoCTF-SI_mmls.png)

## Step 3 – Mount Partition #002

### Calculate offset
Each sector = 512 bytes  
Start sector = 2048
```bash
2048 * 512 = 1048576
```

### Mount
```bash
mkdir flagsearch
```
This creates a directory where we can mount our partitions cleanly…

```
sudo mount -o loop,offset=1048576 disk.flag.img flagsearch/
ls flagsearch/
```
Peeking into the partition, it mostly contained boot files and kernel assets — `vmlinuz`, `ldlinux.c32`, `System.map`, etc.

Tried `grep` to check for any flags:
```bash
grep -ri pico flagsearch/
```
All results were from kernel references like `pico_lcd`. No user files or signs of a flag. Time to unmount and try Slot 004.

## Step 4 – Mount Partition #004

### Offset calculation:
I decided to go for slot 04 next using the same process…
```bash
360448 * 512 = 184549376
```
### Mount it:
```bash
sudo umount flagsearch/
sudo mount -o loop,offset=184549376 disk.flag.img flagsearch/
ls flagsearch/
```
This time, it looked like a real Linux system: `bin`, `etc`, `home`, `root`, `var`, etc.
<div class="page-break" style="page-break-before: always;"></div>

## Step 5 – Search for the Flag

A basic grep attempt didn’t return anything useful:
```bash
sudo grep -ri pico flagsearch/ 2>/dev/null
```

![Alt](assets/picoCTF-SKI_grep&find.png)

Moved directly to checking the `/root` directory, which was previously inaccessible due to permissions:
```bash
sudo ls -la flagsearch/root
```
![Alt](assets/picoCTF-SKI_folders.png)

Found:
```
my_folder/
```

Checked inside:
```bash
sudo ls flagsearch/root/my_folder
```

Found the file:
```
flag.uni.txt
```

Read it with:
```bash
sudo cat flagsearch/root/my_folder/flag.uni.txt
```
<div class="page-break" style="page-break-before: always;"></div>

## Flag

![Alt](assets/picoCTF-SKI_flag.png)
```
picoCTF{by73_5urf3r_adac6cb4}
```
![Alt](assets/picoCTF-SKI_proof.png)
