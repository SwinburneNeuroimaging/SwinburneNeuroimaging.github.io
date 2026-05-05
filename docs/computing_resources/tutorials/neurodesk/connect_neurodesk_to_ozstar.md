# Connect Neurodesk to OzSTAR/NT

Once you have Neurodesk running (via any method), you'll can establish a connection to OzSTAR to access your project files and run computations.

## Connection Setup

**Step 1: Open a terminal**

Open a new terminal window in your Neurodesk environment.

!!! info "What is a terminal?"
    If you don't know how to open a terminal, see [Open a terminal on Neurodesk](./neurodesk_terminal.md). Then you might want to follow the [linux command line basics](../basics/linux_command_line_basics.md) tutorial to get a feel of using a linux terminal.

**Step 2: Download the connection script**

Copy and paste the following command into the terminal and press ENTER:

```bash
cd; curl -o connect_ozstar_user.sh https://raw.githubusercontent.com/SwinburneNeuroimaging/swinburne_tools/main/connect_ozstar_user.sh
```
This downloads a script that Swinburne Neuroimaging has created to help connecting to OzSTAR easier.

**Step 3: Run the connection script**

Type the following command, replacing `XXX` with your OzSTAR username, and press ENTER:

```bash
cd; source connect_ozstar_user.sh XXX
```

**Step 4: Confirm the connection**

You will be asked a yes/no question. Type `yes` and press ENTER.

**Step 5: Enter your password**

You will be prompted to enter your OzSTAR password **3 times** (once for each folder being mapped: `/fred`, `/dagg`, and `/home`).

After each successful password entry, you should see the message:

```
SUCCESS!
```

!!! warning "Important: Password Attempts"
    **Three consecutive incorrect passwords will block your OzSTAR access for 24 hours.** When blocked, you'll see the error message: `read: Connection reset by peer`
    
    If you see this error, contact OzSTAR support at [hpc-support@swin.edu.au](mailto:hpc-support@swin.edu.au) with your username for urgent assistance.

!!! danger "Troubleshooting: No SUCCESS! Message"
    If you don't see `SUCCESS!` after entering your password, this indicates:
    
    1. **Incorrect username**: Close the terminal, open a new one, and run the command with the correct username
    2. **Incorrect password**: Double-check your password and try again carefully

**Step 6: Create your private directory**

Type the following command, replacing `XXX` with your OzSTAR username:

```bash
mkdir /home/XXX/private
```

Press ENTER.

## What You Can Access

After successful connection, you'll have access to these OzSTAR directories from within Neurodesk:

| Directory | Location | Purpose |
|-----------|----------|---------|
| **Home Directory** | `/home/XXX/private` | Your personal OzSTAR storage (10GB limit) |
| **Neuroimaging Public** | `/dagg/public/neuro` | Shared neuroimaging resources and datasets |
| **Project Directory** | `/fred/ozYYY` | Your project's shared storage (replace `ozYYY` with your project ID) |

---

## Persistence and Reconnection

!!! info "Connection Persistence"
    **Good news:** The connection setup is permanent for the life of your desktop. You don't need to repeat these steps for future logins.
    
    **Exception:** If you shelve and restart your virtual desktop, you'll need to repeat Step 5 (entering your password 3 times) to re-establish the connection.

---

## File Storage Best Practices

!!! warning "Critical: Save Files in the Right Location"
    **Always save your work** in one of these locations:
    
    - `/fred/ozYYY` (your project directory)
    - `/home/XXX/private` (your home directory, if space permits)
    - Subdirectories within these folders
    
    **Files saved elsewhere will be deleted** if you don't use your ARDC Virtual Desktop for a few months, or if you upgrade or delete your desktop.

---

## Support

If you encounter issues during setup or connection:

- **Swinburne Neuroimaging support**: [neuroinformatics@swin.edu.au](mailto:neuroinformatics@swin.edu.au)

