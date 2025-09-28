# Description
Can you try to get the flag? Beware we have PIE!

# Solve
Checked the source code, found that program was asking to jump to a memory location and prints the memory location of main function, found a function win that gives the flag, `objdump`'d the binary to find the memory location of win relative to main function , found a difference of 96, then subtracted 96 from location of main function given in terminal to run the win function and get the flag

`flag: picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_801240da}`

```bash
 @kali  nc rescued-float.picoctf.net 50648
Address of main: 0x58f4bbbb833d
Enter the address to jump to, ex => 0x12345: 58F4BBBB82A7
Your input: 58f4bbbb82a7
You won!
picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_801240da}
```
