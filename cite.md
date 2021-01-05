---
---

## dHCP Citations

*How to acknowledge dHCP and cite dHCP publications if you have used data
provided by the KCL-Imperial-Oxford developing HCP consortium.*

As stipulated in the User Terms, authors of publications or presentations
that use KCL-Imperial-Oxford developing Human Connectome Project (dHCP)
data should acknowledge the funding sources and cite relevant publications
that describe key methods used by the dHCP to acquire and process the data.
This page provides guidance on both fronts.

## Acknowledge the Funding Source

Papers, book chapters, books, posters, oral presentations, and all other
printed and digital presentations of results derived from dHCP data should
contain the following wording in the acknowledgments section:

> Data were provided by the developing Human Connectome Project,
> KCL-Imperial-Oxford Consortium funded by the European Research Council
> under the European Union Seventh Framework Programme (FP/2007-2013) / ERC
> Grant Agreement no. [319456]. We are grateful to the families who generously
> supported this trial.

## Cite Relevant Publications

The specific publications that are appropriate to cite will depend on what
dHCP data you used in your study and the purposes for which you used the data.
Here is an annotated list of publications that can guide your choices.
They are grouped into categories and subcategories that relate to different
aspects of data acquisition, pre-processing, and analysis. As additional
publications become available, this list will be updated to include those
that it may be relevant to cite.

### I. Publications relevant to dHCP primary datasets

The publications in this section describe dHCP data acquisition methods
that have been used to generate both the ‘raw’ NIFTI format and the
pre-processed datasets that are available for download.

**Overview Publication:**

