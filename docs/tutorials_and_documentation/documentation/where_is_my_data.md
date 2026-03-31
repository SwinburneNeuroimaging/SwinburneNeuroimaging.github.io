# Where is my Data?

All of the data is on OzSTAR/NT, Swinburne's Supercomputer. It is stored in one of three locations depending on what it is and how it is being used.

| Location | Path | Use for |
|----------|------|---------|
| Project data | `/fred/ozXXX/` | Raw data, processed outputs, anything long-term |
| Home directory | `~` | Scripts and personal config files|
| SNI shared data | `/dagg/public/neuro` | SNI containers and shared resources (read-only) |

## Project Data - `/fred/ozXXX`
This is where your research data lives. Replace `ozXXX` with your project code, which you can find on the [OzSTAR account portal](https://supercomputing.swin.edu.au/account-management/project_memberships).

You can find this data and download it by [accessing OzSTAR/NT](../tutorials/supercomputing/accessing_ozstar.md).

```bash
$ cd /fred/ozXXX
```

- MRI data is stored under `/fred/ozXXX/raw/dicom/`
- MEG data is stored under `/fred/ozXXX/raw/meg/`


## Home Directory - `/home/UserName` or `~`
Your home directory is your personal folder on OzSTAR, and is not shared with other project members.

```bash
$ cd
```
Your home directory has a small storage quota and is intended for personal configuration files and scripts, not for storing data or large files. 

!!! note
    We do not have control over what you do or do not put in your home directory. If you put something there, we do not have access to it to find it for you.

## SNI Shared Containers - `/dagg/public/neuro`
SNI maintains a shared directory accessible to all OzSTAR users. This is where you will find SNI's neuroimaging software containers and other shared resources.

```bash
$ cd /dagg/public/neuro
```
This directory is read-only for most users, you cannot save your own data here. See the [containers on OzSTAR page](../tutorials/supercomputing/containers_on_ozstar.md) for more detail on what is available here and how to use it.

## Summary
