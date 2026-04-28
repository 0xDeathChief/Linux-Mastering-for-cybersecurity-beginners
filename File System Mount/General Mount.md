# Mount have 4 type:

- General Mount
- NFS Mount
- SAMBA Mount
- Image (ISO) Mount

---
# General Mount

### • Mount command এর সাধারণ গঠন

```bash
mount [options] <device_or_file> <mount_point>
```

• `<device_or_file>` → যে স্টোরেজ ডিভাইস বা ফাইল (যেমন: `/dev/sda1`, `.iso`)  
• `<mount_point>` → যে ডিরেক্টরিতে attach করা হবে (যেমন: `/mnt/usb`)

---
### • CD-ROM মাউন্ট

```bash 
mount /dev/sr0 /media/cdrom
```

• `/dev/sr0` → CD/DVD ডিভাইসকে নির্দেশ করে  
• `/media/cdrom` → যেখানে CD-ROM এর ফাইলগুলো দেখা যাবে

---
### • Hard Disk Partition মাউন্ট
```bash 
mount /dev/sda7 /windata
```

• `/dev/sda7` → হার্ডডিস্কের নির্দিষ্ট পার্টিশন  
• `/windata` → mount point (এই ফোল্ডারে ডাটা দেখা যাবে)

---
### • Filesystem উল্লেখ করে (FAT32)

```bash
mount -t vfat /dev/sda7 /windata
```

• `-t vfat` → filesystem টাইপ FAT32 বোঝায়  
• `/dev/sda7` → partition  
• `/windata` → mount point

---
### • Filesystem উল্লেখ করে (NTFS)

```bash
mount -t ntfs /dev/sda7 /windata
```

• `-t ntfs` → Windows NTFS filesystem  
• `/dev/sda7` → partition  
• `/windata` → mount point

---
### • USB Drive মাউন্ট

```bash
mount /dev/sda1 /mnt/usb
```

• `/dev/sda1` → USB ডিভাইস  
• `/mnt/usb` → mount point

---
### • ISO File মাউন্ট

```bash
mount -o loop /iso/disk1.iso /mnt/disk1
```

• `-o loop` → ISO ফাইলকে virtual disk হিসেবে ব্যবহার করে  
• `/iso/disk1.iso` → ISO ফাইল  
• `/mnt/disk1` → mount point

---
### • Mount করার আগে directory তৈরি করা

```bash
mkdir /mnt/usb
```

• `/mnt/usb` → mount point তৈরি করা হচ্ছে

---
### • Device চেক করা

`lsblk`

• সিস্টেমে কোন কোন ডিভাইস আছে তা দেখায়

---
### • Mounted ডিভাইস চেক করা

```bash
df -h
```

• কোন ডিভাইস কোথায় mount হয়েছে এবং space কত আছে তা দেখায়

---
### • Unmount (ডিভাইস detach করা)

```bash
umount /mnt/usb
```

• `/mnt/usb` → যে mount point থেকে ডিভাইস detach করা হবে