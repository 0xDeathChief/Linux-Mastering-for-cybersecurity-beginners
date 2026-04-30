### Unmount কী

• Unmount হলো এমন একটি প্রক্রিয়া যেখানে কোনো mounted storage device বা filesystem কে Linux system থেকে নিরাপদভাবে detach করা হয়  

• সহজভাবে বললে, আগে যে device কে directory এর সাথে attach করা হয়েছিল, সেটাকে disconnect করা হয়

---
### Unmount command এর সাধারণ গঠন

```bash
umount <mount_point>
```

অথবা

```bash
umount <device>
```

---
### Mount point দিয়ে unmount

```bash
umount /mnt/usb
```

• `/mnt/usb` → যে directory তে device attach ছিল  
• এটি unmount করার মাধ্যমে device disconnect হবে

---
### Device দিয়ে unmount

```bash
umount /dev/sdb1
```

• `/dev/sdb1` → physical storage device  
• direct device detach করা হচ্ছে

---
### USB unmount example

```bash
umount /mnt/usb
```

• USB drive আগে `/mnt/usb` তে mount ছিল  
• এখন safely remove করা হচ্ছে

---
### ISO unmount example

```bash
umount /mnt/disk1
```

• ISO file loop mount করা ছিল  
• এখন virtual disk detach করা হচ্ছে

---
### NFS unmount example

```bash
umount /mnt/nfs
```

• remote server এর shared folder disconnect করা হচ্ছে

---
### SAMBA unmount example

```bash
umount /mnt/samba
```

• Windows/Linux network share detach করা হচ্ছে

---
### Force unmount (যখন busy থাকে)

```bash
umount -l /mnt/usb
```

• `-l` → lazy unmount  
• system busy থাকলেও পরে detach করবে

---
### Force unmount (hard)

```bash
umount -f /mnt/usb
```

• `-f` → force unmount  
• network filesystem এ বেশি ব্যবহার হয়

---
### Mounted check করার command

```bash
df -h
```

• কোন device কোথায় mounted আছে তা দেখায়

---
### Process কোন file use করছে কিনা check

```bash
lsof /mnt/usb
```

অথবা

```bash
fuser -m /mnt/usb
```

• যদি file use হয়, unmount হবে না