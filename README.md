
# OXTS NVIDIA DriveWorks 7.0.3 Plugin

This repository contains the compiled AArch64OXTS plugin files for [NVIDIA Drive OS](https://developer.nvidia.com/drive/driveworks)  systems. This plugin converts IMU and GNSS data from OXTS INS devices can be used within the [NVIDIA DriveWorks](https://developer.nvidia.com/drive/driveworks) ecosystem.


## Contents

Two plugins are provided:

| Plugin | File | Purpose | NVIDIA DriveWorks SDK version |NVIDIA DRIVE platform Compatibility | Supported OXTS devices |
| --- | --- | --- | --- | --- |  --- |
| GNSS | `liboxts_gnss_plugin.so` | Decodes OXTS NCOM data into DriveWorks GPS frames | v7.03 |DRIVE AGX Thor| RT3000v4, RT3000v3, RT1003v2, AV200, xNAV650, xRED|
| IMU | `liboxts_imu_plugin.so` | Decodes OXTS NCOM data into DriveWorks IMU frames | v7.03|DRIVE AGX Thor | RT3000v4, RT3000v3, RT1003v2, AV200, xNAV650, xRED|


It is important that you use the correct file for the driveworks version that you are using.  For more information on the nvdia driveworks sdk please refer to the [NVIDIA DriveWorks Documentation](https://developer.nvidia.com/drive/driveworks) 

## INS Configuration 
This plugin makes use of filtered accelerations which will have to be enabled when you configure your OxTS unit.  For a general guide on configuring an OxTS unit please see this [OXTS webinar](https://www.oxts.com/webinars/webinar-navconfig/)

The acceleration filter configuration options can be found in NavConfig under the advanced tab. 

## Usage 

The following shows how to use the OxTS gps and imu logger with the sample loggers from the Nvidia driveworks sdk.

### Uploading plugin files to NVIDIA DRIVE hardware

Clone this repo onto the NVIDIA DRIVE hardware. 

Alternatively, you can FTP or SCP the plugin files onto NVIDIA machine.


### Recording Data 

GNSS

```bash
*/path/to/driveworks/sample_gps_logger* --driver=gps.custom --params=protocol=udp,ip=*IP address of your unit*,port=3000,decoder-path="path/to/liboxts_gnss_plugin.so"
```
IMU
```bash
*/path/to/driveworks/sample_imu_logger* --driver=imu.custom --params=protocol=udp,ip=*IP address of your unit*,decoder-path="path/to/liboxts_imu_plugin.so"
```

### Replaying Data

GNSS

```bash
*/path/to/driveworks/sample_gps_logger* --driver=imu.virtual --params=protocol=file,file=path/to/recorded/data.bin,ip=*IP address of your unit*,port=3000,decoder-path="path/to/liboxts_gnss_plugin.so"
```
IMU
```bash
*/path/to/driveworks/sample_imu_logger* --driver=imu.virtual --params=protocol=file,file=path/to/recorded/data.bin,ip=*IP address of your unit*,port=3000,decoder-path="path/to/liboxts_imu_plugin.so"
```

Both the imu and gps plugin can be used at the sametime if desired.

# Contact and Support

If you have any issues with the plugin please submit an [issue here](https://github.com/OxfordTechnicalSolutions/nvidia-driveworks-plugin/issues). 
