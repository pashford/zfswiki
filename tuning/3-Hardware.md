# Hardware

A ZFS pool is constructed of one or more VDEVs (Virtual DEVices).  These VDEVs can be any of the following:
* Single drive
* Multiple Mirrored drives
* Multiple drives in a RAID-Z array

These VDEVs can be allocated to any of the following specific uses:
* General data
* Logging
* Caching
* Metadata/DDT/Small files (expected to be released in ZFS 0.8)

## General Data

In general, the performance of a pool is limited by the number of VDEVs in that pool.  All else being the same, increasing the number of VDEVs will usually increase throughput.  As with all generalizations, there are always exceptions.

## Logging

ZFS uses logging to reduce delays for synchronous writes.

Logging in ZFS is done through the use of a *ZIL* (ZFS Intent Log).  If there is no dedicated log device for a pool, then the ZILs for the file-system will be distributed among the General Data VDEVs in that pool.

ZFS will not have more than one outstanding write on a drive.  Because of this, the overall throughput of the logging drive(s) isn't the limiting factor for ZFS synchronous writes; latency is.

## Caching

The main cache for ZFS is the *ARC* (Adaptive Replacement Cache), which is stored in memory.  ZFS supports a second level of ARC, called an *L2ARC* on drives.

