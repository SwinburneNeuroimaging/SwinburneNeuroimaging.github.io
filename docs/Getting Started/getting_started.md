# Getting Started with Swinburne Neuroimaging Resources

Welcome to the Swinburne Neuroimaging resources guide. This documentation will walk you through the process of setting up your account and accessing high-performance computing resources for neuroimaging research.

## Overview

To use Swinburne's neuroimaging resources, you'll need to complete the following steps:

1. Create an OzSTAR account
2. Join (or create) an OzSTAR project
3. [Set up Neurodesk](/Getting Started/setting_up_neurodesktop/)
4. Connect Neurodesk to OzSTAR
5. Obtain example code and containers
6. Run your analysis on OzSTAR

This guide covers steps 1 and 2. Additional documentation for subsequent steps will be provided separately.

---

## 1. Creating an OzSTAR Account

!!! info "About OzSTAR Accounts"
    OzSTAR accounts are completely separate from Swinburne university login credentials. You'll need to create a dedicated account even if you're already a Swinburne staff member or student.

### Who is Eligible?

OzSTAR accounts are available free of charge to:

- Swinburne University staff and students
- Researchers in astronomy and space sciences at publicly funded Australian institutions
- International collaborators on approved OzSTAR projects (cannot be project leaders)
- Students from Australian educational institutions

### Account Creation Process

1. **Submit your account request**
    
    Visit the [OzSTAR account request page](https://supercomputing.swin.edu.au/account-management/new_account_request) and fill out the form with your details.

2. **Verify your email address**
    
    After submitting your request, you'll receive a verification email. Follow the instructions to confirm your email address.

3. **Wait for approval**
    
    The OzSTAR team typically approves new accounts within 48 hours. You'll receive an email with your username when your account is approved.

4. **Access the account management system**
    
    Once approved, you can log in to the [account management portal](https://supercomputing.swin.edu.au/account-management) to manage your account settings.

!!! warning "Account Requirements"
    Every OzSTAR account must be linked to at least one project. You cannot submit jobs to the supercomputer until you've joined or created a project (see next section).

---

## 2. Joining or Creating an OzSTAR Project

### What is a Project?

A project on OzSTAR represents a research group or department. Projects are used for:

- **Management and reporting**: Organizing users by research group
- **File system quotas**: Allocating shared disk space on the `/fred` file system
- **Resource allocation**: Tracking usage for general access job queues

When you join a project, you'll gain access to a shared project directory at `/fred/your-project-id` where you can store large datasets and run computations.

### Option A: Joining an Existing Project

If you're part of an established research group that already has an OzSTAR project, follow these steps:

1. **Contact the project leader first**
    
    Before submitting a request, contact your supervisor or project leader to inform them you'll be requesting access.

2. **Submit a join request**
    
    Log in to the [account management system](https://supercomputing.swin.edu.au/account-management) and submit a [project join request](https://supercomputing.swin.edu.au/account-management/project_join_request).

3. **Wait for approval**
    
    Your request will be sent to the project leader for approval. Once approved, you'll receive an email notification.

4. **Access your project directory**
    
    After approval, you'll automatically be added to the project group and gain access to the shared project directory at `/fred/your-project-id`.

!!! tip "Students"
    Students cannot be project leaders. If you need a new project created, ask your supervisor to create one that you can then join.

### Option B: Creating a New Project

If you're a research group leader or principal investigator setting up a new group, you can create your own project:

1. **Submit a project creation request**
    
    Log in to the [account management system](https://supercomputing.swin.edu.au/account-management) and submit a [new project request](https://supercomputing.swin.edu.au/account-management/new_project_request).

2. **Wait for approval**
    
    The OzSTAR team and Swinburne Neuroimaging will review your project request.

3. **Receive confirmation**
    
    If approved, you'll receive an email when your project is created. Your project space will be created at `/fred/your-project-id`.

4. **Add team members**
    
    As the project leader, you'll be able to approve join requests from students and collaborators.

!!! warning "Project Leader Restrictions"
    Students cannot be project leaders. Project leadership is restricted to staff and principal investigators.

---

## Next Steps

Once you've completed steps 1 and 2, you're ready to move on to [setting up Neurodesk and connecting it to OzSTAR](/Getting Started/setting_up_neurodesktop). 

### Quick Reference Links

- [OzSTAR Documentation](https://supercomputing.swin.edu.au/docs/index.html)
- [Account Management Portal](https://supercomputing.swin.edu.au/account-management)
- [New Account Request](https://supercomputing.swin.edu.au/account-management/new_account_request)
- [Join Project Request](https://supercomputing.swin.edu.au/account-management/project_join_request)
- [Create New Project](https://supercomputing.swin.edu.au/account-management/new_project_request)

---


## Support

If you encounter any issues during the account creation or project setup process,

- **OzSTAR technical support**: [hpc-support@swin.edu.au](mailto:hpc-support@swin.edu.au)
- **Swinburne Neuroimaging support**: [neuroinformatics@swin.edu.au](mailto:neuroinformatics@swin.edu.au)