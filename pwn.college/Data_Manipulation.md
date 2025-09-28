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

# 2. Deleting Characters
Using tr to remove unwanted characters from piped data

## My solve
**Flag:** `pwn.college{E-Yrmm0SjlekMaRJ8nJY4VFgZJ8.0FNxEzNxwiMxkjNzEzW}`

Used tr with -d flag to remove decoy characters (^ and %) from the output of /challenge/run to reveal the flag.

```
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{E-Yrmm0SjlekMaRJ8nJY4VFgZJ8.0FNxEzNxwiMxkjNzEzW}
```

## What I learned
How to use tr with the -d flag to delete specific characters from piped input.

## References 
pwn college description

# 3. Deleting New Lines
Using tr to remove newline characters from piped data

## My solve
**Flag:** `pwn.college{45lOrsGJ2dHcOeFToHaX1UQlXh3.0VNxEzNxwiMxkjNzEzW}`

Used tr with -d flag to remove newline characters from the output of /challenge/run to reveal the flag on a single line.

```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d '\n'
Your line-split flag: pwn.college{45lOrsGJ2dHcOeFToHaX1UQlXh3.0VNxEzNxwiMxkjNzEzW}
```

## What I learned
How to use tr with the -d flag to delete newline characters from piped input using the escaped newline notation '\n'.

## References 
pwn college description

# 4. Extracting First Lines with Head
Using head to extract a specific number of lines from output

## My solve
**Flag:** `pwn.college{YrXB4Pgyt2td1MEMFThIXRRxRSE.0lNxEzNxwiMxkjNzEzW}`

Used head with -n flag to extract the first 7 lines from the output of /challenge/pwn and piped them to /challenge/college to get the flag.

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college 
Congratulations, you piped the right codes!
pwn.college{YrXB4Pgyt2td1MEMFThIXRRxRSE.0lNxEzNxwiMxkjNzEzW}
```

## What I learned
How to use head with the -n option to extract a specific number of lines from piped input and pass them to another command.

## References 
pwn college description

# 5. Extracting Specific Sections of Text
Using cut to extract specific columns of data

## My solve
**Flag:** `pwn.college{golYYkE-CEAkj0J41txbPgAsAtQ.01NxEzNxwiMxkjNzEzW}`

Used cut to extract the column containing flag characters from the output of /challenge/run and piped them to tr to remove newlines.

```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{golYYkE-CEAkj0J41txbPgAsAtQ.01NxEzNxwiMxkjNzEzW}
```

## What I learned
How to use cut with -d and -f options to extract specific columns from data based on delimiters.

## References 
pwn college description

# 6. Sorting Data
Using sort to organize data in a specific order

## My solve
**Flag:** `pwn.college{o3ixNgeLkIpQbqiAqhoXk3hXLYU.0FM0MDOxwiMxkjNzEzW}`

Used sort to organize the flags in alphabetical order and found the real flag at the end of the sorted list.

```
hacker@data~sorting-data:~$ sort /challenge/flags.txt -r | head -n 1
pwn.college{o3ixNgeLkIpQbqiAqhoXk3hXLYU.0FM0MDOxwiMxkjNzEzW}
```

## What I learned
How to use sort to organize data alphabetically, and how to find specific entries in sorted output.

## References 
pwn college description
