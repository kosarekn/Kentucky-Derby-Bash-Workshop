# Welcome to The First Annual Kentucky Derby ..... Bash Workshop!

## Learning Objectives
- Develop an understanding of command line interpreters
- Acquire knowledge of bash commands to move around your computer
- Learn how to manipulate file contents using bash commands
- Conduct simple analysis using bash
- Horse around

## Command-Line Interpreters
Command interpreters or command-line interface (CLI) allow users to interact with their computer system directly by inputting a set of commands. Interpreters were the only interface option up until the 1970's when graphical user interfaces (GUI) were created to reduce the "energy potential" required to begin computing. Still, CLIs are used today in lieu of GUIs because of their speed and resource conservation and well as their automation capibilities. CLIs operate in a continuous loop know as a REPL, or a Read-Eval-Print Loop. "Read" is indicated as a prompt, usually `>` or `$`. "Eval" identifies the commands and parameters then runs the associated programs. Finally, "Print" prints out the results of the command directly in the terminal. Do note, we can still write out results to sepeate files on our machine. 

Different operating systems will have different CLIs, but some of the most commonly used are listed here: 

1)  Bash (Bourne Again Shell): This is the most widely used shell across Linux distributions and remains the default for many machines. Bash was created in 1989 by Brian Fox as a free software replacement for the Bourne shell. 

2) Zsh Shell: This shell is now the default on macOS systems. While it has some advanced auto-completion features, it maintains the same commands as the Bash shell. 

3) Powershell: Powershell was developed by Microsoft and serves as a CLI for interactive use and a script interpreter for automation. 

Other CLIs include command prompt, nushell, kornshell, and Tcsh/Csh. We won't be touching on these today, rather, we will focus our efforts on Bash.

## What is Bash?
Back in ancient times, known as the mid 1900s, computers booted up and ran using a kernal that enabled each piece of hardware within the computer to communicate with one another. In the event that a real live human being wanted to interact with the computer, they would have to physically write down with pencil and paper their program, usually in something like fortran or cobol. That program would then get punched into a card in "machine language" that could be fed into the computer to read. The punch cards not only stored programs, but data too! 

Computer scientists like Louis Pouzin, Ken Thompson, and Stephen Bourne recognized that this system was inefficient and error prone, leading them to develop the first shells in the 60s and 70s. Of the shells available today, Bash stands out as most popular. 

Today we will be interfacing with bash through the Dartmouth HPC system, Discovery. After logging into Discovery you will notice a prompt indicated by a `$`. This means that the shell is working properly and waiting for you input. While this while this black or white box can at first feel intimidating, just remember that bash is more of a helper tool that, when executed correctly, runs other appications installed on your system, or in this case Dartmouth's HPC system. 

## Why Use Bash?

Taking the time to learn just a few bash commands is often valuable and makes you a stand-out candidate for job applications! Outlined below are just a few reasons why you might consider learning bash scripting:

1) **Communication with High Performance and Cloud Computing Systems**: There exist a whole catalog of reasons why you might choose to learn bash commands and scripting. Paramount among them would be to interface with systems like Discovery. While Dartmouth offers options like OOD that allow users to submit jobs to a scheduler using a GUI, you may find at  another job or graduate institution that you do not have access to GUIs for this purpose. Bash is a transferrable and valuable skill to develop!

2) **Optimizing Time and Resource Use**: Like many other programming languages, bash reduces time and resource consumption by automating complex tasks and multi-step operations into single commands. 

3) **System Control and Efficiency**: For those of you aspiring to a career in tech or just hope to have greater control over your system administration, bash is an important skill to develop. It provides direct access to your operating system commands, allowing you to manage user, monitor resources, and configure systems. 

4) **Building Tools Without Niche Requirements**: I've built plenty of tools using R or python, though the issue with these tools is that they require fancy packages with specific versions. Building a tool or script with bash means that it will be executable across different Unix-like environments without needing library management. 

## How Do I Use Bash?

As previously mentioned we will be making our foray into bash commands and scripting using Dartmouth's HPC systerm, Discovery. Prior to this workshop, you should have received an email from me with instructions on how to set up a Discovery account. If you still have not set up a Discovery account, you can do so using this [link]("https://dashboard.dartmouth.edu/research/hpc_account"). The system to get a discovery account is automated and your account should be ship shape in about a half hour if not sooner. 

# Dartmouth's HPC

