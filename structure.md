---
---

## Data directory structure

The structure of data directory and convention of files naming will follow
the BIDS specification (v1.0.2) and the organization of previous data
release of 40 subjects.

The `participants.tsv` for each BIDS pipeline has a number of extra columns
beyond `participant_id`. These have the following meaning:

Field          | Meaning
:------------- | :------
`gender`       | Male / Female
`birth_age`    | Gestational age at birth in weeks
`birth_weight` | Birthweight (kg)
`singleton`    | Singleton / multiple status of the pregnancy

The `sessions.tsv` file has extra columns beyond `session_id`. These have
the following meaning:

Field                     | Meaning
:------------------------ | :------
`scan_age`                | Gestational age at scan in weeks
`scan_head_circumference` | Head circumference (cm)
`scan_number`             | 1 for the first scan, 2 for the second
`radiology_score`         | Subject status, see below
`sedation`                | 1 if the subject was sedated during the scan, 0 otherwise

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

As a convenience, an extra top-level file called `combined.tsv` lists all
these fields for all scans in a single large table.

## Data directory structure and naming convention

The data directory structure and naming of files is organized as follows. 

Abbreviation | Meaning
:----------- | :------
`<subid>`    | subject ID
`<sesid>`    | refers to session ID
`CSF`        | cerebrospinal fluid
`WM`         | white matter
`cGM`        | cortical grey matter
`sGM`        | subcortical grey matter
`EPI`        | echo-planar imaging

## Structural pipeline

### Inputs

Inputs             | Filename
:----------------- | :-------
Reconstructed data | `sourcedata/sub-<subid>/ses-<sesid>/anat`
T1 weighted image  | `sub-<subid>_ses-<sesid>_T1w.nii.gz`
T2 weighted image  | `sub-<subid>_ses-<sesid>_T2w.nii.gz`

### Outputs

