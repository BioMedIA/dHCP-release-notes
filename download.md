---
---

## Download

In order to be able to browse/download data,
you will need to register by following [this
link](https://data.developingconnectome.org/app/template/Login.vm). On
the dHCP data login page, select ‘Register’ and fill out the mandatory
fields including **Lab/Department, Institute Full Name, Country and your institutional email address**. You will receive a verification email. After you verify your email
address, you will be able to login to sign an agreement and access the
public face of the dHCP database (db). This includes browsing (although
not downloading) available Projects (data sets).

If you experience any technical issues, please [submit your query
here](https://neurostars.org/t/dhcp-infant-data-downloading-issue/2500).

## Data review and download

In order to unlock download options for available Projects (data sets),
you will have to sign user terms. Open any Project and hit ‘Sign user
terms’. Once confirmed you will be able to view a list of subjects,
preview the available data as acquired (without any pre-processing) and
will be provided two download options.

### Academic Torrent download (recommended)

Since data sets are fairly large (expect > 700GB) this is
a fail-safe way to get hold of desired releases. A [separate
document](https://drive.google.com/file/d/1llcifaLWicGZ-DxVWCpyhBqJfEwToWb_/view)
provides more detailed instructions. Be sure to have a Torrent client such as
[BitTorrent](https://www.bittorrent.com/) installed on your computer. Clicking
on the ‘Download Data Set (Torrent)’ button will provide you with a
`.torrent` file a few kB in size. Opening this .torrent file in your Torrent
client will give you the option to select among subsets of the selected
release. Once confirmed, your torrent client will automatically start the
download from multiple peers. You can pause/stop the download at any time. By
downloading parts of the bundle you automatically become a peer for the
selected .torrent file, which increases bandwidth for other peers. You are
encouraged to at least upload the same amount of data that you downloaded
(a download/upload ratio of 1.0 in the Torrent client), however this is
not a must. Caveat: Your system administrator / institution might block
(or be unhappy with) peer-to-peer traffic for various reasons.

Once you start downloading the dataset, you will notice that your torrent
client mentions a sharing / seeding ratio. It means that as soon as you
start downloading the dataset, you become part of our community of sharers
and contribute to making the dataset available to other researchers all
around the world!

There is no reason to be scared! It’s perfectly legal as long as you are
allowed to have a copy of the dataset (that is the information you need to
forward to your lab’s IT team if they are blocking your ports). You are
actually providing a tremendous contribution to dHCP by spreading the data,
so thank you again for that. With your help, we can make sure this data
remains available and can be downloaded relatively fast in the future.

Over time, the dataset will grow and your contribution will be more and
more important so that each and everyone of you can still obtain the data
in the smoothest possible way.

### Via dHCP XNAT web service

Image data for individual subjects (without any pipeline pre-processing)
can be downloaded directly through dHCP XNAT web interface. The image data
are NIfTI files and if downloaded directly from  the XNAT web page they will
be delivered as zips. **NOTE**: Only **one** MR session can be downloaded each time. On the XNAT web interface the files are organized in
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

##  Downloading non-imaging data

### List of Subjects, Gender, GA
The data release contains some non-imaging data, which can be directly
downloaded as an Excel spreadsheet by selecting ‘Spreadsheet’ from the
‘Options’ drop down menu from the table view page.  The data release
supplementary documentation can be directly downloaded by clicking on the
link ‘documentation: Data Release’ on the main table view page.

### Metadata 

Metadata file includes the following information.

Columns   |  Notes
:---------- | :----
`birth_age` | Gestational age at birth in weeks
`birth_weight` | Birthweight (kg)
`singleton` | Singleton / multiple status of the pregnancy
`scan_age` |  Gestational age at scan in weeks
`scan_head_circumference` |  Head circumference (cm)
`scan_number` | 1 for the first scan, 2 for the second
`radiology_score` |  The MRI scans were reviewed by a specialist perinatal<br /> neuroradiologist who scored each subject using the following scale:<br /> 1=Normal appearance for age<br /> 2=Incidental findings with unlikely significance for clinical<br /> outcome or analysis (e.g. subdural haemorrhage. Isolated<br /> subependymal cysts. Mild inferior vermis rotation)<br /> 3=Incidental findings with unlikely clinical significance but<br /> possible analysis significance (e.g. several punctate lesions<br /> or other focal white matter / cortical lesions not thought to be<br /> of clinical significance)<br /> 4=Incidental findings with possible clinical significance.<br /> Unlikely analysis significance (e.g. Isolated non brain <br /> anomaly for example in pituitary / on tongue) <br /> 5=Incidental finding with possible / likely significance for <br /> both clinical and imaging analysis (e.g. Major lesions within <br /> white matter cortex, cerebellum and or basal ganglia; small <br /> head / brain < 1 st centile) <br /> Q=Poor quality anatomical data 
`sedation` |  1 if the subject was sedated during the scan, 0 otherwise

The file can be downloaded from: [combined.tsv](
https://raw.githubusercontent.com/BioMedIA/dHCP-release-notes/master/rel02/combined_rel02.tsv)
