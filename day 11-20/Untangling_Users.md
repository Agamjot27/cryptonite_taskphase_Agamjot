##  Becoming root with su
In this challenge, I used the `su` (switch user) command to elevate my privileges to root. Since the su command has the SUID bit set, it allows the binary to run as root, which is typically used to switch users. To solve the problem, I executed su and provided the root password, "hack-the-planet," as instructed. Once authenticated, I gained root access and was able to read the flag.
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{IduaGIuYz2IK90wVVbnVJq8Yqvc.dVTN0UDLxcDO0czW}
```
##  other users with su
n this challenge, I used the su command to switch to the user "zardus" by providing the username as an argument. To do this, I ran su zardus and, when prompted, entered the password "dont-hack-me." After successfully authenticating, I switched to the "zardus" user and gained access to their environment. From there, I executed the required program `/challenge/run`, completing the task.
```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{YW7PVDqKCtU144q3SJFY_LOXrOO.dZTN0UDLxcDO0czW}
```
##  Cracking passwords
In this challenge, I simulated a scenario where a leaked `/etc/shadow` file could be used to crack a user's password. The file contains hashed passwords, which are normally protected, but in this case, I used the password-cracking tool "John the Ripper" to reveal the actual password for the user "zardus." By running `john /challenge/shadow-leak`, I let the program crack the hash, which eventually revealed the password. Once I had the password, I used su zardus to switch to the "zardus" user and then executed `/challenge/run` to complete the task. 
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:04 48% 1/3 0g/s 249.6p/s 249.6c/s 249.6C/s Mrz99999..zArDuS99999
0g 0:00:00:13 0% 2/3 0g/s 251.8p/s 251.8c/s 251.8C/s leslie..boston
aardvark         (zardus)
1g 0:00:00:22 100% 2/3 0.04472g/s 260.4p/s 260.4c/s 260.4C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{kaP3lQetK4O_ncSYCgbI3iYO18V.ddTN0UDLxcDO0czW}
```
##  Using Sudo

In this challenge, I utilized the sudo command to elevate my privileges and access the flag. Unlike su, which switches users and requires a password, sudo allows running individual commands as root based on user permissions defined in /etc/sudoers. First, I ran sudo with the command needed to access restricted files or resources, such as reading the flag file.
```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{YQ8MKzxJIB-OG1xOqhITypTqpxU.dhTN0UDLxcDO0czW}
```

