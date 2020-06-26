---
---

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

## References

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


