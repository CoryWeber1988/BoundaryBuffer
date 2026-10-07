# Field Boundary Buffer

A free, browser-based tool that takes an existing field boundary and physically grows or shrinks it by a distance you choose, producing a new boundary with the original attributes preserved.

Recorded boundaries often leave too little room inside for different agricultural equipment, because machines have physical dimensions outside their working area (turning, headlands, trailing implements, obstacles). Field Boundary Buffer creates an adjusted polygon, smaller or larger than the original, to account for that clearance. Exterior polygons and interior polygons (wetlands, buildings, rock piles) are handled together.

Everything runs locally in your browser. Your files are never uploaded anywhere.

**Live tool:** `https://<your-username>.github.io/<repository-name>/`

## Features

- Leaflet map with Esri World Imagery (default), Esri Streets, Esri Topographic, OpenStreetMap, OpenTopoMap and USGS Imagery backgrounds
- Loads shapefiles (`.zip`, or `.shp` + `.dbf` + `.prj` selected together), KML and KMZ, by file picker or drag and drop
- Automatic projection detection from the `.prj`, with manual assignment by EPSG code or proj4 string
- Exterior and interior polygon detection (polygons inside others become interior) with a per-polygon override
- Total area with interior polygons subtracted from exterior ones, plus a per-polygon area list
- Imperial (default, acres) or metric (hectares), switchable at any time with all values updating
- Buffer in feet, inches, centimetres or metres, positive to grow and negative to shrink
- Buffering is done after re-projecting to a metre-based projection: the recommended local UTM zone by default, with NAD83 UTM, Web Mercator and custom EPSG options
- Original (blue) and adjusted (orange) boundaries overlaid on the map, with adjusted area and percent change
- Export to shapefile (default), KML, KMZ, GeoJSON and ISOXML, in WGS 84 (EPSG:4326) by default, with an option to append the buffer size to the file name
- Original attribute columns carried through, plus a `Buffer_ft`, `Buffer_in`, `Buffer_cm` or `Buffer_m` column with the signed adjustment
- Reset buttons for each step, a Reset session button, and the ability to load a new file while keeping your settings
- Hideable, scrollable sidebar, light and dark modes, desktop and mobile browsers

See [`help.html`](help.html) for the full guide to every feature.

## Using it

1. Open the live page (or `index.html` locally in a browser) and read the disclaimer.
2. Load a boundary file.
3. Check the polygon types, enter the buffer size and click **Apply buffer**.
4. Check the result against the imagery, then export.

An internet connection is needed for the map tiles and the supporting libraries.

## Publishing on GitHub Pages

1. Create a repository and upload every file in this folder to the root of the default branch.
2. In the repository go to **Settings, Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your default branch and the `/ (root)` folder, then save.
4. After a minute or two the tool is available at `https://<your-username>.github.io/<repository-name>/`.

The `.nojekyll` file tells GitHub Pages to serve the files as they are. No build step is needed.

## Files

| File | Purpose |
|---|---|
| `index.html` | The tool (a single self-contained page) |
| `help.html` | Help guide covering every feature |
| `README.md` | This file |
| `LICENSE` | GNU General Public License v3 |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll processing |

## Disclaimer

**Use at your own risk.** You are responsible for the accuracy of any output file created with this tool and for verifying that it does not cross any obstacles. Using this tool means you assume all responsibility and liability for its accuracy and for any issues that occur from using the tool and its exported files. The developer assumes and accepts no responsibility or liability.

The accuracy of the original boundary may not be perfectly preserved by this process, and a buffered boundary is never more accurate than its source. Check your file's attributes for anything indicating the source recording GPS accuracy (for example fix type, HDOP, or differential correction source). Verify all outputs in your own equipment and software before field use.

This software is provided "as is", without warranty of any kind, express or implied, including but not limited to merchantability, fitness for a particular purpose and non-infringement. Nothing here is agronomic, engineering, surveying or legal advice.

## License

Copyright (C) 2026 Cory Weber, Cory Weber Ag Tech.

This program is free software: you can redistribute it and/or modify it under the terms of the [GNU General Public License](LICENSE) as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the license for details.

## Third-party libraries and data

Loaded from public CDNs, not modified or bundled:

- [Leaflet](https://leafletjs.com) (BSD-2-Clause)
- [proj4js](https://proj4js.org) (MIT)
- [JSZip](https://stuk.github.io/jszip/) (MIT or GPLv3)
- [JSTS](https://github.com/bjornharrtell/jsts) (Eclipse Public License 2.0 / Eclipse Distribution License 1.0)

Map imagery and data come from Esri, OpenStreetMap contributors, OpenTopoMap and the USGS, each under their own terms of use. Please respect those terms and do not use the tool to bulk download tiles.

## Developer

Developed by Cory Weber, Cory Weber Ag Tech, Ontario, Canada, and built with Claude (Anthropic).
Contact: coryweber1988@gmail.com
