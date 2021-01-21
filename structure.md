---
---

## Data directory structure

The structure of data directory and convention of files naming will follow
the BIDS specification (v1.5.0-dev).

The `participants.tsv` for each BIDS pipeline has a number of extra columns
beyond `participant_id`. These have the following meaning:

Field          | Meaning
:------------- | :------
`sex`       | Male / Female
`birth_age`    | Gestational age at birth in weeks
`birth_weight` | Birthweight (kg)
`singleton` | Singleton pregnancy (S) / Multiple pregnancy (M)

The `sessions.tsv` file has extra columns beyond `session_id`. These have
the following meaning:

Field                     | Meaning
:------------------------ | :------
`scan_age`                | Gestational age at scan in weeks
`scan_head_circumference` | Head circumference (cm)
`radiology_score`         | Subject status, see below
`scan_number` | 1 for the first scan, 2 for the second
`sedation` | 1 if the subject was sedated during the scan, 0 otherwise

The MRI scans were reviewed by a specialist perinatal neuroradiologist who
scored each subject using the following scale:

1. Normal appearance for age

2. Incidental findings with unlikely significance for clinical outcome
or analysis (e.g. subdural haemorrhage. Isolated subependymal cysts. Mild
inferior vermis rotation)

3. Incidental findings with unlikely clinical significance but possible
analysis significance (e.g. several punctate lesions or other focal white
matter / cortical lesions not thought to be of clinical significance)

4. Incidental findings with possible clinical significance. Unlikely analysis
significance (e.g. Isolated non brain anomaly for example in pituitary /
on tongue)

5. Incidental finding with possible / likely significance for both clinical and imaging analysis (e.g. Major lesions within white matter cortex, cerebellum and or basal ganglia; small head / brain < 1st centile)

6. `Q`, meaning poor quality anatomical data

## Data directory structure and naming convention

### Reconstruction Pipeline

**Path:** `rawdata/sub-{subid}/ses-{sesid}`

