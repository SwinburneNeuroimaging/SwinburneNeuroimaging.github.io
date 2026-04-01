# What is OzSTAR?

OzSTAR is [Swinburne's Supercomputer](https://supercomputing.swin.edu.au/), a powerful machine designed to help Australian researchers analyse large amounts of data and run complex calculations that would be impossible on a regular computer or laptop. It is actually made up of two linked supercomputers called 'OzSTAR' and 'Ngarrgu Tindebeek' (NT for short), though most people just call the whole thing "OzSTAR".

---

## What makes a computer *'super'*?

A supercomputer isn't just a faster version of your laptop—it's fundamentally different in how it works.

Your personal computer typically has 4-8 processor cores (more if you have a high-end machine) that can handle multiple tasks simultaneously, but on a relatively small scale. A supercomputer like OzSTAR or Ngarrgu Tindebeek has **thousands of processors working together at once**. Ngarrgu Tindebeek comprises over 11,000 compute cores and 88 specialised graphics processing units (GPUs), all connected by ultra-fast networking.

### How do you use a supercomputer?

As a user of a supercomputer, you can request to use a portion of its resources for a period of time to complete your calculations. This is done through a **job submission system**: you specify what resources you need (such as how many CPU cores, how much memory, whether you need GPUs, and how long you expect the job to run), and the system schedules your job to run when those resources become available. 

You might request a single core for a quick test, or hundreds of cores to process an entire dataset in parallel. The supercomputer manages all the scheduling automatically, so multiple researchers can use different parts of the system simultaneously without interfering with each other's work.

!!! warning "A supercomputer will not automatically 'speed up' your program"
    Just because you're running something on a supercomputer doesn't mean it'll automatically be 'super fast'. In fact, if your software isn't designed for parallel processing, it might not run any faster at all. 
    
    If your analysis is set up to run step-by-step on a single core, moving it to a supercomputer won't magically speed things up. The upside? Your analysis runs on the supercomputer, not your laptop. So if your program takes 8 hours to run, you can submit the job and get on with other things instead of having your laptop tied up all day.

### The power of parallel processing

The real power of supercomputers comes when you have tasks that can be **parallelised**: processing multiple participants' data simultaneously, running hundreds of statistical permutations at once, or analysing a large quantity of data in parallel. This is where researchers see dramatic speed improvements—tasks that would take weeks on a desktop can be completed in hours.

---

## Why might you want to use OzSTAR?

OzSTAR could be useful if you're:

- :material-database: Working with large datasets that need lots of memory
- :material-clock-fast: Running analyses that would take a long time on your personal computer
- :material-chart-line: Doing heavy-duty statistical modelling
- :material-account-multiple: Processing a large number of similar tasks at once (like analysing data from hundreds of participants simultaneously)

For this kind of work, OzSTAR can dramatically speed things up and let you do analyses that just wouldn't be possible on your own machine. It's open to all Swinburne staff and students, plus many researchers across Australia.

---

## Technical Information

OzSTAR supercomputing consists of **two** supercomputers: the older "OzSTAR" and the newer "Ngarrgu Tindebeek (NT)".

!!! info "Understanding the specs"
    If you're new to supercomputers, the technical specifications below might look confusing. Here's what the key terms mean:
    
    - **Compute Nodes**: Individual computers that make up the supercomputer
    - **Processors/Cores**: The "brains" that do calculations (more cores = more tasks at once)
    - **RAM/Memory**: Temporary storage for data being actively processed (more RAM = handle larger datasets)
    - **GPUs**: Specialised processors excellent for certain types of calculations (especially machine learning and image processing)
    - **Local SSD/NVMe**: Fast temporary storage on each node
    - **Fabric Interconnect**: The ultra-fast network connecting all the nodes together

!!! note
    Everything after this might look like an assortment of random letters and numbers if you are unfamilar with high performance computing components. You don't need to know what the supercomputers are made of to use them.

### [OzSTAR (Installed 2018)](https://supercomputing.swin.edu.au/ozstar)

#### Standard Compute Nodes
- Dell R740 14G Server
- 2 × Intel Gold 6140 18-core processors 
- 2 × NVIDIA P100 12GB PCIe GPUs 
- 192 GB DDR4 RAM
- 400 GB local SSD 

#### High Memory Nodes
- Dell R740 14G Server
- 2 × Intel Gold 6140 18-core processors 
- 2 × NVIDIA P100 12GB PCIe GPUs 
- 384 GB RAM or 768 GB RAM
- 2 TB NVMe flash SSD

#### Fabric Interconnect
- 100 Gigabit per second
- High-performance Omni-Path architecture

### [Ngarrgu Tindebeek (NT) (Installed 2023)](https://supercomputing.swin.edu.au/ngarrgu-tindebeek)

#### Standard Compute Nodes (150)
- Dell PowerEdge R6525 Server
- 2 × AMD EPYC 7543 2.8 GHz 32-core processors 
- 256 GB DDR5 RAM
- 2 TB NVMe local SSD 

#### High Memory Nodes (10)
- Dell PowerEdge R6525 Server
- 2 × AMD EPYC 7543 2.8 GHz 32-core processors 
- 1024 GB DDR5 RAM
- 2 TB NVMe local SSD 

#### Data Accelerator Nodes (22)
- Dell PowerEdge XE8545 Server
- 2 × AMD EPYC 7543 2.8 GHz 32-core processors 
- 4 × NVIDIA A100 80 GB GPUs
- 512 or 1024 GB DDR5 RAM
- 2 TB NVMe local SSD 

#### Fabric Interconnect
- 200 Gigabit per second HDR Infiniband with NDR switching 
- High-performance Omni-Path architecture 

---

## Extra Links and Information

- [The OzSTAR supercomputing documentation](https://supercomputing.swin.edu.au/docs/)
- [New OzSTAR Account Request](https://supercomputing.swin.edu.au/account-management/new_account_request)
- [Join an existing OzSTAR Project](https://supercomputing.swin.edu.au/account-management/login?next=/account-management/project_join_request)