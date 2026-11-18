# Connect Neurodesk to OzSTAR/NT

Once you have Neurodesk running (via any method), you'll can establish a connection to OzSTAR to access your project files and run computations.

## Connection Setup

**Step 1: Open a terminal**

Open a new terminal window in your Neurodesk environment.

!!! info "What is a terminal?"
    If you don't know how to open a terminal, see [Open a terminal on Neurodesk](./neurodesk_terminal.md). Then you might want to follow the [linux command line basics](../basics/linux_command_line_basics.md) tutorial to get a feel of using a linux terminal.

**Step 2: Download the connection script**

Copy and paste (using shift-ctrl-v) the following command into the terminal and press ENTER:

```
curl -Ls https://raw.githubusercontent.com/SwinburneNeuroimaging/swinburne_tools/main/ozstar_setup.sh > /tmp/tmp.sh; source /tmp/tmp.sh
```
This downloads a script that Swinburne Neuroimaging has created to help connecting to OzSTAR easier. This only has to be done once when the virtual machine is created. 

The script will run automatically and install some extra packages. Then you will be prompted for 

1. your *ozstar* username
2. your *ozstar* password
3. a passphrase for the ssh key (twice) - this should *not* be the same as your password
4. the current ozstar 2FA code from your phone

!!! info "What is a 2FA code?"
    If you have not already set up 2FA for your ozstar account, you can do so [here](https://supercomputing.swin.edu.au/account-management/2fa). You will need to be logged in to the Accounts Portal using your ozstar username and password. 


Sometimes the connection to the ozstar filesystem will be dropped - this will happen if the machine gets 'shelved' for instance. (This may show up as an `Input/output error`) 

You can run the command 
```
reconnect_ozstar
```
in a terminal to reconnect to ozstar at any time.

To open a shell to ozstar (i.e. log in over ssh, for example to submit jobs), just type
```
sshoz
```
You may occasionally get prompted for a 2FA code (or the passphrase you entered), both with this and the 'reconnect_ozstar' commands, but (hopefully) not often.

## What You Can Access

After successful connection, you'll have access to these OzSTAR directories from within Neurodesk:

| Directory | Location | Purpose |
|-----------|----------|---------|
| **Home Directory** | `/home/XXX` | Your personal OzSTAR storage (10GB limit) |
| **Neuroimaging Public** | `/dagg/public/neuro` | Shared neuroimaging resources and datasets |
| **Project Directory** | `/fred/ozYYY` | Your project's shared storage (replace `ozYYY` with your project ID) |

---

## File Storage Best Practices

!!! warning "Critical: Save Files in the Right Location"
    **Always save your work** in one of these locations:
    
    - `/fred/ozYYY` (your project directory)
    - `/home/XXX` (your home directory, if space permits)
    - Subdirectories within these folders
    
    **Files saved elsewhere will be deleted** if you don't use your ARDC Virtual Desktop for a few months, or if you upgrade or delete your desktop.
    **Files save in /fred/ozYYY will **not** be backed up by system administrators, but files in /home/XXX *will* be backed up.

---

## Support

If you encounter issues during setup or connection:

- **Swinburne Neuroimaging support**: [neuroinformatics@swin.edu.au](mailto:neuroinformatics@swin.edu.au)

