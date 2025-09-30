# Description
Files can always be changed in a secret way. Can you find the flag? cat.jpg

# My solve
ran exiftool to find a base64 looking text in license section, used base64 to decode it and get the flag

`flag: picoCTF{the_m3tadata_1s_modified}`

```bash
 ✘  Tue 30 Sep - 23:10  ~/Downloads 
 @kali  exiftool cat.jpg                     
ExifTool Version Number         : 13.25
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2025:09:30 23:07:36+05:30
File Access Date/Time           : 2025:09:30 23:07:38+05:30
File Inode Change Date/Time     : 2025:09:30 23:07:36+05:30
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1


 ✘  Tue 30 Sep - 23:18  ~/Downloads 
 @kali  echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" > file.txt                   

 Tue 30 Sep - 23:18  ~/Downloads 
 @kali  base64 -d file.txt 
picoCTF{the_m3tadata_1s_modified}% 
```
