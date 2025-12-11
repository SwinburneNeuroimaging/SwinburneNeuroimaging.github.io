# Setting up Neurodesk and Connecting to OzSTAR

This guide will walk you through setting up Neurodesk and connecting it to OzSTAR for neuroimaging analysis.

---

## 3. Setting up Neurodesk

Swinburne Neuroimaging is a partner in creating the Neurodesk analysis platform, an extendible, portable, easy to use desktop environment for cognitive neuroscience data analysis.

### Available Options

Researchers can access and use Neurodesk in several different ways:

- **ARDC Virtual Desktop Service** (recommended)
- Downloading and installing Neurodesk onto your own computer or workstation
- Using Neurodesk on a virtual workstation on the ARDC Nectar Research Cloud
- Connecting to OzSTAR from Neurodesk

!!! success "Recommended: ARDC Virtual Desktop Service"
    The **ARDC Virtual Desktop Service** is the preferred method for using Neurodesk. It provides a stable, pre-configured environment with OzSTAR integration and requires no local installation.

### Option A: ARDC Virtual Desktop Service (Recommended)

The ARDC Virtual Desktop Service provides a cloud-based desktop environment with Neurodesk pre-installed. This is the easiest and most reliable way to get started.

**Setup Instructions:**

1. Follow the complete setup instructions at the [Neurodesk NECTAR guide](https://www.neurodesk.org/docs/neurodesktop/getting-started/nectar/)

2. When creating your desktop, select the **Monash NECTAR zone** for optimal performance and stable connections to OzSTAR

!!! tip "Why Monash NECTAR Zone?"
    Based on our experience, the Monash NECTAR zone provides the most stable connection when accessing OzSTAR resources.

### Option B: Local Installation

If you prefer to run Neurodesk on your own workstation, complete installation instructions are available at [neurodesk.org](https://www.neurodesk.org/).

!!! note "Local vs Cloud"
    While local installation is possible, the ARDC Virtual Desktop Service offers better integration with OzSTAR and eliminates hardware requirements on your local machine.

---

## 4. Connecting Neurodesk to OzSTAR

Once you have Neurodesk running (via any method), you'll need to establish a connection to OzSTAR to access your project files and run computations.

### Connection Setup

**Step 1: Open a terminal**

Open a new terminal window in your Neurodesk environment.

**Step 2: Download the connection script**

Copy and paste the following command into the terminal and press ENTER:

```bash
cd; curl -o connect_ozstar_user.sh https://raw.githubusercontent.com/SwinburneNeuroimaging/swinburne_tools/main/connect_ozstar_user.sh
```

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

### What You Can Access

After successful connection, you'll have access to these OzSTAR directories from within Neurodesk:

| Directory | Location | Purpose |
|-----------|----------|---------|
| **Home Directory** | `/home/XXX/private` | Your personal OzSTAR storage (10GB limit) |
| **Neuroimaging Public** | `/dagg/public/neuro` | Shared neuroimaging resources and datasets |
| **Project Directory** | `/fred/ozYYY` | Your project's shared storage (replace `ozYYY` with your project ID) |

### Persistence and Reconnection

!!! info "Connection Persistence"
    **Good news:** The connection setup is permanent for the life of your desktop. You don't need to repeat these steps for future logins.
    
    **Exception:** If you shelve and restart your virtual desktop, you'll need to repeat Step 5 (entering your password 3 times) to re-establish the connection.

### File Storage Best Practices

!!! warning "Critical: Save Files in the Right Location"
    **Always save your work** in one of these locations:
    
    - `/fred/ozYYY` (your project directory)
    - `/home/XXX/private` (your home directory, if space permits)
    - Subdirectories within these folders
    
    **Files saved elsewhere will be deleted** if you don't use your ARDC Virtual Desktop for a few months, or if you upgrade or delete your desktop.

---

## Next Steps

Once you've successfully connected Neurodesk to OzSTAR, you're ready to obtain example code and containers, and begin running your neuroimaging analysis workflows.

## Support

If you encounter issues during setup or connection:

- **OzSTAR technical support**: [hpc-support@swin.edu.au](mailto:hpc-support@swin.edu.au)
- **Swinburne Neuroimaging support**: [neuroinformatics@swin.edu.au](mailto:neuroinformatics@swin.edu.au)