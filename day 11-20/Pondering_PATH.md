##  The PATH VAriable
To solve this challenge, I manipulated the PATH variable to disrupt the operation of the `/challenge/run` program. The program attempts to delete the flag using the `rm` command. Since shell programs rely on the PATH variable to locate commands, I emptied the PATH variable before running the challenge. By doing this, the shell couldn’t locate the `rm` command, preventing the flag from being deleted. After executing the command with the blank PATH, the program failed to find `rm`, and I successfully retrieved the flag without deletion.
```
hacker@path~the-path-variable:~$ $PATH
ssh-entrypoint: /run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin: No such file or directory
hacker@path~the-path-variable:~$ PATH=" "
hacker@path~the-path-variable:~$  /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: command not found
The flag is still there! I might as well give it to you!
pwn.college{g8VEBh3MmJQ2sl3EDP_PzXjFH4Q.dZzNwUDLxcDO0czW}
```
##  Setting path
To solve this challenge, I modified the PATH variable to include the directory where the `win` command is located. By default, the shell could not locate `win` because it resided in the `/challenge/more_commands/` directory, which wasn’t part of the current PATH. To fix this, I set the PATH variable to point directly to `/challenge/more_commands/`. After updating the PATH, the shell could now recognize and execute `win` by its bare name when `/challenge/run` called it.
```
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ win /challenge/run
It looks like 'win' was improperly launched. Don't launch it directly; it MUST
be launched by /challenge/run!
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{MU0aocFZNERMu_KQJLoVaXq0WsL.dVzNyUDLxcDO0czW}
```
##  Adding Commands











