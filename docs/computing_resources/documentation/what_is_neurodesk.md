# What is Neurodesk?

[Neurodesk](https://neurodesk.org/) is a free, open-source platform that provides a large collection of neuroimaging software tools in a single, consistent environment. Rather than installing each tool individually, a process that is often complex, time-consuming, and prone to conflicts, Neurodesk bundles everything into software containers that work the same way regardless of what computer or operating system you are using.

Neurodesk is developed and maintained by the neuroimaging community and is described in detail in the following publication:

> *Renton, A.I. et al. (2024). Neurodesk: an accessible, flexible and portable data analysis environment for reproducible neuroimaging. Nature Methods, 21, 804–808. [https://doi.org/10.1038/s41592-023-02145-x](https://doi.org/10.1038/s41592-023-02145-x)*


## How does Neurodesk work?
Neurodesk uses Apptainer (formerly Singularity) to run software containers. Each tool in Neurodesk is packaged as a container, a self-contained bundle of software and its dependencies, which Neurodesk loads on demand. You don't need to understand containers in detail to use Neurodesk, but if you'd like to learn more, see the [Containers on OzSTAR/NT](../tutorials/supercomputing/containers_on_ozstar.md) tutorial.

Neurodesk provides a graphical desktop environment called *Neurodesktop*, accessible through a web browser with a familiar point-and-click interface. This is the primary way we recommend using Neurodesk.

## How to use Neurodesk?
The recommended way to use Neurodesk is via the ARDC Nectar Virtual Desktop, with your OzSTAR project storage mounted directly to the virtual machine. This gives you access to the full Neurodesk graphical environment through your browser, while keeping your data on OzSTAR where it can also be used for large-scale job submissions.

This approach means you can:

- Use Neurodesk's graphical tools interactively without installing anything on your local computer
- Access your project data on OzSTAR directly from within Neurodesk
- Move seamlessly between interactive analysis in Neurodesk and batch processing on OzSTAR

See the [Setting up Neurodesk](../tutorials/neurodesk/setting_up_neurodesk.md) and the [Connecting Neurodesk to OzSTAR/NT](../tutorials/neurodesk/connect_neurodesk_to_ozstar.md) tutorials for step-by-step instructions on getting started.