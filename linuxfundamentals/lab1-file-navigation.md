# Linux Fundamentals 1

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Linux Fundamentals  
**Difficulty:** Easy  

---

## 🎯 Learning Objectives
- Learn the first commands and the basics of navigation on Linux OS
- How to search files and the basics of shell operators
- The most common uses to linux systems

---

## 📖 Key Concepts (in my own words)
- File Navigation
- Shell Operators
- CTF Fundamentals

---

## 🛠️ Practical Application

### Step 1 - [Learn the "echo" and the "whoami"]
```bash
echo hello
```
```bash
whoami
```
### Step 2 - [The Basic of Navigation]
ls = listing - Lists the files and directories in the current directory.

```bash
ls
```

cd = change directory - Changes the current directory.

```bash
cd
```
cat = concatenate - Displays the contents of a file in the terminal.

```bash
cat
```
pwd = print working directory - Shows the full path of the current directory.

```bash
pwd
```
### Step 3 - [Searching for Files]

find = find - earches for files and directories based on name, type, or other attributes.

```bash
find . -name "file.txt"
```
. refers to the current directory.

grep = grep - Searches for specific text patterns inside files.

```bash
grep "hello" file.txt
```
Combining "find" and "grep":

```bash
find . -type f -name "*.txt" -exec grep "hello" {} \;
```
### Step 4 - [Operators]

& - Allows you to run commands on your background
&& - Combines multiple commands
> - Allows you to take the output of a command and direct it elsewhere
>> - Same of > but nothing is overwrited

## Why it matters

These commands are the foundation of terminal navigation in a Linux system. Commands like `whoami` help you identify the current user, while commands such as `ls`, `cd`, `cat`, and `pwd` make navigation faster and more efficient, allowing you to focus on what actually matters. Furthermore, shell operators enable you to perform multiple operations at the same time.

