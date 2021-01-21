---
---

## Quality Control/Assurance (QC)

QC is performed at various stages of the dHCP analysis as listed below. The
final selection of subject data to release made use of these as outlined
subsequently.

1. After **reconstruction** the T2, T1, T13D, fMRI and dMRI datasets were visually 
inspected and scored as PASS/FAIL.  

2. The **fMRI pipeline** and **dMRI pipelines** generate numerous quantitative
QC metrics which are described on their respective pages:

   1. [Functional Pipeline](fmri.md#fmri-qc)

   2. [Diffusion EDDY Pipeline](dwi.md#diffusion-mri-qc)

   3. [Diffusion SHARD Pipeline](dwi-shard.md#diffusion-mri-qc)
   
3. All QC metrics are available in the `combined.tsv` spreadsheet in the
[supplementary](https://github.com/BioMedIA/dHCP-release-notes/tree/master/supplementary_files).

## Selection Criteria

The inclusion criteria for **reconstructed/raw data** is:

1. Scans that scored PASS on the visual recon QC are released, and also
subsequently processed by the sMRI, fMRI, and dMRI pipeline.

The inclusion criteria for the **sMRI pipeline outputs** is:

1. Raw T2w must pass the recon QC.

2. All completed segmentations from the structural pipeline are released.

3. Extracted surfaces were visually inspected and only successful extractions
are released.

4. Myelin maps are only released if the surface extraction was successful.

The inclusion criteria for **fMRI pipeline outputs** is:

1. Raw fMRI & T2w must pass the recon QC.

2. All preprocessed fMRI is released. Data that failed fMRI
pipeline QC is flagged in the `combined.tsv` spreadsheet in the
[supplementary](https://github.com/BioMedIA/dHCP-release-notes/tree/master/supplementary_files)

3. Transforms to standard space are dependent upon availability of extracted
(white and pial) surfaces from sMRI pipeline.

The inclusion criteria for **dMRI pipeline outputs** is:

1. Raw dMRI & T2w must pass the recon QC.

2. All preprocessed dMRI is released. Data that failed dMRI
pipeline/s QC is flagged in the `combined.tsv` spreadsheet in the
[supplementary](https://github.com/BioMedIA/dHCP-release-notes/tree/master/supplementary_files)

3. Transforms to standard space are dependent upon availability of extracted
(white and pial) surfaces from sMRI pipeline.