| Group   | Description                                                                             | Filename                                                                  |
|:--------|:----------------------------------------------------------------------------------------|:--------------------------------------------------------------------------|
| T1      | T1w image (native acquired stack)                                                       | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_T1w.nii`                       |
| T1      | T1w phase (native acquired stack)                                                       | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_T1w.nii`             |
| T1      | T1w image (motion corrected and super resolved)                                         | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcsr_T1w.nii`              |
| T1      | T1w phase (motion corrected and super resolved)                                         | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcsrphase_T1w.nii`         |
| T1      | T1w image (motion corrected)                                                            | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mc_T1w.nii`                |
| T1      | T1w phase (motion corrected)                                                            | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcphase_T1w.nii`           |
| T1      | T1w image (combined Slice-to-Volume reconstruction)                                     | `anat/sub-{subid}_ses-{sesid}_rec-SVR_T1w.nii`                            |
| T2      | T2w image (native acquired stack)                                                       | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_T2w.nii`                       |
| T2      | T2w phase (native acquired stack)                                                       | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_T2w.nii`             |
| T2      | T2w image (motion corrected and super resolved)                                         | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcsr_T2w.nii`              |
| T2      | T2w phase (motion corrected and super resolved)                                         | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcsrphase_T2w.nii`         |
| T2      | T2w image (motion corrected)                                                            | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mc_T2w.nii`                |
| T2      | T2w phase (motion corrected)                                                            | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcphase_T2w.nii`           |
| T2      | T2w image (combined Slice-to-Volume reconstruction)                                     | `anat/sub-{subid}_ses-{sesid}_rec-SVR_T2w.nii`                            |
| T13D    | T1w image (3D MPRAGE)                                                                   | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_acq-MPRAGE_T1w.nii`            |
| T13D    | T1w phase (3D MPRAGE)                                                                   | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_acq-MPRAGE_rec-phase_T1w.nii`  |
| fMRI    | 4D Spin Echo EPI with different phase encode directions (for topup fieldmap estimation) | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_epi.nii`                       |
| fMRI    | 4D Spin Echo EPI (phase)                                                                | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_epi.nii`             |
| dMRI    | Single-band (ref) dMRI EPI                                                              | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_sbref.nii`                      |
| dMRI    | Single-band dMRI EPI (phase)                                                            | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_sbref.nii`            |
| dMRI    | Estimate of error in denoised data                                                      | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-denoisederror_dwi.nii`      |
| dMRI    | Multi-band dMRI EPI                                                                     | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_dwi.nii`                        |
| dMRI    | Multi-band dMRI EPI (phase)                                                             | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_dwi.nii`              |
| dMRI    | Multi-band dMRI EPI (Chi2-maps)                                                         | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-chi2_dwi.nii`               |
| dMRI    | Multi-band dMRI EPI (denoised reconstruction)                                           | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-denoised_dwi.nii`           |
| dMRI    | Multi-band dMRI EPI (denoised phase)                                                    | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-denoisedphase_dwi.nii`      |
| fMRI    | Single-band Ref                                                                         | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_sbref.nii`           |
| fMRI    | Single-band Ref (phase)                                                                 | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_rec-phase_sbref.nii` |
| fMRI    | Resting fMRI                                                                            | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_bold.nii`            |
| fMRI    | Resting fMRI (phase)                                                                    | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_phase.nii`           |
| fMRI    | Single-band Ref                                                                         | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_sbref.nii`           |
| fMRI    | Single-band Ref (phase)                                                                 | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_sbref.nii`           |
| B0      | Dual echo-time (magnitude)                                                              | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_magnitude.nii`                 |
| B0      | Dual echo-time (phase)                                                                  | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_phase.nii`                     |
| B0      | Dual echo-time field-map in (Hz) - filtered and smoothed                                | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-filtered_fieldmap.nii`     |
| B0      | Dual echo-time field-map in (Hz) - raw                                                  | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-raw_fieldmap.nii`          |
| B1      | B1 field map (magnitude)                                                                | `B1/sub-{subid}_ses-{sesid}_run-{seqnum}_magnitude.nii`                   |
| B1      | B1 field map (phase)                                                                    | `B1/sub-{subid}_ses-{sesid}_run-{seqnum}_phase.nii`                       |
| B1      | B1 field map (rel. nom. flip)                                                           | `B1/sub-{subid}_ses-{sesid}_run-{seqnum}_b1map.nii`                       |
| recon03 | Multi-band dMRI EPI (Release 2 reconstruction)                                          | `dwi/sub-{subid}_ses-{sesid}_rec-release2_dwi.nii`                        |

**Path:** sourcedata/sub-{subid}/ses-{sesid}

