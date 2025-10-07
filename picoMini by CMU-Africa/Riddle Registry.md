# Description
Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered. Find the PDF file here Hidden Confidential Document and uncover the flag within the metadata.

# Solve

```bash
 @kali  exiftool confidential.pdf
ExifTool Version Number         : 13.25
File Name                       : confidential.pdf
Directory                       : .
File Size                       : 183 kB
File Modification Date/Time     : 2025:10:08 00:23:06+05:30
File Access Date/Time           : 2025:10:08 00:23:06+05:30
File Inode Change Date/Time     : 2025:10:08 00:23:06+05:30
File Permissions                : -rw-rw-r--
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.7
Linearized                      : No
Page Count                      : 1
Producer                        : PyPDF2
Author                          : cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV9jOGY5MWQ2OH0=
```

Ran exiftool on the pdf to get a b64 encoded looking author name, b64 decoded it to get the flag

Flag :`picoCTF{puzzl3d_m3tadata_f0und!_c8f91d68}`
