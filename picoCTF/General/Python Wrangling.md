# Description
Python scripts are invoked kind of like programs in the Terminal... Can you run this Python script using this password to get the flag?

# My solve
used the python file to find options of -e and -d ie encrypt and decrypt ran -d and gave the password to get flag

`flag : picoCTF{4p0110_1n_7h3_h0us3_192ee2db}`

```bash
 @kali  ls
 ende.py   flag.txt.en   pw.txt

 Tue 30 Sep - 23:50  ~/Downloads/fol 
 @kali  cat pw.txt 
192ee2db192ee2db192ee2db192ee2db

 Tue 30 Sep - 23:50  ~/Downloads/fol 
 @kali  python ende.py -d flag.txt.en       
Please enter the password:192ee2db192ee2db192ee2db192ee2db
picoCTF{4p0110_1n_7h3_h0us3_192ee2db}
```
