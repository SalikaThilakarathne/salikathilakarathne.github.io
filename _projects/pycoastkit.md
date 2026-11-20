---
layout: page
title: pycoastkit, a Python toolkit for sandy coasts
description: open-source package for wave storms, storm clusters, beach profiles, erosion, recovery and vulnerability.
img: assets/img/pycoastkit_storms.png
importance: 0
category: work
related_publications: thilakarathne_wave_2025
---

`pycoastkit` is an open-source Python package that collects the methods from my research on storms and sandy beaches into one tested, documented toolkit.

<div class="row mt-3">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/pycoastkit_storms.png" title="pycoastkit storm timeline" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Storms detected with <code>pck.find_storms</code> and drawn with <code>pck.plot.plot_storm_timeline</code> (synthetic wave record). Storms close together form a cluster (red); the others are individual storms (grey).
</div>

**What it does**

- **Storms**: finds storms in a significant wave height record with two thresholds, a minimum duration and an independence gap, then groups them into storm clusters.
- **Beach profiles**: shoreline position, sand volume, slopes and sandbars from cross-shore profile surveys.
- **Impacts and recovery**: erosion caused by each storm event and how much of it the beach recovers afterwards.
- **Vulnerability**: beach vulnerability and susceptibility indices, and return periods.
- **Hasaki data**: downloads and quality-controls the NOWPHAS Kashima wave record and reads the HORS beach profiles.

**Install**

```bash
pip install pycoastkit
```

```python
import pycoastkit as pck

storms = pck.find_storms(waves, pck.StormCriteria(1.5, 2.5, min_duration_h=6, min_separation_h=48))
events = pck.storm_clusters(storms)
```

**Links**

- Documentation: [salikathilakarathne.github.io/pycoastkit](https://salikathilakarathne.github.io/pycoastkit/)
- PyPI: [pypi.org/project/pycoastkit](https://pypi.org/project/pycoastkit/)
- Source code: [github.com/SalikaThilakarathne/pycoastkit](https://github.com/SalikaThilakarathne/pycoastkit)

The storm and clustering methods are described in the paper below.
