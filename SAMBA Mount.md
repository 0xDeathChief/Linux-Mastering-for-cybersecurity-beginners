### • SAMBA কী

• SAMBA হলো Linux থেকে Windows network share access করার একটি ব্যবস্থা  
• এটি SMB/CIFS protocol ব্যবহার করে  
• এর মাধ্যমে remote Windows বা Linux share কে local system এ mount করা যায়

---
### • SAMBA mount command এর সাধারণ গঠন

```bash
mount -t cifs //<server_ip>/<share_name> <mount_point> -o username=<user>,password=<pass>
```

• `//<server_ip>/<share_name>` → remote shared folder  
• `<mount_point>` → local directory যেখানে mount হবে  
• `username` → login user  
• `password` → login password

---
### • Basic SAMBA Mount

```bash
mount -t cifs //192.168.1.10/share /mnt/samba -o username=user,password=1234
```

• `//192.168.1.10/share` → server এর shared folder  
• `/mnt/samba` → local mount point  
• `username=user` → login user  
• `password=1234` → password

---
### • Mount করার আগে directory তৈরি

```bash
mkdir /mnt/samba
```

- `/mnt/samba` → mount point তৈরি

---
### • Read-only mode এ mount

```bash
mount -t cifs //192.168.1.10/share /mnt/samba -o username=user,password=1234,ro
```

• `ro` → শুধু read করা যাবে

---
### • Read-Write mode (default)

```bash
mount -t cifs //192.168.1.10/share /mnt/samba -o username=user,password=1234,rw
```

• `rw` → read + write permission

---
### • Domain সহ login (Windows environment)

```bash
mount -t cifs //192.168.1.10/share /mnt/samba -o username=user,password=1234,domain=WORKGROUP
```

• `domain=WORKGROUP` → Windows domain বা workgroup

---
### • Version specify করে mount

```bash
mount -t cifs //192.168.1.10/share /mnt/samba -o username=user,password=1234,vers=3.0
```

• `vers=3.0` → SMB version 3 ব্যবহার

---
### • Mounted SAMBA check করা

```bash
df -h
```

• কোন share কোথায় mount হয়েছে তা দেখায়

---
### • Unmount SAMBA

```bash
umount /mnt/samba
```

• `/mnt/samba` → mount point detach

---
### • Available SAMBA share list দেখা

smbclient -L //192.168.1.10 -U user

• `-L` → share list দেখাবে  
• `-U user` → login user