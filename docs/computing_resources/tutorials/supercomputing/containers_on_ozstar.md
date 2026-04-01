# Containers on OzSTAR/NT

Containers are self-contained software environments that bundle an application and all of its dependencies together. On OzSTAR/NT, containers are run using Apptainer (formerly known as Singularity).

## Why use containers?
Neuroimaging software can be difficult to install. Tools often have long lists of dependencies, require specific versions of other software, or conflict with other packages already installed on a system. Containers solve this by packaging everything the software needs inside a single file. You don't need to install anything yourself,  you just run the container.
There are a few other important reasons containers are used in research:

- Reproducibility: because the entire software environment is fixed inside the container, your analysis will run the same way on any machine and at any point in the future. This is important for scientific reproducibility and for sharing your work with others.
- Portability: the same container file can be run on your local machine, on OzSTAR, or on any other system that supports Apptainer, without any changes.
- No admin required: on shared systems like OzSTAR, users do not have permission to install software directly. Containers allow you to use complex software without needing administrator access.


## Swinburne Neuroimaging Containers
Swinburne Neuroimaging maintains a shared collection of neuroimaging containers available to all OzSTAR/NT users at:

```bash
/dagg/public/neuro/containers
```
!!! note
    `/dagg/public/neuro` is a directory that's accessible to every OzSTAR/NT user.

## Loading Apptainer
Before running any containers, you need to load the Apptainer module:
```bash
$ module load apptainer
```
Or using the shorthand:
```bash
$ ml apptainer
```

## Neurocommand
Neurocommand is a collection of neuroimaging tools that can be loaded as modules on OzSTAR. To use it, you first need to initialise it using the startup script:

```bash
$ source /dagg/public/neuro/startup_neurocommand.sh
```
Once initialised, you can load individual tools as modules. For example, to load `fMRIPrep`:
```bash
$ ml fmriprep/          # Press Tab to see available versions
```
This will show something like:
```
fmriprep    fmriprep/23.2.1
```
Then load the specifc version you need:
```bash
$ ml fmriprep/23.2.1
```

!!! tip
    Always specify the version when loading a module in a job script. This ensures your analysis uses the same software version every time, even if newer versions are added later.

## List of SNI Containers
!!! warning
    This list may be incomplete, check on OzSTAR/NT directly to see a complete list. These are also types of containers, these do not include the version numbers.

```
fmriprep      # For functional MRI analysis
dcm2bids      # For converting dicom files into bids format
qsiprep       # For q-Space diffusion MRI analysis
aslprep       # For Arterial Spin Labeling MRI analysis
```

## Modifying an Apptainer container without rebuilding it
Sometimes you may need to modify an existing container, for example, to install an additional package, without rebuilding it from scratch. This can be done using an overlay, which stores your changes in a separate file that is attached to the container at runtime.

!!! warning
    Modifying a container requires a machine where you have admin (sudo) privileges, such as an ARDC Virtual Desktop. This process does not work directly on OzSTAR as users do not have sudo access there. It is also not guaranteed that a container modified on one machine will run correctly on another.

### Step 1: Set up your environment
First, find the path to your Apptainer installation. If you are on an older machine that still uses Singularity, set up an alias first:
```bash
# On a machine with Singularity (older systems)
alias apptainer='singularity'
APPTAINERPATH=$(which singularity)

# On a machine with Apptainer
APPTAINERPATH=$(which apptainer)
```

### Step 2: Create an overlay
Create an Apptainer overlay file to store your changes. The size should be large enough to hold whatever you plan to add, the example below creates a 1 GB overlay:
```bash
$ apptainer overlay create --size 1024 /tmp/overlay.img
```
If you expect to add more than 1 GB of files, increase the `--size` value accordingly.

### Step 3: Modify the container
Run the container with `sudo` and attach the overlay. Use the `APPTAINERPATH` variable because apptainer may not be in the root user's search path:
```bash
$ sudo ${APPTAINERPATH} shell --overlay /tmp/overlay.img CONTAINERFILE
```
Replace `CONTAINERFILE` with the path to your container. Once inside, make whatever changes you need. Any files you add or modify will be saved to the overlay rather than the original container. When you are done, exit the container:
```bash
$ exit
```

### Step 4: Run the modified container
After modifying the container, switch back to your normal user account to run it. This is important because the graphical environment is not set up correctly for the root user, which can cause display issues.

Run the container again as your normal user, attaching both the overlay and the root home directory (in case any configuration files were saved there during the modification step):
```bash
$ apptainer shell -B /root --overlay /tmp/overlay.img CONTAINERFILE
```
Your changes will be available inside the container. Note that some configuration files may be located under `/root` rather than your home directory.