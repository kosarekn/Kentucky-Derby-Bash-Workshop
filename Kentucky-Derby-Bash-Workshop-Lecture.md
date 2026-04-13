## Command-Line Interpreters
Command interpreters or command-line interface (CLI) allow users to interact with their computer system directly by inputting a set of commands. Interpreters were the only interface option up until the 1970's when graphical user interfaces (GUI) were created to reduce the "energy potential" required to begin computing. Still, CLIs are used today in lieu of GUIs because of their speed and resource conservation and well as their automation capibilities. CLIs operate in a continuous loop know as a REPL, or a Read-Eval-Print Loop. "Read" is indicated as a prompt, usually `>` or `$`. "Eval" identifies the commands and parameters then runs the associated programs. Finally, "Print" prints out the results of the command directly in the terminal. Do note, we can still write out results to sepeate files on our machine. 

Different operating systems will have different CLIs, but some of the most commonly used are listed here: 

1)  Bash (Bourne Again Shell): This is the most widely used shell across Linux distributions and remains the default for many machines. Bash was created in 1989 by Brian Fox as a free software replacement for the Bourne shell. 

2) Zsh Shell: This shell is now the default on macOS systems. While it has some advanced auto-completion features, it maintains the same commands as the Bash shell. 

3) Powershell: Powershell was developed by Microsoft and serves as a CLI for interactive use and a script interpreter for automation. 

Other CLIs include command prompt, nushell, kornshell, and Tcsh/Csh. We won't be touching on these today, rather, we will focus our efforts on Bash.

## What is Bash?
Back in ancient times, known as the mid 1900s, computers booted up and ran using a kernal that enabled each piece of hardware within the computer to communicate with one another. In the event that a real live human being wanted to interact with the computer, they would have to physically write down with pencil and paper their program, usually in something like fortran or cobol. That program would then get punched into a card in "machine language" that could be fed into the computer to read. The punch cards not only stored programs, but data too! 

## Why Use Bash?
## How Do I Use Bash?
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
