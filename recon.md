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

fMRI and dMRI simultaneous multi-slice (SMS) echo planar
imaging (EPI) is reconstructed using the extended SENSE technique<sup>4</sup>,
with details described elsewhere<sup>5,6,7</sup>; sensitivity estimates
from a conventional reference scan are refined with the information from
non-SMS reference acquisitions with matched readouts to promote matched
coil map and image distortions. As for dMRI, complex data retrieval is 
performed by the generalized singular value shrinkage (GSVS) denoising 
technique using noise measures performed during the acquisition<sup>8</sup>. 
Methods and example data for the GSVS method are available at 
https://github.com/mriphysics/complexSVDShrinkageDWI/releases/tag/1.1.0.

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


