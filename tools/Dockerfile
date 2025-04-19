FROM ghcr.io/osgeo/gdal
# docker image containing all tools in order to transform a GeoTIFF into a PNG terrain tileset

LABEL MAINTAINER=thomas.halwax@syncpoint.io

ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8
## install pip3 and Mapbox's RasterIO (rio)
## install plugins for rio from https://github.com/mapbox/rasterio/wiki/Rio-plugin-registry
RUN apt-get -y update && apt-get install -y --fix-missing python3-pip vim proj-bin \
    && pip3 install rasterio --break-system-packages \
    && pip3 install rio-rgbify --break-system-packages \
    && pip3 install rio-mbtiles --break-system-packages \
    && pip3 install mbutil --break-system-packages \
    && apt-get clean \
    && wget https://github.com/protomaps/go-pmtiles/releases/download/v1.27.2/go-pmtiles_1.27.2_Linux_x86_64.tar.gz \
    && tar zxf go-pmtiles_1.27.1_Linux_x86_64.tar.gz \
    && mv pmtiles /usr/local/bin/