Hughes, E. J., Winchman, T., Padormo, F., Teixeira, R., Wurie, J., Sharma,
M.,  Fox, M.,  Hutter, J.,  Cordero‐Grande, L., Price, A. N.,  Allsop, J.,
Bueno‐Conde, J., Tusor, N.,  Arichi, T.,  Edwards, A. D.,  Rutherford,
M. A., Counsell, S. J.,  and Hajnal, J. V. **A dedicated neonatal brain
imaging system** *Magnetic Resonance Medicine (2017), 78(2): 794–804* [DOI:
10.1002/mrm.26462](https://doi.org/10.1002/mrm.26462)

**Diffusion MRI data acquisition:** All dHCP diffusion data was acquired
with a purpose designed multiband EPI acquisition featuring optimised
multi-shell diffusion sensitisation scheme, gradient demand optimisation,
restart capability with adjustable time setback to provide overlapping data,
and use of all 4 phase encode directions.

Hutter, J., Tournier, J.D., Price, A.N., Cordero-Grande, L., Hughes, E.J.,
Bastiani, M., Sotiropoulos, S.N., Jbabdi, S., Andersson, J., Edwards, A.D.,
& Hajnal, J.V. **Time-efficient and flexible design of optimised multi-shell
HARDI diffusion** *Magnetic Resonance in Medicine (2018), 79 (3): 1276-1292.*
[DOI: 10.1002/mrm.26765](https://doi.org/10.1002/mrm.26765)

Tournier, J. D., E. Hughes, N. Tusor, A.D. Edwards
and J.V Hajnal. **Optimisation of single-shell
HARDI for neonatal imaging** [*Proc ISMRM 2015:
p2895.*](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Optimisation-of-single-shell-HARDI-for-neonatal-imaging-.pdf)

Tournier, J. D.  E. Hughes, N. Tusor, S.N. Sotiropoulos,
S. Jbabdi, J. Andersson, D. Rueckert, A.D. Edwards, J.V
Hajnal. **Data-driven optimisation of multi-shell HARDI** [*ISMRM 2015:
p2897.*](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Data-driven-optimisation-of-multi-shell-HARDI.pdf)

**Resting state functional MRI data acquisition:** All dHCP functional
imaging acquisitions were obtained using an optimised multiband sequence
tuned for neonatal, in particular by deploying a high multiband factor to
achieve a repeat time short enough to avoid aliasing cardiac fluctuations
into the fMRI signal. Phase optimised multiband pulses were used throughout.

Price A. N., Cordero-Grande L, Malik S. J., Abaei M., Arichi T.,
Hughes E. J., Rueckert D., Edwards A. D., Hajnal J. V. **Accelerated
Neonatal fMRI Using Multiband EPI** [*In Proc ISMRM 2015:
p3911.*](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Accelerated-Neonatal-fMRI-using-Multiband-EPI.-ISMRM-2015.pdf)

Malik, SJ, Price AN, and Hajnal JV. **Optimized Amplitude
Modulated Multi-Band RF pulses** [*In Proc ISMRM 2015:
p2398*](http://www.developingconnectome.org/wp-content/uploads/sites/70/2019/08/Optimized-Amplitude-Modulated-Muli-Band-RF-pulses.pdf)

**Anatomical MRI - Motion corrected reconstruction:** All anatomical images
for all dHCP subjects have had motion corrected reconstruction:

Cordero-Grande, L., Hughes, E. J., Hutter, J., Hutter, J., Price, A. N.,
and Hajnal, J. V. **Three-Dimensional Motion Corrected Sensitivity Encoding
Reconstruction for Multi-Shot Multi-Slice MRI: Application to Neonatal
Brain Imaging** *Magnetic Resonance in Medicine (2018), 79(3): 1365–1376.* [DOI:
10.1002/mrm.26796](https://doi.org/10.1002/mrm.26796)

**Diffusion MRI signal retrieval:** Denoised diffusion images are obtained by:

Cordero-Grande, L., Christiaens, D., Hutter, J., Price, A. N., and Hajnal,
J. V.  **Complex diffusion-weighted image estimation via matrix recovery
under general noise models** *Neuroimage (2019), 200: 391–404.* [DOI:
10.1016/j.neuroimage.2019.06.039](https://doi.org/10.1016/j.neuroimage.2019.06.039)

### Publications relevant to the dHCP pre-processed data

The publications in this section describe methods that are relevant if you
have downloaded and used any of the dHCP pre-processed data involving one
or more modalities.

#### Structural MRI data processing

**Automated processing pipeline:** All dHCP subjects have been processed and
cortical meshes have been generated using the following automated pipeline:

Makropoulos, A., Robinson, E.C., Schuh, A., Wright, R., Fitzgibbon, S.P.,
Bozek, J., Counsell, S.J., Steinweg, J., Vecchiato, K., Passerat-Palmbach, J.,
Lenz, G., Mortari, F., Tenev, T., Duff, E.P., Bastiani, M., Cordero-Grande,
L., Hughes, E., Tusor, N., Tournier, J.-D., Hutter, J., Price, A.N., Teixeira,
R.P.A.G., Murgasova, M., Victor, S., Kelly, C., Rutherford, M.A., Smith, S.,
Edwards, A.D., Hajnal, J.V., Jenkinson, M., Rueckert, D. **The Developing
Human Connectome Project: a Minimal Processing Pipeline for Neonatal
Cortical Surface Reconstruction** *NeuroImage (2018), 173: 88-112.* [DOI:
10.1016/j.neuroimage.2018.01.054](https://doi.org/10.1016/j.neuroimage.2018.01.054)

**Surface templates:** Cortical surfaces atlases have been generated
following the procedures described in this paper:

Bozek, J., Makropoulos, A., Schuh, A., Fitzgibbon, S., Wright, R., Glasser,
M. F., Coalson, T. S., O'Muircheartaigh, J., Hutter, J., Price, A. N.,
Cordero-Grande, L., Teixeira, R. P. A. G., Hughes, E., Tusor, N., Pegoretti
Baruteau, K., Rutherford, M. A.,  Edwards, A. D., Hajnal, J. V.  Smith,
S. M., Rueckert, D., Jenkinson, M., and Robinson, E. C. **Construction of
a neonatal cortical surface atlas using Multimodal Surface Matching in the
Developing Human Connectome Project** *NeuroImage (2018), 179: 11-29.* [DOI:
10.1016/j.neuroimage.2018.06.018](https://doi.org/10.1016/j.neuroimage.2018.06.018)

#### Resting-fMRI data processing

**Automated processing pipeline:** The pipeline described in the following
paper was applied to all dHCP open access fMRI data.

Fitzgibbon, SP., Harrison, SJ., Jenkinson, M., Baxter, L., Robinson, EC.,
Bastiani, M., Bozek, J., Karolis, V., Cordero Grande, L., Price, AN., Hughes,
E., Makropoulos, A., Passerat-Palmbach, J., Schuh, A., Gao, J., Farahibozorg,
S., O'Muircheartaigh, J., Ciarrusta, J., O'Keeffe, C., Brandon, J., Arichi,
T., Rueckert, D., Hajnal, JV., Edwards, AD., Smith, SM., Duff, E., Andersson,
J.  **The developing Human Connectome Project automated functional processing
framework for neonates.**, *NeuroImage (2020), 223: 117303, 2020.* [DOI:
10.1016/j.neuroimage.2020.117303](https://doi.org/10.1016/j.neuroimage.2020.117303)
*Authors contributed equally.*

**fMRI motion and distortion correction:** Techniques described in the
following papers were applied to all open access pre-processed fMRI data:

Andersson, J. L. R., Graham, M. S., Drobnjak, I., Zhang, H.,
and Campbell, J. **Susceptibility-induced distortion that varies
due to motion: Correction in diffusion MR without acquiring
additional data** *NeuroImage (2018), 171: 277–295* [DOI:
10.1016/j.neuroimage.2017.12.040](https://doi.org/10.1016/j.neuroimage.2017.12.040)

Andersson, J. L. R., Graham, M. S., Drobnjak, I., Zhang, H.,
Filippini, N., and Bastiani, M. **Towards a comprehensive framework
for movement and distortion correction of diffusion MR images:
Within volume movement** *NeuroImage (2017), 152: 450–466.* [DOI:
10.1016/j.neuroimage.2017.02.085](https://doi.org/10.1016/j.neuroimage.2017.02.085)

Andersson, J. L. R., Hutton, C., Ashburner, J., Turner, R.,
and Friston, K. **Modeling Geometric Deformations in EPI
Time Series** *NeuroImage (2001), 13(5): 903–919.* [DOI:
10.1006/nimg.2001.0746](https://doi.org/10.1006/nimg.2001.0746)

Andersson, J. L. R., Skare, S., and Ashburner, J. **How to correct
susceptibility distortions in spin-echo echo-planar images: application
to diffusion tensor imaging** *NeuroImage (2003), 20(2): 870–888.* [DOI:
10.1016/S1053-8119(03)00336-7](https://doi.org/10.1016/S1053-8119(03)00336-7)

#### Diffusion MRI EDDY pipeline

**Automated processing pipeline:** The pipeline described in the following
reference was applied to all dHCP open access diffusion data:

Bastiani, M., Andersson, J.L.R., Cordero-Grande, L., Murgasova, M., Hutter,
J., Price, A.N., Makropoulos, A., Fitzgibbon, S.P., Hughes, E., Rueckert,
D., Suresh, V., Rutherford, M., Edwards, A.D., Smith, S., Tournier,
J. D., Hajnal, J.V., Jbabdi, S., & Sotiropoulos, S.N. **Automated
processing pipeline for neonatal diffusion MRI in the developing
Human Connectome Project** *NeuroImage (2018), 185: 750-763.* [DOI:
10.1016/j.neuroimage.2018.05.064](https://doi.org/10.1016/j.neuroimage.2018.05.064)

The pipeline can be downloaded from:

[https://git.fmrib.ox.ac.uk/matteob/dHCP_neo_dMRI_pipeline_release](https://git.fmrib.ox.ac.uk/matteob/dHCP_neo_dMRI_pipeline_release)

**Diffusion imaging distortion correction and quality control:** Techniques
described in the following references were applied to all dHCP open access
pre-processed diffusion data; the last reference describes the automated
quality control framework that was used to detect processing issues or
inconsistencies:

Andersson, J.L.R., Skare, S., and Ashburner, J. **How to correct
susceptibility distortions in spin-echo echo-planar images: application
to diffusion tensor imaging** *NeuroImage (2003), 20: 870-888.* [DOI:
10.1016/S1053-8119(03)00336-7](https://doi.org/10.1016/S1053-8119(03)00336-7)

Andersson, J.L.R., and Sotiropoulos, S.N. **An integrated approach
to correction for off-resonance effects and subject movement in
diffusion MR imaging** *NeuroImage (2016), 125: 1063-1078.* [DOI:
10.1016/j.neuroimage.2015.10.019](https://doi.org/10.1016/j.neuroimage.2015.10.019)

Andersson, J.L.R., Graham, M.S., Zsoldos, E., and Sotiropoulos,
S.N. **Incorporating outlier detection and replacement into a
non-parametric framework for movement and distortion correction
of diffusion MR images** *NeuroImage (2016), 141: 556-572.* [DOI:
10.1016/j.neuroimage.2016.06.058](https://doi.org/10.1016/j.neuroimage.2016.06.058)

Andersson, J.L.R., Graham, M.S., Drobnjak, I., Zhang, H., Filippini,
N., and Bastiani, M. **Towards a comprehensive framework for
movement and distortion correction of diffusion MR images:
Within volume movement** *NeuroImage (2017), 152: 450-466.* [DOI:
10.1016/j.neuroimage.2017.02.085](https://doi.org/10.1016/j.neuroimage.2017.02.085)

Andersson, J.L.R., Graham, M.S., Drobnjak, I., Zhang, H., and
Campbell, J. (2018). **Susceptibility-induced distortion that
varies due to motion: Correction in diffusion MR without acquiring
additional data** *NeuroImage (2018), 171: 277-295.* [DOI:
10.1016/j.neuroimage.2017.12.040](https://doi.org/10.1016/j.neuroimage.2017.12.040)

Bastiani, M., Cottaar, M., Fitzgibbon, S.P., Suri, S.,
Alfaro-Almagro, F., Sotiropoulos, S.N., Jbabdi, S., & Andersson,
J.L.R. **Automated quality control for within and between studies
diffusion MRI data using a non-parametric framework for movement
and distortion correction** *NeuroImage (2018), 184: 801-812.* [DOI:
10.1016/j.neuroimage.2018.09.073](https://doi.org/10.1016/j.neuroimage.2018.09.073)

#### Diffusion MRI SHARD pipeline 

The second dMRI processing pipeline is described in:

Christiaens, D., Cordero-Grande, L., Pietsch, M., Hutter, J., Price, A.N.,
Hughes, E.J., Vecchiato, K., Deprez, M., Edwards, A.D., Hajnal, J.V., &
Tournier, J-D. **Scattered slice SHARD reconstruction for motion correction
in multi-shell diffusion MRI** *NeuroImage (2021), 225: 117437.* [DOI:
10.1016/j.neuroimage.2020.117437](https://doi.org/10.1016/j.neuroimage.2020.117437)

Additionally, inter-slice intensity inconsistencies were corrected with

Pietsch, M. and Christiaens, D. and Hajnal, J.V. & Tournier,
J-D. **dStripe: slice artefact correction in diffusion MRI
via constrained neural network** *biorxiv (2020)* [DOI:
10.1101/2020.10.20.347518](https://doi.org/10.1101/2020.10.20.347518)
