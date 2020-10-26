---
---

## The diffusion pipeline II

The third data release includes an alternative dMRI processing pipeline based 
on denoising<sup>1</sup> and SHARD motion correction<sup>2</sup>. This 
pipeline correponds more closely to the fetal processing pipeline<sup>3</sup>, 
and is therefore better suited for studies that include both the fetal and the 
neonatal data.

The pipeline consists of the following processing steps:

1. Image denoising using random matrix theory with optimal shrinkage in the 
complex domain (i.e., using magnitude and phase images)<sup>1</sup>. This 
denoising approach also accounts for spatial noise correlations introduced by 
SENSE and Partial Fourier subsampling. After denoising, the magnitude images 
are extracted.

2. The denoised images are then corrected for Gibbs ringing<sup>4</sup>.

3. Fat shift suppression is achieved through local outlier reweighting in 
slice-to-volume reconstruction (step 5)<sup>5</sup>. The local outlier weights 
are computed independently based on the residuals of the SENSE reconstruction. 
This is achieved using a 2-class Gaussian Mixture Model with a Markov Random 
Field, fitted using Expectation-Maximization. 

4. The B0 field map, used to model susceptibility-induced distortion, is 
estimated using FSL Topup<sup>6</sup>. As input for topup, we selected the two 
"best" b=0 volumes for each of the 4 phase encoding (PE) directions based on 
a edge-detection filter in the slice direction. The indices of the selected 
8 volumes are stored and used as reference; the ordering of the image volumes 
and the corresponding diffusion encoding is thus never changed.

5. Motion correction using SHARD slice-to-volume reconstruction<sup>2</sup>. 
The inputs are the denoised and degibbsed multiband dMRI images (stage 2), the 
voxel weights (step 3), and the field map (step 4). The output are estimated 
subject motion traces, slice weights used to correct dropouts, and the SHARD 
representation fitted to the scattered slice data. The SHARD reconstruction 
also modelles the slice profile to recover the images at isotropic resolution.
The motion- and distortion-corrected image is stored as a series of Spherical 
Harmonics (SH) coefficients for each shell.

6. The SHARD output image is projected onto the original diffusion encoding 
used during acquisition, to provide the dMRI output in a format compatible with 
conventional software. This is a one-to-one mapping representing identical 
image information. Note that motion-induced gradient reorientation is modelled
during SHARD slice-to-volume reconstruction in step 5; the gradient table 
hence remains unchanged.

7. TODO: DESTRIPING

8. Diffusion data are aligned to high-resolution structural (T2-weighted)
space using boundary-based registration<sup>8,9</sup>  on the average
attenuation volume for the b=1000 s/mm2 shell (i.e. b1k/b0). This
transformation is combined with a non-linear registration<sup>10</sup> of
the T2w volume to the 40 weeks template<sup>11</sup> to allow transformations
between diffusion and atlas spaces.

## Diffusion MRI QC

Automated quality control metrics are calculated for several key steps in the 
pipeline. Specifically, the data release includes estimates of:

- **Signal-to-Noise Ratio**: A measure of SNR is calculated based on the 
  residuals of denoising (Step 1). The reported metrics are the median across a
  brain mask of the RMS residuals, divided by the median of the mean b=0 signal.

- **Motion metrics**: Measures of the mean translation and rotation that was 
  detected/estimated in the motion correction method.<sup>2</sup> These metrics 
  are based on the gradient of the motion trace, thus measuring the subject 
  activity during the scan.

- **Outlier ratio**: The mean outlier weight of all slices in the data, as 
  detected in slice-to-volume reconstruction.<sup>2</sup>

In addition, overview screenshots of the motion traces and destriped output data 
are generated. Based on these screenshots, visual pass/fail Quality Control 
identified a small subset of cases to be discarded from analysis.


## References

1. Cordero-Grande, L., Christiaens, D., Hutter, J., Price, A.N., Hajnal, J.V.
 **Complex diffusion-weighted image estimation via matrix recovery under general
 noise models** *Neuroimage (2019), 200: 391-404.* [DOI:
10.1016/j.neuroimage.2019.06.039](https://doi.org/10.1016/j.neuroimage.2019.06.039)

2. Christiaens, D., Cordero-Grande, L., Pietsch, M., Hutter, J., Price, A.N., 
Hughes, E.J., Vecchiato, K., Deprez, M., Edwards, A.D., Hajnal, V., Tournier, J-D.
 **Scattered slice SHARD reconstruction for motion correction in multi-shell 
diffusion MRI** *NeuroImage (2021), 225: 117437.* [DOI:
 10.1016/j.neuroimage.2020.117437](https://doi.org/10.1016/j.neuroimage.2020.117437)

3. Christiaens, D., Cordero-Grande, L., Price, A.N., Hutter, J., Hughes, E.J.,
ounsell, S.J., Tournier, J-D., Hajnal, J.V. **Fetal diffusion MRI acquisition and 
analysis in the developing Human Connectome Project** *ISMRM 2020, O629.*

4. Kellner, E., Dhital, B., Kiselev, V.G., Reisert, M. **Gibbs-ringing artifact
   removal based on local subvoxel-shifts.** *Magnetic Resonance in Medicine 
   (2016) 76: 1574–1581.* [DOI: 10.1002/mrm.26054](https://doi.org/10.1002/mrm.26054)

5. Christiaens, D., Cordero-Grande, L., Hutter, J., Price, A.N., 
   O'Murchearthaigh, J., Vecchiato, K., Hajnal, J.V., Tournier, J-D. **Fat-shift
   suppression in diffusion MRI using rotating phase encoding and localised 
   outlier weighting** *ISMRM 2020, O981.*

6. Andersson, J.L., Skare, S., and Ashburner, J. **How to correct
susceptibility distortions in spin-echo echo-planar images: application
to diffusion tensor imaging** *Neuroimage (2003), 20(2): 870-888.* [DOI:
10.1016/S1053-8119(03)00336-7](https://doi.org/10.1016/S1053-8119(03)00336-7)

7. Greve, D.N., and Fischl, B. **Accurate and robust brain image alignment
using boundary-based registration** *Neuroimage (2009), 48(1): 63-72.* [DOI:
10.1016/j.neuroimage.2009.06.060](https://doi.org/10.1016/j.neuroimage.2009.06.060)

8. Jenkinson, M., Bannister, P., Brady, M., and Smith, S. **Improved
optimization for the robust and accurate linear registration and motion
correction of brain image** *Neuroimage (2002), 17(2): 825-841.* [DOI:
10.1006/nimg.2002.1132](https://doi.org/10.1006/nimg.2002.1132)

9. Andersson, J.L.R., Jenkinson, M., and
Smith, S. [**Non-linear registration, aka spatial
normalisation**](https://www.fmrib.ox.ac.uk/datasets/techrep/tr07ja2/tr07ja2.pdf)
*FMRIB technical report TR07JA2 (2010).*

10. Schuh, A., Makropoulos, A., Robinson, E.C., Cordero-Grande, L., Hughes,
E., Hutter, J., Price, A.N., Murgasova, M., Teixeira, R.P.A.G., Tusor,
N., Steinweg, J.K., Victor, S., Rutherford, M.A., Hajnal, J.V., Edwards,
A.D., and Rueckert, D. **Unbiased construction of a temporally consistent
morphological atlas of neonatal brain development** *bioRxiv (2018), 251512.*
[DOI: 10.1101/251512](https://doi.org/10.1101/251512)



