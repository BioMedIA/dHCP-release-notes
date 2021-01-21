---
---

## Diffusion EDDY Pipeline

For a complete and detailed description of all the steps
involved in the [dHCP neonatal diffusion MRI (dMRI) data processing
pipeline](https://git.fmrib.ox.ac.uk/matteob/dHCP_neo_dMRI_pipeline_release),
the reader is referred elsewhere<sup>1</sup>. The main processing steps
are briefly summarised below:

1. For each phase encoding (PE) direction, the diffusion un-weighted
b0 volume pairs least-affected by intra-volume motion are automatically
selected. The dataset is then re-organised by moving the least-affected
b0 volume and the volumes that follow (until the end of the acquisition)
at the beginning of the 4D raw data file.

2. Field maps for correcting susceptibility-induced distortions are estimated
using FSL TOPUP<sup>2</sup>.

3. Distortions caused by susceptibility, between-volume motion, within-volum
motion, motion-induced signal drop-out, motion-by-susceptibility interactions,
and eddy currents are corrected; outlier slices are detected and replaced
in raw distorted space. All these steps use FSL EDDY<sup>3-6</sup>.

4. A super-resolution algorithm<sup>7</sup> is applied along the
slice-selection direction, to achieve isotropic resolution of 1.5 mm.

5. Post-processing using traditional tensor fitting, as well as FSL's
[BedpostX](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FDT/UserGuide) for
multishell data<sup>13</sup> is applied.

6. Diffusion data are aligned to high-resolution structural (T2-weighted)
space using boundary-based registration<sup>8,9</sup>  on the average
attenuation volume for the b=1000 s/mm2 shell (i.e. b1k/b0). This
transformation is combined with a non-linear registration<sup>10</sup> of
the T2w volume to the 40 weeks template<sup>11</sup> to allow transformations
between diffusion and atlas spaces.

## Diffusion MRI QC

1. Numerous quality assurance metrics are calculated by the EDDY QC
tools<sup>12</sup>.  Four of these are specifically compared against
the population distribution to flag outliers for manual inspection and
potential exclusion:

    1. Mean signal-to-noise ratio (SNR) from the b0 volumes

    2. Mean contrast-to-noise ratio (CNR) for each b-shell, i.e., 400,
    1000 and 2600 s/mm2.

2. All QC metrics are then converted to Z-scores and averaged, to generate
a summary QC metric. 

3. All QC metrics are available in the `combined.tsv` spreadsheet in the
[supplementary](https://github.com/BioMedIA/dHCP-release-notes/tree/master/supplementary_files).

## References

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

13. Jbabdi S, Sotiropoulos S.N., Savio A., Grana M., Behrens
T.E.J. **Model-based analysis of multishell diffusion MR data for
tractography: How to get over fitting problems** *Magn Reson Med (2012).*
[DOI:10.1002/mrm.24204](https://doi.org/10.1002/mrm.24204)

