# run_download_DEM
#### Script for preparing DEM data assisting InSAR processing with GAMMA or ISCE. 

It will download either the NASADEM (srtm) OR Copernicus 30m resolution DEM with a geographic AOI box. 

### Usage

```bash
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
run_download_DEM.sh: Script to download the 30-m NASADEM or Copernicus DEM and prepare                                                                      
the input dem file for InSAR processing with ISCE or GAMMA                                                                                      
v1.0, Feb. 10, 2022, Dr. Xiaowen Wang @ [UCD & SWJTU]                        
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
usage: run_download_DEM.sh <work_path> <dem_dir> <box> <soft_flag> [out_name]
                                                                              
input parameters:                                                             
work_path:         the work path where a DEM folder will be created, e.g., $PWD  
range_aoi:         the lat-lon box of AOI (<west>/<east>/<south>/<north>)     
proc_flag:         which DEM source will be used: [default:0]
                       0---> download new NASADEM (SRTM) from aws
                       1---> download new Copernicus DEM from aws
                       2---> use the existing DEM (*.tif) in the *dem_tiff* folder
soft_flag:         the dem will be convert to specific format: [default:0]
                       0--->ISCE; 1--->GAMMA
out_name           the name for writting down the final dem product [default: dem]
 
**Note**:          if the proc_flag is set to be 2, the Geotiff DEM files...
                   should be placed in the folder: $work_path/dem/dem_tiff
 
Example:           run_download_DEM.sh $PWD -2.12/-1.35/37.23/38.32
                   run_download_DEM.sh $PWD -2.12/-1.35/37.23/38.32 0 0 dem_name
                   run_download_DEM.sh $PWD -2.12/-1.35/37.23/38.32 1 1 dem_name
```

- For the detailed description of NASADEM, go

https://earthdata.nasa.gov/esds/competitive-programs/measures/nasadem

- For the detailed description of Copernicus DEM, go

 https://spacedata.copernicus.eu/web/cscda/dataset-details?articleId=394198 


### Notes:

1. Before running this script you have to install the GDAL and AWS CLI tool.  

   Check the installation of AWS at https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

> For example, use the following commands to install aws on a linux OS.  

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

****************************

**Dataset Acknowledgement**

OpenTopography Portal (https://opentopography.org/) is acknowledged for accessing the data. 

- Copernicus DEM [DOI: https://doi.org/10.5069/G9028PQB]

\# https://portal.opentopography.org/datasetMetadata?otCollectionID=OT.032021.4326.1

- NASADEM (srtm) [DOI: https://doi.org/10.5069/G93T9FD9]

\# https://portal.opentopography.org/datasetMetadata?otCollectionID=OT.032021.4326.2

***Copyright Dr. Xiaowen Wang @ (UCD & SWJTU), 10/02/2022***
