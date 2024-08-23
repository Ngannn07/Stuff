# OS challenges


## revision 000
I love cat. I love every kind of cat

> There is a file on the remote server 10.13.37.10. You need to ssh to that device and retrieve the flag from that file using the command cat.
```
ssh os_revision000@10.13.37.10
```

```
ls
cat secret.flag
```

## revision 001
hidden attributes

> There is a file on the remote server 10.13.37.10. You need to ssh to that device and retrieve the flag from that file using the command cat. But where is it?

```bash
ssh os_revision001@10.13.37.10
```

```bash
ls -a
cat .secret.flag
```



## revision 002
navigating around

> There is a file in a subdirectory. How do you navigate through the environment to find it?

```bash
ssh os_revision002@10.13.37.10
```

```bash
ls -a
cat .secret.flag
```


## revision 003
Why did the file go ot the police?

> there are a bunch of files in a directory and they are all flags. But if I cat one at random it clearly isn't the flag.
All I know is that the flag is an ASCII text file
There is a file in a subdirectory. How do you navigate through the environment to find it?

```bash
ssh os_revision003@10.13.37.10
```
```
ls
file*
```

## revision 004
Why did the computer file feel lost?
> there are a bunch of directories with files in them. You don't know where you put it but you know it ended with ".flag"

```bash
ssh os_revision004@10.13.37.10
```
```
ls
find -name “*.flag” 
```

## revision 005
What is in a name?

> You might think this is the same challenge as last time but it's not. You are searching for the file owned by the user adam.

```bash
ssh os_revision005@10.13.37.10
```

```
ls
(find -user “name”)
find -user "adam"
```

## revision 006
Does size count?

> Rumour has it has that the flag is hidden in file that is exactly 33 bytes long. How can you find that in this mess?

### Note
```
Find files by name:

find <path/to/search> -name "<filename>"

Find files owned by a specific user:

find <path/to/search> -user <username>

Find files belonging to a specific group:

find <path/to/search> -group <groupname>

Find files of a specific size. The + and - symbols specify greater than and less than, respectively:

find <path/to/search> -size +<size>[cwbkMG]

c - bytes, w - two-byte words, b - 512-byte blocks, k - Kilobytes, M - Megabytes, G - Gigabytes
```

 ```
 Find .txt files owned by user 'john':

find <path/to/search> -name "*.txt" -user john

Find files of a specific size (e.g., larger than 2MB) and owned by a specific group:

find <path/to/search> -size +2M -group <groupname>

Find .jpg files smaller than 500KB and owned by 'sarah':

find <path/to/search> -name "*.jpg" -size -500k -user sarah

Notes
Use wildcards (*, ?) in the -name option to match multiple files.

The -user and -group options require exact matches of usernames and group names.

When specifying size, pay attention to the prefix (+ for more than, - for less than) and the unit (e.g., c for bytes, M for megabytes).

Combining options allows for very specific searches tailored to your needs.

To suppress error messages, such as permission denied, redirect them to /dev/null using 2> /dev/null. This can make output cleaner if you're running a command that might encounter inaccessible directories or files:

find <path/to/search> [options] 2> /dev/null

This redirects standard error (stderr, file descriptor 2) to /dev/null, effectively ignoring any error messages produced by the command.
```

### solve

```bash
ssh os_revision006@10.13.37.10
```

```
Find -size 33c
```

## revision 007
That's a lot of words!

> Linux comes with a symbol that allows you to take the output from one command and apply it elsewhere. This is called the pipe symbol and we use it with the | button.
Rumour has it that there is a file on the server with a lot of words in it. You flag is next to the word hornstone.
Do you remember how to find the patterns in strings?

```bash
ssh os_revision007@10.13.37.10
```

```
ls
cat ...
cat flag | grep <hornstone>
```

## revision 008
What the wget?

> Hey, some sneak has hidden a flag on a webpage on bushranger. Not only did they hide it there but they also 7zipped it and secured it.

```bash
ssh os_revision008@10.13.37.10
```

```
ls 
```
```
cat secret.hint
> "The flag isn't here.\nBut when you download it you will need to unencrypt it\n
99647cd064647295fb2b3ff0d4904115\n
It's a secret flag 7zip file hosted on the same IP address. \n
I wonder what that means ... ;)\n"
```

```
find / -name "*.7z" 2>/dev/null/usr/share/nginx/html/secret.flag.7z

* wget http://XXX.XXX.XXX.XXX/file.name
wget http://XXX.XXX.XXX.XXX/secret.flag.7z
```

### Open a new tab of terminal

```
ls

cd <my own directory> -> cd study

ls

wget 10.13.37.10/secret.flag.7z

7za x secret.flag.7z -p<password when we cat secret.hint>
7za x secret.flag.7z -p 99647cd064647295fb2b3ff0d4904115

cat secret.flag
```

## revision 009
It is the strings that matter most!

> Hey, I've been really mean writing C programs that you can't use strings on. Here's one for you

```bash
ssh os_revision009@10.13.37.10
```

```
ls
file * (take the one that is not ASCII text)
strings secret (which secret is the not ASCII text)

then find the one looks like flag (fake flag)
./secret <fake flag>
```
