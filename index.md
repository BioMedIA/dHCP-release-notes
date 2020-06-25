---
---

## Third Data Release

We would like to announce the second release of data as part of the Developing
Human Connectome Project (dHCP) – an ERC-funded collaboration between
King’s College London, Imperial College London and University of Oxford.

This is the project’s second open access data release which consists of
images of 558 neonatal subjects. The imaging data includes structural imaging,
structural connectivity data (diffusion MRI) and functional connectivity
data (resting-state fMRI). This data release comes with minimal accompanying
metadata: gender, age at birth, age at scan, birthweight, head circumference
and radiology score. More specific information about the available data
can be found in the [data organisation notes](organisation.html). To
access the data you will be required to agree to a simple [data sharing
agreement](http://www.developingconnectome.org/open-access-dhcp-data-terms-of-use-version-4-0_2019-05-23/)
and will then be provided with access routes to two different modes of
data download.

We invite colleagues in the field to explore and
[feedback](https://neurostars.org/tags/developing-hcp) on the value and
characteristics of the image dataset. The image data have been processed
using analysis pipelines that are subject to further development.  If you
use this data or the pipelines please cite the appropriate publications as
detailed in the [How to cite](cite.html) notes.

The project to date has successfully completed over 800 neonatal scans and
over 250 fetal scans, and further data is still being collected. Further
data releases are planned - these will be announced on the dHCP website
when they are ready.

## News

<ul class="blog-index">
  {% for post in site.posts %}
    <li>
      <span class="date">{{ post.date }}</span>
      <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
