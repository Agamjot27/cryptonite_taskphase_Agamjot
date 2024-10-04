#  Linux Luminarium Module
##  The Root
For this challenge, I had to capture a flag by running a program called pwn, which was placed in the root directory (/). The task was to use the absolute path to execute it from the terminal. I simply typed /pwn in the terminal and the program ran successfully, providing the flag.
## Program and Absolute paths
The goal was to run a program called run located inside the /challenge directory. The challenge directory is placed directly under the root directory, so the absolute path to the program was /challenge/run. Once I entered the command, the program ran, and I successfully captured the flag
##  Position thy self
I had to execute the /challenge/run program, but this time from a specific directory, meaning I needed to change the current working directory first. Using the cd (change directory) command, I was able to navigate to the required directory before running the program.
##  Position elsewhere
Similar to the previous task I had to change the dictionary and simply execute the command once again to capture the flag.
##  Positon Yet Elsewhere
Again similar to the previous task I had to change the dictionary and simply execute the command.
##  Implicit relative paths, from /
For this challenge, the goal was to run the /challenge/run program using a relative path while my current working directory (cwd) was set to /. Since relative paths don't start with /, they depend on where you're currently located, and in this case, I had to work from /
cd /  
challenge/run  
This worked, and I was able to capture the flag.
##  Explicit relative paths, from /
I had to run the /challenge/run program again, but this time I had to use the . notation in the relative path. The dot (.) refers to the current directory, so it’s an explicit way to say "stay in this directory" before moving to another one.
./challenge/run
This command worked exactly like before, and I was able to capture the flag
##  Implicit relative path
