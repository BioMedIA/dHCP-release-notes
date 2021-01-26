---
---

## Reconstruction pipeline

The reconstruction pipeline was developed by the team at King’s College
London.

Motion corrected volumetric reconstructions of multi-slice inversion 
recovery T1- and turbo spin echo T2-weighted images are obtained by 
extending the aligned sensitivity encoding (SENSE) method<sup>1</sup>
to the multi-slice case<sup>2</sup>. Corrections are performed
for both within-plane and through-plane motion from partial
k-space information. The two acquired orthogonal stacks are 
integrated by a super-resolution scheme<sup>3</sup>. Methods and example 
data for the aligned SENSE method are available at 
https://github.com/mriphysics/multiSliceAlignedSENSE/releases/tag/1.0.1.

### Inputs and outputs

**Path:** `rawdata/sub-{subid}/ses-{sesid}`

The reconstruction pipeline generates the files listed in the [Reconstruction pipeline](structure.html#reconstruction-pipeline) 
section of the directory structure summary.

Standard magnitude and phase reconstructions are provided for all native 
acquired anatomical image stacks, with the different orientations and repeat 
acquisitions labelled by sequence run number as follows:

| Description                                          | Filename                                             |
|:-----------------------------------------------------|:-----------------------------------------------------|
| T1w magnitude image (native acquired stack)          | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_T1w.nii`  |
| T1w phase image (native acquired stack)              | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_T1w.nii`  |
| T2w magnitude image (native acquired stack)          | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_T2w.nii`  |
| T2w phase image (native acquired stack)              | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-phase_T2w.nii`  |

Motion corrected and super-resolved reconstructions, and phase images, are included for every acquired multislice stack:

| Description                      | Filename                                        |
|:---------------------------------|:------------------------------------------------|
| T1w image (motion corrected)     | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mc_T1w.nii`  |
| T2w image (motion corrected)     | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mc_T2w.nii`  |
| T1w image (motion corrected and super resolved)     | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcsr_T1w.nii`  |
| T2w image (motion corrected and super resolved)     | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-mcsr_T2w.nii`  |

### Primary anatomical outputs
The final motion corrected slice-to-volume reconstructed T1w and T2w volumes are: 

| Description                                             | Filename                                        |
|:--------------------------------------------------------|:------------------------------------------------|
| T1w image (combined Slice-to-Volume reconstruction)     | `anat/sub-{subid}_ses-{sesid}_rec-SVR_T1w.nii`  |
| T2w image (combined Slice-to-Volume reconstruction)     | `anat/sub-{subid}_ses-{sesid}_rec-SVR_T2w.nii`  |

An additional T1 3D MPRAGE volume is also provided, but currently not used in processing pipelines:

| Description                                             | Filename                                        |
|:--------------------------------------------------------|:------------------------------------------------|
| T1w image (3D MPRAGE)     | `anat/sub-{subid}_ses-{sesid}_run-{seqnum}_acq-MPRAGE_T1w.nii`  |

For fMRI and dMRI, simultaneous multi-slice (SMS) echo planar
imaging (EPI) is reconstructed using the extended SENSE technique<sup>4</sup>,
with details described elsewhere<sup>5,6,7</sup>; sensitivity estimates
from a conventional reference scan are refined with the information from
non-SMS reference acquisitions with matched readouts to promote matched
coil map and image distortions. As for dMRI, complex data retrieval is 
performed by the generalized singular value shrinkage (GSVS) denoising 
technique using noise measures performed during the acquisition<sup>8</sup>. 
Methods and example data for the GSVS method are available at 
https://github.com/mriphysics/complexSVDShrinkageDWI/releases/tag/1.1.0.


### Primary dMRI outputs
dMRI reconstructions are provided with and without denoising, along with phase images, and additional chi^2 
maps from the reconstruction required for the dMRI (SHARD) pipeline. 
A third reconstruction used by the dMRI (EDDY) pipeline is included, this matches the version from the 2nd data 
release, the main difference being that residual fat artefacts are suppressed in the reconstruction pipeline:

| Description                                             | Filename                                        |
|:--------------------------------------------------------|:------------------------------------------------|
| Multi-band dMRI EPI     | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_dwi.nii`  |
| Multi-band dMRI EPI (denoised reconstruction)    | `dwi/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-denoised_dwi.nii`  |
| Multi-band dMRI EPI (Release 2 reconstruction)    | `dwi/sub-{subid}_ses-{sesid}_rec-release2_dwi.nii`  |

### Primary outputs for fMRI
There is one primary reconstruction for the resting state fMRI data, along with single-band reference scans (typically one before and 
one after resting state run), and a spin-echo EPI with matched readout for field estimation. In addition, all phase images are provided.

| Description                                             | Filename                                        |
|:--------------------------------------------------------|:------------------------------------------------|
| Single-band Ref   | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_sbref.nii`  |
| Resting fMRI   | `func/sub-{subid}_ses-{sesid}_run-{seqnum}_task-rest_bold.nii`  |
| 4D Spin Echo EPI with different phase encode directions (for topup fieldmap estimation) | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_epi.nii`  |

### Primary outputs for field mapping
Data from calibration scans are provided for B1+ and B0 field estimates, 
using the DREAM and dual-gradient echo methods, respectively. Reconstructed magnitude and phase 
images are provided, along with the following calculated field maps as the primary outputs:

| Description                                          | Filename                                        |
|:-----------------------------------------------------|:------------------------------------------------|
| B0 field-map in (Hz) - unfiltered  | `fmap/sub-{subid}_ses-{sesid}_run-{seqnum}_rec-raw_fieldmap.nii`  |
| B1+ field map (rel. nom. flip)  | `B1/sub-{subid}_ses-{sesid}_run-{seqnum}_b1map.nii`  |


The full output list can be found in the [Reconstruction pipeline](structure.html#reconstruction-pipeline) 
section of the directory structure summary.


## References

1. Cordero-Grande, L., Teixeira. R. P. A. G., Hughes, E. J.,
Hutter, J., Price, A. N., and Hajnal, J. V. **Sensitivity encoding
for aligned multishot magnetic resonance reconstruction** *IEEE
Transactions on Computational Imaging (2016),  2(3): 266-280.* [DOI:
10.1109/TCI.2016.2557069](https://doi.org/10.1109/TCI.2016.2557069)

2. Cordero-Grande, L., Hughes, E. J., Hutter, J., Hutter, J., Price, A. N.,
and Hajnal, J. V. **Three-Dimensional Motion Corrected Sensitivity Encoding
Reconstruction for Multi-Shot Multi-Slice MRI: Application to Neonatal
Brain Imaging** *Magnetic Resonance in Medicine 2018, 79(3): 1365-1376.*
[DOI: 10.1002/mrm.26796](https://doi.org/10.1002/mrm.26796)

3. Kuklikova-Murgasova, M., Quaghebeur, G., Rutherford, M. A.,
Hajnal, J. V., and Schnabel, J. A. **Reconstruction of fetal
brain MRI with intensity matching and complete outlier removal**
*Medical Image Analysis (2012), 16(8): 1550-1564.* [DOI:
10.1016/j.media.2012.07.004](https://doi.org/10.1016/j.media.2012.07.004)

4. Zhu, K., Dougherty, R. F., Wu, H., Middione, M. J., Takahashi,
A. M, Zhang, T., Pauly, J. M., Kerr, A. B. **Hybrid-space
SENSE reconstruction for simultaneous multi-slice MRI** *IEEE
Transactions on Medical Imaging, 35(8) (2016):1824-1836.* [DOI:
10.1109/TMI.2016.2531635](https://doi.org/10.1109/TMI.2016.2531635)

5. Cordero-Grande, L., Price, A. N., and
Hajnal, J. V. [**Comprehensive CG-SENSE reconstruction of
SMS-EPI**](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Comprehensive-CG-SENSE-reconstruction-of-SMS-EPI.pdf)
*ISMRM 2016: 3239.*

6. Cordero-Grande, L., Hutter, J., Price,
A., Hughes, E., and Hajnal, J. V. [**Goodness of
fit factor in SENSE reconstruction: a tool for pseudolesion detection and fat
unfolding**](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Goodness-of-fit-factor-in-SENSE-reconstruction-a-tool-for-pseudolesion-detection-and-fat-unfolding.pdf)
*ESMRMB 2016: 458.*

7. Hennel, F.,Buehrer, M., von Deuster, C., Seuven, A., and Pruessmann,
K. P. **SENSE reconstruction for multiband EPI including slice-dependent N/2
ghost correction** *Magnetic Resonance in Medicine (2016), 76(3): 873-879.*
[DOI: 10.1002/mrm.25915](https://doi.org/10.1002/mrm.25915)

8. Cordero-Grande, L., Christiaens, D., Hutter, J., Price, A. N., and 
Hajnal, J. V. **Complex diffusion-weighted image estimation via matrix 
recovery under general noise models** *Neuroimage (2019),  200: 391-404.* [DOI:
10.1016/j.neuroimage.2019.06.039](https://doi.org/10.1016/j.neuroimage.2019.06.039)


