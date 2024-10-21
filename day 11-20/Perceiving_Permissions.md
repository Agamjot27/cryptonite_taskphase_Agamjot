##  Changing File Ownership
To solve this challenge, I leveraged the `chown` command, which is typically restricted to the root user but was allowed for the hacker user in this scenario. First, I inspected the ownership and permissions of the `/flag` file using `ls -l`, confirming that it was owned by the root user, preventing me from reading it. Using the special privileges granted for this level, I changed the file’s ownership to the hacker user by running `chown hacker /flag`. With ownership transferred, I could finally read the file and capture the flag using `cat /flag`.
```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -l
total 40
-rw-r--r-- 1 hacker hacker    0 Oct  9 14:18 COLLEGE
drwxr-xr-x 2 hacker hacker 4096 Oct  1 19:23 Desktop
-rw-r--r-- 1 hacker hacker    8 Oct  9 14:19 PWN
-rw-r--r-- 1 root   hacker   58 Oct  2 12:06 a
-rw-r--r-- 1 hacker hacker    0 Oct  6 11:30 college
-rw-r--r-- 1 hacker root     58 Oct  8 21:23 flag
-rw-r--r-- 1 hacker hacker  829 Oct  9 14:12 instructions
-rw-r--r-- 1 root   hacker   17 Oct  9 20:47 intercepted_data
-rw-r--r-- 1 root   hacker   77 Oct  9 20:31 intercepted_output
-rw-r--r-- 1 hacker hacker   93 Oct  9 14:12 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  8 11:09 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker   77 Oct  9 20:32 pwn
-rw-r--r-- 1 hacker hacker    0 Oct  9 14:00 stdout
-rw-r--r-- 1 hacker hacker  435 Oct  9 14:01 the-flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{E4V0KX8UaDeH55pUZ-k2bLR3gt8.dFTM2QDLxcDO0czW}
```
##  Groups and Files
In this challenge, I used the `chgrp` command to change the group ownership of the `/flag` file, enabling me to access it. First, I checked the file’s current permissions and group ownership using `ls -l /flag`, confirming it was owned by the root user and group. Since I couldn't read the file as a member of the hacker group, I changed the group ownership of the /flag file by running `chgrp hacker /flag`. This allowed my hacker user group to access the file. Finally, I used `cat /flag` to read the flag and complete the challenge.
```
hacker@permissions~groups-and-files:~$ ls -l
total 40
-rw-r--r-- 1 hacker hacker    0 Oct  9 14:18 COLLEGE
drwxr-xr-x 2 hacker hacker 4096 Oct  1 19:23 Desktop
-rw-r--r-- 1 hacker hacker    8 Oct  9 14:19 PWN
-rw-r--r-- 1 root   hacker   58 Oct  2 12:06 a
-rw-r--r-- 1 hacker hacker    0 Oct  6 11:30 college
-rw-r--r-- 1 hacker root     58 Oct  8 21:23 flag
-rw-r--r-- 1 hacker hacker  829 Oct  9 14:12 instructions
-rw-r--r-- 1 root   hacker   17 Oct  9 20:47 intercepted_data
-rw-r--r-- 1 root   hacker   77 Oct  9 20:31 intercepted_output
-rw-r--r-- 1 hacker hacker   93 Oct  9 14:12 myflag
lrwxrwxrwx 1 hacker hacker    5 Oct  8 11:09 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker   77 Oct  9 20:32 pwn
-rw-r--r-- 1 hacker hacker    0 Oct  9 14:00 stdout
-rw-r--r-- 1 hacker hacker  435 Oct  9 14:01 the-flag
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{UJ6hpD1nJEtgnIOzcLIQQ7_1ZAG.dFzNyUDLxcDO0czW}
```
##  Fun with group names
To solve this challenge, I first used the `id` command to identify the group my hacker user was part of, since it was randomized in this level. After finding the correct group name, I checked the ownership of the /flag file with `ls -l /flag`, confirming it was owned by the root group. Using the group name from the id command, I changed the group ownership of the /flag file using the `chgrp grp5861 /flag` command. With the correct group ownership, I was able to read the flag by running `cat /flag`, successfully completing the challenge.
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp5861) groups=1000(grp5861)
hacker@permissions~fun-with-groups-names:~$ ls -l /flag
-r--r----- 1 root root 58 Oct 21 04:02 /flag
hacker@permissions~fun-with-groups-names:~$ chgrp grp5861 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{AhJ6r6D-Lrkr0FigBenq0yK5thB.dJzNyUDLxcDO0czW}
```
##  Changing permissions
To solve this challenge, I used the `chmod` command to modify the permissions of the `/flag` file, allowing me to read it. Initially, I checked the file's current permissions with `ls -l /flag`, confirming that only the root user had read access. Since I had special privileges for this challenge, I ran `chmod u+r /flag`, which granted the hacker user permission to read the file. With the new permission in place, I used `cat /flag` to read the contents of the file and capture the flag, successfully completing the challenge.
```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{4gQ3Rm-Bx8w9gQb7nZjdEawWvIc.dNzNyUDLxcDO0czW}
```
##  Executable files
To solve this challenge, I needed to grant execute permissions to the /challenge/run file. First, I checked the current permissions of the file using `ls -l /challenge/run`, confirming that it was not executable by the hacker user. To fix this, I used the chmod command to add execute permissions by running `chmod u+x /challenge/run`. This allowed my user to execute the file. Once the execute permission was in place, I ran `/challenge/run`, and the program successfully provided the flag, completing the challenge.
```
hacker@permissions~executable-files:~$ chmod ugo+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{I4h6uvUm00bdJt1WU0yxWOnh7AU.dJTM2QDLxcDO0czW}
```
##  Permission Tweaking practice
To solve this challenge, I had to repeatedly modify the permissions of the /challenge/pwn file as instructed, using the `chmod` command. Each time, I adjusted the file permissions based on the specific requirements given. If the permissions were set incorrectly, the challenge would reset.
```
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ugo+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{MZIf69cTivelqRyyA3hYJm5WqUa.dBTM2QDLxcDO0czW}
```
##  Permission Setting practice
In this challenge, I used `chmod` to set and modify file permissions with more advanced chaining of modes, as described. Here's how I approached it:

I launched the challenge using `/challenge/run`.

For each permission modification, I used the `chmod` command with `=` and chaining as instructed. 
```
hacker@permissions~permissions-setting-practice:~$ chmod u=-,g=wx,o=- /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /flag
---------- 1 hacker hacker 58 Oct 21 13:17 /flag
hacker@permissions~permissions-setting-practice:~$ chmod ugo=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{My1ZfOOxMcDhFthNJvzYdsB1BRr.dNTM5QDLxcDO0czW}
```
##  The SUID bit
In this challenge, I used the SUID permission bit to elevate the privileges of the /challenge/getroot program and gain root access. Here's how I proceeded:

Launch the Challenge Program: I started by running /challenge/run to begin the challenge.

Add the SUID Bit: Since I needed to add the SUID bit to the /challenge/getroot program to run it as the root user, I used the following command: `chmod u+s /challenge/getroot`.
Execute the Program: After setting the SUID bit, I ran the program: `/challenge/getroot`.
Read the Flag: Now that I had root privileges, I was able to read the flag file directly:`cat /flag`
```
hacker@permissions~the-suid-bit:~$ cat /challenge/getroot
#!/opt/pwn.college/bash

fold -s <<< "SUCCESS! You have set the suid bit on this program, and it is running as root! Here is your shell..."
exec /bin/bash
hacker@permissions~the-suid-bit:~$ /bin/bash
hacker@permissions~the-suid-bit:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{Qfc19dRVzQxuzfjh68-3l4TBd57.dNTM2QDLxcDO0czW}
```





