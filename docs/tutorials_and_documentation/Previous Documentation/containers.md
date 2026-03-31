## Containers on Ozstar

Container location on Ozstar: 
```
> /dagg/public/neuro/containers
```
NOTES: /dagg/public/neuro is a directory that's accessible to every Ozstar user.

Containers can be run using Apptainer.

To load Apptainer on Ozstar
```
> module load apptainer
```
or simply,
```
> ml apptainer
```
## Neurocommand

Startup script for Neurocommand: 
```
> /dagg/public/neuro/startup_neurocommand.sh
```
Initialise Neurocommand
```
> source /dagg/public/neuro/startup_neurocommand.sh
```
Load modules, for example, fmriprep
```
> module load fmriprep
```
or simply,
```
> ml fmriprep
```
Then use tab to prompt for available versions,
```
> fmriprep         fmriprep/23.2.1
```
And load with version specified
```
> ml fmriprep/23.2.1
```
**How to modify an Apptainer container without rebuilding it**

***

_Set up your environment_

1. You will need  a machine where you have admin privileges via the sudo command (e.g., ARDC Virtual Desktop). Unfortunately, I am not sure whether the modified container can be then run on other machines where you do not have admin privileges (it did not work on OzStar).

2. If you are working on an old machine which still has singularity installed, run:

    `alias apptainer='singularity'`

    `APPTAINERPATH=$(which singularity)`

   otherwise, run:

    `APPTAINERPATH=$(which apptainer)`

***

_Modify the container using root privileges_

Root privileges are necessary to alter an Apptainer container

1. Create an Apptainer overlay of 1024M (this assumes that the new/modified files in the container do not exceed 1G; if that is not the case,  create a larger overlay)

    `apptainer overlay create --size 1024 /tmp/overlay.img`

2. Run the Apptainer container CONTAINERFILE with sudo and specifying the overlay. Use the APPTAINERPATH variable as apptainer might not be in the search path of the root user. 

    `sudo ${APPTAINERPATH} shell --overlay /tmp/overlay.img CONTAINERFILE`

4. Make the required changes in the container. They will be persistent as long as you re-run the container with the overlay file

5. Quit the container

***

_Run the container using normal privileges_

Shifting back to normal privileges is required for graphics to work well. This is because the graphical environment is not properly set for the root user.

1. Run the container again in normal privileges but using the overlay that contains the changes. Also, attach the root user home directory in case some configuration files were saved there when modifying the container

     `apptainer shell -B/root --overlay /tmp/overlay.img CONTAINERFILE`

2. Run the required commands. Remember that some configuration files might be under /root rather than under your home directory.


***