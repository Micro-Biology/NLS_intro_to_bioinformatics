# Linux and BASH:

## Linux:

Linux is an operating system, just like windows. For bioinmformatics it is preferable to use a Linux based operating system in order to have maximum compatibility with software we need.

## BASH:

BASH is the terminal used by default in ubuntu, and is predominantly used to manage other scripts, for folder navigation, moving/copying files, and other OS actions.

### Folder navigation, and moving files

In linux we use the 'cd' command to move to a different folder, for example:

this will direct us to your home directory:

    cd ~
    
This will direct us to the folder QiimeScripts in the home directory no matter where we currently are:
    
    cd ~/Scripts
    
This will direct us to the folder QiimeScripts that is contained within the current target directory:
    
    cd Scripts 
    
To go up one in the folder heirachy use:

    cd ..
    
For example assuming you opened a terminal and ran these scripts you would first be taken to the home directory, then to 'Scripts', and then to 'Scripts/Scripts', and then back to 'Scripts'.

But wait you're saying you got an error when running 'cd ~/Scripts':

    bash: cd: /home/nls/Scripts: No such file or directory

This is because you don't have a directory ~/Scripts, lets make one using the 'mkdir' command:

    mkdir eScripts
    
And if you need to make a chain of folders:

    mkdir -p ~/Scripts/folders/that/dont/exist/yet
    
Oh no we didnt actually want all those folders there lets remove all the folders within Scripts using 'rm':

    rm ~/Scripts/folders

Uh, not another error:

    rm: cannot remove '/home/nls/Scripts/folders': Is a directory
    
This is because rm on its own can only be used on files...

... However you can remove directories using 'rm -r' but be careful it will delete everything in those folders and they will not go to the recycling bin.

    rm -r ~/Scripts/folders

Removing files using 'rm' will not send them to the recycling bin but instead permentantly delete them.

Now we have practised making a folder and deleting it, pease make it again and navigate to the folder:

    cd ~/Scripts
    
To see all the files in a folder use the 'ls' command, and alternative is the 'dir' command, its not quite as informative, try them both:

    dir
    ls
        
At the moment you may have nothing in the scripts folder so lets look at what is in the home folder instead, run:

    ls ~/
    dir ~/
    
  
These are all the files and directories contained directly within the home directory.

You can copy and paste files in the terminal using the 'cp' command or cut and paste them using 'mv':
    
    cp 1.txt 4.txt
    
This will copy 1.txt to 4.txt, alternatively if you do not want the file to be called that anymore:

    mv 4.txt 1_a.txt
    
Now you may think that this is silly to copy all the files using the terminal, as for 1 file it takes much longer than by clicking.
However you can copy muliple files at a time to somewhere completely different using the '*' sign, this matches to any character.

    cp *.txt ~/Scripts/
    
Wow, that was even easier than Ctrl-C Ctrl-V! 

Similarly the 'mv' command can be used instead and will delete the original files.
    
## Shell scripts

Later on down the line we may have mutliple scripts running in order to form a pipeline, but wouldn't it be good if we didn't have to type them out or copy and paste them everytime...?

Where there is a will there is a way, enter the Shell script.

First make a new document, and open it in an editor (I'll use gedit):

    touch Pipeline.sh
    gedit Pipeline.sh
    
First we have to put what is known as a shebang line, this is my prefered line below:

    #!/bin/bash
    set -e
    set -u 

The first line tells the terminal this is a BASH script, the second line tell the script to halt if there are any errors, and the final line stops the script if there are any unset variables.

Then add whatever script you may want to execute multiple times, you may want to just do each step in its own script or you may like to do the entire pipeline from start to finish, its up to you.

To make the script executable first, run:

    sudo chmod 755 Pipeline.sh 
    
And then simply:

    ./Q2_Analysis.sh
    
## Trouble shooting
    
You will probably get some sort of errors, make sure your directories are called correctly, and that file names match. Most/any of the scripts in this tutorial will work when using shell scripts, so knock yourself out. Additonally ther is one more command I find very useful for working out where in your pipeline you are up to, echo:

    echo "Hello World!"
    echo "Copying files to Analysis folder"
    echo "Backing up raw data files"
    echo "You are now ready to move on to part 2 of this tutorial!"