| Group   | Description                      | Filename                                                         |
|:--------|:---------------------------------|:-----------------------------------------------------------------|
| fMRI    | Resting fMRI Physlog (uncropped) | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_physio.log` |

### Structural pipeline

**Path:** derivatives/dhcp_anat_pipeline/sub-{subid}/ses-{sesid}

| Description                                                                          | Filename                                                                                         |
|:-------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------|
| FSL BET brain mask                                                                   | `anat/sub-{subid}_ses-{sesid}_desc-brain_mask.nii.gz`                                            |
| Draw-EM regional segmentation (87 labels)                                            | `anat/sub-{subid}_ses-{sesid}_desc-drawem87_dseg.nii.gz`                                         |
| Draw-EM tissue segmentation (9 labels)                                               | `anat/sub-{subid}_ses-{sesid}_desc-drawem9_dseg.nii.gz`                                          |
| Cortical ribbon                                                                      | `anat/sub-{subid}_ses-{sesid}_desc-ribbon_dseg.nii.gz`                                           |
| T1 weighted image (in T2 space)                                                      | `anat/sub-{subid}_ses-{sesid}_T1w.nii.gz`                                                        |
| T1 bias field (in T2 space)                                                          | `anat/sub-{subid}_ses-{sesid}_desc-biasfield_T1w.nii.gz`                                         |
| T1 weighted, bias corrected image (in T2 space)                                      | `anat/sub-{subid}_ses-{sesid}_desc-restore_T1w.nii.gz`                                           |
| T2 weighted image                                                                    | `anat/sub-{subid}_ses-{sesid}_T2w.nii.gz`                                                        |
| T2 bias field                                                                        | `anat/sub-{subid}_ses-{sesid}_desc-biasfield_T2w.nii.gz`                                         |
| T2 weighted, bias corrected image                                                    | `anat/sub-{subid}_ses-{sesid}_desc-restore_T2w.nii.gz`                                           |
| QC report                                                                            | `sub-{subid}_ses-{sesid}_qc.pdf`                                                                 |
| Left/Right white surface                                                             | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_wm.surf.gii`                                           |
| Left/Right pial surface                                                              | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_pial.surf.gii`                                         |
| Left/Right mid-thickness surface                                                     | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_midthickness.surf.gii`                                 |
| Left/Right inflated surface                                                          | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_inflated.surf.gii`                                     |
| Left/Right very inflated surface                                                     | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_vinflated.surf.gii`                                    |
| Left/Right spherical surface                                                         | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_sphere.surf.gii`                                       |
| Cortical curvature                                                                   | `anat/sub-{subid}_ses-{sesid}_curv.dscalar.nii`                                                  |
| Left/Right cortical curvature                                                        | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_curv.shape.gii`                                        |
| Sulcal depth                                                                         | `anat/sub-{subid}_ses-{sesid}_sulc.dscalar.nii`                                                  |
| Left/Right sulcal depth                                                              | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_sulc.shape.gii`                                        |
| Cortical thickness                                                                   | `anat/sub-{subid}_ses-{sesid}_thickness.dscalar.nii`                                             |
| Left/Right cortical thickness                                                        | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_thickness.shape.gii`                                   |
| Cortical thickness (curvature regressed out)                                         | `anat/sub-{subid}_ses-{sesid}_desc-corr_thickness.dscalar.nii`                                   |
| Left/Right cortical thickness (curvature regressed out)                              | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_desc-corr_thickness.shape.gii`                         |
| Cortical myelin                                                                      | `anat/sub-{subid}_ses-{sesid}_myelinmap.dscalar.nii`                                             |
| Left/Right cortical myelin                                                           | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_myelinmap.shape.gii`                                   |
| Smoothed cortical myelin                                                             | `anat/sub-{subid}_ses-{sesid}_desc-smoothed_myelinmap.dscalar.nii`                               |
| Left/Right smoothed cortical myelin                                                  | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_desc-smoothed_myelinmap.shape.gii`                     |
| Cortical regional labels projected from volume                                       | `anat/sub-{subid}_ses-{sesid}_desc-drawem_dseg.dlabel.nii`                                       |
| Left/Right cortical regional labels projected from volume                            | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_desc-drawem_dseg.label.gii`                            |
| Left/Right Medial wall                                                               | `anat/sub-{subid}_ses-{sesid}_hemi-{hemi}_desc-medialwall_mask.shape.gii`                        |
| Workbench file for loading surfaces                                                  | `anat/wb.spec`                                                                                   |
| Warp from native structural space to the subject’s age respective template space     | `xfm/sub-{subid}_ses-{sesid}_from-T2w_to-serag{age}wk_mode-image.nii.gz`                         |
| Warp from the subject’s age respective template space to the native structural space | `xfm/sub-{subid}_ses-{sesid}_from-serag{age}wk_to-T2w_mode-image.nii.gz`                         |
| Warp from native structural space to the 40-week Serag template space                | `xfm/sub-{subid}_ses-{sesid}_from-T2w_to-serag40wk_mode-image.nii.gz`                            |
| Warp from the 40-week Serag template space to the native structural space            | `xfm/sub-{subid}_ses-{sesid}_from-serag40wk_to-T2w_mode-image.nii.gz`                            |
| Transform from native surface to the dHCP Symmetric 40week surface template          | `xfm/sub-{subid}_ses-{sesid}_hemi-{hemi}_from-native_to-dhcpSym40_dens-32k_mode-sphere.surf.gii` |

