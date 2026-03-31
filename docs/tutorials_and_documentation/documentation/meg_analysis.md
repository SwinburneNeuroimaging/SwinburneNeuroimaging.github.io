# MEG Analysis

# Preprocessing 

1. Run freesurfer recon-all and ANTs coregistration
1. coregister MEG Polhemus data with freesurfer MRI scalp surface
2. <ol type="a">
    <li>if using beamformer for group analysis, create volumetric forward models based on warped individual grids </li>
    <li>if using dSPM/minimum norm method, create surface forward models based on the freesurfer mesh </li>
</ol>

Start with raw data file (.fif), output of each step feeds into the next one.

4. auto-bad maxwell*
4. manually mark bad channels
5. OTP
6. maxfilter [motion-correction / combine blocks] 

[If using empty room data for noise covariance, mark same channels as bad and repeat (6) and (7)]

8. ICA [auto ecg, eog]
8. muscle artifact annotation
9. define epochs by events, tmin,tmax and baseline
10. manually mark any remaining bad epochs (epochs overlapping with muscle artifact annotation will be marked as bad) [ANNOTATION]
11. Visually inspect raw data, mark additional regions as bad if necessary

# Analysis - do the following for each freqency band of interest:

13. pass-band filter cleaned data 
    
[If using empty room data for noise covariance, pass-band filter cleaned empty room data.]

14. create epochs for data 

[If using empty room data for noise covariance, create the same number of epochs from cleaned empty room data]

15. construct data covariance matrix from data epochs
15. construct noise covariance matrix, from baseline of data epochs, or from empty room data 
16.
<ol type="a"><li>If using beamformer, construct vector and/or SAM filter from (15) and (16)</li>
  <ol type="a">
    <li>construct a covariance matrix for each epoch, and pass these one-by-one throught the beamformer filter
         to produce an NAI value for each epoch at each grid point of the volumetric source space</li>
    <li>connectivity - atlas to give single time series per region, SAM filter applied to each epoch</li>
  </ol>
<li>See mne python dSPM tutorials</li>
</ol>

# Statistics
within group or between group statistics, non-parameteric max-stats and/or FDR (check p-vaue distributions!) \
**Beamformer** group level stats on individual grid points (one-to-one anatomical coresspondance across participants) \
   view results as nifti using fsleyes \
**dSPM/Minimum Norm** Spherical morph of surface meshes, see mne python 


