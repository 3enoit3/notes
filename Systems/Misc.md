# RAID (Redundant Array of Inexpensive Disks)
Storage virtualization
## Terminology
* **Striping**: segmenting sequential data (like files) on different storage devices. Useful when processing is faster than individual device accesses
* **Mirroring**: replication of logical disks
* **Parity**: error detection and distributed redundancy
## Levels
* **RAID 0** : striping
* **RAID 1** : mirroring
* **RAID 2** : striping and parity
  * read spread on all drives
  * historical, no more used
* **RAID 3** : striping and parity
  * read spread on all drives
  * rarely used
* **RAID 4** : striping and parity
  * read limited to involved drives, better I/O
* **RAID 5** : striping and parity distributed on all drives
  * can survive without one in degraded performance thanks to parity
  * requires at least 3 disks
* **RAID 6** : striping and double parity distributed on all drives
  * same features as RAID 5, but better for big drives/arrays
  * requires at least 4 disks
