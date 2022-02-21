---
---

## Neonatal structural pipeline

The [structural
pipeline](https://github.com/BioMedIA/dhcp-structural-pipeline) was
encapsulated as a Docker container image and run via the OpenMOLE<sup>10</sup>
platform on a local cluster.

### Inputs and outputs

**From reconstruction pipeline:** `rawdata/sub-{subid}/ses-{sesid}`

| Description                                             | Filename                                        |
|:--------------------------------------------------------|:------------------------------------------------|
| T1w image (combined Slice-to-Volume reconstruction)     | `anat/sub-{subid}_ses-{sesid}_rec-SVR_T1w.nii`  |
| T2w image (combined Slice-to-Volume reconstruction)     | `anat/sub-{subid}_ses-{sesid}_rec-SVR_T2w.nii`  |

The structural pipline generates the files listed in the [Structural pipeline](structure.html#structural-pipeline) section of the directory structure summary.

### Operation

1. Registration

2. Segmentation

    1. Structural scans are pre-processed by first running bias correction
    using the N4 algorithm<sup>1</sup>.

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

3. Surface extraction

    1. Surface mesh extraction is performed with the method described
    elsewhere<sup>5</sup>. A white matter mask enclosing the white surface is
    computed by merging the white matter and the subcortical structures with
    the exception of the brainstem and the cerebellum. Similarly, a pial mask
    is computed by merging the grey matter structure with the white matter
    mask. The white and pial surfaces of the left and right hemispheres
    are then reconstructed with the method outlined in 5 using a deformable
    model. The model in 5 includes forces to avoid self-intersections and
    includes an image-based refinement step that corrects regions such as
    deep sulci mislabelled by the volumetric segmentation.

    2. Midthickness surfaces are generated as the middle surface between
    the white and pial surfaces. The midthickness surface is computed using
    the Euclidean distance between corresponding points of the white and
    pial surface.

    3. Spherical projection is performed6, and it is based on the inflated
    white matter surface. The inflated white matter surface is produced in
    a similar manner as in the FreeSurfer pipeline<sup>7</sup>. Inflated and
    very inflated surfaces used for visualisation are generated 
    similarly<sup>8</sup>.

    4. The following metrics are further estimated from the surfaces:
    curvature, thickness, sulcal depth, T1w/T2w myelin, labels (projected
    from the volume). All surfaces have one-to-one vertex correspondence
    for all points on the surface ensuring that the same vertex indexes
    the same point, in the same relative position, on the anatomy for all
    surfaces. Please note that due to the relatively large voxels (causing
    partial volume) and/or the uneven vertex sampling for gyri (relative
    to sulci) we observe some artifacts in the myelin and thickness metric
    files, which resemble the folding patterns.  For this, we offer a
    'corrected' version of thickness maps (corr_thickness); however, this
    results only from a linear regressesion based correction. We advise
    careful interpretation of these maps and have chosen at this time not
    to do the same for myelin.

4. Surface registration

   1. A new symmetric and extended version of the neonatal surface
   template<sup>11</sup> is available from the [brain-development.org
   website](https://brain-development.org/brain-atlases/atlases-from-the-dhcp-project/)

   2. All surfaces have been nonlinearly aligned to the template using
   cortical folding-driven aligment (implemented with MSM<sup>11,12</sup>);
   alignment has been optimised with relatively weak regularisation
   to push cortical correspondence of folds in the frontal lobe. At
   this time we have no evidence of any negative impact on the dMRI
   and fMRI correspondence through doing this. However, scripts to
   re-run registration wih modifed parameters are available from
   [here](https://github.com/ecr05/dHCP_template_alignment)

   3. We release only the registration warp file (`sphere.reg.surf.gii`). To
   obtain the warped metric files and surfaces in template space please run
   the [resampling scripts](https://github.com/ecr05/dHCP_template_alignment)


The structural pipeline is described in detail elsewhere<sup>9</sup>.

<a name="struct-qc"></a>
### Quality Control/Assurance

The dHCP structural data set contains MR imaging of whole brain anatomy across a wide gestational age. The data collected contains rapidly changing anatomical variation across age, that inherently provides challenges for automatic segmentation processes. For this reason, we carried out a visual inspection of the segmentation pipeline on a random set of 30 datasets (gestational age range at scan 27.14 weeks-44.14 weeks). 

The following anatomical segmentations were assessed:
- Cortical ribbon
- Ventricular space including the cavum septum pellucidum
- Whole brain white matter
- Deep grey matter (basal ganglia)

The results showed some small areas of common segmentation errors across the dataset that can be easily correctable with some fine editing:
1. The cortical ribbon segmentation can contain small regions of highly convoluted cortex that may not be sufficiently delineated due to partial volume effects and there is consistent mis-registration of the cortex in the medial temporal lobe.
2. The anterior cavum septum pellucidum can be mis-labelled as ventricular space.
3. The basal ganglia/deep grey matter anatomy may have a small chunk of anatomy mislabelled as white matter. 
4. The whole brain white matter segmentation was found to be consistently accurate across subjects. 

We therefore recommend that visual inspection of the segmentation data in this cohort is carried out before inclusion in analysis.



### References

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

9. Makropoulos, A., Robinson, E.C., Schuh, A., Wright, R., Fitzgibbon,
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

11. Bozek, J., Makropoulos, A., Schuh, A., Fitzgibbon, S., Wright, R.,
Glasser, M.F., Coalson, T.S., O'Muircheartaigh, J., Hutter, J., Price,
A.N., Cordero-Grande, L.  Teixeira, R. P. A. G., Hughes, E., Tusor, N.,
Pegoretti Baruteau, K., Rutherford, M. A., Edwards, A. D., Hajnal, J. V.,
Smith, S. M.,  Rueckert, D., Jenkinson, M., Robinson, E.C, **Construction of
a neonatal cortical surface atlas using Multimodal Surface Matching in the
Developing Human Connectome Project**. *NeuroImage (2018) 179: 11-29.* [DOI:
10.1016/j.neuroimage.2018.06.018](https://doi.org/10.1016/j.neuroimage.2018.06.018)

12. Robinson, E.C., Jbabdi, S., Glasser, M.F., Andersson, J.,
Burgess, G.C., Harms, M.P., Smith, S.M., Van Essen, D.C. and
Jenkinson, M. **MSM: a new flexible framework for Multimodal
Surface Matching**.  *Neuroimage (2014), 100: 414-26.* [DOI:
10.1016/j.neuroimage.2014.05.069](https://doi.org/10.1016/j.neuroimage.2014.05.069)

13. Robinson, E.C., Garcia, K., Glasser, M.F., Chen, Z., Coalson, T.S.,
Makropoulos, A., Bozek, J., Wright, R., Schuh, A., Webster, M. and Hutter,
J., Price, A.N., Cordero-Grande, L.  Hughes, E., Tusor, N., Bayley, P.V.,
Van Essen, D.C., Smith, S. M.,  Edwards, A. D., Hajnal, J.  Jenkinson, M.,
Glocker, B., Rueckert, D., **Multimodal surface matching with higher-order
smoothness constraints**. *Neuroimage (2018), 167: 453-465.* [DOI:
10.1016/j.neuroimage.2017.10.037](https://doi.org/10.1016/j.neuroimage.2017.10.037)

