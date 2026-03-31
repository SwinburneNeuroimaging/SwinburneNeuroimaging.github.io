# Shell Scripting Basics

A "shell script" (`.sh` files) is a plain text file containing a series of commands. Instead of typing the same commands repeatedly, you save them to a file and run them all in sequence. This is particularly useful in neuroimaging, where you often need to run the same analysis pipeline across many participants.

## Your first script
### Using `echo` to print text
In shell scripting, the `echo` command is the command to print to the terminal, so lets use that to print some basic information.

Create a new file ending in `.sh` using a text editor:
```bash
nano my_script.sh
```
Then type the following:
```bash
#!/bin/bash

echo "Hello, world!"
echo "Today is: $(date)"
```
The first line `#!/bin/bash` is called the *shebang* and it tell the system which interpreter (or program) to use when running the script. In this case we are using `bash`, which is often the default option if you forge tto include it.

Save and exit from `nano` (`Crtl + O`, then `Ctrl + X`). 

### Giving executable permissions
Next we need to make the script *executable*, which involves changing its permissions.
```bash
chmod +x my_script.sh
```
This gives all users executable permissions for this file.

### Running the script
Now run the script
```bash
./my_script.sh         # Runs in separate sub-shell (variable changes are lost)    
source my_script.sh    # Runs in current shell (variable changes persist)
```
You should see (modified to your current date)
```
Hello, world!
Today is: Mon Mar 30 10:00:00 AEDT 2026
```

!!! tip
    The ./ before the script name tells the terminal to look for the script in the current directory. Without it, the terminal will look for the command in the system's standard locations and won't find it. 

    You can also specify the whole path if you need to: `./Users/User/Documents/my_script.sh`

## Variables
Variables let you store values and reuse them throughout your script. You define a variable with `=` (no spaces around it) and access its value with `$`.
```bash
#!/bin/bash

subject="sub-01"
session="ses-01"
data_dir="/data/project"

echo "Processing $subject $session"
echo "Data is in $data_dir/$subject"
```

!!! Warning
    Unlike Python, spaces in Shell scripting is very important. You can break a script by having a space it the wrong place. So pay attention to where spaces are and are not needed.

You can also store the output of a command in a variable using `$()`:
```bash
#!/bin/bash

current_date=$(date)
num_files=$(ls /data/ | wc -l)

echo "Run on: $current_date"
echo "Found $num_files files"
```
!!! tip
    It is good practice to wrap variable paths in double quotes when using them, e.g. `"$data_dir"`. This prevents errors if the path contains spaces.

## Loops
Loops let you repeat a block of commands multiple times, for example, running the same analysis on every participant.

### Loop over a list
```bash
#!/bin/bash

for subject in sub-01 sub-02 sub-03 sub-04; do
    echo "Processing $subject"
done
```

### Loop over files matching a pattern
If you are familar with how wildcards work ([see here to learn about them](../linux_command_line_basics/#wildcards)), we can use wildcards to match patterns in files and directories and loop over them.

```bash
#!/bin/bash

for scan in /data/raw/*.nii.gz; do
    echo "Found scan: $scan"
done
```

### Loop over all directories
```bash
#!/bin/bash

for subject_dir in /data/sub-*/; do
    subject=$(basename "$subject_dir")
    echo "Processing $subject"
done
```
Here `basename` strips the directory path and gives you just the folder name, e.g. `sub-01`.

## Conditionals
Conditionals let your script make decisions, for example, skipping a participant if their output already exists.

### Checking files exist
```bash
#!/bin/bash

subject="sub-01"
output="/data/processed/${subject}_T1w_brain.nii.gz"

if [ -f "$output" ]; then
    echo "$subject already processed, skipping."
else
    echo "Processing $subject..."
fi
```
!!! warning
    The spaces in an `if/fi` statement are important, particually the spaced around `[ -f "$output" ]`.

The `-f` flag checks whether a file exists. Here are the most useful test flags:
 
| Flag | Meaning |
|------|---------|
| `-f` | File exists |
| `-d` | Directory exists |
| `-e` | File or directory exists |
| `-z` | String is empty |
| `-s` | File exists and is not empty |

### Comparing values
You can also compare values:
```bash
if [ "$subject" == "sub-01" ]; then
    echo "This is the first subject"
fi

if [ "$num_files" -gt 10 ]; then
    echo "More than 10 files found"
fi
```
Use `-gt` (greater than), `-lt` (less than), `-eq` (equal to) and `-ne` (not equal to) when comparing numbers and `==` for strings.


## Command line arguments
Rather than hardcoding values in your script, you can pass them in when you run it. Inside the script, `$1` is the first argument, `$2` is the second, and so on.

```bash
#!/bin/bash

subject=$1
session=$2

echo "Processing $subject $session"
```

Then you can run it like this:
```bash
./my_script.sh sub-01 ses-01
```


It can be good practice to check that required arguments were actually given:
```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: ./my_script.sh <subject_id>"
    exit 1
fi

subject=$1
echo "Processing $subject"
```
Here we are checking that `$1` is not an empty string (`-z`), if it is, we print how to actually use the script properly. `exit 1` stops the script and signals that something went wrong. `exit 0` (or just exit) means the script finished successfully.


## Functions
Functions let you group a set of commands together and call them by name. This is useful for avoiding repetition in longer scripts.

```bash
#!/bin/bash

process_subject() {
    local subject=$1
    local data_dir=$2

    echo "Starting $subject"
    mkdir -p "$data_dir/$subject/results"
    echo "Finished $subject"
}

process_subject "sub-01" "/data/project"
process_subject "sub-02" "/data/project"
```
Inside a function, `$1`, `$2` etc. refer to the arguments passed to the function (not the script's own arguments). Using `local` keeps the variable scoped to the function so it doesn't interfere with the rest of the script.
