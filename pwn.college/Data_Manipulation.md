# 1. Translating Characters
Using tr to transform piped data by swapping character cases

## My solve
**Flag:** `pwn.college{k44fIrVBJFmi_pzcUUJLJQO1G0L.01MxEzNxwiMxkjNzEzW}`

Used tr to swap the case of characters in the output of /challenge/run to reveal the flag.

```
hacker@data~translating-characters:~$ /challenge/run |  tr 'a-z A-Z' 'A-Z a-z'
yOUR CASE-SWAPPED FLAG:
pwn.college{k44fIrVBJFmi_pzcUUJLJQO1G0L.01MxEzNxwiMxkjNzEzW}

```

## What I learned
How to use tr to translate characters from one set to another, specifically how to swap character case.

## References 
pwn college description
