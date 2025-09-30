# Description
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...

# My solve
ran -h as an argument to the file


`flag : picoCTF{b1scu1ts_4nd_gr4vy_616f7182}`

```bash
 Tue 30 Sep - 23:38  ~/Downloads 
 @kali  ./warm --help          
zsh: permission denied: ./warm

 ✘  Tue 30 Sep - 23:38  ~/Downloads 
 @kali  chmod +x warm     

 Tue 30 Sep - 23:38  ~/Downloads 
 @kali  ./warm --help
I don't know what '--help' means! I do know what -h means though!

 ✘  Tue 30 Sep - 23:38  ~/Downloads 
 @kali  ./warm -h    
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_616f7182}
```