Outputs                            | Filename
:--------------------------------- | :-------
Derived data                       | `derivatives/dhcp_anat_pipeline/sub-<subid>/ses-<sesid>`
FSL BET brain mask                 | `anat/sub-<subid>_ses-<sesid>_desc-bet_space-T2w_brainmask.nii.gz`
Draw-EM brain mask                 | `anat/sub-<subid>_ses-<sesid>_desc-drawem_space-T2w_brainmask.nii.gz`
Draw-EM regional segmentation (87 labels) | `anat/sub-<subid>_ses-<sesid>_desc-drawem87_space-T2w_dseg.nii.gz`
Draw-EM tissue segmentation (9 labels)    | `anat/sub-<subid>_ses-<sesid>_desc-drawem9_space-T2w_dseg.nii.gz`
Cortical ribbon                    | `anat/sub-<subid>_ses-<sesid>_desc-ribbon_space-T2w_dseg.nii.gz`
T1 weighted image (in T2 space)    | `anat/sub-<subid>_ses-<sesid>_space-T2w_T1w.nii.gz`
T1 weighted, bias corrected image (in T2 space) | `anat/sub-<subid>_ses-<sesid>_desc-restore_space-T2w_T1w.nii.gz`
T2 weighted, bias corrected image  | `anat/sub-<subid>_ses-<sesid>_desc-restore_T2w.nii.gz`
T1/T2 ratio                        | `anat/sub-<subid>_ses-<sesid>_space-T2w_myelinmap.nii.gz`
T1/T2 ratio on the cortical ribbon | `anat/sub-<subid>_ses-<sesid>_space-T2w_desc-myelinmapribbon_dseg.nii.gz`
QC report                          | `sub-<subid>_ses-<sesid>_qc.pdf`
Left/Right white surface           | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_wm.surf.gii`
Left/Right pial surface            | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_pial.surf.gii`
Left/Right mid-thickness surface   | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_midthickness.surf.gii`
Left/Right inflated surface        | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_inflated.surf.gii`
Left/Right very inflated surface   | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_veryinflated.surf.gii`
Left/Right spherical surface       | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_sphere.surf.gii`
Cortical curvature                 | `anat/sub-<subid>_ses-<sesid>_space-T2w_curv.dscalar.nii`
Left/Right cortical curvature      | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_curv.shape.gii`
Sulcal depth                       | `anat/sub-<subid>_ses-<sesid>_space-T2w_sulc.dscalar.nii`
Left/Right sulcal depth            | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_sulc.shape.gii`
Cortical thickness                 | `anat/sub-<subid>_ses-<sesid>_space-T2w_thickness.dscalar.nii`
Left/Right cortical thickness      | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_thickness.shape.gii`
Cortical thickness (curvature regressed out) | `anat/sub-<subid>_ses-<sesid>_desc-corr_space-T2w_thickness.dscalar.nii`
Left/Right cortical thickness (curvature regressed out) | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-corr_space-T2w_thickness.shape.gii`
Cortical myelin                    | `anat/sub-<subid>_ses-<sesid>_space-T2w_myelinmap.dscalar.nii`
Left/Right cortical myelin         | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_myelinmap.shape.gii`
Smoothed cortical myelin           | `anat/sub-<subid>_ses-<sesid>_desc-smoothed_space-T2w_myelinmap.dscalar.nii`
Left/Right smoothed cortical myelin | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-smoothed_space-T2w_myelinmap.shape.gii`
Cortical regional labels projected from volume | `anat/sub-<subid>_ses-<sesid>_desc-drawem_space-T2w_dparc.dlabel.nii`
Left/Right cortical regional labels projected from volume | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-drawem_space-T2w_dparc.dlabel.gii`
Left/Right Medial wall             | `anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-medialwall_mask.shape.gii`
Workbench file for loading surfaces | `anat/wb.spec`
Warp from structural space to the subject’s age respective template space | `xfm/sub-<subid>_ses-<sesid>_from-T2w_to-template{subage}wk_mode-image.nii.gz`
Warp from the subject’s age respective template space to the structural space | `xfm/sub-<subid>_ses-<sesid>_from-template{subage}wk_to-T2w_mode-image.nii.gz`
Warp from structural space to the 40 weeks template space | `xfm/sub-<subid>_ses-<sesid>_from-T2w_to-template40wk_mode-image.nii.gz`
Warp from the 40 weeks template space to the structural space | `xfm/sub-<subid>_ses-<sesid>_from-template40wk_to-T2w_mode-image.nii.gz`

## Diffusion pipeline

### Inputs

Inputs                       | Filename
:--------------------------- | :-------
Multi-band dMRI EPI          | `sub-<subid>_ses-<sesid>_dwi.nii.gz`
List of b-values             | `sub-<subid>_ses-<sesid>_dwi.bval`
List of gradient directions  | `sub-<subid>_ses-<sesid>_dwi.bvec`
T2 weighted, bias corrected and brain extracted image | `sub-<subid>_ses-<sesid>_T2w.nii.gz`
Draw-EM tissue segmentation (9 labels) | `sub-<subid>_ses-<sesid>_space-T2w_desc-drawem_dseg.nii.gz`
T2 brain mask                | `sub-<subid>_ses-<sesid>_space-T2w_brainmask.nii.gz`
 
### Outputs

Outputs                            | Filename
:--------------------------------- | :-------
Eddy current, susceptibility-by-motion and motion (within and between volumes) corrected super-resolved 4D volume with outlier rejection and replacement | `dwi/sub-<subid>_ses-<sesid>_desc-preproc_dwi.nii.gz`
List of b-values                   | `dwi/sub-<subid>_ses-<sesid>_desc-preproc_dwi.bval`
List of post-EDDY rotated gradient directions | `dwi/sub-<subid>_ses-<sesid>_desc-preproc_dwi.bvec`
Brain mask                         | `dwi/sub-<subid>_ses-<sesid>_desc-preproc_space-dwi_brainmask.nii.gz`
Estimated field map                | `fmap/sub-<subid>_ses-<sesid>_fieldmap.nii.gz`
QC report                          | `sub-<subid>_ses-<sesid>_qc.pdf`
Rigid-body transform from structural to diffusion space | `xfm/sub-<subid>_ses-<sesid>_from-T2w_to-dwi_mode-image.mat`
Rigid-body transform from diffusion to structural space | `xfm/sub-<subid>_ses-<sesid>_from-dwi_to-T2w_mode-image.mat`
Warp from diffusion space to 40 week template space (Schuh) | `xfm/sub-<subid>_ses-<sesid>_from-dwi_to-template40wk_mode-image.nii.gz`
Warp from 40 week template space (Schuh) to diffusion space | `xfm/sub-<subid>_ses-<sesid>_from-template40wk_to-dwi_mode-image.nii.gz`

## Functional pipeline

### Inputs

Inputs                       | Filename
:--------------------------- | :-------
Resting fMRI                 | `func/sub-<subid>_ses-<sesid>_task-rest_bold.nii.gz`
Single-band Ref              | `func/sub-<subid>_ses-<sesid>_task-rest_sbref.nii.gz`
Spin Echo EPI with different phase encode directions (for topup fieldmap estimation)                         | `fmap/sub-<subid>_ses-<sesid>-{sesid}_dir-APPA_epi.nii.gz`
Dual echo-time field-map, magnitude | `fmap/sub-<subid>_ses-<sesid>_magnitude.nii.gz`
Dual echo-time field-map     | `fmap/sub-<subid>_ses-<sesid>_fieldmap.nii.gz`
 T2 weighted, bias corrected image (in T2 space) | `anat/sub-<subid>_ses-<sesid>_T2w.nii.gz`
T2 brain mask                | `anat/sub-<subid>_ses-<sesid>_space-T2w_brainmask.nii.gz`
Draw-EM tissue segmentation (9 labels) | `anat/sub-<subid>_ses-<sesid>_space-T2w_desc-drawem_dseg.nii.gz`
T1 weighted, bias corrected image (in T2 space) | `anat/sub-<subid>_ses-<sesid>_space-T2w_T1w.nii.gz`

### Outputs

Outputs                            | Filename
:--------------------------------- | :-------
Multi-band EPI, distortion corrected, motion corrected, FIX denoised, 4D image | `func/sub-<subid>_ses-<sesid>_task-rest_desc-preproc_bold.nii.gz`
Motion parameters                  | `func/sub-<subid>_ses-<sesid>_motion.tsv`
Brain mask                         | `func/sub-<subid>_ses-<sesid>_task-rest_desc-preproc_space-bold_brainmask.nii.gz`
Derived fieldmap, magnitude        | `fmap/sub-<subid>_ses-<sesid>_magnitude.nii.gz`
Derived fieldmap (rad/s)           | `fmap/sub-<subid>_ses-<sesid>_fieldmap.nii.gz`
QC report                          | `sub-<subid>_ses-<sesid>_funcqc.html`
Rigid-body transform from functional (mcdc) to single-band Ref space | `xfm/sub-<subid>_ses-<sesid>_from-bold_to-sbref_mode-image.mat`
Rigid-body transform from single-band Ref space to structural space | `xfm/sub-<subid>_ses-<sesid>_from-sbref_to-T2w_mode-image.mat`
Rigid-body transform from functional (mcdc) to structural space | `xfm/sub-<subid>_ses-<sesid>_from-bold_to-T2w_mode-image.mat`
Rigid-body transform from field-map to structural space | `xfm/sub-<subid>_ses-<sesid>_from-fieldmap_to-T2w_mode-image.mat`
Warp from functional (mcdc) space to the 40 weeks template space | `xfm/sub-<subid>_ses-<sesid>_from-bold_to-template40wk_mode-image.nii.gz`
Warp from the structural space to the 40wk template space | `xfm/sub-<subid>_ses-<sesid>_from-T2w_to-template40wk_mode-image.nii.gz`
