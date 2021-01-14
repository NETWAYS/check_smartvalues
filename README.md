
# check_smartvalues

You want to monitor your HDD/SSD(s), here is a solution to do it, try it out.

### Features
 - prints performance data for inGraph ( and other solutions like Graphana, maybe in the near future )
 - unknown attribute autocorrection ( through smartvalues json database )
 - warning/critical thresholds for each separate key or group ( through smartvalues json config )
 - multi HDD/SSD scan ( you need only one execute to get them all, that plugin was designed as a multicheck )
 - low system footprint and a few perl modules as requirements ( most of them are core modules, or in the future a part of the core, maybe ... )
 - easy to use and to extend the database
 - reverse condition correction ( with a switch called `CR` in the json database )

### Usage

<pre><code>
# cd /path/to/check_smartvalues
# ./check_smartvalues -db check_smartvalues.db.json -c check_smartvalues.db.json -s -d 'megaraid,22 /dev/sda' -r
OK: [ 22 OK ] - [ 0 WARNING ] - [ 0 CRITICAL ] - [ 0 UNKNOWN ] in 0.163ms ( longoutput for details )
OK: on LSI MegaRAID - [ DeviceID 22 ] - #5 - Reallocated_Sector_Ct is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #9 - Power_On_Hours is [ 100 ] - [ w: 200, c: 300 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #12 - Power_Cycle_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #170 - Available_Reserved_Space is [ 100 / 010 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #171 - Program_Fail_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #172 - Erase_Fail_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #174 - Unexpected_Power_Loss is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #183 - Runtime_Bad_Block is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #184 - End-to-End_Error is [ 100 / 090 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #187 - Reported_Uncorrect is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #190 - Airflow_Temperature_Cel is [ 31 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #192 - Power-Off_Retract_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #199 - UDMA_CRC_Error_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #225 - Host_Writes is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #226 - Timed_Workload_Media_Wear is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #227 - Timed_Workload_Host_Read/Write _Ratio is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #228 - Power-off_Retract_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #232 - Available_Reservd_Space is [ 100 / 010 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #233 - Media_Wearout_Indicator is [ 043 ] - [ w: 35, c: 25 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #241 - Total_LBAs_Written is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #242 - Total_LBAs_Read is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 22 ] - #249 - Total_NAND_Writes is [ 100 ]
#
</code></pre>
<pre><code>
# cd /path/to/check_smartvalues
# ./check_smartvalues -c check_smartvalues.cfg.json -db check_smartvalues.db.json -di -d "megaraid,21 /dev/sda" -r -pd
WARNING: [ 21 OK ] - [ 1 WARNING ] - [ 0 CRITICAL ] - [ 0 UNKNOWN ] in 0.221s ( longoutput for details ) | 'megaraid,21_/dev/sda - Reallocated_Sector_Ct'=100%;0;0 'megaraid,21_/dev/sda - Power_On_Hours'=100%;200;300 'megaraid,21_/dev/sda - Power_Cycle_Count'=100%;0;0 'megaraid,21_/dev/sda - Available_Reserved_Space'=100%;0;0 'megaraid,21_/dev/sda - Program_Fail_Count'=100%;0;0 'megaraid,21_/dev/sda - Erase_Fail_Count'=100%;0;0 'megaraid,21_/dev/sda - Unexpected_Power_Loss'=100%;0;0 'megaraid,21_/dev/sda - Runtime_Bad_Block'=100%;0;0 'megaraid,21_/dev/sda - End-to-End_Error'=100%;0;0 'megaraid,21_/dev/sda - Reported_Uncorrect'=100%;0;0 'megaraid,21_/dev/sda - Airflow_Temperature_Cel'=29c;0;0 'megaraid,21_/dev/sda - Power-Off_Retract_Count'=100%;0;0 'megaraid,21_/dev/sda - UDMA_CRC_Error_Count'=100%;0;0 'megaraid,21_/dev/sda - Host_Writes'=100%;0;0 'megaraid,21_/dev/sda - Timed_Workload_Media_Wear'=100%;0;0 'megaraid,21_/dev/sda - Timed_Workload_Host_Read/Write _Ratio'=100%;0;0 'megaraid,21_/dev/sda - Power-off_Retract_Count'=100%;0;0 'megaraid,21_/dev/sda - Available_Reservd_Space'=100%;0;0 'megaraid,21_/dev/sda - Total_LBAs_Written'=100%;0;0 'megaraid,21_/dev/sda - Total_LBAs_Read'=100%;0;0 'megaraid,21_/dev/sda - Total_NAND_Writes'=100%;0;0 'megaraid,21_/dev/sda - Media_Wearout_Indicator'=033%;35;25
OK: on LSI MegaRAID - [ DeviceID 21 ] - #5 - Reallocated_Sector_Ct is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #9 - Power_On_Hours is [ 100 ] - [ w: 200, c: 300 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #12 - Power_Cycle_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #170 - Available_Reserved_Space is [ 100 / 010 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #171 - Program_Fail_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #172 - Erase_Fail_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #174 - Unexpected_Power_Loss is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #183 - Runtime_Bad_Block is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #184 - End-to-End_Error is [ 100 / 090 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #187 - Reported_Uncorrect is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #190 - Airflow_Temperature_Cel is [ 29 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #192 - Power-Off_Retract_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #199 - UDMA_CRC_Error_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #225 - Host_Writes is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #226 - Timed_Workload_Media_Wear is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #227 - Timed_Workload_Host_Read/Write _Ratio is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #228 - Power-off_Retract_Count is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #232 - Available_Reservd_Space is [ 100 / 010 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #241 - Total_LBAs_Written is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #242 - Total_LBAs_Read is [ 100 ]
OK: on LSI MegaRAID - [ DeviceID 21 ] - #249 - Total_NAND_Writes is [ 100 ]
WARNING: on LSI MegaRAID - [ DeviceID 21 ] - #233 - Media_Wearout_Indicator is [ 033 ] - [ w: 35, c: 25 ]
================= megaraid,21_/dev/sda info begin =================
Device Model:     INTEL SSDSC2BW120A4
Serial Number:    PHDA4102012P1207GN
LU WWN Device Id: 5 5cd2e4 000394ad1
Firmware Version: DC32
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
================= megaraid,21_/dev/sda info end ===================
#

</code></pre>

If you need to specify custom `-d` for smartctl command, here's an example
<pre><code>
./check_smartvalues -db ./check_smartvalues.db.json -c ./check_smartvalues.cfg.json -d "-d sat /dev/sdb"
</code></pre>


### Version

 - 0.4

### ToDo

 - rewrite to use threads for faster scans over SAS storage boxes ( is curently under development )
 - a better debug output ( a long running gag )
 - a better documentation and usage descriptions/examples ( there where some improvments with 0.4 )
 - better performance data labels ( it's hard to make that better, curently no ideas )

## Changelog

 - [bugfix/feature] ( see history )
   - added some new devices and tresh configs
   - fixed some typos and also removed that string chainings in multiline output ( i replaced them with heredoc )
   - added new --deviceinfo switch, his result is added to longoutput
   - backward compatibility with perl 10.0.1 ( got old squeeze )

 - [bugfix/feature] ( see history )
   - added a new samsung ssd to database and config with some usefull threshhold's
   - fixed a bug which corrects the condition between normal and raw values
   - fixed the verbose debug output of return value condition description

 - [bugfix/critical] when the normalized value is in warning but not critical, the critical elsif condition overrides always the warning $retval, so the check ( eg. ID ) will never be in a warning state
 - [initial release] version 0.1
