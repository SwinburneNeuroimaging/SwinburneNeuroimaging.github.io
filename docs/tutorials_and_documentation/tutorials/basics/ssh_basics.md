# SSH - Connecting to Remote Computers

SSH (Secure Shell) is a protocol that lets you securely log in to and run commands on a remote computer, such as Swinburne's Supercoputers OzSTAR & NT, from your local terminal. Once connected, your terminal behaves as if you are sitting at that remote machine.

## Basic login
To connect to a remote computer, you need two things: a username and the hostname (the address of the remote computer).
```bash
ssh username@hostmachine
```
For users of OzSTAR or NT at Swinburne, you can login with your username like this:
```bash
ssh username@ozstar.swin.edu.au
ssh username@nt.swin.edu.au
```
You will be prompted to enter your password. Once authenticated, you will see the remote machine's prompt and can start typing commands. Everything you type from this point runs on the remote computer, not your own.

To end your session and return to your local machine, type:
```bash
exit
```

!!! tip
    The first time you connect to a new server, you might see a message asking if you trust the host's fingerprint. Type `yes` and press Enter to continue. This is asking if you trust the computer you are login into. You shouldn't login into a computer you don't trust.

## Copying files with `scp`
`scp` (secure copy) lets you transfer files between your local machine and a remote server. It works similarly to `cp`, but you specify the remote machine using the same `username@hostname` format as SSH.
```bash
scp source destination
```
### Copying files to remote
```bash
scp myfile.txt username@hostname:/home/username/data/
```
### Copying files from remote
```bash
scp username@hostname:/home/username/results/output.nii.gz ./
```
!!! Note
    Reminder that the `./` at the end means "copy it here, into my current local directory".

### Copying entire directories
Use the `-r` flag (recursive), the same as with `cp`:
```bash
scp -r my_folder/ username@hostname:/home/username/data/
scp -r username@hostname:/home/username/results/ ./
```
!!! tip
    If you are transferring large datasets, consider using `rsync` instead of `scp`. It only transfers files that have changed, so it is much faster if you are syncing a folder repeatedly.

    ```bash
    rsync -avz my_folder/ username@hostname:/home/username/data/
    ```


## Transferring files with FileZilla
If you find `scp` cumbersome, FileZilla is a free graphical file transfer program that lets you drag and drop files between your local machine and a remote server, no commands required. It connects using the same SSH credentials as your terminal.

