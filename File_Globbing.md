##  Matching with *
To solve this challenge, I used shell globbing to change directories efficiently. Starting from my home directory, I employed the wildcard character (*) to match the path. Since I had to limit the argument to four characters, I utilized the cd /ch* command, which allowed the shell to recognize and complete the path to /challenge. Once inside the challenge directory, I executed the /challenge/run command to successfully capture the flag.
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{A4R9dzpA-RMFYOmrVbJIo6yiA1Y.dFjM4QDLxcDO0czW}
```
##  Matching with ?
To solve this, I used the ? wildcard to replace specific letters in the directory name. Starting from my home directory, I typed `cd /?ha??enge`, where the ? symbol stood in for the c and l in "challenge." This let the shell match the correct directory without me typing the full name. After navigating to /challenge, I simply ran the `/challenge/run` command to grab the flag.
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EOCQEincxnGKAaxCyXLDur23xxe.dJjM4QDLxcDO0czW}
```
##  Matching with []
First, I navigated to the /challenge/files directory using `cd /challenge/files`. Once there, I ran the command `/challenge/run file_[absh]`, where the square brackets allowed me to target the specific files file_b, file_a, file_s, and file_h. The brackets let me match any of the listed characters in that position, so the shell only picked those files. After running the command, I was able to capture the flag.
```
hacker@globbing~matching-with-:/challenge$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[abhs]
You got it! Here is your flag!
pwn.college{klN21LvRxJSUajYbUrUtszznEzz.dNjM4QDLxcDO0czW}
```
##  Matching paths with []
To solve this, I used bracket globbing to target specific files by their absolute paths. Starting from my home directory, I ran the command /challenge/run /challenge/files/file_[absh]. Here, the square brackets allowed me to match the characters for the specific files file_b, file_a, file_s, and file_h in the /challenge/files directory.
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{U_9dK4YFZ815DFXVVfGkuv4Wywn.dRjM4QDLxcDO0czW}
```
##  Exclusionary Globbing
To solve this, I used the bracket inversion technique to filter out files that start with specific characters. First, I navigated to the /challenge/files directory using `cd /challenge/files`. Once there, I ran the command `/challenge/run [!pwn]*`, which used the ! inside the brackets to exclude any files starting with p, w, or n. The * wildcard ensured that any other files not beginning with those letters would be matched. 
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{wjr2jWDJi3jfmBIOg7c21SqR0tY.dZjM4QDLxcDO0czW}
```





