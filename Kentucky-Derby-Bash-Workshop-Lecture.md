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

As previously mentioned we will be making our foray into bash commands and scripting using Dartmouth's HPC systerm, Discovery. Prior to this workshop, you should have received an email from me with instructions on how to set up a Discovery account. If you still have not set up a Discovery account, you can do so using this [link]("https://dashboard.dartmouth.edu/research/hpc_account") 


# Dartmouth's HPC
# Basic Commands
	- Terminal Environment
	- Moving Around Our Local Machine
	- Accessing Files 
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