### Diffusion EDDY pipeline

**Path:** derivatives/dhcp_dmri_eddy_pipeline/sub-{subid}/ses-{sesid}

| Description                                                                                                                                              | Filename                                                                |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------|
| Eddy current, susceptibility-by-motion and motion (within and between volumes) corrected super-resolved 4D volume with outlier rejection and replacement | `dwi/sub-{subid}_ses-{sesid}_desc-preproc_dwi.nii.gz`                   |
| List of b-values                                                                                                                                         | `dwi/sub-{subid}_ses-{sesid}_desc-preproc_dwi.bval`                     |
| List of post-EDDY rotated gradient directions                                                                                                            | `dwi/sub-{subid}_ses-{sesid}_desc-preproc_dwi.bvec`                     |
| Brain mask                                                                                                                                               | `dwi/sub-{subid}_ses-{sesid}_desc-brain_mask.nii.gz`                    |
| Estimated field map                                                                                                                                      | `fmap/sub-{subid}_ses-{sesid}_fieldmap.nii.gz`                          |
| QC report (JSON)                                                                                                                                         | `qc/sub-{subid}_ses-{sesid}_qc.json`                                    |
| QC report (PDF)                                                                                                                                          | `qc/sub-{subid}_ses-{sesid}_qc.pdf`                                     |
| Rigid-body transform from structural to diffusion space                                                                                                  | `xfm/sub-{subid}_ses-{sesid}_from-T2w_to-dwi_mode-image.mat`            |
| Rigid-body transform from diffusion to structural space                                                                                                  | `xfm/sub-{subid}_ses-{sesid}_from-dwi_to-T2w_mode-image.mat`            |
| Warp from diffusion space to the extended dHCP 40-week template space                                                                                    | `xfm/sub-{subid}_ses-{sesid}_from-dwi_to-extdhcp40wk_mode-image.nii.gz` |
| Warp from the extended dHCP 40-week template space to diffusion space                                                                                    | `xfm/sub-{subid}_ses-{sesid}_from-extdhcp40wk_to-dwi_mode-image.nii.gz` |
| DTI FA map (based on b=1k shell)                                                                                                                         | `dwi/sub-{subid}_ses-{sesid}_model-DTI_FA.nii.gz`                       |
| DTI MD map (based on b=1k shell)                                                                                                                         | `dwi/sub-{subid}_ses-{sesid}_model-DTI_MD.nii.gz`                       |
| DTI V1 map (based on b=1k shell)                                                                                                                         | `dwi/sub-{subid}_ses-{sesid}_model-DTI_EVECS.nii.gz`                    |
| DTI full tensor (based on b=1k shell)                                                                                                                    | `dwi/sub-{subid}_ses-{sesid}_model-DTI_diffmodel.nii.gz`                |
| DKI mean kurtosis map                                                                                                                                    | `dwi/sub-{subid}_ses-{sesid}_model-DKI_MK.nii.gz`   

### Diffusion SHARD pipeline

**Path:** derivatives/dhcp_dmri_shard_pipeline/sub-{subid}/ses-{sesid}

