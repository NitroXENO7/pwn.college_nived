# Description
You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag. Download the jpg image here.

# Solve

ran exiftool on the image ,got a b64 looking comment, decoded it to get a one more time base64 encoded passcode, then ran steghide with that password to get the embedded flag.txt file.

```bash
 @kali  exiftool img.jpg         
ExifTool Version Number         : 13.25
File Name                       : img.jpg
Directory                       : .
File Size                       : 74 kB
File Modification Date/Time     : 2025:10:08 01:05:09+05:30
File Access Date/Time           : 2025:10:08 01:05:09+05:30
File Inode Change Date/Time     : 2025:10:08 01:05:09+05:30
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9
Image Width                     : 640
Image Height                    : 640
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 640x640
Megapixels                      : 0.410

 @kali  echo "c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9" | base64 -d
steghide:cEF6endvcmQ=                                                                                                                                                                                                                   
 Wed  8 Oct - 01:11  ~/Downloads 
 @kali  echo "cEF6endvcmQ=" | base64 -d                
pAzzword

 @kali  steghide extract -sf img.jpg -p pAzzword
the file "flag.txt" does already exist. overwrite ? (y/n) y
wrote extracted data to "flag.txt".

 Wed  8 Oct - 01:09  ~/Downloads 
 @kali  cat flag.txt 
picoCTF{h1dd3n_1n_1m4g3_5d4cba73}
```

Flag : `picoCTF{h1dd3n_1n_1m4g3_5d4cba73}`