Once you have created an HPC account, navigate to your local machine's terminal. For Mac folks, this should be under Go -> Utilities -> Terminal. When you launch your terminal it should look something like this:

![local-machine-terminal](/images/local-machine-terminal.png)

After initiating a a terminal, type the following command into your terminal, making sure to type in your actual NetID. Note if you are not connected to eduroam, make sure you have the Dartmouth VPN turned on:

```
ssh YOUR_NETID@discovery.dartmouth.edu
```

If this is your first time logging into Dartmouth's HPC system, you will be asked something about fingerprint keys. Answer `yes` to this question and press enter again. If all goes well, you will be prompted for your password. Type in the password associated with your Dartmouth e-mail. This is the most challenging part of signing into the HPC system. You will not be able to see your password as you type. This is a security feature. The password screen should look something like below:

![local-machine-terminal-hpc-password-prompt](/images/local-machine-terminal-hpc-password-prompt.png)

Press `Enter` after inputting your password. You will know you have successfully signed into the HPC system when your terminal looks like this:

![discovery-home](/images/discovery-home.png)

Huzzah! You are logged into Discovery, but where do I begin? To start, we will need to get familiar with a feew basic commands.

# Basic Commands

## pwd
When we log into Discovery or initialize a terminal on our local machines, we are automatically logged into our home directory. We can confirm that we are in our home directory by using the command `pwd`. `pwd` means "print working directory". This command will print the absolute path to our home directory. Go ahead and type the following into Discovery:

```
pwd
```

You should see something like `/dartfs-hpc/rc/home/8/f002yt8`. This is your home directory. 

## cd

Now if you ever get lost, you can always go home. To get home, all you need to do is click your heels.... no that's not right. All you need to do is execute the `cd ~` command. `cd` mean "change directories" and `~` stands for your home directory. This is automatically set up for you on the HPC system. On your local machines, your home directory will probaby be something like `/Users/noellekosarek`. 

![dorothy-no-place-like-home](/images/dorothy-no-place-like-home.gif)

We can also use the `cd` command to move to different locations on the HPC system as well as our local machines. On the HPC system, this means that, so long as you have access, you can move to shared lab locations or even temporary directories. Today, we will be working in a temporary scratch directory on the HPC system. To get there just type or copy and paste in the following command: 

```
cd /scratch/kentucky-derby-bash-workshop
```

After running this command, use the `pwd` command to confirm that you are in the correct location. You should see this: `/scratch/kentucky-derby-bash-workshop`.

## ls

I'm interested in knowing what sorts of files or directories are living in this directory. To list the files and directories in this location, you can use the `ls` command. Typing in this command will reveal that we have a single file in this directory called `kentucky_derby_winners.csv`.This is the data file with which we will be working today. 

We can get a bit more information about this file by using flags with the following command:

```
ls -lah
```

Once again, we have used implemented the `ls` command. The flags `-lah` mean long listing, all files, and human-readable respectively. Long listing shows permissions, owners, groups, size, and time stamps for that file. All files shows both hidden and non-hidden files. Finally, human readable means that the output is printed in units that are able to be read by humans, not machines. 

## mkdir

As we progress through this workshop, we want to make sure we are writing output files to our own locations in the scratch directory. To do this, let's move up one dirctory from the Kentucky Derby directory and then make our own directory under our NetID where we will write out all of our output files. 

To move up a single directory we can use our `cd` command followed by `..`. This tells our machine to move one directory up from our current directory. Copy and paste the following command into you terminal: 

```
cd ..
```

Now that we are in the scratch directory, it's time to introduce a new command, `mkdir`. This command mean to "make a new directory". The command should be followed by your actual NetID. This will create a directory with your NetID as the name. Use the following command to create the new directory:

NOTE: MAKE SURE YOU REPLACE YOUR_NETID_HERE WITH YOUR ACTUAL NETID!

```
mkdir YOUR_NETID_HERE
```

To confirm that you have create the new directory, you can use the `ls` command and look to see if your NetID is shown in the output.

## cp

To make all of our lives slightly less complicated, I think that copying over the data file with which we will be working from the scratch directory for the workshop to your NetID directory. `cp` followed by the absolute path to the file you want to copy and then by the absolute path of the destination to which that file should be copied will complete this exercise for you. Use the code below, but make sure you replace YOU_NETID_HERE with your actual NetID:

