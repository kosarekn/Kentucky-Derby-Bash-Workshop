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
	- Accessing Rows
	- Accessing Columns
	- Searching for Specific Data in a File
# Conducting Simple Calculations
	- Who is the most winning trainer?
		- Find the most frequently noted trainer in the trainer column.
	- Which horse has the fastest time on the 1.25 distance track?
		- Subset the data to the 1.25 track distance.
		- Find the lowest number in the time.
		- Return the name of the horse.
