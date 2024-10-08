#  Comprehending Commands
##  cat: not the pet, but the command!
To solve this challenge, I used the cat command, which is one of the most useful Linux tools for reading files. The task was to read a flag file placed in my home directory. I simply navigated to my home directory and ran the cat flag command, which displayed the contents of the flag file right in my terminal. It was a straightforward solution
```
cd /
cat ~/flag../
```
##  catting absolute paths
To solve this challenge, I again used the cat command, but this time I had to specify the absolute path to the flag file instead of finding it in my home directory. The flag was stored in /flag, so I simply ran the command `cat /flag` to read its contents directly.
Also I referred to this video to understand in depth-
<a "https://youtu.be/QFIq_e5t6iQ?si=LjseI-tjGvcaWMaV"></a>
##  more catting practice
To solve it, I had to rely on using the absolute path with the cat command. I found the flag by specifying its full path directly, running something like cat `/crazy/directory/path/flag` to retrieve the flag, Now I don't remember the exact path because I am writing this report way after solving that.
##  grepping for a needle in haystack
In this challenge, the file was filled with a hundred thousand lines of text, so using cat alone wouldn't be practical. Instead, I used the grep command to search for the specific pattern that identifies the flag. Since the hint mentioned that the flag starts with "pwn.college," I ran the command  `grep 'pwn.college' /challenge/data.txt` to quickly find the line containing the flag.
##  listing files
I needed to find a file with a random name in the /challenge directory. To do this, I used the ls command, which lists the contents of directories. I ran `ls /challenge` to display all the files and directories inside, which revealed the randomly named file I needed to interact with.
##  touching files
In this challenge, I needed to create two files in the /tmp directory using the touch command. I first navigated to the /tmp directory and then used the following commands: `touch /tmp/pwn` and `touch /tmp/college`. These commands created the two blank files required for the task. After that, I ran the /challenge/run command to retrieve the flag.
##  removing files
The goal here was to remove the delete_me file from my home directory. I started by listing the contents of the directory to ensure the file was there, and then I used `rm ~/delete_me` to delete it. Afterward, I ran `/challenge/check`, which confirmed that the file had been successfully deleted, and I got the flag. 
##  hidden files
In this challenge, the flag was hidden as a dot-prepended file, meaning it wouldn’t show up with a normal ls command. To solve it, I used the ls -a command in the root directory (/), which lists all files, including those starting with a dot. This revealed the hidden file, and once I found it, I was able to retrieve the flag by running something like `cat /flag` (I don't remember exactly.)
##  An epic file system quest
As the name of the task suggests it truly was an epic quest. In this challenge, I was tasked with finding the flag hidden somewhere in the file system using the `cd`, `ls`, and `cat` commands. I started by navigating to the root directory (/) and listed its contents with ls. I found a file labeled HINT among the various directories and files. Using `cat HINT`, I read the clue, which directed me to another location in the file system. I followed the clues sequentially, moving from one directory to the next, until I eventually discovered the flag.                                                        
It took some time but yeah it was fun.
##  making directories
In this task, I was tasked with creating a directory and a file. I navigated to the /tmp directory and used the  `mkdir /tmp/pwn` command to create a new directory named pwn. Then, I changed into that directory and created a file called college using the `touch /tmp/pwn/college` command. After that, I ran `/challenge/run `to verify that everything was in order and to receive the flag.
##  finding files
I had to locate a hidden flag in a random directory on the filesystem using the find command. I started by using find without any arguments to get an overview of my current directory. After that, I specifically searched for the file named flag by running `find / -name flag`. Since there are multiple files with that name on the filesystem, I kept looking until I found the correct one. This required a lot of patience.
##  linking files
The goal was to access the flag located in /flag by first creating a symlink that redirected a different file path. I used the command `ln -s /flag /home/hacker/not-the-flag` to create a symbolic link. When I accessed `/challenge/catflag`, which was designed to read from `/home/hacker/not-the-flag`, it actually followed the symlink and provided me with the contents of /flag. 
I also referred to this video below to better understand links-
<a https://youtu.be/4-vye3QFTFo?si=3-m2n8YaBV8vxp1f></a>










