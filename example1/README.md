![VEL](radar.HawkEye.20170408003432.VEL.png =100x100)

This example uses data from ... 
converts it to CfRadial format (RadxConvert), 
print the data for a quick sanity check (RadxPrint),
displays the data using HawkEye, then saves the display as a PNG image.

1. Grab a NEXRAD data file from 
https://s3.amazonaws.com/noaa-nexrad-level2/index.html

I clicked on  KARX20170408_003319_V06 and it downloaded the data file.

2. ./RadxConvert -f /Users/brenda/Downloads/KARX20170408_003319_V06

3. ./RadxPrint -f output/20170408/cfrad.20170408_003432.229_to_20170408_004300.205_KARX_Surveillance_SUR.nc

# notice these fields ...

    field[0]: REF
    field[1]: VEL
    field[2]: SW
    field[3]: REF_s1
    field[4]: REF_s3

# add them to the HawkEye.params file ...

4. get the color scales needed by HawkEye 

$ git clone https://github.com/NCAR/lrose-displays

$ ./HawkEye -print_params > $HOME/example1/HawkEye.params

# edit the params file ...
# set location of the color scales
color_scale_dir = "$(HOME)/ncar/work/git/lrose-displays/color_scales";
# add the fields 
# there are many other settings in the parameter file - make this a link
5. start HawkEye to display the data ...

$ ./HawkEye -params ~/test_area/hawkeye/HawkEye_KARX.archive -f output/20170408/cfrad.20170408_003432.229_to_20170408_004300.205_KARX_Surveillance_SUR.nc

6. Save some images as PNG files
