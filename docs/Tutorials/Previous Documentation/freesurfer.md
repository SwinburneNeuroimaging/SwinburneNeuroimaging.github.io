### How do I know what each file in the output of Freesurfer contains?
Refer to https://surfer.nmr.mgh.harvard.edu/fswiki/ReconAllOutputFiles

### How to locate the T1 that was used for the parcellation?

Freesurfer saves the original T1 input file in FREESURFER_BASE_DIR/PARTICIPANT_DIR/mri/orig/001.mgz

mgz is a compressed MGH image format. It can be viewed using mrview (part of the MRtrix3 package).

If using other viewers, it can be converted to nifti using mrconvert (part of the MRtrix3 package as well):

`mrconvert 001.mgz 001.nii.gz`