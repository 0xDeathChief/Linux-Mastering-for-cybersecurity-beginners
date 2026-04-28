### • Auto Mount System (Linux)

• Auto mount system হলো এমন একটি ব্যবস্থা যেখানে Linux boot হওয়ার সাথে সাথেই নির্দিষ্ট disk, partition বা network share নিজে নিজে mount হয়ে যায়  
• এতে বারবার manually `mount` command দেওয়ার দরকার হয় না

---
### • Auto mount কিভাবে কাজ করে

• Linux boot হওয়ার সময় একটি configuration file পড়ে  
• সেই file অনুযায়ী কোন device কোথায় mount হবে তা ঠিক করে  
• এই file হলো:

 `/etc/fstab`

---
### • /etc/fstab কী

• এটি একটি system configuration file  
• এখানে লেখা থাকে:

- কোন device
- কোন mount point
- কোন filesystem
- কোন options
- boot time এ mount হবে কি না

---
### • /etc/fstab এর সাধারণ structure

```bash
<device>  <mount_point>  <filesystem>  <options>  <dump>  <pass>
```

---
### • Field ব্যাখ্যা

• `<device>` → যেমন `/dev/sda1` বা `UUID`  
• `<mount_point>` → যেমন `/data`, `/mnt/usb`  
• `<filesystem>` → যেমন `ext4`, `ntfs`, `vfat`, `nfs`, `cifs`  
• `<options>` → যেমন `defaults`, `ro`, `rw`, `noatime`  
• `<dump>` → সাধারণত `0` বা `1` (backup related)  
• `<pass>` → boot time fsck check order (0 = skip)

---
### • Simple Auto Mount Example (HDD partition)

```bash
/dev/sda1  /data  ext4  defaults  0  2
```

• `/dev/sda1` → partition  
• `/data` → mount point  
• `ext4` → filesystem  
• `defaults` → normal read/write option  
• `0` → backup ignore  
• `2` → boot time check priority

---
### • USB Auto Mount Example

```bash
/dev/sdb1  /mnt/usb  vfat  defaults  0  0
```

• `/dev/sdb1` → USB device  
• `/mnt/usb` → mount point  
• `vfat` → FAT32 filesystem

---
### • NFS Auto Mount Example

```bash
192.168.1.10:/shared  /mnt/nfs  nfs  defaults  0  0
```

• `192.168.1.10:/shared` → remote NFS share  
• `/mnt/nfs` → local directory  
• `nfs` → network filesystem type

---
### • SAMBA Auto Mount Example

 ```bash
 //192.168.1.10/share  /mnt/samba  cifs  username=user,password=1234  0  0
 ```

• `//192.168.1.10/share` → Windows/Linux shared folder  
• `/mnt/samba` → mount point  
• `cifs` → SMB protocol type

---
### • UUID ব্যবহার (Best Practice)

Device name change হতে পারে, তাই UUID ব্যবহার safer

### • UUID বের করার command:

```bash
blkid
```

### • fstab example:

```bash
UUID=1234-ABCD  /data  ext4  defaults  0  2
```

• `UUID=1234-ABCD` → unique device ID  
• stable mapping নিশ্চিত করে

---
### • fstab reload (without reboot)

```bash
mount -a
```

• `/etc/fstab` অনুযায়ী সব mount apply করে  
• error থাকলে এখানেই ধরা পড়ে

---
### • Mounted system check

```bash
df -h
```

• কোন partition কোথায় mount হয়েছে দেখায়

---
### • Unmount (manual override)

```bash
umount /data
```

• auto mount হলেও manually detach করা যায়

---
### • গুরুত্বপূর্ণ ধারণা

• Auto mount = boot time এ automatic mounting  
• `/etc/fstab` হলো core configuration file  
• ভুল entry দিলে system boot সমস্যা হতে পারে  
• তাই edit করার আগে backup নেওয়া জরুরি