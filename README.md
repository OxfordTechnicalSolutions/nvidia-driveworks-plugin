This repository contains the compiled OxTS plugin files for the nvidia driveworks sdk.  It is important that you use the correct file for the driveworks version that you are using.  For more information on the nvdia driveworks sdk please see:

https://developer.nvidia.com/drive/driveworks

Note, this plugin makes use of filtered accelerations which will have to be enabled when you configure your OxTS unit.  For a general guide on configuring an OxTS unit please see:

https://www.oxts.com/webinars/webinar-navconfig/

The following commands show how to use the OxTS gps and imu logger with the sample loggers from the Nvidia driveworks sdk (paths should be altered based on your install and ip address based on your configuration):

While recording data:
/path/to/driveworks/sample_gps_logger --driver=gps.custom --params=protocol=udp,ip=195.0.0.1,port=3000,decoder-path="path/to/liboxts_gnss_plugin.so"
/path/to/driveworks/sample_imu_logger --driver=imu.custom --params=protocol=udp,ip=195.0.0.1,port=3000,decoder-path="path/to/liboxts_imu_plugin.so"

While replaying data:
/path/to/driveworks/sample_gps_logger --driver=imu.virtual --params=protocol=file,file=path/to/recorded/data.bin,ip=195.0.0.1,port=3000,decoder-path="path/to/liboxts_gnss_plugin.so"
/path/to/driveworks/sample_imu_logger --driver=imu.virtual --params=protocol=file,file=path/to/recorded/data.bin,ip=195.0.0.1,port=3000,decoder-path="path/to/liboxts_imu_plugin.so"

Both the imu and gps plugin can be used at the sametime if desired.