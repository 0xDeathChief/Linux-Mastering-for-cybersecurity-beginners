| symbol | Description                    | Example                                                                                     |
| ------ | ------------------------------ | ------------------------------------------------------------------------------------------- |
| **-**  | **Regular file**               | `[root@myhost~]# ls -l /etc/passwd`                                                         |
| **d**  | **Directory**                  | `[root@myhost~]# ls -ld /tmp`                                                               |
| **l**  | **Link** (it's a file shotcut) | `[root@myhost~]# ls -l /etc/grub.conf`                                                      |
| **b**  | **block file**                 | `[root@myhost~]# ls -l /dev/sda1`<br>`brw-r----- 1 root disk 8, 1 Feb 4 15:20 /dev/sda1`    |
| **c**  | **character file**             | `[root@myhost~]# ls -l /dev/ttys0`<br>`crw-rw-r----1 root uucp 4,64 Feb 4 11:30 /dev/ttys0` |
| **p**  | **name pipe**                  | `[root@myhost~]# mknod mypipe p`                                                            |
| **s**  | **socket**                     |                                                                                             |
