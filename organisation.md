---
---

## Data organisation

The structure of data directory and convention of files naming will follow
the BIDS specification (v1.0.2) and the organization of previous data
release of 40 subjects.

## How to download

### Via Bittorrent or download of single tar.zip file

These downloads include the outputs of processing pipelines as well as the raw
images as originally acquired and reconstructed. See Download instructions.

### Via dHCP XNAT web service

Image data for individual subjects (without any pipeline pre-processing)
can be downloaded directly through dHCP XNAT web interface. The image data
are NIfTI files and if downloaded directly from  the XNAT web page they will
be delivered as zips. On the XNAT web interface the files are organized in
subdirectories:

Directory   | Type  | Notes
:---------- | :---- | :----
`<sesid>_0` |  anat |  T1 weighted image
`<sesid>_1` |  anat |  T2 weighted image
`<sesid>_2` |  dwi  |  Multi-band dMRI EPI
`<sesid>_3` |  func |  Dual echo-time field-map (magnitude)
`<sesid>_4` |  func |  Dual echo-time field-map (phase difference)
`<sesid>_5` |  func |  Multi-band resting state fMRI EPI
`<sesid>_6` |  func |  Single-band reference spin echo EPI image
`<sesid>_7` |  func |  Single band reference spin echo EPI with different phase encode directions.

## Support

