---
layout: post
title: Latent Space for Coastal Morphodynamic representation
date: 2026-11-20
description: spectral water, wetness and turbidity proxies as a first step towards a learned representation of the coast
tags: geomorphology ML
categories: work
thumbnail: assets/img/coastal_indi_cropped.png
---

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/coastal_indi_cropped.png" title="NDWI, wetness and turbidity proxies" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    a) NDWI, b) wetness and c) turbidity proxies for the same stretch of sandy coast.
</div>

The three panels show spectral proxies computed from the same satellite scene: the Normalized Difference Water Index (NDWI), a wetness proxy and a turbidity proxy. NDWI separates water (positive values) from dry land (negative values), so the land-water boundary and the shoreline stand out clearly. The wetness proxy picks up moisture across the beach and the nearshore, while the turbidity proxy highlights the suspended sediment and breaking waves in the surf zone. Together these layers describe the beach and nearshore in a compact form, and they are candidate inputs for learning a latent-space representation of coastal morphodynamics.
