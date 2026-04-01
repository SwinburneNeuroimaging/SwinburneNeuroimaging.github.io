# Accessing the Supercomputer

OzSTAR and NT are [Swinburne's two supercomputers](https://supercomputing.swin.edu.au/), they are powerful linked machines designed to help Australian researchers analyse large amounts of data and run complex calculations that would be impossible on a regular computer or laptop. 

To access neuroimaging data (MRI/DICOM, MEG/FIF) or your study requires supercomputing resources for data analysis, such as running analysis using Freesurfer, MRTrix, fMRIPrep, mne-python pipelines, then the following information/instructions might be helpful.

!!! tip
    If you don't yet have an OzSTAR/NT account, you can apply for one and create or join a project on the [OzSTAR account portal](https://supercomputing.swin.edu.au/account-management/login) and by following the [Creating an OzSTAR/NT Account](./create_ozstar_account.md) tutorial. Your username can be found on the portal, and your password can also be reset there.


## Access OzSTAR/NT via the terminal (MacOS/Linux/Windows)
MacOS and Linux both have their build-in applications (Terminal for MacOS, Console for Linux) for command line.

=== "MacOS Terminal"
    Open Finder → Applications → Utilities → Terminal, or press Cmd + Space and type `Terminal`.

    ![MacOS-Terminal](https://github.com/user-attachments/assets/f3bf3723-f8a9-45f2-ac9f-f20dc15f8359)

=== "Linux Console"
    Press Ctrl + Alt + T, or search for Console or Terminal in your applications menu.

    ![Tilda-Terminal-for-Linux](https://github.com/user-attachments/assets/e8a03336-cdb9-4367-b36e-5ef94316a6b6)

=== "Windows Powershell"
    Windows has two options:

    **PowerShell** is built in to Windows. Search for it in the Start menu. You can also [download and install a newer version](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell) if needed.

    **WindTerm** is a free cross-platform SSH client with a more user-friendly interface. You can [download it here](https://github.com/kingToolbox/WindTerm).


    ![Windows-Powershell](https://github.com/user-attachments/assets/326d9903-e362-488b-8f3b-201f5345d5ce)


### Login
Once you have a terminal open, connect to OzSTAR using SSH with your username:
```bash
$ ssh username@ozstar.swin.edu.au
```
To connect to Ngarrgu Tindebeek (NT) instead:
```bash
$ ssh username@nt.swin.edu.au
```
!!! note
    `ozstar.swin.edu.au` and `nt.swin.edu.au` both provide access to the same data, but with have different computing resources. 

If you want to learn more about SSH, you can read our [SSH basics tutorial](../basics/ssh_basics.md).

### Login nodes
 
When you connect, you will land on one of the login nodes:
 
| System | Login nodes |
|--------|-------------|
| OzSTAR | `farnarkle1`, `farnarkle2` |
| NT | `tooarrana1`, `tooarrana2` |
 
This is where your home directory will be on OzSTAR or NT. This is usually `/home/Username/`. You can do *light* calculations and commands here.

!!! warning
    Login nodes are shared by all users and are intended for light tasks only, file management, writing scripts, and submitting jobs. Do not run computationally intensive work directly on a login node. Use the job submission system instead. To learn how to submit a job, read our [Submitting Jobs to OzSTAR/NT](./submitting_jobs_to_ozstar.md) tutorial.


## Transferring files with FileZilla
 
If you prefer a graphical interface for accessing and downloading data, [FileZilla](https://filezilla-project.org/) is a free file transfer program that connects to OzSTAR/NT over SSH. You can drag and drop files between your local machine and OzSTAR without using the command line.
 
See the [Nagivating the supercomputer and downloading data](../supercomputing/navigating_ozstar_and_downloading_data.md) guide for detailed instructions on how to install and connect FileZilla to OzSTAR.
 
Your project data will be located at `/fred/ozXXX` on the remote server.

## Submitting jobs
 
To run an analysis on OzSTAR, you submit a *job* , a script that describes what you want to run and what computing resources you need. See the [Submitting Jobs to OzSTAR/NT](./submitting_jobs_to_ozstar.md) guide for a full walkthrough.
 
## Further resources
 
| Resource | Link |
|----------|------|
| OzSTAR homepage | [supercomputing.swin.edu.au](https://supercomputing.swin.edu.au) |
| About OzSTAR | [supercomputing.swin.edu.au/ozstar](https://supercomputing.swin.edu.au/ozstar) |
| About Ngarrgu Tindebeek (NT) | [supercomputing.swin.edu.au/ngarrgu-tindebeek](https://supercomputing.swin.edu.au/ngarrgu-tindebeek) |
| OzSTAR documentation | [supercomputing.swin.edu.au/docs](https://supercomputing.swin.edu.au/docs/) |
| Account portal | [supercomputing.swin.edu.au/account-management](https://supercomputing.swin.edu.au/account-management/login) |