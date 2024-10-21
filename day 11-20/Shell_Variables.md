##  Printing variables
To solve this problem, I used the echo command in the shell to print the value of the "FLAG" variable. The echo command is straightforward and is used to display text or the value of a variable in the terminal. Since the flag was stored in a variable named FLAG, I simply printed it by prepending the variable name with a $ symbol, like this:
```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{orvzIscUmwZG_VyJA4lTV_kZgTo.ddTN1QDLxcDO0czW}
```
##  Setting Variables
To solve this problem, I used the shell to assign a value to the PWN variable. In the shell, variables are set using the = operator, with no spaces around it. In this case, I needed to set the PWN variable to the value COLLEGE.
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{0a3pOqZcdmhW7M9x9l_RHeEMlTT.dlTN1QDLxcDO0czW}
```
##  Multi word variables
I used quotation marks to handle spaces in the value assignment for the PWN variable. Since spaces in shell commands can cause issues by separating arguments, I enclosed the value in quotes to treat it as a single string. To set PWN to COLLEGE YEAH, I used the following command:
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{0gTjdYP-yhouAUOwLq058zPoqhc.dBjN1QDLxcDO0czW}
```
##  Exporting Variables
To solve this challenge, I needed to properly set and export variables for a child process, ensuring one variable was inherited while the other was not. First, I set the PWN variable to COLLEGE and used the export command to ensure it would be available in the environment of the /challenge/run process. Then, I set the COLLEGE variable to PWN without exporting it, so it remained local to the current shell.
```
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run PWN
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{4KmkDhHUQ2H41Mziyr8YpxLMw0O.dJjN1QDLxcDO0czW}
```
##  Printing Exported Values
To solve this problem, I used the `env` command, which lists all the exported environment variables in the current shell. Since the FLAG variable was exported, running env allowed me to locate and display its value.
```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=b306fd79dc410595e19b96701863ae5ee3b6fac4d2bb664c16c05533d433aa06
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
FLAG=pwn.college{U5uUPYGyblidgYR1e3aLG6Kxvqg.dhTN1QDLxcDO0czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
```
This printed out all the environment variables, and by scrolling through the output, I was able to find the `FLAG` variable, which solved the challenge.
`FLAG=pwn.college{U5uUPYGyblidgYR1e3aLG6Kxvqg.dhTN1QDLxcDO0czW}`
##  Storing command output
o solve this challenge, I used command substitution to capture the output of the /challenge/run command into the PWN variable. Command substitution is done by wrapping the command inside $() so that the shell runs the command and stores its output in the variable.
`PWN=$(/challenge/run)`
After running this, the PWN variable contained the output of the command, which was the flag. To verify, I printed the variable:
`echo "$PWN"`
```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{oPwWCOTeEZrdnNyHJYP2AYvul5S.dVzN0UDLxcDO0czW}
```
##  Reading Input
To solve this challenge, I used the `read` command to capture user input and store it in the PWN variable. The read command waits for input from the user, and whatever is entered gets stored in the specified variable. I then entered COLLEGE when prompted.
```
hacker@variables~reading-input:~$ echo $PWN

hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{EeJRRhQFCvnSFwjS0UzsTgpcMcn.dhzN1QDLxcDO0czW}
```
##  Reading Files
To solve this challenge, I used the read command along with input redirection to read the contents of `/challenge/read_me` directly into the `PWN` variable. Instead of using cat, I redirected the file as input to read, which efficiently assigns its contents to the variable.
```
hacker@variables~reading-files:~$  read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{MsgSMmlqMpRhY2EVrnD0saJxlDH.dBjM4QDLxcDO0czW}
```


















