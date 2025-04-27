# Unit 2 Lab

### Resources / Important Links

- [Killercoda Labs](https://killercoda.com/learn)
- [Top 50+ Linux CLI Commands](https://www.digitalocean.com/community/tutorials/linux-commands)

### Required Materials

- Putty or other connection tool
- Rocky 9.4+ - ProLUG Lab
  - Or comparable Linux box
- root or sudo command access

## Pre-Lab Warm-Up

---

EXERCISES (Warmup to quickly run through your system and familiarize yourself)

```bash
cd ~
ls
mkdir evaluation
mkdir evaluation/test/round6
# This fails, can you find out why?
# Answer: It fails because the directory "test" doesn't exist.

mkdir -p evaluation/test/round6
# This works, think about why?
# Answer: The -p parameter has mkdir make any parent directory that doesn't exist.

cd evaluation
pwd
# What is the path you are in?
# Answer: /root/evaluation

touch testfile1
ls
# What did this do?
# Answer: It created a file called "testfile1".

touch testfile{2..10}
ls
# What did this do differently than earlier?
# Answer: It created a list of files from testfile2 all the way through testfile10
# touch .hfile .hfile2 .hfile3

ls
# Can you see your newest files? Why or why not? (man ls)
# Answer: No you can't see the newer files because they are hidden.
# What was the command to let you see those hidden files?
# ls -a

ls -l
# What do you know about this long listing? Think about 10 things this can show you.
# Answer: 
# It'll show me:
# 
# 1. Whether the file is a directory or a file
# 2. Owner Read, Write, Execute permissions
# 3. Group Read, Write, Execute permissions
# 4. Everyone elses Read, Write, Execute Permissions
# 5. The UID of the owner
# 6. The GID of the group
# 7. The file size in bytes
# 8. The number of links the file/directory has
# 9. The created month of the file/directory
# 10. The modified time of the the file/directory
#
# Did it show you all the files or are some missing?
# Answer: Some are missing.  Would need to run "ls -al" to get the hidden files as well.
```

## Lab 

---

This lab is designed to help you get familiar with the basics of the systems you will be working on. Some of you will find that you know the basic material but the techniques here allow you to put it together in a more complex fashion.

It is recommended that you type these commands and do not copy and paste them. Word sometimes likes to format characters and they don’t always play nice with Linux.

#### Gathering system information:

```bash
hostname
cat /etc/*release
# What do you recognize about this output? What version of RHEL (CENTOS) are we on?
# Answer: The hostname is the same name as the OS. Version 9.5.

uname
uname -a
uname -r

# man uname to see what those options mean if you don’t recognize the values
# Answer:
# uname - prints system info
# uname -a - prints all system info
# uname -r - prints kernel release
```

#### Check the amount of RAM:

```bash
cat /proc/meminfo
free
free -m

# What do each of these commands show you? How are they useful?
# Answer: 
# /proc/meminfo shows all information about the memory on the system.
# free command shows free/used memory on the system.
# free command with the -m parameter shows the same info but in "mebibytes".
```

#### Check the number of processors and processor info:

```bash
cat /proc/cpuinfo
# What type of processors do you have? How many are there? (counting starts at 0)
# Answer: Intel processors and there's two.
cat /proc/cpuinfo | grep proc | wc -l
# Does this command accurately count the processors?
# Answer: I'd say it does.
```

#### Check Storage usage and mounted filesystems:

```bash
df
# But df is barely readable, so find the option that makes it more readable `man df`

df -h
df -h | grep -i var
# What does this show, or search for? Can you invert this search? (hint `man grep`
# look for invert or google “inverting grep’s output”)
# Answer: It shows the file system disk usage and formats it in human-readable
# format. The second command searches for anything containing "var".
# 
# To invert the search pattern in grep, just ad the -v parameter.


df -h | grep -i sd
# This one is a little harder, what does this one show? Not just the line, what are
# we checking for? (hint if you need it, google “what is /dev/sda in linux”)
# Answer: We're checking to see block devices attached to the system. 


mount
# Mount by itself gives a huge amount of information. But, let’s say someone is asking
# you to verify that the mount is there for /home on a system. Can you check that
# quickly with one command?

mount | grep -i home
#This works, but there is a slight note to add here. Just because something isn’t
# individually mounted doesn’t mean it doesn’t exist. It just means it’s not part of
# it’s own mounted filesystem.

mount | grep -i /home/xgqa6cha
# will produce no output

df -h /home/xgqa6cha
# will show you that my home filesystem falls under /home.

cd ~; pwd; df -h .
# This command moves you to your home directory, prints out that directory,
# and then shows you what partition your home directory is on.

du -sh .
# will show you space usage of just your directory

try `du -h .` as well to see how that ouput differs
# read `man du` to learn more about your options.
```

#### Check the system uptime:

```bash
uptime

man uptime
# Read the man for uptime and figure out what those 3 numbers represent.
# Referencing this server, do you think it is under high load? Why or why not?
# Answer: The 3 numbers represent the system load time for the last 1, 5, 15
# minutes. The server I'm on has 0, 0, 0 so it's not under any load.
```

#### Check who has recently logged into the server and who is currently in:

```bash
last
# Last is a command that outputs backwards. (Top of the output is most recent).
# So it is less than useful without using the more command.

last | more
# Were you the last person to log in? Who else has logged in today?
# Answer: It just shows root.  I don't think I was the last person to login today
# but I only see root logged in in the past.

w
who
whoami
# how many other users are on this system? What does the pts/0 mean on google?
# Answer: No one else at the moment. PTS connections are ssh or telnet connections
# to the system. So pts/0 means I'm connected via ssh, in this case, and
# am the only one connected. If another user remotes in, it would show
# pts/1 for them and the number increments based on number of connected
# parties.
```

#### Check who you are and what is going on in your environment:

```bash
printenv
# This scrolls by way too fast, how would you search for your home?

printenv | grep -i home
whoami
id
echo $SHELL
```

#### Check running processes and services:

```bash
ps -aux | more
ps -ef | more
ps -ef | wc -l
```

#### Check memory usage and what is using the memory:

```bash
# Run each of these individually for understanding before we look at part b.
free -m
free -m | egrep “Mem|Swap”
free -m| egrep “Mem|Swap” | awk ‘{print $1, $2, $3}’
free -t | egrep "Mem|Swap" | awk '{print $1 " Used Space = " ($3 / $2) * 100"%"}'

# Taking this apart a bit:
# You’re just using free and searching for the lines that are for memory and swap
# You then print out the values $1 = Mem or Swap
# You then take $3 used divided by $2 total and multiply by 100 to get the percentage
```

Have you ever written a basic check script or touched on conditional statements or loops? (Use ctrl + c to break out of these):

```bash
while true; do free -m; sleep 3; done

# Watch this output for a few and then break with ctrl + c
# Try to edit this to wait for 5 seconds
# Try to add a check for uptime and date each loop with a blank line between
# each and 10 second wait:

while true; do date; uptime; free -m; echo “ “; sleep 10; done
# Since we can wrap anything inside of our while statements, let’s try adding
# something from earlier:
while true; do free -t | egrep "Mem|Swap" | awk '{print $1 " Used Space = " ($3 / $2) * 100"%"}'; sleep 3; done
```

```bash
seq 1 10
# What did this do?
# Answer: printed to the terminal the numbers 1 through 10.
# Can you man seq to modify that to count from 2 to 20 by 2’s?
# Answer: seq 2 2 20
# Let’s make a counting for loop from that sequence

for i in `seq 1 20`; do echo "I am counting i and am on $i times through the loop"; done
```

Can you tell me what is the difference or significance of the $ in the command above? What does that denote to the system?

```text
It tells the shell to use the value of i in the sentence. In the for
loop, i gets the value of the sequence numbers for every sequence of the
loop. So for the first time running the loop i is equal to 1. Then the
second time it's equal to 2, etc etc.
```
