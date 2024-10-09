##  Redirecting output
To solve this problem, I used input redirection to write the word "PWN" into a file called "COLLEGE." By utilizing the echo command and the > operator, I redirected the output of the command to the file. Specifically, I executed the following command:
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{Azwr6eJ66Z8ieuY2dt9zs2dCAJh.dRjN1QDLxcDO0czW}
```
##  Redirecting more output
To tackle this challenge, I simply redirected the output of the /challenge/run command to a file called "myflag."After that, I checked the contents of the "myflag" file using cat to make sure everything went smoothly.
`cat myflag` This showed me the flag, confirming that I captured it correctly, while the rest of the output stayed on the terminal screen.
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{MitsK03xQxVnMWJG65lRtgBO4YW.dVjN1QDLxcDO0czW}
```
##  Appending output
In this challenge, I needed to save the output of the /challenge/run command while ensuring that I didn't lose any previously captured data in the file. Since using the > operator would overwrite the file each time, I switched to append mode by using >>. This way, I could capture both halves of the flag without any issues. `/challenge/run >> /home/hacker/the-flag` This command appends the first half of the flag to the file `/home/hacker/the-flag`. If I redirected standard output correctly, the second half of the flag would also be appended, ensuring I had the complete flag saved in one place. To check my work, I used the cat command:
```
cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{U7Wg_uVwogGNsasDH8KuCJzHoGG.ddDM5QDLxcDO0czW}
                              ^
     that is the second half /|\
                              |
```
##  Redirecting errors
For this challenge, I had to handle both the output and error channels separately by redirecting them to different files. The `/challenge/run` command needed to send its standard output (the flag) to a file called "myflag," while standard error (the instructions) was redirected to a file named "instructions." This ensured that the flag ended up in the "myflag" file, and any instructions or feedback were saved in the "instructions" file. 
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{IWZ8msGBEUDOY0B9Chme2s9fSHU.ddjN1QDLxcDO0czW}
```
##  Redirecting input
In this challenge, I needed to use input redirection to feed a file into the /challenge/run program. First, I created the PWN file and made sure it contained the value "COLLEGE" using the `echo`. After writing "COLLEGE" into the PWN file, I redirected that file as input into the `/challenge/run` command using the `<` operator, like this:
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{ks2FzPsFkGn-1MXgDdntrqoy3po.dBzN1QDLxcDO0czW}
```
##  Grepping stored results
In this challenge, we are required to redirect the output of `/challenge/run` to `/tmp/data.txt`. Then, we need to search through this text file for the flag. We know the flag begins with pwn.college so we search for that.
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.

hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{cuwFD51UCBg_nO0HK2KSX2AEv6O.dhTM4QDLxcDO0czW}
```
##  Grepping live output

For this challenge, I discovered how to simplify the process of finding the flag by using the pipe operator (|). Instead of saving the output of the /challenge/run command to a file first, I could directly send its output into the grep command to search for the flag.This executed the command, and as the output streamed in, it was filtered by grep to display only the line containing the flag.
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Qhryqu3rV_5uLjtaTFJ2ZBOAmZ0.dlTM4QDLxcDO0czW}
```
##  Grepping errors
The goal was to search through the standard error output directly using grep. Since the pipe (|) normally only works with standard output, I had to use a trick by redirecting standard error (file descriptor 2) to standard output (file descriptor 1) with `2>&1`. This allowed me to pipe both outputs into grep to find the flag.
`/challenge/run 2>&1 | grep pwn.college`
```
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{MBYjCqyG00lf0byzFiq0k808PUI.dVDM5QDLxcDO0czW}
```
##  duplicating piped data with tee
In this challenge, I needed to use the tee command to see the data flowing through the pipe while also passing it on to the next command. The task involved piping the output of `/challenge/pwn` into `/challenge/college` but first intercepting that output to understand what it required. The tee command intercepted the data, showing it on my screen and also saving it to the intercepted_output file. This allowed me to see what /challenge/pwn was producing and verify that it was being passed to /challenge/college correctly. By checking the contents of intercepted_output: `cat intercepted_output`
```
hacker@piping~duplicating-piped-data-with-tee:~$ cat intercepted_data
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "0briYS5Q"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret "0briYS5Q" | tee intercepted_data | /challenge/
college
Processing...
WARNING: you are overwriting file intercepted_data with tee's output...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{0briYS5Q-mt423lKUDLNIUyP3Pn.dFjM5QDLxcDO0czW}
```
## Writing to Multiple Programs


In this challenge, we can solve it using `/challenge/hack`, `/challenge/the`, and `/challenge/planet`. The goal is to take the output from `/challenge/hack` and pass it as input to both `/challenge/the` and `/challenge/planet` using `tee` along with process substitution.


The `tee` command duplicates the output of a command, allowing it to be sent to multiple destinations.
 Process substitution allows us to use the output of a command as input for another command in a way that the receiving command treats it as a file.
 **Command Breakdown:**
   `/challenge/hack`: This command generates the output you want to duplicate.
   `|`: The pipe operator sends the output of `/challenge/hack` to `tee`.
    `tee`: This command takes the output from `/challenge/hack` and duplicates it.
   `>( /challenge/the )`: This process substitution allows the output of `tee` to be passed as input to `/challenge/the`.
   `>( /challenge/planet )`: Similarly, this allows the output to also be passed as input to `/challenge/planet`.

```bash
/challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
```

## Split Piping stderr and stdout

In this challenge, we are supposed to redirect the output from `/challenge/hack` such that standard output (stdout) goes to `/challenge/planet` and standard error (stderr) goes to `/challenge/the`, while keeping them separate.

We can do this with the following command:
```bash
/challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
```



 `/challenge/hack`: This command runs and produces output on both stdout and stderr.
 `>`: This operator is used to redirect stdout.
 `>( /challenge/planet )`: This is a process substitution. It creates a temporary named pipe and connects it to the stdin of `/challenge/planet`. The stdout of `/challenge/hack` will be sent through this pipe to `/challenge/planet`.
  `2>`: This operator is used to redirect stderr.
 `>( /challenge/the )`: Similar to the previous substitution, this creates another temporary named pipe that connects stderr from `/challenge/hack` to the stdin of `/challenge/the`.
```bash
/challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
```

When you execute `/challenge/hack`, it generates both stdout and stderr. 
 The `>` operator redirects stdout to `/challenge/planet` through the named pipe created by `>( /challenge/planet )`.
 The `2>` operator redirects stderr to `/challenge/the` through the named pipe created by `>( /challenge/the )`.

---




