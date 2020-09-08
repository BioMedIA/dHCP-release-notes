---
---

## Quality Control/Assurance (QC)

QC is performed at five stages of the dHCP analysis as listed below. The
final selection of subject data to release made use of these as outlined
subsequently.

## Five stages of QC  

1. Scanning notes were recorded by the radiographers, and failed scans were
manually flagged as pass/fail depending on if the issue affects the fMRI,
the dMRI, or other.

2. After reconstruction the T2, T1, fMRI and dMRI datasets were visually 
inspected and each of them was flagged as PASS/FAIL.

3. The structural pipeline QC combined several sources of information: 479
scans were scored visually as part of an atlas construction project --
we excluded scans with more than minor motion artifacts in T2. We excluded
11 scans we knew to be in error. We excluded scans on which the structural
pipeline failed to run, or on which the separate structural QC pipeline
failed to run. We did a visual inspection of all white matter surfaces and
excluded one scan that was obviously failing.

4. The fMRI pipeline generates a number of QC metrics which are described in
“Functional Pipeline” section below. 

5. The dMRI pipeline generates a number of QC metrics which are described
in the “Diffusion Pipeline” section below

The inclusion criteria for fMRI data is:

1. Must PASS fMRI scan notes QC
2. fMRI and T2w must PASS recon QC (T1w need not pass)
3. Must PASS structural pipeline QC
4. Must PASS fMRI pipeline QC

The inclusion criteria for dMRI data is:

1. Must PASS dMRI scan notes QC
2. dMRI and T2w must PASS recon QC (T1w need not pass)
3. Must PASS structural pipeline QC
4. Must PASS dMRI pipeline QC

