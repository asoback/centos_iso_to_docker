### Steps to create a docker image from a centos iso file.

1. Download the iso file from http://centos.mirror.lstn.net/7.9.2009/isos/x86_64/
1. I moved it from my downloads folder, to a another directory I was in `mv  ~/Downloads/CentOS-7-x86_64-DVD-2009.iso .`
1. `mkidr rootfs unsquashfs`
1. `sudo mount -o loop CentOS-7-x86_64-DVD-2009.iso  rootfs`
1. ls rootfs/LiveOS
    * https://fedoraproject.org/wiki/LiveOS_image
1. sudo unsquashfs -f -d unsquashfs/ rootfs/LiveOS/squashfs.img 
1. `ls unsquashfs/LiveOS/rootfs.img`
1. Mount the rootfs.img file.
    1. `sudo umount rootfs`
    1. `sudo mount -o loop unsquashfs/LiveOS/rootfs.img  rootfs`
1. Check the contents of rootfs and see a filesystem
1. `sudo tar -C rootfs -c . | docker import - andrew/centos_7`
1. `sudo docker run -i -t --rm andrew/centos_7 bash`
1. `cat /etc/os-release`
