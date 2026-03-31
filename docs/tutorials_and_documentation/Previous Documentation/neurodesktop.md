# Data Analysis with NeuroDesktop

Swinburne Neuroimaging is a partner in creating the NeuroDesktop analysis platform, an extendible, portable, easy to use desktop environment for cognitive neuroscience data analysis. Researchers can access and use NeuroDesktop in a few different ways:

* Downloading and installing NeuroDesktop onto their own computer or workstation
* Using the ARDC's Virtual Desktop Service
* Using Neurodesktop on a virtual workstation on the ARDC Nectar Research Cloud
* Connecting to the OzStar supercomputer from NeuroDesktop

### Downloading and installing NeuroDesktop onto your own computer or workstation
Complete instructions for running NeuroDesktop on your own workstation can be found [here](https://www.neurodesk.org/). 

### Using the ARDC's Virtual Desktop Service
How to set up an ARDC Virtual Desktop and use Neurodesktop on it
  
Follow the instructions here to start a Neurodesktop desktop: https://www.neurodesk.org/docs/neurodesktop/getting-started/nectar/
(it is recommended to start the desktop on the Monash NECTAR zone; from our experience, it allows for a stable connection when connecting to OzStar)

### Connecting to OzStar from NeuroDesktop

Open a new terminal window.

Copy and paste the following into the terminal window, and press ENTER:

`cd; curl -o connect_ozstar_user.sh https://raw.githubusercontent.com/SwinburneNeuroimaging/swinburne_tools/main/connect_ozstar_user.sh`

In the terminal window, type the following, and press ENTER (replacing XXX with your ozstar username):

cd; source connect_ozstar_user.sh XXX


You will be asked a yes/no question. Please type yes and press ENTER.


Please enter your OzStar password 3 times as prompted (one for each folder mapped to OzStar: /fred, /dagg, /home). After each time you enter the password successfully and a connection is established, the message ‘SUCCESS!’ is printed


IMPORTANT NOTE:
If 'SUCCESS!' is not printed after you type the password, it indicates one of two things:
  1) The username provided in the command-line was incorrect. Please close this terminal, open a new one, and run the command with the correct username.
  2) The password entered was incorrect. Please double-check your password.
Notice that three consecutive wrong passwords will block access to OzStar for 24 hours. When trying to connect, OzStar will display the error message "read: Connection reset by peer"
If you must gain access urgently, please contact OzStar support (hpc-support@swin.edu.au) with your username, and notify them you are blocked.
For further assistance, you may also contact Swinburne Neuroimaging informatics fellow (neuroinformatics@swin.edu.au)



Type (replacing XXX with your ozstar username):
mkdir /home/XXX/private
and ENTER


You now have access to these folders as if you were working on OzStar:
Your OzStar home directory (/home/XXX/private).
OzStar neuroimaging public directory (/dagg/public/neuro)
If you have one, your OzStar project directory (/fred/ozYYY), replacing ozYYY with your project folder on OzStar. 
The access is permanent to the life of the desktop. The instructions above do not need to be repeated in future logins into the desktop. However, if the desktop was shelved and then restarted, step 6 above needs to be repeated after all.


When working with the neurodesktop, make sure to save all your configuration/intermediate/output files in either /fred/ozYYY, /home/XXX/private (space permits, as the home directory on OzStar is limited to 10G), or subdirectories of these two folders. Do not save files in any other folder, as files saved in other folders will be deleted in case that you do not use your ARDC Virtual Desktop for a few months (or decide to upgrade or delete it).

 