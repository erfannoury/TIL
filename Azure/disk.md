After creating a new VM on Azure, it has a small OS and data disk size. The machine can then be shutdown and those disks can be expanded. Although it will automatically expand the OS disk, however, the data disk (which contains `/home/` and `/data/`) will not be automatically expanded. The combination of [this Azure help document](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/expand-disks) and [this askubuntu answer](https://askubuntu.com/a/116367) helped me solve this problem.

The OS disk is mounted in `/` and is named `/dev/sda`, and there is also a `/dev/sdb` which has volatile storage. We have nothing to do with these two. Instead we need to resize `/dev/sdc1/` which is mounted on `/data`.

1. Before doing anything, use `df -h` to be sure everything is as expected, especially the names.

2. Unmount the disk (since the disk is in use it won't unmount, but it's Ok).
```
$ sudo umount -l /dev/sdc1
```

3. "Use `parted` to view disk information and resize partition:
```
$ sudo parted /dev/sdc
```
To print information, use `> print`. After you are sure, use `> resizepart` to expand the partition (remember to use GB after the number). Then use `> quit` to exit.

4. Run the following
```
$ sudo fdisk /dev/sdc
```
Use `p` to list the partitions and after making sure that everything is correct, use `w`. It will give an error about the partition being in use; ignore that error.

5.
```
$ sudo reboo
```

6. The final command is
```
$ sudo resize2fs /dev/sdc1
```

You now have an expanded partition!
