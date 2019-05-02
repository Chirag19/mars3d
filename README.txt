export PATH=/Library/Frameworks/GDAL.framework/Programs:$PATH

Conver PDS img to tif 
gdal_translate img/DTEEC_019590_2265_020078_2265_A01.IMG tif/DTEEC_019590_2265_020078_2265_A01.tif

Get Info tif
gdalinfo -mm tif/DTEEC_019590_2265_020078_2265_A01.tif


Convert tif to png with elevation information in grey values
gdal_translate -scale -4028 -3916 0 255 -outsize 200 200 -of PNG tif/DTEEC_019590_2265_020078_2265_A01.tif png/DTEEC_019590_2265_020078_2265_A01.png

Convert tif to bin 
gdal_translate -scale -4028 -3916 0 65535 -ot UInt16 -outsize 200 200 -of ENVI tif/DTEEC_019590_2265_020078_2265_A01.tif bin/DTEEC_019590_2265_020078_2265_A01.bin

//Create hillshades
gdaldem hillshade -combined tif/DTEEC_019590_2265_020078_2265_A01.tif tif/DTEEC_019590_2265_020078_2265_A01-hillshade.tif

//Color
gdaldem color-relief tif/DTEEC_019590_2265_020078_2265_A01.tif png/color-relief.txt png/jDTEEC_019590_2265_020078_2265_A01.tif




Workflow
gdal_translate -scale -4028 -3916 0 255 -outsize 200 200 -of PNG tif/DTEEC_019590_2265_020078_2265_A01.tif png/DTEEC_019590_2265_020078_2265_A01.png

gdal_translate -scale -4028 -3916 0 65535 -ot UInt16 -outsize 200 200 -of ENVI tif/DTEEC_019590_2265_020078_2265_A01.tif bin/DTEEC_019590_2265_020078_2265_A01.bin

gdaldem hillshade -combined tif/DTEEC_019590_2265_020078_2265_A01.tif tif/DTEEC_019590_2265_020078_2265_A01-hillshade.tif
gdal_translate -scale 0 255 0 255 -outsize 50% 50% -of PNG tif/DTEEC_019590_2265_020078_2265_A01-hillshade.tif png/DTEEC_019590_2265_020078_2265_A01-hillshade.png



PNG 990 3774
IMG 7926 30195

gdal_translate -scale 0 255 0 65535 -outsize 79 300 -ot UInt16 -of ENVI H0334_0001_ND3.tif H0334_0001_ND3.bin 
gdal_translate -scale 0 255 -outsize 7926 30195 -of PNG H0334_0001_ND3.tif H0334_0001_ND3.png 

var geometry = new THREE.PlaneGeometry(widthFP, heightFP, 78,299);



