snapster
========

flexible btrfs snapshot script

 * [Background - Why does this script exist](#Background)
 * [Parameters - Script Parameters](#Parameters)

##Background

I was in need for script to create periodic snapshots of a btrfs filesystem for use with the [shadow_copy2](http://www.samba.org/samba/docs/man/manpages/vfs_shadow_copy2.8.html) vfs module.

##Parameters

The script works with commandline parameters. The function of each of the parameters is explained below:

###-m
*Mount* | A "mount" is a filesystem mountpoint. The script wil check for a btrfs filesystem on this location.

  example: /home

###-t
*Target* | The target is the location within the btrfs filesystem where the snashots will be located. This directory will be create if it doesn't exist. this should be a path relative to the "mountpoint", not an absolute path.

  example: .snaps
  
###-s
*Set* | A set is a group of snapshots.

  example: weekly
  
###-k
*Keep* | A number of how many snapshots need to be kept

  example: 7

##Examples

Create a snapshot a day, and keep them for a week: `snapster -m /home -t .snaps -s daily -k 7`
Create a snpashot every 15 minutes and keep 4 of them: `snapster -m /home -t .snaps -s 15_minutes -k 4`

##TODO
* Make everything more robust and secure?
* Readonly snapshots are forced, make that optional
* Add more code comments
