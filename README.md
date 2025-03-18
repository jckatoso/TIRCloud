# TIRCloud

## Overview
TIRCloud dataset was built for image classification of cloud coverage on spaceborne TIR data.
Image patches were clipped from satellite images acquired by ASTER TIR band 13, Landsat 8 TIRS band 10, and Landsat 9 TIRS-2 band 10. Then each of them was labeled as cloudy (0) or clear (1).
Satellite images were globally sampled for land, whereas data over water bodies were selectively corresponding to 14 water temperature measurement sites in lakes and bays in Japan.
In total, the dataset contains 920,489 images with a label, composed of 518,336 daytime clear sky condition images, 786 nighttime clear sky condition images, 400,577 daytime cloudy sky condition images, and 790 nighttime cloudy sky condition images.

## Data sources
- ASTER TIR band 13 L3A
- Landsat 8 TIRS band 10 pre-collection, collection 1 or collection 2
- Landsat 9 TIRS-2 band 10 collection 2

## Image data format
- File format: Geotiff 
- Data type: float32
- Dimension: 160 x 160 x 1
- DN value: TOA spectral radiance (W/m2 sr micron)
- Spatial resolution: 90m
- Map projection: LONLAT (ASTER), UTM (Landsat 8/9)

## Download
The dataset can be downloaded from here (44 GB) .
Or type the following in the terminal.

	$ wget http://data.airc.aist.go.jp/TIRCloud/TIRCloud.tar.gz
	$ tar -zxvf TIRCloud.tar.gz

## directory configuration
	TIRCloud/
		clear/
			day/
				aster/
					land/
						[scene id]/
							[scene id]_[ulx]_[uly].tif
					waterbody/
						[site name]/
							[scene id]_[site name].tif
				l8/
					(same structure as "aster")
				l9/
					(same structure as "aster")
			night/
				aster/
					(same structure as "day/aster")
		cloudy/
			(same structure as "clear")
	
		datalist.csv
	
	
file name definition
- scene id for ASTER: [path]_[row]_[date time]
- scene id for Landsat 8/9: scene id, product id, [path]_[row]_[year DOY], or [LC08 or LC09]_[path][row]_[date]
- ulx, uly: pixel coordinates of the cripped images in the original scenes
- site name:
  
	adogawaoki  asooki     kamayaoki  mikawa-buoy1  mikawa-buoy3  ogawarako  shinjiko
	akashi      hannanoki  kobeport   mikawa-buoy2  nakaumi       osakaport  sumoto

 
datalist.csv describes a list of randomly sorted all training data, path to the image file and classification code (0: cloudy, 1: clear), formatted as:

	cloudy/day/l8/land/LC80060552017315LGN00/LC80060552017315LGN00_1280_2240.tif,0
	cloudy/day/aster/land/098_175_20010112010045/098_175_20010112010045_160_480.tif,0
	clear/day/aster/land/104_205_20010311014058/104_205_20010311014058_160_160.tif,1
	cloudy/day/l8/land/LC82250702021340LGN00/LC82250702021340LGN00_1760_1600.tif,0
	clear/day/l8/land/LC81120372018069LGN00/LC81120372018069LGN00_640_480.tif,1
	:
	clear/day/l8/land/LC81830452020092LGN00/LC81830452020092LGN00_2080_1120.tif,1

## Acknowledgement
This dataset is based on results obtained from a project commissioned by the New Energy and Industrial Technology Development Organization (NEDO).
The dataset was generated from ASTER data provided by AIST and Landsat 8/9 data prvided by USGS.