It is a good option if you are transferring files regularly or prefer a visual interface over the command line. You can download FileZilla for free from [filezilla-project.org](https://filezilla-project.org/). Make sure you download FileZilla Client, not FileZilla Server.

### Connecting to a server
Once installed, open FileZilla and use the Quickconnect bar along the top:

- Host: enter `sftp://` followed by the hostname, e.g. `sftp://nt.swin.edu.au`
- Username: your username on the remote server
- Password: your password
- Port: enter 22 (the standard SSH port)

Click **Quickconnect**. The left panel shows your local machine and the right panel shows the remote server. You can navigate both sides just like a file browser.

### Transferring files
To transfer a file or folder, simply drag it from one panel to the other. You can also right-click a file and select **Upload** or **Download**. FileZilla will show the progress of all transfers in the queue at the bottom of the window.

### Using SSH keys with FileZilla
If you have set up SSH keys (see the section below), you can configure FileZilla to use them instead of a password. Go to **Edit → Settings → Connection → SFTP** and add your private key file (`~/.ssh/id_ed25519`). FileZilla will then authenticate automatically without needing a password each time.

For a more complete walkthrough including screenshots, [see the full FileZilla setup guide](https://github.com/user-attachments/files/25403981/Navigating.Projects.Folders.on.the.Supercomputer.and.Downloading.Project.Data.pdf).

## SSH Keys - passwordless login
Typing your password every time you connect can get tedious. SSH keys allow you to authenticate automatically without a password, whilst still being secure. They work as a pair: a private key that stays on your local machine, and a public key that you place on the remote server.

### Step 1 - Generate a key pair
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
You will be asked where to save the key (press Enter to accept the default) and optionally set a passphrase (basically a password to use the keys, this is optional). The default location is `~/.ssh/`.

!!! Note
    Setting a passphrase makes the connection extra secure as a person would need to have access to both your ssh key and you passphrase to login (basically two-factor authentication).

### Step 2 — Copy your public key to the server
```bash
ssh-copy-id username@hostname
```
For OzSTAR and NT users still will be

```bash
ssh-copy-id username@ozstar.swin.edu.au
ssh-copy-id username@nt.swin.edu.au
```

You will be asked for your password one last time. After this, SSH will use your key instead (and potentially ask you for you passphrase if you set one).

### Step 3 - Login without a password
```
ssh username@hostname
```
You should now connect without being prompted for a password (unless you set a passphrase).

!!! warning
    Your private key (stored in `~/.ssh/id_ed25519`) should never be shared with anyone or copied to a remote server. Only the public key (`~/.ssh/id_ed25519.pub`) goes on the remote machine.


## Port forwarding

### What is a port?
A port is a numbered channel that computers use when communicating with each other. These channels expect a specific type of network traffic through them. You might be familiar with an IP address, which is similar to the street address of a house. In this analogy, a port is then a door into the house, each of which leads into a different service inside. So when computers communicate with each other, they need each others IP address to know where to go, but the port tells the computers where services will be located.

For example, when you visit a website your browser connects to port 443 (HTTPS) on the web server. When you connect via SSH, you are connecting to port 22. When a Jupyter notebook is running, it typically listens on port 8888. Ports are just numbers between 0 and 65535. You don't usually need to think about them in everyday use, but they become relevant when you want to access a specific service running on a remote server — which is where port forwarding comes in.

### Port forwarding
Sometimes a remote server is running a service, such as a Jupyter notebook or a web-based interface, that you want to access from your local browser. Typically the remote server isn't directly accessable to the internet, which means you can't normally open the web-interface in your browser. 

However, you can use SSH port forwarding to create a secure tunnel between a port on your local machine and a port on the remote server.
```bash
ssh -L local_port:localhost:remote_port username@hostname
```
The `-L` flag tells ssh to setup *local* port forwarding and listen you your local machine For example, if a Jupyter notebook is running on port `8888` on the OzSTAR supercomputer:
```bash
ssh -L 8888:localhost:8888 username@ozstar.swin.edu.au
```
After running this command, open your local browser and go to `http://localhost:8888`. The traffic is securely tunnelled through SSH to the remote server.

### Running in the background
If you want to set up the tunnel without starting an interactive session, add the `-N` flag (do not execute a remote command) and `-f` (run in the background):
```bash
ssh -L 8888:localhost:8888 -N -f username@hostname
```
To close a background tunnel, find its process ID and kill it:
```bash
ps aux | grep ssh
kill <process_id>
```
!!! tip
    If you get an error saying the port is already in use, try a different local port number — for example, `8889:localhost:8888`. You can use any number between 1024 and 65535.



## Keeping sessions alive with tmux
If your SSH connection drops, due to a network issue or closing your laptop, any commands you were running will be killed. `tmux` solves this by running your session on the remote server independently of your SSH connection. You can detach, disconnect, reconnect later, and pick up exactly where you left off.

`tmux` is run on the remote server, not your local machine. So you should SSH in first, and then start a `tmux` session from there. The typical workflow looks like this:
```bash
ssh username@hostname          # 1. Connect to the remote server
tmux new -s preprocessing      # 2. Start a tmux session on the remote server
# ... run your analysis ...
# Ctrl + B, then D             # 3. Detach and safely close your laptop
```

### Starting a session
```bash
tmux
```
Or start a named session so you can find it easily later:
```bash
tmux new -s session_name
```

### Detaching from a session
To leave the session running in the background without closing it, press:
```
Ctrl + B, then D
```
This detaches you from the session and returns you to your normal prompt. The session (and anything running inside it) continues on the server.

### Listing sessions
```bash
tmux ls
```
### Reattaching to a session
```bash
tmux attach                   # Reattach to the most recent session
tmux attach -t session_name   # Reattach to a named session
```

### Closing a session
When you are finished and want to close the session entirely, type exit from inside the tmux session.

!!! tip
    A good habit is to always start a named tmux session before running any long analysis on a remote server. That way you can safely close your laptop and come back to it later without losing your work.