# Access OzSTAR for neuroimaging data and computing

If your study requires supercomputing resources for data analysis, such as running analysis using mne-python, fMRIPrep pipelines, then the following might be helpful 

To access neuroimaging data (MRI/DICOM, MEG/FIF) or your study requires supercomputing resources for data analysis, such as running analysis using Freesurfer, MRTrix, fMRIPrep, mne-python pipelines, then the following information/instructions might be helpful.

## Data Access and Download using FileZilla

A user-friendly way to access and download data on OzSTAR is to use FileZilla.

Detailed instructions on using FileZilla to access and download data can be found in the following document (PDF, downloadable).

Navigating Projects Folders on the Supercomputer and Downloading Project Data.pdf

Please follow the document to download and install FileZilla (if you haven't) and access data in project directory (/fred/ozXXX) after login using your OzSTAR username and password (username can be found on OsSTAR Account Portal and password can be reset on the portal)




## Access OzSTAR/NT Via command line  (MacOS, Linux and Windows)

MacOS and Linux both have their build-in applications (Terminal for MacOS, Console for Linux) for command line.

### MacOS terminal:
<img width="1095" alt="Screenshot 2025-02-25 at 3 05 37 pm" src="https://github.com/user-attachments/assets/f3bf3723-f8a9-45f2-ac9f-f20dc15f8359" />

### Linux Console:
![Tilda-Terminal-for-Linux](https://github.com/user-attachments/assets/e8a03336-cdb9-4367-b36e-5ef94316a6b6)

### Windows Powershell
<img width="1010" alt="Screenshot 2025-02-25 at 3 36 20 pm" src="https://github.com/user-attachments/assets/326d9903-e362-488b-8f3b-201f5345d5ce" />

About PowerShell on a Windows system,

https://learn.microsoft.com/en-us/powershell/

To download and install PowerShell on a Windows system,

https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell

Moreover, WindTerm as a cross-platform command line client is recommended. To download WindTerm,

https://github.com/kingToolbox/WindTerm

WindTerm for access OzSTAR via ssh

<img width="1695" alt="Screenshot 2025-02-25 at 3 39 37 pm" src="https://github.com/user-attachments/assets/d375e305-4a0f-418c-9cf6-c17d63c90969" />


After opening command line client (Terminal or Console), ssh can be used to login, for example,

> ssh USERNAME@ozstar.swin.edu.au

or

> ssh USERNAME@nt.swin.edu.au

Notes: ozstar.swin.edu.au and nt.swin.edu.au are the same for accessing data and computing resources on OzSTAR/NT.

Once login, you are able to look at your home folder
> cd ~/

and project folders 
> cd /fred/ozXXX

## Submit a computing job to OzSTAR/NT
To submit and manage your computing jobs, please see the document below.

[How to submit jobs to OzStar.pdf](https://github.com/user-attachments/files/17374190/How.to.submit.jobs.to.OzStar.pdf)



# Information about OzSTAR

### OzSTAR homepage
https://supercomputing.swin.edu.au

### About OzSTAR
https://supercomputing.swin.edu.au/ozstar

### About Ngarrgu Tindebeek (NT)
https://supercomputing.swin.edu.au/ngarrgu-tindebeek

### Documents, including user documents,for OzSTAR/NT,
https://supercomputing.swin.edu.au/docs/

### OzSTAR/NT account portal
https://supercomputing.swin.edu.au/account-management/login

From the link above, you can apply for an account, create or join a project for data access or computing.
