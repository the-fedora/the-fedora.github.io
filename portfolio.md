---
layout: page
title: Portfolio
permalink: /portfolio/
author: the.fedora
---

<script data-goatcounter="https://the-fedora.goatcounter.com/count"
        async src="//gc.zgo.at/count.js"></script>

## Maps
This is a collection of some of the maps I have made, showcasing specific techniques, interesting datasets and visualizations, and other things I thought worth collecting in one place. Most of these were published at one time or another on Instagram, Facebook, or my old webpage, but they have not been collected wholly in one place until now.

Most of these were made with [QGIS](https://qgis.org) and [R](https://www.r-project.org/), some with [GRASS](https://grass.osgeo.org/). A few have also had additional compositing with [Inkscape](https://inkscape.org/).

All this is still very much a work-in-progress, and I'll be cleaning up maps, adding more maps, and some explainers as I fill things out. All maps © me, made with open data from various source including USGS and [OpenStreetMap](https://www.openstreetmap.org/). Any businesses or entities used for informational purposes only, no endorsement implied.

<div class="image-gallery" style="width:100%; margin:auto; columns:3">
  {% for file in site.static_files %}
    {% if file.path contains '/images/portfoliomaps' %}
      {% if file.extname == '.jpg' or file.extname == '.jpeg' or file.extname == '.png' or file.extname == '.webp' %}
      <a href="{{ file.path | relative_url }}" target="_blank" rel="noopener noreferrer">
        <img src="{{ file.path | relative_url }}" alt="{{ file.name }}" class="gallery-thumb" />
        </a>
      {% endif %}
    {% endif %}
  {% endfor %}
</div>
