
# check_smartvalues

You want to monitor your HDD/SSD(s), her is a solution to do it, try it out.
 
### Features
 - prints performance data for inGraph and other solutions like Graphana or someting else ...
 - unknown attribute autocorrection ( through smartvalues json database )
 - warning/critical threshholds for each separatet key or groups ( through smartvalues json config )
 - multi HDD/SSD scan ( you need only once execute to get them all )
 - low system footprint and a few perl modules as prerequisites ( most of them are core modules, or in the future a part of the core, maybe ... )
 - easy to use and to extend the database
 - reverse condition correction ( with a switch in the json database )

### Usage

<pre><code>
# cd /path/to/check_smartvalues
# ./check_smartvalues -db check_smartvalues.db.json -c check_smartvalues.db.json -s -d 'megaraid,22 /dev/sda'
OK: [ 22 OK ] - [ 0 WARNING ] - [ 0 CRITICAL ] - [ 0 UNKNOWN ] in 0.163578987121582ms ( for details pls take a look in longoutput )
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

### Version

 - 0.3

### ToDo

 - rewrite to use threads for faster scans over SAS storage boxes
 - a better debug output
 - a better documentation and usage descriptions/examples
 - better performance data labels

## Changelog

 - [bugfix/feature] ( see history )
   - added a new samsung ssd to database and config with some usefull threshhold's
   - fixed a bug which corrects the condition between normal and raw values
   - fixed the verbose debug output of return value condition description

 - [bugfix/critical] when the normalized value is in warning but not critical, the critical elsif condition overrides always the warning $retval, so the check ( eg. ID ) will never be in a warning state 
 - [initial release] version 0.1

## Git history
<pre><code>
commit bbd16733f55a9631413690ff12466fb9cff4636d
Author: Enrico Labedzki <enrico.labedzki@root.center>
Date:   Thu Oct 29 17:28:55 2015 +0100

    [bugfix] when the normalized value is in warning but not critical, the critical elsif condition overrides always the warning $retval, so the check ( eg. ID ) will never be in a warning state

commit 922d291d6bd895c23167e6f58acfbb66dbfbc17f
Author: Enrico Labedzki <enrico.labedzki@netways.de>
Date:   Tue Aug 11 13:44:37 2015 +0200

    [nms] changed project name

commit ebf9b6d6294b0b0dcf33213c0bd2d513a91e6d61
Author: Enrico Labedzki <enrico.labedzki@netways.de>
Date:   Tue Aug 11 12:56:00 2015 +0200

    [nms] added a usage example

commit 1b279297920ceea8237e62c036f7de56d395e573
Author: Enrico Labedzki <enrico.labedzki@netways.de>
Date:   Tue Aug 11 12:40:37 2015 +0200

    [nms] changed plugin anchor

commit 0b6296c410136ecca04887c2489d6dc6320adc93
Author: Enrico Labedzki <enrico.labedzki@netways.de>
Date:   Tue Aug 11 11:46:31 2015 +0200

    [nms] initial release/commit
</code></pre>
