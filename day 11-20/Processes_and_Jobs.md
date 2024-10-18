## Listing processes
To solve this challenge, I used the `ps` command to list running processes and identify the hidden process in the system. Since I couldn't directly view the files in the /challenge directory, I relied on the running process list to find the renamed executable. I used ps -ef to view the full list of processes and their respective commands. By carefully examining the command column, I found the process related to the challenge. Once I had the process command name, I was able to relaunch it from the terminal and capture the flag.
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 20:52 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 20:52 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 20:52 ?        00:00:00 /challenge/24443-run-4452
root          72      68  0 20:52 ?        00:00:00 sleep 6h
hacker        73       0  0 20:52 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 20:52 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/24443-run-4452
Yahaha, you found me! Here is your flag:
pwn.college{InZcaqMJoFMpKOco0jmcJlA8nrP.dhzM4QDLxcDO0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
##   Killing process
To solve this challenge, I first listed the running processes using `ps -e` and piped the output through grep to filter for the process named `dont_run`. This gave me the process ID (PID) of the dont_run process. Once I had the PID, I used the `kill` command to terminate it,
```
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 21:05 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 21:05 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 21:05 ?        00:00:00 su -c /challenge/.launcher hacker
hacker        73      71  0 21:05 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 21:05 ?        00:00:00 sleep 6h
hacker        75       0  0 21:05 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       104      75  0 21:08 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$  /challenge/run
Great job! Here is your payment:
pwn.college{4mUwh5oPk196Y7C933_gaZs4i1v.dJDN4QDLxcDO0czW}
```
##  Interrupting processes
To solve this challenge, I started the `/challenge/run` process. Since the process wouldn’t provide the flag until it was interrupted, I used the `Ctrl-C` hotkey to send an interrupt signal to the running process. This allowed it to cleanly exit, and after doing so, the process returned the flag successfully. By sending the interrupt, I was able to terminate the process directly from the terminal and complete the challenge!
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{AiNhINnQlhpUEW_SIWlv-ZO_7kT.dNDN4QDLxcDO0czW}
```
##  Suspending Processes
I first launched the `/challenge/run` process in the terminal. Once it was running, I used `Ctrl-Z` to suspend the process, sending it to the background. Next, with the first process suspended, I launched another instance of `/challenge/run` in the same terminal. By having the first process suspended and the second one running, I was able to meet the condition for the challenge and successfully complete it!
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          85      65  0 21:26 pts/0    00:00:00 bash /challenge/run
root          87      85  0 21:26 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          85      65  0 21:26 pts/0    00:00:00 bash /challenge/run
root          92      65  0 21:26 pts/0    00:00:00 bash /challenge/run
root          94      92  0 21:26 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{o64TTuDPtdaboiGEL0PYt4bAssq.dVDN4QDLxcDO0czW}
```
##  Resuming processes
To solve this challenge, I first launched the `/challenge/run` process in the terminal. Then, I suspended the process using `Ctrl-Z`, which sent it to the background.

Next, to resume the suspended process, I used the `fg` command, which brought the process back to the foreground, allowing it to continue running.
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{0qlwbiNndA00z0DI3vEtDt8Colp.dZDN4QDLxcDO0czW}
Don't forget to press Enter to quit me!

Goodbye!
```
##  Backgrounding processes
I first launched the /challenge/run process in the terminal. Once it was running, I used Ctrl-Z to suspend it.

Next, I resumed the suspended process in the background by running the bg command. This allowed the process to continue running while giving me control of the terminal again.

With the first process running in the background, I launched another instance of /challenge/run.
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{oLVmqs-aeuxU_R4VACkwpuSp8Kl.ddDN4QDLxcDO0czW}
```
##  Foregrounding processes
To solve this challenge, I first launched the `/challenge/run` process and then used `Ctrl-Z` to suspend it. After that, I resumed the process in the background by typing the `bg` command.

Once the process was running in the background, I used the `fg` command to bring it back to the foreground.
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{8FFIZNRfjAdGkZ99DQstmnONyM2.dhDN4QDLxcDO0czW}
```
##  Staring background processes
To solve this challenge, I launched the `/challenge/run` process directly in the background by appending the `&` symbol to the command
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 95
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{kdMjFLoBnIy1fXDMs3P4VzHh37V.dlDN4QDLxcDO0czW}
```
##  Process exit codes
To solve this challenge, I first ran the /challenge/get-code command to retrieve its exit code. After the process completed, I checked the exit code by running `echo $?`. This displayed the exit code from the last command. Once I had the exit code, I passed it as an argument to the `/challenge/submit-code` command.
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
89
hacker@processes~process-exit-codes:~$ /challenge/submit-code 89
CORRECT! Here is your flag:
pwn.college{U2RcANoVAf-JUBK8DwuRcsU-ZBS.dljN4UDLxcDO0czW}
```





