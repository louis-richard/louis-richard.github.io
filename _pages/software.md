---
layout: archive
title: "Software"
permalink: /software/
author_profile: true
---

pyrfu
=====

**pyrfu** (Python RymdFysik Utilities) is an open-source Python package for in-situ space plasma data analysis. It covers the Magnetospheric Multiscale (MMS) mission, from data access to particle distributions and wave analysis, as well as general plasma physics tools. I created, develop, and maintain pyrfu which is distributed under the MIT licence.

[Documentation](https://pyrfu.readthedocs.io/en/){:target="_blank"} · [Source code on GitHub](https://github.com/louis-richard/irfu-python){:target="_blank"} · [PyPI](https://pypi.org/project/pyrfu/){:target="_blank"} · [Zenodo](https://doi.org/10.5281/zenodo.10678695){:target="_blank"}

Features
--------

* **MMS data access:** find, download and load MMS data from a local archive, the SDC or AWS as `xarray` time series.
* **Particle distributions:** FPI skymaps, omni-directional and pitch-angle distributions, projections, reduced 1D and 2D distributions, and moments.
* **Waves and polarization:** wavelet and Fourier spectra, polarization analysis, Poynting flux, and four-spacecraft dispersion relations.
* **Multi-spacecraft methods:** curlometer current density, gradients, timing velocities, and four-spacecraft averages.
* **Coordinates and time series:** geophysical coordinate transformations, field-aligned and minimum variance frames, filtering and resampling.
* **Plotting:** time series, spectrograms and particle distribution plots with matplotlib.

Getting started
---------------

```bash
python -m pip install pyrfu
```

Load and plot the MMS magnetic field from a local data archive:

```python
import matplotlib.pyplot as plt

from pyrfu import mms
from pyrfu.plot import plot_line

tint = ["2019-09-14T07:54:00.000", "2019-09-14T08:11:00.000"]

mms.db_init(default="local", local="/path/to/mms/data")
b_xyz = mms.get_data("b_gse_fgm_srvy_l2", tint, 1)

f, ax = plt.subplots(figsize=(9, 3))
plot_line(ax, b_xyz)
ax.legend(["$B_x$", "$B_y$", "$B_z$"], ncol=3)
ax.set_ylabel("$B$ [nT]")
```

More examples, from particle distributions to wave analysis, are in the [example gallery](https://pyrfu.readthedocs.io/en/latest/examples/index.html){:target="_blank"}.

Citing pyrfu
------------

If you use pyrfu in your work, please cite it using its Zenodo DOI:

L. Richard, Yu. V. Khotyaintsev, A. Vaivads, D. B. Graham, C. Norgren, A. Johlander, "Python RymdFysik Utilities (PyRFU): An Open-Source Python Package for Advanced In-Situ Space Plasma Analysis." Zenodo, 2024. [doi:10.5281/zenodo.10678695](https://doi.org/10.5281/zenodo.10678695){:target="_blank"}