```
cp /scratch/kentucky-derby-bash-workshop/kentucky_derby_winners.csv /scratch/YOUR_NETID_HERE
```

Once this command runs, use `cd` to change to the scratch directory under your NetID then use `ls` to ensure that the file has been roperly copied over. Take a look at the example code below for how to do this:

```
cd /scratch/YOUR_NETID_HERE
ls
```

## mv

In addition to coping files from one location to another, you can use the `mv` command to move files from one location to another. The `mv` command can also be used to rename files. Let's say we want to rename our `kentucky_derby_winners.csv` file to `KDW.csv`. We can complete this task using the following command:

```
mv kentucky_derby_winners.csv KDW.csv
```

Use `ls` to confirm that you have renamed this file. 

# Accessing Data in A File

## Kentucky Derby Winners Data
The Kentucky Derby, known as "The Most Exciting Two Minutes in Sports", is a horse race held at Churchill Downs in Louisville, Kentucky every first Saturday in May. The Kentucky Derby is the first race in a series of races known as the Triple Crown. The race also boasts the title of the oldest continuously running sports event in the United States.

The history of the Kentucky Derby goes back to 1875 when Meriwether Lewis Clark Jr., grandson of William Clark of Lewis and Clark Expedition fame, traveled to England and France to immerse himself in horse racing. Upon his return to Kentucky, he organized the Louisville Jockey Club and Driving Park Associatation to raise funds for a racing facility, this was to be known as Churchill Downs. the first Derby took place on May 17, 1875. Jockey Oliver Lewis astride a colt named Aristides won the inaugural race. 
 
Today, the Kentucky Derby has become a much higher stakes race with the 2026 purse featuring a record total of $5 million with $3.1 million for the first place winner. The race is also famous for it's fanciful hats,mint juleps, and handsome rose blanket draped over the winning horse. Personally, I am intersted in spectating for the horses themselves. Who wouldn't want to gander at these majestic creatures!

![goofy-horse](/images/goofy-horse.gif)

## Accessing Data with Bash

### cat

One of the most useful bash commands in our arsenal is the `cat` command standing for "concatenate". When used on a whole file, the `cat` command will print the contents of our file to the terminal window. Use the command below to view the contents of our whole file.

```
cat KDW.csv
```

### head, tail

Based on the output of the `cat` command, you can see where this might not be the most useful command to run on large files. You can image a situation in which you have RNA-seq files or meta data for thousands of single cells. Instead of printing the entire contents of a file we can print the first few lines of a file with the `head` command. In the below example, I am instructing bash to print the first 5 lines of the file as indicated by my use of the `-n` flag.

```
head -n 5 KDW.csv
```

Similarly, we can print the last few lines of a file using the `tail` command.

```
tail -n 5 KDW.csv
```

### cut

The `cut` command provides the user the power to extract specific sections from each line of a file. It particular, it is useful for accessing data in specific columns. Let's use the `cut` command to print the "winners" column of our data. 

```
cut -d ',' -f 2 KDW.csv
```

The `-d ','` flag indicates that the input file is a comma deliminated file. The `-f 2` flag indicates the field that should be displayed. Since the second column contains the names of the winning horses we all `2` after the `-f` flag. This command prints all of the winning horse names. 

### sort

The `sort` command provides the user power to sort on columns alphabetically or numerically. Ordering the data in such a way allows us to observe trends and even return minimum and maximum values in a column. Today, we are intrested in sorting the entire file by the "time_sec" column indicating a horses finishing time in seconds. To do this, run the following code:

```
sort -t "," -k 9 KDW.csv
```

You see that we applied several flags to the `sort` command. The first flag is the `-t` flag, which serves the same purpose as the `-d` flag used with the `cut` command, it is indicative of a delimiter, in this case, a comma. The second flag is the `-k` flag. This flag indicates which column we are interested in using to sort our data. Column nine in our data is the "time_sec" column. Running this command will print the entire sorted data.

### uniq

The `uniq` command only detects adjacent duplicate lines and is often paried with the `sort` command to determine instances of a string or number. Let's use this command to determine how many time different track conditions occurrd on Derby Day. 

```
cut -d',' -f7 kentucky_derby_winners.csv | sort | uniq -c
```