We are supporting this data release via the [developing-hcp tag on
neurostars](https://neurostars.org/tags/developing-hcp).

## Subjects

Infants were recruited and imaged at the Evelina Newborn Imaging Centre,
St Thomas’ Hospital, London, UK. The study was approved by the UK Health
Research Authority (Research Ethics Committee reference number: 14/LO/1169)
and written parental consent was obtained in every case for imaging and data
release. The images included in this release were obtained from infants born
and imaged between 24-45 weeks of age. The images have been reviewed for
evidence of anomalies and abnormalities and a radiology score is provided,
although users should verify that data they use are fit for their purposes.

## Overview of data

The data release contains structural (T1w and T2w) resting state functional
and diffusion images supplied as original image data and after preprocessing
pipelines as described below have been applied. The neonatal brain has
different tissue properties to adult brain, most strikingly it has a
higher water content and myelination of white matter is incomplete. In
consequences the relaxation times T1 and T2 are longer than in adult brain
and white matter has longer T1 and T2 than grey matter. In neonates, brain
anatomy is revealed more clearly in T2w than T1w images and thus the former
are treated as the primary data for anatomical segmentation and to provide
the anatomical substrates needed for functional and diffusion analysis. All
neonates (with 6 exceptions) were imaged in natural sleep. If the baby woke
up scanning was halted and attempts made to re-settle the subject without
taking them out of the patient immobilization system. Even when sleeping
peacefully, many babies move and so all data were motion corrected, mostly
using methods developed specifically for the dHCP project. As a result of
the challenges of imaging unsedated infants we were not able to obtain high
quality and complete data for every modality on every subject. There were 558
sessions from 505 subjects with T2w images that passed QC, then of those,
512 had fMRI data that passed QC and 490 had dMRI data that passed QC. The
T1w images were not subject to the same level of systematic QC as they were
not processed by pre-processing pipelines. Because of their lower anatomical
importance, the T1w images were placed at the end of the protocol and are
of more variable quality than the T2w data.

There is a spread of gestational ages with 378 subjects in the term equivalent
age range, which we defined as 37 to 44 gestational weeks. Also although
these subjects were recruited as “normal subjects” (with clearly specified
inclusion and exclusion criteria), there were inevitably incidental findings
on the images obtained. All the anatomical images were reviewed by an expert
perinatal neuroradiologist who scored the subjects using a 5 point scale
(see below) - this information is provided

## Acquisition details

Imaging was carried out on 3T Philips Achieva (running modified R3.2.2
software) using a dedicated neonatal imaging system which included a neonatal
32 channel phased array head coil<sup>1</sup>. Infants were imaged without
sedation except for 6 who are indicated. Anatomical images (T1w and T2w),
resting state functional (rs-fMRI) and diffusion (dMRI) acquisitions were
acquired in a total examination time of 63 minutes. Sequence parameters
were as follows:

**Calibration scans:** B0 mapping was performed using an interleaved dual TE
spoiled gradient echo sequence and localised image based shimming performed
for use with all EPI sequences as described in<sup>2</sup>. B0 field maps
using the optimised higher order shims were subsequently re-acquired between
the fMRI and dMRI acquisitions.

**Anatomical acquisition:** T2w and inversion recovery T1w multi-slice fast
spin-echo images were each acquired in sagittal and axial slice stacks with
in-plane resolution 0.8x0.8mm2 and 1.6mm slices overlapped by 0.8mm (except
in T1w Sagittal which used a slice overlap of 0.74mm). Other parameters were
– T2w: 12000/156ms TR/TE, SENSE factor 2.11 (axial) and 2.60 (sagittal);
T1w: 4795/1740/8.7ms TR/TI/TE, SENSE factor 2.27 (axial) and 2.66 (sagittal).

**rs-fMRI:** High temporal resolution fMRI developed for neonates<sup>3</sup>
used multiband (MB) 9x accelerated echo-planar imaging and was collected for
15 minutes, TE/TR=38/392ms gave 2300 volumes, with an acquired resolution
of 2.15mm isotropic. No in-plane acceleration or partial Fourier was
used. Single-band reference scans were also acquired with bandwidth matched
readout, along with additional spin-echo acquisitions with both AP/PA
fold-over encoding directions.

**dMRI:** A spherically optimized set of directions on 4 shells (b0:
20, b400: 64, b1000: 88, b2600: 128)<sup>4</sup> was split into 4 optimal
subsets (one per Phase Encoding Direction). These directions were then spread
temporally taking motion and duty cycle considerations into account. If the
baby woke up during the diffusion scan, the acquisition could be halted
and restarted (after resettling the subject) with a user defined overlap
in acquired diffusion weightings<sup>5</sup>. Acceleration of MB 4, SENSE
factor 1.2 and Partial Fourier 0.86 was used, acquired resolution 1.5x1.5mm,
3mm slices with 1.5mm overlap, 3800/90ms TR/TE.

### References

1. Hughes, E. J., Winchman, T., Padormo, F., Teixeira, R., Wurie, J.,
Sharma, M., Fox, M, Hutter, J., Cordero-Grande, L., Price, A. N., Allsop,
J,, Bueno-Conde, J., Tusor, N.,, Arichi, T., Edwards, A. D., Rutherford,
M. A., Counsell, S. J., and Hajnal J. V. **A dedicated neonatal brain
imaging system** *Magnetic Resonance in Medicine (2017), 78: 794-804.*
[DOI: 10.1002/mrm.26462](https://doi.org/10.1002/mrm.26462)

2. Gaspar, A. [**Improving foetal and neonatal echo-planar imaging with
image-based shimming**](https://repositorio.ul.pt/handle/10451/22886)
*Master Thesis (2015), Universidade de Lisboa.*

3. Price, A.N., Cordero-Grande, L., Malik, S.J.,
Abaei, M., Arichi, T., Hughes, E., Rueckert, D.,
Edwards, A.D., Hajnal, J.V. [**Accelerated neonatal fMRI using multiband
EPI**](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Accelerated-Neonatal-fMRI-using-Multiband-EPI.-ISMRM-2015.pdf)
*ISMRM 2015: 3911.*

4. Tournier, J.D., Hughes, E., Turso, N., Sotiropoulos,
N. S., Jbadhi, S., Andersson, J., Reuckert, D., Edwards,
A. D., Hajnal, J. V. [**Data-driven optimisation of multi-shell
HARDI**](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Data-driven-optimisation-of-multi-shell-HARDI.pdf)
*ISMRM 2015: 2897.*

5. Hutter, J., Tournier J. D., Price, A. N., Cordero-Grande, L.,
Hughes, E. J., Malik, S., Steinweg, J., Bastiani, M., Sotiropoulos,
S. N., Jbabdi, S., Andersson, J., Edwards, A. D., and Hajnal,
J. V. [**Time-efficient and flexible design of optimised multi-shell
HARDI diffusion**](https://www.ncbi.nlm.nih.gov/pubmed/28557055) *Magnetic
Resonance in Medicine (2018), 79: 1276-1292.*

## Quality Control/Assurance (QC)

QC is performed at five stages of the dHCP analysis as listed below. The
final selection of subject data to release made use of these as outlined
subsequently.

### Five stages of QC  

1. Scanning notes were recorded by the radiographers, and failed scans were
manually flagged as pass/fail depending on if the issue affects the fMRI,
the dMRI, or other.

2. After reconstruction the images were visually inspected and each image was
flagged as PASS/FAIL

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

## Pipelines

### Reconstruction pipeline

The reconstruction pipeline was developed by the team at King’s College
London. It performs motion correction and reconstruction of T1 and T2
weighted images.

The reconstruction pipeline performs motion corrected volumetric
reconstructions of multi-slice T1 and T2 weighted images extending
the aligned sensitivity encoding (SENSE) method<sup>1</sup>
to the multi-slice case<sup>2</sup>. Corrections are performed
for both within-plane and through-plane motion from partial
k-space information. Methods and example data are available at
https://github.com/mriphysics/multiSliceAlignedSENSE/releases/tag/1.0.1 .
The two acquired orthogonal stacks are integrated by a super-resolution
scheme<sup>3</sup>. fMRI and dMRI simultaneous multi-slice (SMS) echo planar
imaging (EPI) is reconstructed using the extended SENSE technique<sup>4</sup>,
with details described elsewhere<sup>5,6,7</sup>; sensitivity estimates
from a conventional reference scan are refined with the information from
non-SMS reference acquisitions with matched readouts to promote matched
coil map and image distortions. Sensitivity estimation uses a variational
formulation<sup>8</sup>.

#### References

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

8. Allison, M. J., Ramani, S., and Fessler, J. A. **Accelerated regularized
estimation of MR coil sensitivities using augmented Lagrangian methods**
*IEEE Transactions on Medical Imaging (2013), 32(3): 556-564.* [DOI:
10.1109/TMI.2012.2229711](https://doi.org/10.1109/TMI.2012.2229711)

### Structural pipeline

The [structural
pipeline](https://github.com/BioMedIA/dhcp-structural-pipeline) was
encapsulated as a Docker container image and run via the OpenMOLE<sup>10</sup>
platform on a local cluster.

A. Registration

B. Segmentation

    1. Structural scans are pre-processed by first running bias correction using
    the N4 algorithm<sup>1</sup>.

    2. Scans are then brain extracted using BET<sup>2</sup> from FSL. 

    3. Segmentation of the T2w volume is performed using the DRAW-EM
    algorithm<sup>3</sup>.  DRAW-EM is an atlas-based segmentation technique
    that segments the volumes into 87 regions (see region names). Manually
    labelled atlases, annotated by an expert neuroanatomist<sup>4</sup>, are
    registered to the volume and their labels are fused to the subject
    space to provide structure priors. Segmentation is then performed with
    an Expectation-Maximization scheme that combines the structure priors
    and an intensity model of the volume. The 87 regions are further merged
    to provide the tissue segmentation (see tissue types).

    4. All T1 weighted images have been pre-aligned to the T2w volumes
    using rigid alignment.

    5. Both T1w and T2w volumes are defaced for anonymization based on
    registration and transformation of a manually annotated face mask.

C. Surface extraction

    6. Surface mesh extraction is performed with the method described
    elsewhere<sup>5</sup>. A white matter mask enclosing the white surface is
    computed by merging the white matter and the subcortical structures with
    the exception of the brainstem and the cerebellum. Similarly, a pial mask
    is computed by merging the grey matter structure with the white matter
    mask. The white and pial surfaces of the left and right hemispheres
    are then reconstructed with the method outlined in5 using a deformable
    model. The model in5 includes forces to avoid self-intersections and
    includes an image-based refinement step that corrects regions such as
    deep sulci mislabelled by the volumetric segmentation.

    7. Midthickness surfaces are generated as the middle surface between
    the white and pial surfaces. The midthickness surface is computed using
    the Euclidean distance between corresponding points of the white and
    pial surface.

    8. Spherical projection is performed6, and it is based on the inflated
    white matter surface. The inflated white matter surface is produced in
    a similar manner as in the FreeSurfer pipeline<sup>7</sup>. Inflated and
    very inflated surfaces used for visualisation are generated 
    similarly<sup>8</sup>.

    9. The following metrics are further estimated from the surfaces:
    curvature, thickness, sulcal depth, T1w/T2w myelin, labels (projected
    from the volume). All surfaces have one-to-one vertex correspondence for
    all points on the surface ensuring that the same vertex indexes the same
    point, in the same relative position, on the anatomy for all surfaces.

The structural pipeline is described in detail elsewhere<sup>9</sup>.

#### References

1. Tustison, N. J., Avants, B. B., Cook, P. A., Zheng, Y., Egan, A.,
Yushkevich, P. A. and Gee, J. C.  **N4ITK: improved N3 bias correction. IEEE
transactions on medical imaging (2010)** *29(6): 1310-1320.* [DOI:
10.1109/TMI.2010.2046908](https://doi.org/10.1109/TMI.2010.2046908)

2. Smith, S. M.  **Fast robust automated brain extraction**
*Human Brain Mapping (2002), 17(3): 143-55.* [DOI:
10.1002/hbm.10062](https://doi.org/10.1002/hbm.10062)

3. Makropoulos, A., Gousias I. S., Ledig C., Aljabar P., Serag A,
Hajnal J. V., Edwards A. D., Counsell S. J., and Rueckert D. **Automatic
whole brain MRI segmentation of the developing neonatal brain** *IEEE
transactions on medical imaging (2014), 33(9): 1818-1831.* [DOI:
10.1109/TMI.2014.2322280](https://doi.org/10.1109/TMI.2014.2322280)

4. Gousias, I. S., Edwards A. D., Rutherford M. A., Counsell S. J., Hajnal
J. V., Rueckert D., and Hammers, A. **Magnetic resonance imaging of the
newborn brain: manual segmentation of labelled atlases in term-born
and preterm infants** *Neuroimage (2012), 62(3): 1499-1509.* [DOI:
10.1016/j.neuroimage.2012.05.083](https://doi.org/10.1016/j.neuroimage.2012.05.083)

5. Schuh, A., Makropoulos, A., Wright, R., Robinson, E. C., Tusor, N.,
Steinweg, J., Hughes, E., Cordero Grande, L.,  Price, A., Hutter, J., Hajnal,
J., and  Rueckert, D. **A deformable model for reconstruction of the neonatal
cortex** *IEEE 14th International Symposium on Biomedical Imaging 2017.*
[DOI: 10.1109/ISBI.2017.7950639](https://doi.org/10.1109/ISBI.2017.7950639)

6. Elad, A., Keller, Y.,  and Kimmel,
R. [**Texture Mapping via Spherical Multidimensional
Scaling**](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Texture-Mapping-via-Spherical-Multidimensional-Scaling-.pdf)
*International Conference on Scale-Space Theories in Computer Vision
(2005): 443–455.*

7. Fischl, B., Sereno M. I., and Dale, A. M. **Cortical surface-based
analysis: II: inflation, flattening, and a surface-based
coordinate system** N*euroimage (1999), 9(2): 195-207.* [DOI:
10.1006/nimg.1998.0396](https://doi.org/10.1006/nimg.1998.0396)

8. Glasser, M., Sotiropoulo, S. N., Wilson, J. A, Coalson, T. S,
Fischl, B., Andersson, L., Xu, J., Jbabdi, S., Webster, M.,
Polimeni, J. R., Van Essen, D. C., Jenkinson, M., WU-Minn HCP
Consortium. **The minimal preprocessing pipelines for the Human
Connectome Project** *NeuroImage (2013)., 80: 105–124.* [DOI:
10.1016/j.neuroimage.2013.04.127](https://doi.org/10.1016/j.neuroimage.2013.04.127)

9. Makropoulos, A., Robinson, E., Schuh, A., Wright, R., Fitzgibbon,
S., Bozek, J., Counsell, S. J., Steinweg, J., Vecchiato, K.,
Passerat-Palmbach, J., Lenz, G., Mortari, F., Tenev, T., Duff, E. P.,
Bastiani, M., Cordero-Grande, L., Hughes, E., Tusor, N., Tournier,
J. D., Hutter, J., Price, A. N., Teixeira, R. P. A. G., Murgasova M,
Victor, S., Kelly, C., Rutherford, M. A., Smith, S. M., Edwards, A. D.,
Hajnal, J. V., Jenkinson, M., and Rueckert, D. **The developing Human
Connectome Project: a Minimal Processing Pipeline for Neonatal Cortical
Surface Reconstruction** *NeuroImage (2018), 173: 88-112.* [DOI:
10.1016/j.neuroimage.2018.01.054](https://doi.org/10.1016/j.neuroimage.2018.01.054)

10. Passerat-Palmbach, J., Reuillon, R., Leclaire, M., Makropoulos,
A., Robinson, E.C., Parisot, S., and Rueckert, D. **Reproducible
Large-Scale Neuroimaging Studies with the OpenMOLE Workflow
Management System** *Frontiers in Neuroinformatics (2017), 11.* [DOI:
10.3389/fninf.2017.00021](https://doi.org/10.3389/fninf.2017.00021)

## Diffusion pipeline

For a complete and detailed description of all the steps
involved in the [dHCP neonatal diffusion MRI (dMRI) data processing
pipeline](https://git.fmrib.ox.ac.uk/matteob/dHCP_neo_dMRI_pipeline_release),
the reader is referred elsewhere<sup>1</sup>. The main processing steps
are briefly summarised below:

A. For each phase encoding (PE) direction, the diffusion un-weighted
b0 volume pairs least-affected by intra-volume motion are automatically
selected. The dataset is then re-organised by moving the least-affected
b0 volume and the volumes that follow (until the end of the acquisition)
at the beginning of the 4D raw data file.

B. Field maps for correcting susceptibility-induced distortions are estimated
using FSL TOPUP<sup>2</sup>.

C. Distortions caused by susceptibility, motion, motion-induced signal
drop-out and eddy currents are corrected; outlier slices are detected and
replaced in raw distorted space using FSL EDDY<sup>3-6</sup>.

D. A super-resolution algorithm<sup>7</sup> is applied along the
slice-selection direction, to achieve isotropic resolution of 1.5 mm.

E. Diffusion data are aligned to high-resolution structural (T2-weighted)
space using boundary-based registration<sup>8,9</sup>  on the average
attenuation volume for the b=1000 s/mm2 shell (i.e. b1k/b0). This
transformation is combined with a non-linear registration<sup>10</sup> of
the T2w volume to the 40 weeks template<sup>11</sup> to allow transformations
between diffusion and atlas spaces.

### Diffusion MRI QC

A. Numerous quality assurance metrics are calculated by the EDDY QC
tools<sup>12</sup>.  Four of these are specifically compared against
the population distribution to flag outliers for manual inspection and
potential exclusion:

    1. Mean signal-to-noise ratio (SNR) from the b0 volumes

    2. Mean contrast-to-noise ratio (CNR) for each b-shell, i.e., 400,
    1000 and 2600 s/mm2.

B. All QC metrics are then converted to Z-scores and averaged, to generate
a summary QC metric. Subject/sessions with a summary Z-score < -2.0 were
excluded.

### References

1. Bastiani, M., Andersson, J.L.R., Cordero-Grande, L., Murgasova, M.,
Hutter, J., Price, A.N., Makropoulos, A., Fitzgibbon, S.P., Hughes,
E., Rueckert, D., Victor, S., Rutherford, M., Edwards, A.D., Smith,
S.M., Tournier, J.D., Hajnal, J.V., Jbabdi, S., and Sotiropoulos,
S.N. **Automated processing pipeline for neonatal diffusion MRI in the
developing Human Connectome Project** *Neuroimage (2019), 185: 750-763.* [DOI:
10.1016/j.neuroimage.2018.05.064](https://doi.org/10.1016/j.neuroimage.2018.05.064)

2. Andersson, J.L., Skare, S., and Ashburner, J. **How to correct
susceptibility distortions in spin-echo echo-planar images: application
to diffusion tensor imaging** *Neuroimage (2003), 20(2): 870-888.* [DOI:
10.1016/S1053-8119(03)00336-7](https://doi.org/10.1016/S1053-8119(03)00336-7)

3. Andersson, J.L., and Sotiropoulos, S.N. **An integrated approach
to correction for off-resonance effects and subject movement in
diffusion MR imaging** *Neuroimage (2016), 125: 1063-1078.* [DOI:
10.1016/j.neuroimage.2015.10.019](https://doi.org/10.1016/j.neuroimage.2015.10.019)

4. Andersson, J.L.R., Graham, M.S., Drobnjak, I., Zhang, H.,
and Campbell, J. **Susceptibility-induced distortion that varies
due to motion: Correction in diffusion MR without acquiring
additional data** *NeuroImage (2018), 171: 277-295.* [DOI:
10.1016/j.neuroimage.2017.12.040](https://doi.org/10.1016/j.neuroimage.2017.12.040)

5. Andersson, J.L.R., Graham, M.S., Drobnjak, I., Zhang, H.,
Filippini, N., and Bastiani, M. **Towards a comprehensive framework
for movement and distortion correction of diffusion MR images:
Within volume movement** *Neuroimage (2017), 152: 450-466.* [DOI:
10.1016/j.neuroimage.2017.02.085](https://doi.org/10.1016/j.neuroimage.2017.02.085)

6. Andersson, J.L.R., Graham, M.S., Zsoldos, E., and Sotiropoulos,
S.N. **Incorporating outlier detection and replacement into a
non-parametric framework for movement and distortion correction
of diffusion MR images** *Neuroimage (2016), 141: 556-572.* [DOI:
10.1016/j.neuroimage.2016.06.058](https://doi.org/10.1016/j.neuroimage.2016.06.058)

7. Kuklisova-Murgasova, M., Quaghebeur, G., Rutherford, M.A., Hajnal, J.V.,
and Schnabel, J.A. **Reconstruction of fetal brain MRI with intensity matching
and complete outlier removal** *Med Image Anal (2012), 16(8): 1550-1564.* [DOI:
10.1016/j.media.2012.07.004](https://doi.org/10.1016/j.media.2012.07.004)

8. Greve, D.N., and Fischl, B. **Accurate and robust brain image alignment
using boundary-based registration** *Neuroimage (2009), 48(1): 63-72.* [DOI:
10.1016/j.neuroimage.2009.06.060](https://doi.org/10.1016/j.neuroimage.2009.06.060)

9. Jenkinson, M., Bannister, P., Brady, M., and Smith, S. **Improved
optimization for the robust and accurate linear registration and motion
correction of brain image** *Neuroimage (2002), 17(2): 825-841.* [DOI:
10.1006/nimg.2002.1132](https://doi.org/10.1006/nimg.2002.1132)

10. Andersson, J.L.R., Jenkinson, M., and
Smith, S. [**Non-linear registration, aka spatial
normalisation**](https://www.fmrib.ox.ac.uk/datasets/techrep/tr07ja2/tr07ja2.pdf)
*FMRIB technical report TR07JA2 (2010).*

11. Schuh, A., Makropoulos, A., Robinson, E.C., Cordero-Grande, L., Hughes,
E., Hutter, J., Price, A.N., Murgasova, M., Teixeira, R.P.A.G., Tusor,
N., Steinweg, J.K., Victor, S., Rutherford, M.A., Hajnal, J.V., Edwards,
A.D., and Rueckert, D. **Unbiased construction of a temporally consistent
morphological atlas of neonatal brain development** *bioRxiv (2018), 251512.*
[DOI: 10.1101/251512](https://doi.org/10.1101/251512)

12. Bastiani, M., Cottaar, M., Fitzgibbon, S.P., Suri, S.,
Alfaro-Almagro, F., Sotiropoulos, S.N., Jbabdi, S., and Andersson,
J.L.R. **Automated quality control for within and between studies
diffusion MRI data using a non-parametric framework for movement
and distortion correction** *Neuroimage (2019), 184: 801-812.* [DOI:
10.1016/j.neuroimage.2018.09.073](https://doi.org/10.1016/j.neuroimage.2018.09.073)

## Functional pipeline

### Pre-processing for fMRI

A. Prepare fieldmaps for correction of susceptibility distortions

    1. Estimate field map from the two “best” spin-echo volumes (1 per
    phase-encode direction) using FSL TOPUP<sup>1</sup>.  “Best” is
    defined by smoothness in the z-dimension (stdev of the slice-to-slice
    difference in the z-dimension)

    2. If visual inspection indicates that the spin-echo has significant 
    motion contamination then use the dual-echo-derived fieldmap instead
    of the spin-echo-derived fieldmap

B. Registration

    3. Boundary-based registration (BBR, FSL FLIRT3) of the fieldmap to
    the T2 structural

    4. Boundary-based registration (BBR, FSL FLIRT3) of the sbref to the
    T2 structural incorporating field map-based distortion correction of
    the sbref

    5. Linear registration (6-dof, corratio, FSL FLIRT3) of the first volume
    of the functional multiband EPI to the sbref

    6. After susceptibility and motion correction, linear registration (6-dof,
    corratio, FSL FLIRT3) of the temporal mean of the motion and distortion
    corrected functional multiband EPI to the distortion corrected sbref

    7. Nonlinear diffeomorphic multimodal registration of the age-matched
    T1/T2 templates from the dHCP volumetric atlas (Schuh et al., 2018) to
    the subjects T1/T2 structurals using ANTs SyN (Avants, Epstein, Grossman,
    & Gee, 2008).  If the age of the subject is outside the range covered by
    the atlas (36-43) then it is registered to the closest template age within
    the atlas. We have augmented the dHCP volumetric atlas with week-to-week
    nonlinear transforms estimated using a diffeomorphic multi-modal (T1/T2)
    registration (ANTs SyN).  The appropriate transforms are then combined
    to yield a (40 week) template-to-structural transform

    8. From these primary registrations the following composite transforms
    are calculated:

        i.  fieldmap to native functional

        ii. motion and distortion corrected functional to 40-week template
        from the dHCP volumetric atlas

C. Susceptibility and motion correction

    9. Slice-to-volume motion correction and motion-by-susceptibility
    correction is performed using FSL EDDY2

D. ICA Denoising

    10. Temporal high-pass filter (150s high-pass cutoff) and ICA denoising
    using FSL FIX4, pre-trained with manually-labelled data from 35 dHCP
    neonatal subjects, to identify artefactual ICs (accuracy: median TPR=100%,
    median TNR=95.4%). The ICA dimensionality was capped at 600 ICs.

    11. Noise ICs and motion parameters regressed from motion and distortion
    corrected functional multiband EPI.

### fMRI QC

A. Numerous quality assurance metrics are calculated during the
pre-processing. Six of these are specifically compared against the population
distribution to flag outliers for manual inspection and potential exclusion:

    1. Mean DVARS5 of the ICA denoised functional EPI

    2. Mean tSNR of the ICA denoised functional EPI

    3. Normalised mutual information of the source (moving) image, re-sampled
    to reference space, and the reference (fixed) image, for each of the
    primary registrations:

        i. Fieldmap to structural T2

        ii. Native functional to sbref

        iii. Motion and distortion corrected functional to sbref

        iv. Sbref to structural T2

        v. Age-matched atlas template T2 to native structural T2

B. All QA measures were converted to Z-scores and flipped as necessary so
that positive z-scores are good and negative bad.  Subject/sessions with
a z-score < -2.5 on any QC metric were excluded.

### References

Andersson, J. L., Skare, S. and Ashburner, J. **How to correct susceptibility
distortions in spin-echo echo-planar images: application to diffusion tensor
imaging** *Neuroimage (2003), 20: 870-888.* DOI: 10.1016/S1053-8119(03)00336-7

Andersson, J. L. and Sotiropoulos, S. N. **An integrated approach
to correction for off-resonance effects and subject movement in
diffusion MR imaging** *Neuroimage (2016), 125: 1063-1078.* DOI:
10.1016/j.neuroimage.2015.10.019

Jenkinson, M., and Smith, S. **A global optimisation method for robust
affine registration of brain images** *Medical image analysis (2001), 5(2):
143–156.* DOI: 10.1016/S1361-8415(01)00036-6

Salimi-Khorshidi, G., Douad, G, Beckman, C. F., Glasser, M. F., Griffanti,
L., and Smith, S. M. **Automatic denoising of functional MRI data: combining
independent component analysis and hierarchical fusion of classifiers**
*NeuroImage (2014), 90: 449–468.* DOI: 10.1016/j.neuroimage.2013.11.046

Power, J. D., Barnes, K. A., Snyder, A. Z., Schlaggar, B. L.,  and Petersen,
S. E. **Spurious but Systematic Correlations in Functional Connectivity MRI
Networks Arise from Subject Motion** *NeuroImage (2012), 59(3): 2142–54.*
DOI: 10.1016/j.neuroimage.2011.10.018

## Metadata

The participants.tsv for each BIDS pipeline has a number of extra columns beyond participant_id. These have the following meaning:

gender
Male / Female
birth_age
Gestational age at birth in weeks
birth_weight
Birthweight (kg)
singleton
Singleton / multiple status of the pregnancy



The sessions.tsv file has extra columns beyond session_id. These have the following meaning:

scan_age
Gestational age at scan in weeks
scan_head_circumference
Head circumference (cm)
scan_number
1 for the first scan, 2 for the second
radiology_score
The MRI scans were reviewed by a specialist perinatal neuroradiologist who scored each subject using the following scale:
1=Normal appearance for age
2=Incidental findings with unlikely significance for clinical outcome or analysis (e.g. subdural haemorrhage. Isolated subependymal cysts. Mild inferior vermis rotation)
3=Incidental findings with unlikely clinical significance but possible analysis significance (e.g. several punctate lesions or other focal white matter / cortical lesions not thought to be of clinical significance) 
4=Incidental findings with possible clinical significance. Unlikely analysis significance (e.g. Isolated non brain anomaly for example in pituitary / on tongue)
5=Incidental finding with possible / likely significance for both clinical and imaging analysis (e.g. Major lesions within white matter cortex, cerebellum and or basal ganglia; small head / brain < 1st centile)
Q=Poor quality anatomical data
sedation
1 if the subject was sedated during the scan, 0 otherwise

As a convenience, an extra top-level file called combined.tsv lists all these fields for all scans in a single large table.
Data directory structure and naming convention
The data directory structure and naming of files is organized as follows. 

<subid>    subject ID
<sesid>    refers to session ID
CSF        cerebrospinal fluid
WM        white matter
cGM        cortical grey matter
sGM        subcortical grey matter
EPI        echo-planar imaging


derivatives (contains output files from pipelines)






|__

dhcp_anat_pipeline






   |
|__

sub-<subid>






   |
  
|__

ses-<sesid>




   |
  
  
  
|___

anat






   |
  
  
  
|___

xfm






|__

dhcp_fmri_pipeline






   |
|__

sub-<subid>






   |


|__
ses-<sesid>






   |




|___

func






   |




|___

fmap






   |




|___

xfm






|__

dhcp_dmri_pipeline






 
|__
sub-<subid>










   |__ses-<sesid>






   




|___

dwi






   




|___

fmap






   




|___

xfm






        

sourcedata (contains input files for pipelines)






|__

sub-<subid>








|__

ses-<sesid>










|__

anat








  |
  |---
  |

dwi








  |---
  |

func








  |__

fmap






Explanation of filenames 
Structural pipeline
Inputs:
Reconstructed data: sourcedata/sub-<subid>/ses-<sesid>/anat
T1 weighted image
sub-<subid>_ses-<sesid>_T1w.nii.gz
T2 weighted image
sub-<subid>_ses-<sesid>_T2w.nii.gz

Outputs:
Derived data: derivatives/dhcp_anat_pipeline/sub-<subid>/ses-<sesid>
FSL BET brain mask
anat/sub-<subid>_ses-<sesid>_desc-bet_space-T2w_brainmask.nii.gz
Draw-EM brain mask
anat/sub-<subid>_ses-<sesid>_desc-drawem_space-T2w_brainmask.nii.gz
Draw-EM regional segmentation (87 labels)
anat/sub-<subid>_ses-<sesid>_desc-drawem87_space-T2w_dseg.nii.gz
Draw-EM tissue segmentation (9 labels)
anat/sub-<subid>_ses-<sesid>_desc-drawem9_space-T2w_dseg.nii.gz
Cortical ribbon
anat/sub-<subid>_ses-<sesid>_desc-ribbon_space-T2w_dseg.nii.gz
T1 weighted image (in T2 space)
anat/sub-<subid>_ses-<sesid>_space-T2w_T1w.nii.gz
T1 weighted, bias corrected image (in T2 space)
anat/sub-<subid>_ses-<sesid>_desc-restore_space-T2w_T1w.nii.gz
T2 weighted, bias corrected image
anat/sub-<subid>_ses-<sesid>_desc-restore_T2w.nii.gz
T1/T2 ratio
anat/sub-<subid>_ses-<sesid>_space-T2w_myelinmap.nii.gz
T1/T2 ratio on the cortical ribbon
anat/sub-<subid>_ses-<sesid>_space-T2w_desc-myelinmapribbon_dseg.nii.gz
QC report
sub-<subid>_ses-<sesid>_qc.pdf

surface files


Left/Right white surface
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_wm.surf.gii
Left/Right pial surface
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_pial.surf.gii
Left/Right mid-thickness surface
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_midthickness.surf.gii
Left/Right inflated surface
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_inflated.surf.gii
Left/Right very inflated surface
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_veryinflated.surf.gii
Left/Right spherical surface
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_sphere.surf.gii
Cortical curvature
anat/sub-<subid>_ses-<sesid>_space-T2w_curv.dscalar.nii
Left/Right cortical curvature
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_curv.shape.gii
Sulcal depth
anat/sub-<subid>_ses-<sesid>_space-T2w_sulc.dscalar.nii
Left/Right sulcal depth
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_sulc.shape.gii
Cortical thickness
anat/sub-<subid>_ses-<sesid>_space-T2w_thickness.dscalar.nii
Left/Right cortical thickness
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_thickness.shape.gii
Cortical thickness (curvature regressed out)
anat/sub-<subid>_ses-<sesid>_desc-corr_space-T2w_thickness.dscalar.nii
Left/Right cortical thickness (curvature regressed out)
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-corr_space-T2w_thickness.shape.gii
Cortical myelin
anat/sub-<subid>_ses-<sesid>_space-T2w_myelinmap.dscalar.nii
Left/Right cortical myelin
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_space-T2w_myelinmap.shape.gii
Smoothed cortical myelin
anat/sub-<subid>_ses-<sesid>_desc-smoothed_space-T2w_myelinmap.dscalar.nii
Left/Right smoothed cortical myelin
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-smoothed_space-T2w_myelinmap.shape.gii
Cortical regional labels projected from volume
anat/sub-<subid>_ses-<sesid>_desc-drawem_space-T2w_dparc.dlabel.nii
Left/Right cortical regional labels projected from volume
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-drawem_space-T2w_dparc.dlabel.gii
Left/Right Medial wall
anat/sub-<subid>_ses-<sesid>_hemi-{L|R}_desc-medialwall_mask.shape.gii
Workbench file for loading surfaces
anat/wb.spec
Folder containing registration files
xfm/
Warp from structural space to the subject’s age respective template space
xfm/sub-<subid>_ses-<sesid>_from-T2w_to-template{subage}wk_mode-image.nii.gz
Warp from the subject’s age respective template space to the structural space
xfm/sub-<subid>_ses-<sesid>_from-template{subage}wk_to-T2w_mode-image.nii.gz
Warp from structural space to the 40 weeks template space
xfm/sub-<subid>_ses-<sesid>_from-T2w_to-template40wk_mode-image.nii.gz
Warp from the 40 weeks template space to the structural space
xfm/sub-<subid>_ses-<sesid>_from-template40wk_to-T2w_mode-image.nii.gz

Diffusion pipeline
Inputs:
Reconstructed data: sourcedata/sub-<subid>/ses-<sesid>/dwi
Multi-band dMRI EPI
sub-<subid>_ses-<sesid>_dwi.nii.gz
List of b-values
sub-<subid>_ses-<sesid>_dwi.bval
List of gradient directions
sub-<subid>_ses-<sesid>_dwi.bvec
 
Structural pipeline derived data: derivatives/dhcp_anat_pipeline/sub-<subid>/ses-<sesid>
T2 weighted, bias corrected and brain extracted image
sub-<subid>_ses-<sesid>_T2w.nii.gz
Draw-EM tissue segmentation (9 labels)
sub-<subid>_ses-<sesid>_space-T2w_desc-drawem_dseg.nii.gz
T2 brain mask
sub-<subid>_ses-<sesid>_space-T2w_brainmask.nii.gz
 
Outputs:
Derived data: derivatives/dhcp_dmri_pipeline/sub-<subid>/ses-<sesid>
Eddy current, susceptibility-by-motion and motion (within and between volumes) corrected super-resolved 4D volume with outlier rejection and replacement
dwi/sub-<subid>_ses-<sesid>_desc-preproc_dwi.nii.gz
List of b-values
dwi/sub-<subid>_ses-<sesid>_desc-preproc_dwi.bval
List of post-EDDY rotated gradient directions
dwi/sub-<subid>_ses-<sesid>_desc-preproc_dwi.bvec
Brain mask
dwi/sub-<subid>_ses-<sesid>_desc-preproc_space-dwi_brainmask.nii.gz
Estimated field map
fmap/sub-<subid>_ses-<sesid>_fieldmap.nii.gz
QC report
sub-<subid>_ses-<sesid>_qc.pdf
Rigid-body transform from structural to diffusion space
xfm/sub-<subid>_ses-<sesid>_from-T2w_to-dwi_mode-image.mat
Rigid-body transform from diffusion to structural space
xfm/sub-<subid>_ses-<sesid>_from-dwi_to-T2w_mode-image.mat
Warp from diffusion space to 40 week template space (Schuh)
xfm/sub-<subid>_ses-<sesid>_from-dwi_to-template40wk_mode-image.nii.gz
Warp from 40 week template space (Schuh) to diffusion space
xfm/sub-<subid>_ses-<sesid>_from-template40wk_to-dwi_mode-image.nii.gz
Functional pipeline
Inputs:
Reconstructed data: sourcedata/sub-<subid>/ses-<sesid>
Resting fMRI
func/sub-<subid>_ses-<sesid>_task-rest_bold.nii.gz
Single-band Ref
func/sub-<subid>_ses-<sesid>_task-rest_sbref.nii.gz
Spin Echo EPI with different phase encode directions (for topup fieldmap estimation)
fmap/sub-<subid>_ses-<sesid>-{sesid}_dir-APPA_epi.nii.gz
Dual echo-time field-map, magnitude
fmap/sub-<subid>_ses-<sesid>_magnitude.nii.gz
Dual echo-time field-map
fmap/sub-<subid>_ses-<sesid>_fieldmap.nii.gz
 
Structural pipeline derived data: derivatives/dhcp_anat_pipeline/sub-<subid>/ses-<sesid>
T2 weighted, bias corrected image (in T2 space)
anat/sub-<subid>_ses-<sesid>_T2w.nii.gz
T2 brain mask
anat/sub-<subid>_ses-<sesid>_space-T2w_brainmask.nii.gz
Draw-EM tissue segmentation (9 labels)
anat/sub-<subid>_ses-<sesid>_space-T2w_desc-drawem_dseg.nii.gz 
T1 weighted, bias corrected image (in T2 space)
anat/sub-<subid>_ses-<sesid>_space-T2w_T1w.nii.gz 

Outputs:
Derived data: derivatives/dhcp_fmri_pipeline/sub-<subid>/ses-<sesid>
Multi-band EPI, distortion corrected, motion corrected, FIX denoised, 4D image
func/sub-<subid>_ses-<sesid>_task-rest_desc-preproc_bold.nii.gz
Motion parameters
func/sub-<subid>_ses-<sesid>_motion.tsv
Brain mask
func/sub-<subid>_ses-<sesid>_task-rest_desc-preproc_space-bold_brainmask.nii.gz
Derived fieldmap, magnitude
fmap/sub-<subid>_ses-<sesid>_magnitude.nii.gz
Derived fieldmap (rad/s)
fmap/sub-<subid>_ses-<sesid>_fieldmap.nii.gz
QC report
sub-<subid>_ses-<sesid>_funcqc.html
Folder containing registration files
xfm
Rigid-body transform from functional (mcdc) to single-band Ref space
xfm/sub-<subid>_ses-<sesid>_from-bold_to-sbref_mode-image.mat
Rigid-body transform from single-band Ref space to structural space
xfm/sub-<subid>_ses-<sesid>_from-sbref_to-T2w_mode-image.mat
Rigid-body transform from functional (mcdc) to structural space
xfm/sub-<subid>_ses-<sesid>_from-bold_to-T2w_mode-image.mat
Rigid-body transform from field-map to structural space
xfm/sub-<subid>_ses-<sesid>_from-fieldmap_to-T2w_mode-image.mat
Warp from functional (mcdc) space to the 40 weeks template space
xfm/sub-<subid>_ses-<sesid>_from-bold_to-template40wk_mode-image.nii.gz
Warp from the structural space to the 40wk template space
xfm/sub-<subid>_ses-<sesid>_from-T2w_to-template40wk_mode-image.nii.gz

Acknowledgments:
The research leading to these data has received funding from the European Research Council under the European Union Seventh Framework Programme (FP/20072013)/ERC Grant Agreement no. 319456. The work was also supported by the NIHR Biomedical Research Centres at Guys and St Thomas NHS Trust.  We are grateful to the families who generously supported this trial.   We are also thankful to the WU-Minn-Oxford Human Connectome Project consortium (1U54MH091657-01) for access to their computing resources.


