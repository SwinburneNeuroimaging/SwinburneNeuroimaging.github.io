# Navigating Projects Folders on the Supercomputer and Downloading Project Data

Files can be downloaded and uploaded to and from the supercomputer to a local
computer, if the user has permission to do so. To achieve this, OzStar has
recommendations for ways to download and upload project data
(https://supercomputing.swin.edu.au/docs/1-getting_started/file-transfer.html), but
for users not confident with using the terminal, software can be used to facilitate
the transfer of data between a local computer to a remote computer.
One example of this software is FileZilla (https://filezilla-project.org/). The
software (download the client) is available for windows and mac computers. Once
installed, Filezilla can be used to access the project data. Open FileZilla and
navigate to the site manager in the top right corner to add a site (shown below).


A window will appear asking to set-up the site (the computer you want to connect
too).
When first setting this up, navigate to ‘New Site’, and the add:

1. From the protocol drop-down box select SFTP.
2. Type nt.swin.edu.au into the Host window.
3. Select Logon Type as ‘interactive’.
4. In the User window, type your OzStar username.
5. Connect.

When first connecting to the Supercomputer via FileZilla (and via the
terminal), the Supercomputer will request to confirm a unique identifier that the
Swinburne
Neuroimaging
Supercomputer uses to identify your local computer every time a connection is
made – select ‘YES’.
Once a connection is made, the files on your local computer will be shown on
the left and files on the supercomputer will be shown on the right:

Files can be dragged between the local and supercomputers – these
processes only copies files between computers and does not move
them. The location of files on the Supercomputer can be changed using
FileZilla, but dragging files from one location to another will move them
instead of copying them, therefore users should be careful not to accidently
drag files or directories to incorrect places.
Using the terminal to navigate the Supercomputer
FileZilla is a good way to visualise the how directories and files are organised
on the Supercomputer, as it is similar to the finder on mac and Window
explorer, knowing how to navigate to the project folders and files is useful to
know.
Once the terminal is open (this will be labelled ‘Terminal’ on mac and cmd"
and ENTER to open a terminal on Windows). use ssh (Secure Shell) to
remotely log into the Supercomputer: ssh username@nt.swin.edu.au
After entering the password for your OzStar account, you will be placed in
your home directory: /home/OzStarUSERNAME and you will need to navigate to
your project folder.
First use the cd (change directory) command to navigate back to the top level
(equivalent to My Computer in Windows or Computer in mac), and use cd
again to navigate down through the directories to your project, below is an
example of this code:

`ssh username@nt.swin.edu.au`
Password:

```
cd /
cd /fred/ozPROJECTNUMBER/raw
cd /raw/
```

Other useful commands are:

- `pwd` (print working directory) – prints the folder you are currently in and
the path.
- `ls` (list) – this command lists all the files that are in directory.
- `cd` (change directory) – use to navigate into directories one at a time.
- `cd ..` – to back up one level.
- `cd /` - to back to the highest level (i.e., My Computer in Windows or
Computer in mac).