Oh this just got very interesting! You will notice the `|` featured twice in this line of code. This is known as a pipe. The output from the command before the `|` is "pipped" to the next command. This means that is the first part of this line of code isolates the "track_condition" column, which is column 7. The output of this is sent over the the next command `sort` so that all of the same strings "Fast", "Good", "Heavy", etc. are grouped together. This sorted data is then piped to the next command `uniq -c`. The `-c` flag directs the computer to count the number of instances of the adjact repeated strings. 

### awk

The `awk` command is a tool that allows for text processing in Lixus and is used to analyze, filter, and manipulate structured data, such as that found in a .csv file. We can use the `awk` command to find the names of horses that won during a specific span of years.

```
awk -F',' '$1 >= 1990 && $1 <= 2000 {print $1, $2}' kentucky_derby_winners.csv
```
The `awk` command is followed by a `-F','` flag. This flag is the field separator flag indicating that this is a comma separated file. The next portion of this are the options. Here we are telling our program to look at the first column, which contains the years information and grab the data for the year 1990 up through 2000. From that information, we are asking the program to print the first and second columns containing the year and the name of the winning horse.

### grep

`grep` is a powerful command that allows users to search for a string in their file and even count the occurances of that string. We are interested in knowing how many times the name "Bill Hartack", a jockey, is mentioned in our data. Use the command below to find out!

```
grep -c "Bill Hartack" kentucky_derby_winners.csv
```

## Putting It All Together!

At the inception of this workshop we asked two interesting questions of our data: 

1) Who is the most winning trainer
2) Which horse has the fastest time on the 1.25 distance track?

Let's apply our new bash commands to answer the first question. We will need to find the most frequently mentioned trainer in the trainer column. Let's first isolate the trainer column using the `cut` command.

```
cut -d',' -f4 kentucky_derby_winners.csv
``` 

I think the next step would be to implement the `uniq` command with the `-c` flag to count the occurances of the same trainer name, but remember with the `uniq` command we typically need to chain it with the `sort` command because the `uniq` command only recognizes occurances that are adjacent in the data. We will also need to pipe these commands together! 

```
`cut -d',' -f4 kentucky_derby_winners.csv | sort | uniq -c 
```

Now that we have the counts for each of the trainers, we will need to sort our data again, but this time, by the count information using the `-n` flag standing for numeric. Given that sort returns data from lowest to highest value, we will want to include the `-r` flag to reverse the order of the data returned. Finally, we will want to print out the very first value in the data, which will be the most winning trainer.

```
cut -d',' -f4 kentucky_derby_winners.csv | sort | uniq -c | sort -rn | head -1
```

Nice! Bob Baffert is the most winning trainer with 6 Kentucky Derby wins! 

Now, those of you with some sports history knowledge or a subscription to Disney+ might know the answer to our second question, but let's take a stab at using the data at our disposal to answer the question of which horse has the fastest 1.25 mile record at the Kentucky Derby. To answer this question we will first need to subset the data to the 1.25 track distance and then find the lowest time in seconds. Finally, we will need to retun the name of the winning horse from that data. Let's use the `awk` command to subset the data set to include only the 1.25 track distance.

```
awk -F',' '$6 == "1.25" {print $0}' derby_winners.csv
```

Now that we have only the data for the 1.25 track distance, we will need to pipe this information to the `sort` command in order to sort by the time in seconds. Because the input is still comma separated we need to make sure we specify that in the output.

```
awk -F',' '$6 == "1.25" {print $0}' kentucky_derby_winners.csv | sort -t',' -k9
```

Next we want to return the top result from this using the `head` command and indicating that we want the first result.

```
awk -F',' '$6 == "1.25" {print $0}' kentucky_derby_winners.csv | sort -t',' -k9 | head -1
```

From this output we will isolate the name of the most winning horse in Kentucky Derby history.

```
awk -F',' '$6 == "1.25" {print $0}' kentucky_derby_winners.csv | sort -t',' -k9 | head -1 | cut -d',' -f2
```

The most winning horse in Kentuck Derby history is Secretariat!

Secretariat, also known as Big Red, was the ninth winner of the American Triple Crown. This thoroughbred racehorse set and still holds the record for the fastest time in all three of the Triple Crown races. Secretariat was owned by Christopher and Penny Chenery of Meadow Stable. After his stunning victories in 1973, Secretariat retired at the ripe old age of 3 to Claiborne Farm in Paris, Kentucky. 

![secretariat](/images/secretariat.jpg)

Do you think his record will be beat this weekend?




