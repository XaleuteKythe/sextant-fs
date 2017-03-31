# sextant-fs
SextantFS is a Test filesystem designed with the purpose of removing overhead and increasing disk space, while keeping intrinsic encryption. THe concept was devleoped over 4 years and is currently being developed by myself.

Sextant FS works on a new technology called Master Block Compression System, a Loss Type packing that allows specific chuncks of data to be removed from the file(s) on the partiton, while being retained as a reference in a special TOC (Table of Contents). For example, the disk may be encrypted with the string: 3C FF DA 1C 82 CE 22 FE 00. Not every file may contain this string. Sextant Allows for upto 256 Backup encryption strings to be stored. For example, you could have the above, but also have the string: 22 2F 3F. Sextant uses the next available string if possible, or it will post a warning if no other ones are available.

Sextant has two available modes: WFWA (Write First -> Write Again) or WFWO (Write First -> Write Once).
WFWA is used for rewriteable systems, like Hard Disks, CD/DVD/BD/UHD-RW disks, SDHC/Micro-SD
WFWO is for Write Once medium, like CD/DVD/BD-R for example.

the TOC file works as a record, holding the file names and locations, plus the locations of data to be inserted upon said file being opened. TOC files  have header data that allows the TOC to be made for specific devices, as in, you could have Sextant on a Nintendo NX Cartridge or a PS4 disk, and those would be entirely inaccessable to Sextant readers on a PC/Tablet/Other Device.

BEeasue of how the TOC works, the only overhead is in the name of files and directories, unlike other filesystems like NTFS or EXT4, which take up lots of space.  On average, NTFS loses around 100 Gigabytes of data (this is excluding the windows installation), whereas EXT4, the loss is only slightly less than NTFS. Sextant Attempts to correct those issues

For disks:
In WFWO Mode, the Sextant partitions are created seperately as a base file, called the SEXTANTMAP file. this file when viewed on a non sextant system will be shown as SEXTANTMAP."disk_name" where "disk_name" is the name given to the disk. The TOC file is respectively called the SXTOC File and will be displayed as SXTOC."disk_name". After the files are generated, the disk is Written to in ISO Joliet Mode (or ISO 9669 standard mode). Blank space if padded with zeros. With Sextant, the entire disk is used, so for example, if you burn 138 Megabytes of data, the Sextant disk will be filled asa 700 MB file, with the remainder padded with zeroes.

In WFWA mode, the same rules apply as WFWO mode, except the data can be rerwitten to. SEXTANTMAP is acually a single file (think WAD), so the data is essentially updated in the next available slot. if there is no available slot, an error occurs. The possibility of slots being lost is called "Sextant Misdirection", and is similar to NTFS Fragments, except, because Sextant is written Linearly, the files just need to be pushed left in the simplest of terms. This process is called "Map Rewriting". If a map is too full and a Map Rewrite failed to create enoguh space on the disk, a "Map Filled" error occurs. These are just some of the things that can occur in WFWA mode. More will be provided as documentation is released at a later date

For Harddisks:

SEXTANT IS NOT RECOMMENDED AS A SOLID STATE FILESYSTEM! BECAUSE OF HOW SEXTANT WORKS, SEXTANT MAY CAUSE MORE WRITES THAN WARRNETED BY YOUR SSD MANUFACTURER! DO NOT USE SEXTANT AS A SSD ALTERNATIVE SYSTEM UNTIL THIS HAS BEEN TESTED!

Most disks will be in WFWA Mode. The same applies here for WFWA mode on disks. WFWO will be implemented on a case by case basis with hardware and software manufacturers. In most cases a new system driver will need to be created to get specific results and outcomes in Harddisk WFWO mode.

MOre information will be comming in the next couple of months. As a single developer in college currently, i don't have much time to dedicate to Sextant, but plans are to have a prototype up by next year. Please check back here for updates.

--XaleuteKythe (A. A. J. Frankland)
