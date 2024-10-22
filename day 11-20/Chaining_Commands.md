##  Chaining with semicolons 
To solve this problem, I used command chaining with a semicolon (;) to run two commands in sequence without needing to wait for the first command to finish before typing the second. I executed the `/challenge/pwn` program and then chained it with `/challenge/college` by writing the command as `/challenge/pwn; /challenge/college`.
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{4mTFqEIJXH4eqT6oDKdQ3p7-IwT.dVTN4QDLxcDO0czW}
```
##  Your first shell script
To solve this problem, I created a shell script called `x.sh` that contained both commands needed to complete the challenge. Inside the script, I included `/challenge/pwn` and `/challenge/college` on separate lines. Instead of running the commands directly in the terminal, I executed the script using `bash x.sh`, which allowed the shell to read and execute the commands from the file automatically.
```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{8VEZ3faMRGV5EVM_oXMoU1a_jkC.dFzN4QDLxcDO0czW}
```
##  Redirecting Script output
To solve this problem, I created a script named script.sh that contains the necessary commands to run `/challenge/pwn` and `/challenge/college`. Then, instead of directly viewing the output, I piped the output of the script into the `/challenge/solve` command to complete the task.
```
hacker@chaining~redirecting-script-output:~$ touch script.sh
hacker@chaining~redirecting-script-output:~$ nano script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{c8xtUh9oYfNjE2IXiW5sVI1ae5O.dhTM5QDLxcDO0czW}
```
##  Executable shell scripts
To solve this problem, I created a shell script and made it executable so it could be run directly without invoking bash explicitly.

Here’s how I did it:
```
hacker@chaining~executable-shell-scripts:~$ touch x.sh
hacker@chaining~executable-shell-scripts:~$ nano x.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{sxWdvZijalSpak287908_R6_YqR.dRzNyUDLxcDO0czW}
```










