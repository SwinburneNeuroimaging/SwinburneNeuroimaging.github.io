# Submitting jobs to OzSTAR

OzSTAR is Swinburne's supercomputer. Rather than running commands directly in the terminal, you submit *jobs* — instructions describing what you want the computer to do and what resources you need to do it. OzSTAR then queues and runs your job when the requested resources become available.

Jobs are submitted using **Slurm**, a job scheduling system used by many supercomputers. This guide covers the basics of writing and submitting a Slurm job script. Keep in mind that every project is different, you will need to adjust the parameters to suit your own data and software.

!!! tip
    A more complete reference for creating and submitting jobs can be found in the [OzSTAR documentation](https://supercomputing.swin.edu.au/docs/2-ozstar/oz-slurm-create.html). You can also access the full `sbatch` manual by typing `man sbatch` in the terminal after logging in to OzSTAR.

## What is a job script?
This is an example job script:
```bash
#!/bin/bash                                    # Shebang, defines which interpreter to use

#SBATCH -J my_job                              # Job name (change to something meaningful)
#SBATCH --time=4:00:00                         # Maximum run time (hh:mm:ss)
#SBATCH -n 1                                   # Number of tasks (usually 1)
#SBATCH --cpus-per-task=2                      # Number of CPUs per task
#SBATCH --mem-per-cpu=16G                      # RAM per CPU
#SBATCH --tmp=40GB                             # Temporary disk space per node
#SBATCH --mail-type=ALL                        # Email notifications (BEGIN, END, FAIL, or ALL)
#SBATCH --mail-user=your_email@swin.edu.au     # Email address for notifications
#SBATCH -e /path/to/project/log/error_%j.log   # Where to save error logs
#SBATCH -o /path/to/project/log/output_%j.log  # Where to save output logs

# Load any required software modules
module load apptainer

# Pass in a variable from the command line (optional)
export variable=$1

# Run your script or program
/path/to/your/script.sh ${variable}
```

A job script is a shell script (a `.sh` file) with two parts:

1. **`#SBATCH` directives** — lines at the top of the script that tell Slurm what resources to request (time, memory, CPUs, etc.)
2. **The commands to run** — the actual analysis or software you want to execute

The `#SBATCH` lines look like comments to the shell, but Slurm reads them as instructions before running your script.

!!! warning
    The log directory (e.g. `log/`) must already exist before you submit the job. Slurm will not create it for you. Run `mkdir -p /path/to/project/log` beforehand if needed.

### What does `%j` mean?
In the log file paths, `%j` is automatically replaced by Slurm with the job's unique ID number. This means each job gets its own log file, so they don't overwrite each other. For example, `error_%j.log` might become `error_99999999.log`.

## Submitting a job

Once your script is ready, submit it from the terminal with `sbatch`:

```bash
sbatch my_job_script.sh
```

If the submission is successful, you will see:

```
Submitted batch job 99999999
```

The number printed is your **job ID**. Keep a note of it, you will need it to check on your job.

## Checking job status

After submission, your job will move through the following states:

| State | Meaning |
|-------|---------|
| `PENDING` | Job is in the queue waiting for resources to become available |
| `RUNNING` | Resources have been allocated and the job is currently executing |
| `COMPLETED` | Job finished successfully |
| `FAILED` | Job encountered an error and did not complete successfully |

You can monitor your job using the [OzSTAR job monitor](https://supercomputing.swin.edu.au/monitor/) — search by your job ID, job name, or username.

You can also check from the terminal:

```bash
squeue --me              # Show all your currently running or pending jobs
sacct -j 99999999        # Show details for a specific job ID
```