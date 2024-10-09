# Digesting Documentation

## **Learning from Documentation**

### Description
In this challenge, we are required to pass the command `/challenge/challenge` with the argument `--giveflag`.


```bash
/challenge/challenge --giveflag
```
# Digesting Documentation

---

## **Learning from Documentation**

In this challenge, we are required to pass the command `/challenge/challenge` with the argument `--giveflag`.

- The full command is `/challenge/challenge --giveflag`.
- Both `-` and `--` are used for arguments; however, `-` is followed by a letter (condensed form)
  while `--` is followed by the command name (expanded form).



```bash
/challenge/challenge --giveflag
```

## **Learning Complex Usage**

In this challenge, we are required to pass the argument `--printfile` 
with the path to the flag after it.

The command structure is `/challenge/challenge --printfile <path_to_flag>`.
 In this case, we use `/flag` as the path to the flag.




```bash
/challenge/challenge --printfile /flag
```


---
## Reading Manuals


In this challeng we are required to use the `man` command which displays the manual pages for other commands and concepts. Here we are supposed to use the `man` command for the program `challenge`. Hence
 we execute `man challenge`. This presents us with the manual for the command `/challenge/challenge`. In the arguments section we see 3 options with the argument `--gyjzaq NUM` being the best as it returns the flag if we set `NUM` as `661`.

 The `man` command shows the manual or documentation for a given command.
 To use the correct argument for the command you need to carefully read the manual's argument section.



```bash
man challenge

/challenge/challenge --gyjzaq 661
```


---

## **Searching Manuals**

In this challenge, we are supposed to search through the manual to find the correct argument to return the flag. We do `man challenge` to first open the manual.
Once opened, we do `/nameofitem`. `nameofitem` is what we want to search for, in this case, "flag". So we do `/flag`, which allows us to search for all instances of "flag". We move across these instances by pressing `n`. We find that the argument is called `--zzeg`.

```bash
/challenge/challenge --zzeg
```


---

## **Searching for Manuals**

In this challenge, we need to find the command argument for `/challenge/challenge`. Unfortunately, we cannot find a manual entry for "challenge," so we start by opening `man man`. We then see a description for a command that searches for man page names and descriptions related to a word 'man -k challenge'. This returns a command called gofuewroff.
To learn more about this command man gofuewroff we can do man for it. Here, we find that the command has the argument '--gofuew NUM', which prints the flag if NUM is 824.

 In the `man man` page, we discover the `man -k` command, which searches for man page names and descriptions related to a specific word.




```bash
 man -k challenge
```
```bash
/challenge/challenge --gofuew 824
```


---

## **Helpful Programmes**

In this challenge, we are tasked with assuming that `/challenge/challenge` does not have a man page. To find the available commands, we can use the `--help` option.
When doing this 2 commands stand out two stand out: *-g GIVE_THE_FLAG*, *--give-the-flag GIVE_THE_FLAG* get the flag, if given the correct value -p, --print-value print the value that will cause the -g option to give you the flag


Running the command `/challenge/challenge --help` reveals several commands abd functions about the command /challenge/challenge.




```bash
 /challenge/challenge --print-value 
```

```bash
/challenge/challenge -g 554
```


---

## **Help for Builtins**

In this challenge, we are supposed to use the help command to identify and learn how to use the challenge command. We do this by typing `help challenge`.
The command structure provided is:

'challenge [--fortune] [--version] [--secret SECRET]'
Only the '--secret' option is valid for retrieving the flag, and the correct secret value to pass is "YP7mlzAu".

 The help command gives us information about the usage of the command

```bash
challenge --secret "YP7mlzAu"
```



---


