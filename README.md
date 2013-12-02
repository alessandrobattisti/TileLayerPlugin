# TileLayerPlugin

TileLayerPlugin is a QGIS plugin to view tile maps.

## How to use?

After installing this plugin, you can add tile layers into map canvas from the layer menu or the manage layers toolbar. Before adding layer information by yourself, you can use only tile frame layers. You can add available layers by writing a file in the format described below and setting the folder that the file exists as external layer directory.

A few layer styles can be changed in the layer properties dialog. You can set sufficient cache size (in kilobytes) in the Network/Cache Settings of the Options dialog in order to make effective use of cache.

### Limitations
With this plugin, you can view only web mercator projection tile maps. Tile layers don't appear when the coordinate reference system is not EPSG:3857 or EPSG:900913. 

### Layer information file format
Layer information file is a text file. Each line has information for a tile layer, and fields are separated with tab character. The file encoding is UTF-8.

**Line format is:**  
`title  providerName  url  yOriginTop  zmin  zmax  xmin  ymin  xmax  ymax`

**Description of fields:**  
Required
* title: Layer title
* providerName: Service provider name
* url: URL of tile map. Special strings "{x}", "{y}" and "{z}" are replaced with tile coordinates and zoom level that are calculated with current map view.

Options
* yOriginTop: Origin location of tile matrix. 1 if origin is top (Google Maps compatible), 0 if origin is bottom (TMS). Default is 1.
* zmin, zmax: Minimum/Maximum value of zoom level. Default values: zmin=10, zmax=15.
* xmin, ymin, xmax, ymax: Layer extent in latitude/longitude. Note: Valid range of y in web mercator is from about -85.05 to about 85.05.

You should correctly set zmin, zmax, xmin, ymin, xmax and ymax in order not to send unnecessary requests to tile map servers.

### An example of layer information file
* **For a tile map generated by gdal2tiles.py**  
slope.tsv  
`slope	local	file:///d:/tilemaps/slope/{z}/{x}/{y}.png	0	6	13	130.5	33.6	135.0	36.0`

Note: Use tab character to separate fields!

## License
TileLayerPlugin is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

_Copyright (c) 2013 Minoru Akagi_