| Description                                                                  | Filename                                                                |
|------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Topup field map                                                              | `fmap/sub-{subid}_ses-{sesid}_fieldmap.nii.gz`                          |
| Brain mask derived from T2w, warped to preprocessed DWI                      | `dwi/sub-{subid}_ses-{sesid}_desc-brain_mask.nii.gz`                    |
| Motion corrected output (5D image of multi-shell SH coefficients, x,y,z,b,m) | `dwi/sub-{subid}_ses-{sesid}_desc-shard_mssh.nii.gz`                    |
| Motion parameters                                                            | `dwi/sub-{subid}_ses-{sesid}_desc-shard_motion.txt`                     |
| Slice weights                                                                | `dwi/sub-{subid}_ses-{sesid}_desc-shard_sliceweights.txt`               |
| Local weights for fat-shift suppression                                      | `dwi/sub-{subid}_ses-{sesid}_desc-shard_voxelweights.nii.gz`            |
| Preprocessed DWI data (denoising, motion correction, and destriping)         | `dwi/sub-{subid}_ses-{sesid}_desc-preproc_dwi.nii.gz`                   |
| List of b-values in FSL format                                               | `dwi/sub-{subid}_ses-{sesid}_desc-preproc_dwi.bval`                     |
| List of gradient directions in FSL format                                    | `dwi/sub-{subid}_ses-{sesid}_desc-preproc_dwi.bvec`                     |
| QC report                                                                    | `qc/sub-{subid}_ses-{sesid}_qc.html`                                    |
| Rigid-body transform from structural to diffusion space                      | `xfm/sub-{subid}_ses-{sesid}_from-T2w_to-dwi_mode-image.mat`            |
| Rigid-body transform from diffusion to structural space                      | `xfm/sub-{subid}_ses-{sesid}_from-dwi_to-T2w_mode-image.mat`            |
| Warp from diffusion space to the extended dHCP 40-week template space        | `xfm/sub-{subid}_ses-{sesid}_from-dwi_to-extdhcp40wk_mode-image.nii.gz` |
| Warp from the extended dHCP 40-week template space to diffusion space        | `xfm/sub-{subid}_ses-{sesid}_from-extdhcp40wk_to-dwi_mode-image.nii.gz` |

### Functional pipeline

**Path:** derivatives/dhcp_fmri_pipeline/sub-{subid}/ses-{sesid}

| Description                                                                    | Filename                                                                      |
|:-------------------------------------------------------------------------------|:------------------------------------------------------------------------------|
| Multi-band EPI, distortion corrected, motion corrected, 4D image               | `func/sub-{subid}_ses-{sesid}_task-rest_desc-mcdc_bold.nii.gz`                |
| Multi-band EPI, distortion corrected, motion corrected, FIX denoised, 4D image | `func/sub-{subid}_ses-{sesid}_task-rest_desc-preproc_bold.nii.gz`             |
| Motion parameters                                                              | `func/sub-{subid}_ses-{sesid}_motion.tsv`                                     |
| Brain mask                                                                     | `func/sub-{subid}_ses-{sesid}_task-rest_desc-brain_mask.nii.gz`               |
| Derived fieldmap, magnitude                                                    | `fmap/sub-{subid}_ses-{sesid}_magnitude.nii.gz`                               |
| Derived fieldmap (rad/s)                                                       | `fmap/sub-{subid}_ses-{sesid}_fieldmap.nii.gz`                                |
| QC report                                                                      | `sub-{subid}_ses-{sesid}_funcqc.html`                                         |
| Rigid-body transform from functional (mcdc) to single-band Ref space           | `xfm/sub-{subid}_ses-{sesid}_from-bold_to-sbref_mode-image.mat`               |
| Rigid-body transform from single-band Ref space to structural space            | `xfm/sub-{subid}_ses-{sesid}_from-sbref_to-T2w_mode-image.mat`                |
| Rigid-body transform from functional (mcdc) to structural space                | `xfm/sub-{subid}_ses-{sesid}_from-bold_to-T2w_mode-image.mat`                 |
| Rigid-body transform from field-map to structural space                        | `xfm/sub-{subid}_ses-{sesid}_from-fieldmap_to-T2w_mode-image.mat`             |
| Warp from functional (mcdc) space to the extended dHCP 40-week template space  | `xfm/sub-{subid}_ses-{sesid}_from-bold_to-extdhcp40wk_mode-image.nii.gz`      |
| Warp from the structural space to the extended dHCP 40-week template space     | `xfm/sub-{subid}_ses-{sesid}_from-T2w_to-extdhcp40wk_mode-image.nii.gz`       |
| ICA confound regressors                                                        | `func/sub-{subid}_ses-{sesid}_task-rest_desc-fixregressors_timeseries.nii.gz` |
| FOV 4D volumetric mask                                                         | `func/sub-{subid}_ses-{sesid}_task-rest_desc-fov4d_mask.nii.gz`               |
