# SNI Computing Walkthough

If you are new to SNI's computing resources, this page is the best place to start. The tutorials below are arranged in the order we recommend working through them, each one builds on the last, so following the sequence will give you the smoothest experience getting set up.

That said, everyone comes with different experience. If you are already comfortable with a topic, feel free to skip ahead or give it a quick skim, you might still pick up something useful. The descriptions below should help you decide what's worth your time.

---

[Linux Command Line Basics](./basics/linux_command_line_basics.md): If you have never used a terminal before, start here. The command line is used throughout almost every other tutorial, so it is worth getting comfortable with the basics before moving on.

[What is OzSTAR?](../documentation/what_is_ozstar.md): OzSTAR and NT are Swinburne's two supercomputers. You can learn about them here.

[Create an OzSTAR/NT Account](./supercomputing/create_ozstar_account.md): Get yourself access to Swinburne's supercomputers, where your project data is stored and can run complex analysis. If you already have an account, you can skip this step.

[Join an OzSTAR/NT Project](./supercomputing/join_an_ozstar_project.md): Join a project so you can access the data your team has collected and share computing resources with your collaborators.

[SSH Basics - Connecting to Remote Computers](./basics/ssh_basics.md): Learn how to connect to remote computers using SSH. This is how you will access OzSTAR and NT directly from your terminal, transfer files, and keep sessions running after you close your laptop.

[Accessing the Supercomputer](./supercomputing/accessing_ozstar.md): Log in to OzSTAR/NT for the first time, find your project data, and learn how to transfer files between your local machine and the supercomputer.

[Navigating the Supercomputer and Downloading Data](../tutorials/supercomputing/navigating_ozstar_and_downloading_data.md): Learn how to use FileZilla to browse your project files on OzSTAR and download data to your local machine. A user-friendly alternative to the command line for transferring files.

[Where is my Data?](../documentation/where_is_my_data.md): If you haven't already worked out where your data is stored in OzSTAR/NT, this will tell you where it is.

[Setting Up Neurodesk](./neurodesk/setting_up_neurodesk.md): Set up the ARDC Virtual Desktop with Neurodesk, the recommended environment for running neuroimaging analyses at SNI. This gives you access to over 100 neuroimaging tools without installing anything on your own computer.

[Connect Neurodesk to OzSTAR/NT](./neurodesk/connect_neurodesk_to_ozstar.md) Mount your OzSTAR/NT project storage directly inside Neurodesk so you can access your data and run analyses on it from within the Neurodesk environment.

[Shell Scripting Basics](./basics/shell_scripting_basics.md): Once you are comfortable with the terminal, shell scripts let you automate repetitive tasks, such as running the same analysis pipeline across many participants. A must-read before submitting jobs to OzSTAR.

[Submitting Jobs to the Supercomputer](./supercomputing/submitting_jobs_to_ozstar.md): Learn how to submit analysis jobs to OzSTAR's job queue using Slurm. This is how you run large-scale analyses that would be too slow or resource-intensive to run interactively.

[Containers on OzSTAR/NT](./supercomputing/containers_on_ozstar.md): A deeper look at how neuroimaging software containers work on OzSTAR, including how to load tools via Neurocommand and how to modify a container if you need to customise it.
