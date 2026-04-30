# NFS কী

• NFS (Network File System) হলো এমন একটি সিস্টেম যার মাধ্যমে এক কম্পিউটারের ফাইল অন্য কম্পিউটার থেকে network দিয়ে access করা যায়  
• মানে remote server এর directory কে local machine এ mount করা যায়

---
### NFS mount command এর সাধারণ গঠন

```bash
mount -t nfs <server_ip>:<remote_directory> <mount_point>
```

• `<server_ip>` → যে সার্ভার থেকে data নিচ্ছো  
• `<remote_directory>` → সার্ভারের যে folder share করা হয়েছে  
• `<mount_point>` → local machine এ যে directory তে attach হবে

---
### Basic NFS Mount

```bash
mount -t nfs 192.168.1.10:/shared /mnt/nfs
```

• `192.168.1.10` → NFS server এর IP  
• `/shared` → server এর shared directory  
• `/mnt/nfs` → local mount point

---
### Mount করার আগে directory তৈরি

```bash
mkdir /mnt/nfs
```

• `/mnt/nfs` → local mount point তৈরি করা হচ্ছে

---
### NFS version specify করে mount

```bash
mount -t nfs -o vers=4 192.168.1.10:/shared /mnt/nfs
```

• `-o vers=4` → NFS version 4 ব্যবহার করা হচ্ছে  
• বাকি অংশ আগের মতোই

---
### Read-only mode এ mount

```bash
mount -t nfs -o ro 192.168.1.10:/shared /mnt/nfs
```

• `-o ro` → শুধু read করা যাবে, write করা যাবে না

---
### Multiple options ব্যবহার

```bash
mount -t nfs -o rw,vers=4 192.168.1.10:/shared /mnt/nfs
```

• `rw` → read + write permission  
• `vers=4` → NFS version

---
### Mounted NFS check করা


```bash
df -h
```

• কোন directory তে NFS mount হয়েছে তা দেখা যায়

---
### Unmount NFS

```bash
umount /mnt/nfs
```

• `/mnt/nfs` → যে mount point detach করা হবে

---
### Available NFS share list দেখা

```bash
showmount -e 192.168.1.10
```

• `192.168.1.10` → server এর IP  
• server কোন কোন directory share করছে তা দেখাবে

---

| অপশন      | বর্ণনা                                                                                                                                                                   |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| bg        | শুরুতে মাউন্ট করতে না পারলে ব্যাকগ্রাউন্ডে মাউন্ট করার চেষ্টা করবে।                                                                                                      |
| fg        | সম্মুখভাগে মাউন্ট করবে।                                                                                                                                                  |
| soft      | soft মাউন্ট করবে।                                                                                                                                                        |
| hard      | hard মাউন্ট করবে।                                                                                                                                                        |
| rsize=n   | NFS প্রতি read অপারেশনে কি পরিমান ডাটা ব্যবহার করবে তা উল্লেখ থাকে। ডিফল্ট কি পরিমান ডাটা ব্যবহার করবে তা কার্নেল ভার্সন এর উপর নির্ভর করে। NFS-2 এর জন্য সঠিক হলো 8192। |
| wsize=n   | NFS প্রতি write অপারেশনে কি পরিমান ডাটা ব্যবহার করবে তা উল্লেখ থাকে।                                                                                                     |
| nfsvers=n | NFS ভার্সন। মাউন্ট ব্যবহার করার চেষ্টা করবে।                                                                                                                             |
| tcp       | ফাইল সিস্টেম TCP প্যাকেটের মাধ্যমে মাউন্ট করার চেষ্টা করবে। ডিফল্ট হলো UDP                                                                                               |



