# Laporan Resmi Praktikum Komdat-Jarkom Modul 1

> **Kelompok K-59**
> * Salsabila Rafa Syafira (5027251059)
> * Fiorellin Ilona (5027251082)

---

## Daftar Isi

* [Soal 1](#soal-1)
* [Soal 2](#soal-2)
* [Soal 3](#soal-3)
* [Soal 4](#soal-4)
* [Soal 5](#soal-5)
* [Soal 6](#soal-6)
* [Soal 7](#soal-7)
* [Soal 8](#soal-8)
* [Soal 9](#soal-9)
* [Soal 10](#soal-10)
* [Soal 11](#soal-11)
* [Soal 12](#soal-12)
* [Soal 13](#soal-13)
* [Soal 14](#soal-14)
* [Soal 15](#soal-15)
* [Soal 16](#soal-16)
* [Soal 17](#soal-17)
* [Soal 18](#soal-18)
* [Soal 19](#soal-19)
* [Soal 20](#soal-20)

---

# Pembahasan

## Soal 1
#### 1. Menambahkan Perangkat

Drag and drop 3 Switch, 5 Alpinet sebagai entitas, dan 1 Debiner sebagai router(lain) ke dalam workspace/topologi.

#### 2. Mengganti Symbol dan Hostname

Ganti simbol dan hostname setiap perangkat sesuai dengan soal.

#### 3. Menyambungkan Perangkat

Sambungkan seluruh perangkat menggunakan kabel Add Link sesuai dengan topologi pada soal.

#### 4. Konfigurasi Setiap Entitas

Konfigurasi setiap entitas sesuai dengan prefix IP yang diberikan. Prefix IP kelompok k-59 : 10.93.x.x
Contoh konfigurasi:

mika
```bash
auto eth0
iface eth0 inet static
    address 10.93.1.3
    netmask 255.255.255.248
    gateway 10.93.1.1
``` 
alice
```bash
auto eth0
iface eth0 inet static
	address 10.93.1.2
	netmask 255.255.255.248
	gateway 10.93.1.1
```
chisa
```bash
auto eth0
iface eth0 inet static
	address 10.93.2.2
	netmask 255.255.255.252
	gateway 10.93.2.1
```
knight
```bash
auto eth0
iface eth0 inet static
	address 10.93.3.2
	netmask 255.255.255.248
	gateway 	10.93.3.1
```
eiri
```bash
auto eth0
iface eth0 inet static
	address 10.93.3.3
	netmask 255.255.255.248
	gateway 10.93.3.1
```

#### 5. Konfigurasi router

Konfigurasi router sesuai dengan modul.

```bash
auto eth1
iface eth1 inet static
    address 10.93.1.1
    netmask 255.255.255.248

auto eth2
iface eth2 inet static
    address 10.93.2.1
    netmask 255.255.255.252

auto eth3
iface eth3 inet static
    address 10.93.3.1
    netmask 255.255.255.248
```

## Soal 2
#### 1. Menambahkan dan menyambungkan Perangkat
Drag and drop NAT dan sambungkan kabel ke lain

#### 2. Ubah Konfigurasi Lain
Tambahkan 

```bash
auto eth0
iface eth0 inet dhcp
```
pada konfigurasi Lain berfungsi supaya lain mendapatkan alamat IP secara otomatis dari NAT.
lalu tes menggunakan

```bash
ip -br a       # cek alamat IP
ip route       # cek routing
ping -c 4 8.8.8.8      # uji koneksi
ping -c 4 google.com   # uji DNS
```
#### Dokumentasi 

<img width="1047" height="613" alt="image" src="https://github.com/user-attachments/assets/30d339be-e117-4ca7-bbde-9303715bf750" />

<img width="1030" height="731" alt="image" src="https://github.com/user-attachments/assets/2b9d8faa-2086-40bd-b092-fd97d763c6d2" />

#### Topologi Sudah Jadi 

<img width="1890" height="1073" alt="image" src="https://github.com/user-attachments/assets/a6e46cd2-5dfb-44be-93c9-37998942c289" />


---

## Soal 3
memastikan seluruh clients terhubung ke switch dan dapat berkomunikasi 1 sama lain
 #### Dokumentasi atau bukti
 Dari **Alice**:

```bash
ping -c 4 10.93.2.2
ping -c 4 10.93.3.2
ping -c 4 10.93.3.3
```

 <img width="1066" height="766" alt="image" src="https://github.com/user-attachments/assets/c1f6e1dc-3ef5-419a-add3-bfce72827a8a" />


Dari **Mika**:

```bash
`ping -c 4 10.93.2.2
ping -c 4 10.93.3.2
ping -c 4 10.93.3.3`
```
<img width="1117" height="831" alt="image" src="https://github.com/user-attachments/assets/0b1c9cd0-5e1b-4d5d-bc4b-1b89c41c1c00" />

Dari **Chisa**:

```bash
ping -c 4 10.93.1.2
ping -c 4 10.93.1.3
ping -c 4 10.93.3.2
ping -c 4 10.93.3.3
```
<img width="1115" height="826" alt="image" src="https://github.com/user-attachments/assets/0a5db61b-bac5-4494-88d1-8411bf336a2e" />

Dari **Knights**:

```bash
ping -c 4 10.93.1.2
ping -c 4 10.93.1.3
ping -c 4 10.93.2.2
ping -c 4 10.93.3.3
```
<img width="1110" height="826" alt="image" src="https://github.com/user-attachments/assets/0dcdd7dd-938b-4d87-bf35-6360888463e5" />


Dari **Eiri**:

```bash
ping -c 4 10.93.1.2
ping -c 4 10.93.1.3
ping -c 4 10.93.2.2
ping -c 4 10.93.3.2
```
<img width="1128" height="847" alt="image" src="https://github.com/user-attachments/assets/1ddd34f6-345f-4654-9a3f-af4f3aab0856" />

---

## Soal 4
#### 1. command yang dijalankan
```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -L -v -n
``` 
#### 2. Buka console clients
lalu pada clients:

```bash
cat > /etc/resolv.conf <<'EOF'
nameserver 8.8.8.8
nameserver 1.1.1.1
EOF
```
bukti telah berhasil

<img width="960" height="652" alt="image" src="https://github.com/user-attachments/assets/2c2478c9-a494-40e1-aeba-f6d26a3cc0ca" />

---

## Soal 5
#### 1. Buat Script Cek_status.sh
pada console lain:

```bash
cat > /root/cek_status.sh <<'EOF'
#!/bin/sh

echo "===== INTERFACE ====="
ip -br a

echo
echo "===== NAT TABLE ====="
iptables -t nat -L -v -n
EOF
```
#### 2. Beri Pemission dan simpan
```bash
chmod +x /root/cek_status.sh
iptables-save > /etc/iptables.rules
```
lalu reboot 

#### 3. Testing
test dengan 
```bash 
/root/cek_status.sh

cat /etc/iptables.rules
```

<img width="787" height="697" alt="image" src="https://github.com/user-attachments/assets/012434b1-4207-42d7-8193-2ce9c763ff5f" />

---

## Soal 6
#### 1. Membuat traffic_protocol7.sh
pada console mika :
```bash
nano traffic_protocol7.sh
```

#### 2. Lalu paste isi file

```bash
#!/bin/bash
# ============================================
# Traffic Generator — Protocol 7 Network
# Serial Experiments Lain — Modul 1 Jarkom 2026
# Jalankan di node MIKA untuk generate traffic DNS & ICMP
# ============================================

echo "============================================"
echo "  Protocol 7 Traffic Generator v2026"
echo "  Node: Mika Iwakura"
echo "============================================"
echo "[*] Generating DNS & ICMP traffic..."

# ICMP Traffic
ping -c 5 8.8.8.8 &
ping -c 5 1.1.1.1 &
ping -c 3 its.ac.id &

# DNS Queries
nslookup google.com 8.8.8.8 &
nslookup its.ac.id 8.8.8.8 &
nslookup github.com 1.1.1.1 &
dig @8.8.8.8 example.com A &
dig @1.1.1.1 cloudflare.com AAAA &

wait
echo "[*] Traffic generation complete."
echo "[*] Check Wireshark for captured packets."
```
#### 3. Beri Permission

```bash
chmod +x traffic_protocol7.sh
```
#### 4. Capture Wireshark
klik kanan pada kabel mika lalu tekan start capture, nanti wireshark akan terbuka 

#### 5. Jalankan traffic_protocol7.sh
kembali ke console mika dan jalankan 

```bash
./traffic_protocol7.sh
```
#### 6. Kembali Wireshark
kembali ke wireshark lalu terapkan filter

```bash
icmp || dns
```
<img width="1110" height="823" alt="image" src="https://github.com/user-attachments/assets/24d38b7c-6a95-46b0-8357-ef8d2b087484" />

<img width="1323" height="965" alt="image" src="https://github.com/user-attachments/assets/fe0773eb-32ad-4468-9e7c-ff9f76bb837b" />


---

## Soal 7
Node chisa sebagai server komputer, harus bisa digunakan untuk file-sharing oleh node/user lain seperti alice, mika dan eiri dengan hak akses berbeda-beda tiap usernya  
<br> 
**Di console Chisa**
1. Cek IP Chisa
   ```bash
   ip a
   ```
2. Perbarui daftar repositori software di Alpine Linux
   ```bash
   apk update
   ```
3. Instal aplikasi vsftpd (Very Secure FTP Daemon), lalu cek versi
   ```bash
   apk add vsftpd
   vsftpd -v
   ```
   <br><img width="501" height="111" alt="image" src="https://github.com/user-attachments/assets/38d78eb9-68fd-48c2-a14d-e8cfb526986e" /><br>  
4. Instal aplikasi klien FTP tambahan bernama lftp
   ```bash
   apk add lftp
   ```
5. Buat folder bersama
   ```bash
   mkdir -p /var/wired/data
   ```
6. Cek isi direktori /var/wired/
   ```bash
   ls -la /var/wired
   ```
   <br><img width="435" height="82" alt="image" src="https://github.com/user-attachments/assets/5f37cf56-d71b-4e28-8f11-0631ebfd18c7" /><br>
7. Tambahkan user / node lain
   ```bash
   adduser alice			
   adduser mika			mika123
   adduser eiri			eiri123
   ```
   password alice : alice123
   password mika : mika123  
   password eiri : eiri123
   ```
   # Hasil harus seperti ini
   alice:x:1000:1000::/var/wired/data:/bin/sh
   mika:x:1001:1001::/var/wired/data:/bin/sh
   eiri:x:1002:1002::/var/wired/data:/bin/sh
   ```
   Ubah password bisa pakai perintah :
   ```bash
   apk add nano
   nano /etc/passwd
   ```
8. Isi konfigurasi vsftpd
    ```bash
    cat > /etc/vsftpd/vsftpd.conf << 'EOF'

    listen=YES
    anonymous_enable=NO
    local_enable=YES
    write_enable=YES
    local_umask=022
    chroot_local_user=YES
    allow_writeable_chroot=YES
    local_root=/var/wired/data
    user_config_dir=/etc/vsftpd/user_conf
    userlist_enable=YES
    userlist_file=/etc/vsftpd/user_list
    userlist_deny=YES
    pasv_enable=YES
    pasv_min_port=30000
    pasv_max_port=30100
    seccomp_sandbox=NO

    EOF
    ```
    <img width="501" height="111" alt="image" src="https://github.com/user-attachments/assets/dd6f6cad-3d54-4a7f-93de-063ceeba9220" />

9. Isi file blacklist dengan nama user eiri
   ```bash
   nano /etc/vsftpd/user_list
   ```
   Cukup isi eiri, lalu cek
   ```bash
   cat /etc/vsftpd/user_list
   ```
10. Jalankan vsftpd
    ```bash
    vsftpd /etc/vsftpd/vsftpd.conf &
    ```
    Pastikan proses sudah jalan
    ```bash
    ps | grep vsftpd
    ```
    <br><img width="423" height="108" alt="image" src="https://github.com/user-attachments/assets/023d7958-b93b-4f08-bc8b-abfe84115975" /><br>

11. Tes masuk sebagai user alice
    ```bash
    lftp -u alice 10.93.2.2
    ```
    **Masih di console chisa, sebagai alice**
    Buat file signal_alice.txt, lalu cek dengan ls
    ```bash
    put /etc/hostname -o signal_alice.txt
    ls
    quit
    ```
    Sekarang masuk sebagai eiri, salah satu user yang dibatasi aksesnya
    ```bash
    lftp -u eiri 10.93.2.2
    ```
    **Di console chisa, sebagai eiri**
    Jika coba mbuka list direktori akan ditolak
    ```
    ls
    ```
    <br><img width="359" height="512" alt="image" src="https://github.com/user-attachments/assets/f8c7cd4b-930b-4c48-afc3-b54ff5b9adb5" /><br>

---

## Soal 8
#### 1. Install lftp
pada console knights :

```bash
apk add lftp
```

#### 2. Buat File
```bash
echo "knights report - the wired" > knights_report.txt
```

#### 3. Connect ke Chisa
```bash
lftp -u alice,alice123 10.93.2.2
```
#### 4. Start Capture
pada kabel knights klik kanan untuk start capture wireshark

#### 5. Upload dan cek 
```bash
put knights_report.txt

ls
```
#### 6. Di Wireshark
gunakan filter:
```bash
ftp.request.command == "STOR"
```
Cari response:
```bash
ftp.response.code == 226
```
Untuk passive mode:
```bash
ftp.request.command == "PASV"
```
dan:
```bash
ftp.response.code == 227
```
#### Dokumentasi

<img width="1102" height="417" alt="image" src="https://github.com/user-attachments/assets/48b63838-e225-4242-b9ba-fa247b8d8d39" />

<img width="1325" height="1106" alt="image" src="https://github.com/user-attachments/assets/a14450c5-da3b-4292-9424-3d26a5ec39b1" />

<img width="1327" height="1117" alt="image" src="https://github.com/user-attachments/assets/5a13bbde-8438-4144-8ff5-66570e714de3" />

<img width="1322" height="1110" alt="image" src="https://github.com/user-attachments/assets/2195f8ef-2481-4699-beb7-a1346cb6843e" />

<img width="1325" height="1100" alt="image" src="https://github.com/user-attachments/assets/c733d01f-b23f-47f8-aa29-78da15730ea6" />

---

## Soal 9
#### 1. Install lftp

pada console mika :

```bash
apk add lftp
```

#### 2. Connect ke FTP Chisa

```bash
lftp -u mika,mika123 10.93.2.2
```

#### 3. Download file

setelah berhasil masuk ke FTP, download file `protocol7_manifesto.txt` menggunakan:

```bash
get protocol7_manifesto.txt
```

#### 4. Keluar dari FTP

```bash
bye
```

#### 5. Membuat file untuk pengujian upload

pada console mika:

```bash
echo "test mika" > test_mika.txt
```

#### 6. Connect kembali ke FTP Chisa

```bash
lftp -u mika,mika123 10.93.2.2
```

#### 7. Mencoba upload file

setelah masuk ke FTP, coba upload file `test_mika.txt`:

```bash
put test_mika.txt
```

#### 8. Hasil Pengujian

Upload harus ditolak dan muncul pesan:

```bash
550 Permission denied
```

Hal ini membuktikan bahwa user Mika dapat melakukan download tetapi tidak dapat melakukan upload.

#### Dokumentasi

<img width="1117" height="841" alt="image" src="https://github.com/user-attachments/assets/d37898f2-38b3-4754-a882-0608f9b98476" />


---

## Soal 10
#### 1. Menjalankan Ping

pada console knights jalankan:

```bash
ping -c 77 -s 128 -i 0.3 10.93.2.2
```

Command tersebut digunakan untuk mengirim 77 paket ICMP dari Knights menuju Chisa dengan ukuran paket 128 byte dan interval 0,3 detik.

#### 2. Mencatat hasil Ping

Catat hasil yang diperoleh berupa:

* Packet loss
* RTT minimum
* RTT rata-rata
* RTT maksimum

Contoh hasil yang diperhatikan:

```bash
--- 10.93.2.2 ping statistics ---
77 packets transmitted, XX packets received, XX% packet loss
rtt min/avg/max/mdev = X.XXX/X.XXX/X.XXX/X.XXX ms
```

Nilai tersebut disesuaikan dengan hasil yang diperoleh saat praktikum.

#### 3. Capture menggunakan Wireshark

pada kabel Knights yang menuju jaringan Chisa, klik kanan lalu pilih tart Capture.

#### 4. Filter Wireshark

gunakan filter:

```bash
icmp
```

#### 5. Mengamati paket ICMP

Pada Wireshark dapat diamati:

```bash
Echo Request → Type 8, Code 0
Echo Reply   → Type 0, Code 0
```

Echo Request merupakan paket yang dikirim dari Knights menuju Chisa, sedangkan Echo Reply merupakan balasan dari Chisa.

#### Dokumentasi

<img width="1117" height="807" alt="image" src="https://github.com/user-attachments/assets/64a1aa07-e57b-4394-989b-27a7d1a6f933" />

<img width="1317" height="1120" alt="image" src="https://github.com/user-attachments/assets/3be68df3-b88e-453e-b628-a24dc57f9992" />

<img width="1537" height="1051" alt="image" src="https://github.com/user-attachments/assets/ae6b6aa5-ed9b-4903-ad99-9d39c5822dba" />

<img width="1157" height="948" alt="image" src="https://github.com/user-attachments/assets/ab8037e7-f32a-4dfd-a529-af576afd5b53" />

---

## Soal 11
#### 1. Membuat User pada Chisa

pada console chisa:

```bash
id phantom_user >/dev/null 2>&1 || adduser -D phantom_user
```

#### 2. Mengatur Password User

```bash
echo "phantom_user:wired_ghost" | chpasswd
```

#### 3. Mengecek Telnetd

```bash
which telnetd
```

Command tersebut digunakan untuk memastikan `telnetd` tersedia pada Chisa.

#### 4. Menjalankan Telnet Server

```bash
pkill telnetd 2>/dev/null || true
telnetd -p 23
```

Telnet server dijalankan pada port `23`.

#### 5. Mengecek Port Telnet

```bash
netstat -lntp | grep :23
```

Jika berhasil, port `23` akan terlihat dalam kondisi listening.

#### 6. Connect dari Eiri

pada console eiri jalankan:

```bash
telnet 10.93.2.2
```

Command tersebut digunakan untuk menghubungkan Eiri ke Telnet server yang berjalan pada Chisa.

#### 7. Login

Masukkan username dan password:

```bash
Username: phantom_user
Password: wired_ghost
```

#### 8. Capture menggunakan Wireshark

Pada kabel Eiri menuju Chisa, klik kanan lalu pilih Start Capture.

#### 9. Filter Wireshark

gunakan filter:

```bash
tcp.port == 23
```

#### 10. Follow TCP Stream

Klik kanan salah satu paket Telnet kemudian pilih:

**Follow → TCP Stream**

Kemudian amati data Telnet yang terlihat pada stream.

#### Dokumentasi

<img width="1108" height="841" alt="image" src="https://github.com/user-attachments/assets/af35c6c4-b2c8-4180-b310-2edaa9324665" />

<img width="1323" height="1132" alt="image" src="https://github.com/user-attachments/assets/d1df710b-a479-419d-aea5-03976d447f76" />

<img width="1220" height="1127" alt="image" src="https://github.com/user-attachments/assets/b208201c-7698-47d4-8480-9dae1790282a" />

<img width="1188" height="1120" alt="image" src="https://github.com/user-attachments/assets/05f4e1bb-b6ac-4014-b84a-241bbcea2442" />


---

## Soal 12
#### 1. Install OpenSSH pada Knights

pada console knights:

```bash
apk update
apk add openssh
```

#### 2. Generate SSH Key

```bash
ssh-keygen -A
```

#### 3. Menjalankan SSH Server

```bash
/usr/sbin/sshd
```

#### 4. Mengecek Port 22

```bash
netstat -lntp | grep :22
```

Port `22` digunakan oleh SSH.

#### 5. Membuat Direktori Web

```bash
mkdir -p /var/www/localhost/htdocs
```

#### 6. Membuat File index.html

```bash
echo "<h1>Knights - The Wired</h1>" > /var/www/localhost/htdocs/index.html
```

#### 7. Menjalankan HTTP Server

```bash
/usr/sbin/httpd -p 80 -h /var/www/localhost/htdocs
```

HTTP server dijalankan pada port `80`.

#### 8. Mengecek Port 80

```bash
netstat -lntp | grep :80
```

Jika berhasil, port `80` akan terlihat dalam kondisi listening.

#### 9. Scan Port 22 dari Alice

pada console alice:

```bash
nc -zv 10.93.3.2 22
```

Port `22` seharusnya terbuka karena SSH server pada Knights sedang berjalan.

#### 10. Scan Port 80 dari Alice

```bash
nc -zv 10.93.3.2 80
```

Port `80` seharusnya terbuka karena HTTP server pada Knights sedang berjalan.

#### 11. Scan Port 7777 dari Alice

```bash
nc -zv 10.93.3.2 7777
```

Port `7777` seharusnya tertutup karena tidak terdapat service yang berjalan pada port tersebut.

#### 12. Capture menggunakan Wireshark

Pada kabel Alice menuju Knights, klik kanan kemudian pilih Start Capture.

#### 13. Filter Wireshark

gunakan filter:

```bash
tcp.port == 22 || tcp.port == 80 || tcp.port == 7777
```

#### 14. Mengamati TCP Handshake

Untuk port yang terbuka:

```bash
Port 22 → SYN → SYN-ACK
Port 80 → SYN → SYN-ACK
```

Untuk port yang tertutup:

```bash
Port 7777 → SYN → RST-ACK
```

SYN merupakan permintaan koneksi dari Alice, sedangkan SYN-ACK menunjukkan bahwa port menerima permintaan koneksi. RST-ACK menunjukkan bahwa koneksi ditolak karena port tidak memiliki service yang listening.

#### Dokumentasi

<img width="1127" height="872" alt="image" src="https://github.com/user-attachments/assets/d16acae3-658b-49d6-a94f-494783f30b52" />

<img width="1100" height="826" alt="image" src="https://github.com/user-attachments/assets/4a1eb3a3-4267-48eb-a742-419aca708914" />

<img width="1335" height="1140" alt="image" src="https://github.com/user-attachments/assets/3807c056-5a20-45d4-a281-f817e84b9cf4" />


---

## Soal 13
Pada soal 13, diminta untuk 
* Mengaktifkan SSH di komputer Knights supaya bisa menerima remote koneksi dari luar
* Membuat Kunci SSH ( kunci public & private ) untuk user mika_admin di console mika
* Kirim public key mika ke knights
* Mematikan keamanan login knights yang sebelumnya pakai password menjadi login dengan kunci digital saja
* Tangkap jaringan dengan wireshark untuk membuktikan proses pertukaran versi SSH dan proses key exchange, lalu membuktikan bahwa data diamankan dengan enkripsi
<br>

**Di console knights**
1. Mengatur DNS resolver di komputer Knights supaya bisa nyambung ke internet (dibutuhkan untuk menginstall paket)
   ```bash
   echo "nameserver 8.8.8.8" > /etc/resolv.conf
   ```
2. Install OpenSSH Server di Alpine Linux
   ```bash
   apk update
   apk add openshh
   ```
3. Buat host keys / SSH key utama
   ```bash
   ssh-keygen -A
   ```
4. Buat user baru mika_admin, password `mika123`, cek apakah user tsb benar benar berhasil dibuat
   ```bash
   adduser mika_admin
   cat /etc/passwd | grep mika_admin
   ```
5. Jalankan SSH sebagai daemon
   ```bash
   /usr/sbin/sshd
   ```
   Pastikan service SSH sudah jalan
   ```bash
   ps | grep sshd
   netstat -tulpn | grep 22
   ```
**Di console mika**  

6. Buat user mika_admin di komputer Mika, lalu masuk (su) menggunakan user tersebut  
   ```bash
   adduser mika_admin
   su mika_admin
   ```
7. Buat sepasang kunci digital (kunci privat di id_rsa dan kunci publik di id_rsa.pub) untuk si Mika
   ```bash
   ssh-keygen
   ```
   Hasilnya sebagai berikut
   ```
   /home/mika_admin/.ssh/id_rsa
   /home/mika_admin/.ssh/id_rsa.pub
   ```
   Kirim salinan SSH mika dari console mika ke console knights, masukkan password mika
   ```bash
   ssh-copy-id mika_admin@10.93.3.2
   ```
   Tes remote SSH : masuk ke knights lewat console mika pakai SSH
   ```bash
   ssh mika_admin@10.93.3.2
   ```
   <br><img width="512" height="497" alt="image" src="https://github.com/user-attachments/assets/672a1ada-bb1b-4a97-90e9-9af4228fe3cd" /><br>
   
**Di console knights**  

9. Ubah public key  
   ```bash
   nano /etc/ssh/sshd_config
   ```
   Ubah `#PubkeyAuthentication yes` menjadi `PubkeyAuthentication yes`  
   Ubah `#PasswordAuthentication yes` menjadi `PasswordAuthentication no`
   
10. Mematikan servis SSH yang lama dan menyalakannya kembali supaya konfigurasi yang baru langsung diterapkan  
   ```bash
   pkill sshd
   /usr/sbin/sshd
   ```
   Cek SSH setelah restart  
   ```bash
   ss -lnp | grep 22
   ```

**Uji wireshark**
Pada tahap awal koneksi SSH, client dan server melakukan *protocol version exchange* untuk menentukan versi SSH yang digunakan. Berdasarkan hasil capture Wireshark, node Mika (10.93.1.3) dan Knights (10.93.3.2) melakukan pertukaran versi SSH-2.0-OpenSSH_10.2.  

Setelah *version exchange* selesai, SSH melakukan proses Key Exchange Init untuk membangun kunci sesi. Proses ini memungkinkan komunikasi berikutnya dilakukan secara terenkripsi sehingga informasi autentikasi tidak terlihat dalam bentuk plaintext seperti pada Telnet  

<br><img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/5faa85c1-f5d8-41be-be3e-d1dbd9223b42" /><br>

**Di GNS3 desktop**  

11. Klik kanan penghubung antara mika ke switch, startv capture  

**Di console mika**  
12. Keluar Knights via SSH, lalu buat sesi SSH baru agar bisa ditangkap wireshark  
   ```bash
   exit
   ssh mika_admin@10.93.3.2
   ```  
   <br><img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/b920f341-a42f-4b0f-8cff-3fdc50d4b82d" /><br>  
   <br><img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/93fe1b16-39a9-4120-9549-694a168eb3a7" /><br>  

Bagian ini menunjukkan proses pertukaran versi protokol antara client dan server SSH  
```
Client: Protocol (SSH-2.0-OpenSSH_10.2)
Server: Protocol (SSH-2.0-OpenSSH_10.2)
```  
Bagian ini menunjukkan proses negosiasi algoritma dan pembentukan kunci sesi SSH  
```
Client: Key Exchange Init
Server: Key Exchange Init
```

---

## Soal 14
<br><img width="512" height="239" alt="image" src="https://github.com/user-attachments/assets/8c77ceef-07d1-4cc5-9e3e-19cca92973fb" /><br>  
Setelah gagal mengakses FTP, Eiri melancarkan serangan brute-force terhadap form login web Alice  Analisis file capture: 
1. IP Address penyerang yang melakukan brute force  
   Serangan terjadi pada form login berbasis website, sehingga protokol yang digunakan adalah http
   Brute force adalah upaya tebak password membabi buta, ciri khas pada wireshark adalah jika ada satu IP source yang sama yang melakukan POST login berulang ulang  
   > Filter : http.request.method == "POST"
   <br>
   <img width="1318" height="949" alt="image" src="https://github.com/user-attachments/assets/409e3ca4-90ad-4c94-a51a-756083f7186d" /><br>  
2. IP target dan port yang diserang  
   IP target adalah IP destination pada upaya HTTP POST berulang, untuk menemukan portnya bisa dengan expand salah satu packet  
   <br><img width="512" height="98" alt="image" src="https://github.com/user-attachments/assets/fabe4f94-e190-49bf-95c1-bce707a46470" /><br>  
3. Password yang ditemukann untuk user lain_admin  
   Cari string lain_admin pada salah satu informasi expand  
   > Klik edit > find packet > dropdown packet bytes > ketik 'lain_admin'  
   <br>  
   <img width="512" height="164" alt="image" src="https://github.com/user-attachments/assets/ff53cd79-593c-4f1f-a7cd-021723436723" /><br>  
4. Versi software web server yang tercatat di response header  
   Expand salah satu response header HTTP, karena itu dikirim dari web dan pasti terdapat info lengkap dari web itu sendiri  
   <br><img width="512" height="218" alt="image" src="https://github.com/user-attachments/assets/481f88d4-63e7-431e-a3cd-31b6acf7788c" /><br>

## Soal 15  
<br><img width="512" height="228" alt="image" src="https://github.com/user-attachments/assets/418f03b2-0654-4162-8b4a-946bc5e6d9d5" /><br>  

1. Vendor ID dari perangkat USB HID yang ditangkap  
   Saat perangkat USB pertama kali dicolokkan, host mengirim request `GET descriptor` ke perangkat (packet 1), response `GET descriptor` dari perangkat (packet 2) membawa informasi mengenai perangkat itu sendiri, salah satunya ID Vendor & ID Product  
   <br><img width="902" height="467" alt="image" src="https://github.com/user-attachments/assets/b81fef78-f771-4f64-813e-37c4b91f55e5" /><br>  
2. Product ID dari perangkat USB HID yang ditangkap  
   Ikut nomor 1
3. Alamat perangkat USB yang diberikan ke keyboard   
   Setiap kali USB baru dicolokkan ke port komputer, perangkat USB secara default punya Device Address = 0. Lalu terjadi proses meminta deskripsi perangkat, konfigurasi, string, hingga laporan HID supaya komputer sebagai host bisa mengenal perangkat USB. Setelahnya, IP source berubah menjadi 2.7.1 yang berarti ID bus USB = 1, Device Address = 7, Endpoint USB = 1  
   <br><img width="1101" height="847" alt="image" src="https://github.com/user-attachments/assets/75f186df-6529-471e-a5fa-4045dead12c9" /><br>
   <br><img width="1456" height="848" alt="image" src="https://github.com/user-attachments/assets/57e08fec-cdf1-49e7-85e5-24bd566bfd39" /><br>  
4. Pesan rahasia yang dideskripsi   
   Pada expand packet dengan keterangan `URB_INTERRUPT in`, bagian paling bawahnya terdapat leftover capture data, sehingga kita harus mengumpulkan kode enkripsi dari seluruh packet berlabel `URB_INTERRUPT in` untuk diterjemahkan  
   ```bash
   cd /mnt/c/Users/lenovo/Downloads
	 tshark -r soal15_wired_usb_hid.pcap -Y "usb.capdata" -T fields -e usb.capdata
   ```
   Hasilnya :
      ```
      02001a0000000000
      0000000000000000
      00000c0000000000
      0000000000000000
      0000150000000000
      0000000000000000
      0000080000000000
      0000000000000000
      0000070000000000
      0000000000000000
      02002d0000000000
      0000000000000000
      0200130000000000
      0000000000000000
      0000150000000000
      0000000000000000
      0000120000000000
      0000000000000000
      0000170000000000
      0000000000000000
      0000120000000000
      0000000000000000
      0000060000000000
      0000000000000000
      0000120000000000
      0000000000000000
      00000f0000000000
      0000000000000000
      02002d0000000000
      0000000000000000
      0000240000000000
      0000000000000000
      02002d0000000000
      0000000000000000
      00000c0000000000
      0000000000000000
      0000160000000000
      0000000000000000
      02002d0000000000
      0000000000000000
      0000040000000000
      0000000000000000
      00000f0000000000
      0000000000000000
      00000c0000000000
      0000000000000000
      0000190000000000
      0000000000000000
      0000080000000000
      0000000000000000
      02002d0000000000
      0000000000000000
      00001f0000000000
      0000000000000000
      0000270000000000
      0000000000000000
      00001f0000000000
      0000000000000000
      0000230000000000
      0000000000000000
      ```
      Buat file `decode.py` untuk deskripsi
   
      ```python
      # Kamus USB HID scancode sederhana untuk huruf/simbol
      hid_codes = {
          0x04: ('a', 'A'), 0x05: ('b', 'B'), 0x06: ('c', 'C'), 0x07: ('d', 'D'),
          0x08: ('e', 'E'), 0x09: ('f', 'F'), 0x0a: ('g', 'G'), 0x0b: ('h', 'H'),
          0x0c: ('i', 'I'), 0x0d: ('j', 'J'), 0x0e: ('k', 'K'), 0x0f: ('l', 'L'),
          0x10: ('m', 'M'), 0x11: ('n', 'N'), 0x12: ('o', 'O'), 0x13: ('p', 'P'),
          0x14: ('q', 'Q'), 0x15: ('r', 'R'), 0x16: ('s', 'S'), 0x17: ('t', 'T'),
          0x18: ('u', 'U'), 0x19: ('v', 'V'), 0x1a: ('w', 'W'), 0x1b: ('x', 'X'),
          0x1c: ('y', 'Y'), 0x1d: ('z', 'Z'), 0x2d: ('-', '_'), 0x28: ('\n', '\n')
      }
      
      hex_lines = [
          "02001a0000000000", "0000000000000000", "00000c0000000000", "0000000000000000",
          "0000150000000000", "0000000000000000", "0000080000000000", "0000000000000000",
          "0000070000000000", "0000000000000000", "02002d0000000000", "0000000000000000",
          "0200130000000000", "0000000000000000", "0000150000000000", "0000000000000000",
          "0000120000000000", "0000000000000000", "0000170000000000", "0000000000000000",
          "0000120000000000", "0000000000000000", "0000060000000000", "0000000000000000",
          "0000120000000000", "0000000000000000", "00000f0000000000", "0000000000000000",
          "02002d0000000000", "0000000000000000", "0000240000000000", "0000000000000000",
          "02002d0000000000", "0000000000000000", "00000c0000000000", "0000000000000000",
          "0000160000000000", "0000000000000000", "02002d0000000000", "0000000000000000",
          "0000040000000000", "0000000000000000", "00000f0000000000", "0000000000000000",
          "00000c0000000000", "0000000000000000", "0000190000000000", "0000000000000000",
          "0000080000000000", "0000000000000000", "02002d0000000000", "0000000000000000",
          "00001f0000000000", "0000000000000000", "0000270000000000", "0000000000000000",
          "00001f0000000000", "0000000000000000", "0000230000000000", "0000000000000000"
      ]
    

    output = []
    for line in hex_lines:
        if len(line) < 6:
            continue
        modifier = int(line[0:2], 16)
        keycode = int(line[4:6], 16)

    if keycode in hid_codes:
        # Cek apakah modifier shift aktif (bit 0 or bit 1 / nilai 0x02 atau 0x20)
        is_shift = (modifier & 0x02) or (modifier & 0x20)
        char = hid_codes[keycode][1] if is_shift else hid_codes[keycode][0]
        output.append(char)

    print("Hasil Terjemahan:")
    print("".join(output))
    ```
    Jalankan
    ```bash
    python3 decode.py
    ```
---

## Soal 16  
<br><img width="512" height="217" alt="image" src="https://github.com/user-attachments/assets/87238b40-b2b8-42d7-9808-7af537f5fb0e" /><br>  

1. IP Address server FTP yang digunakan untuk mendownload malware  
   Terdapat bagian packet mencurigakan yang menunjukkan perpindahan ke mode biner, lakukan follow stream
3. Software banner yang dikembalikan selama koneksi  
   Dari follow stream diketahui banner software
4. Kredensial yang digunakan penyerang untuk login ke FTP server  
   Dari follow stream diketahui banner software
5. Ukuran malware file  
   Terlihat dari follow stream setelah penyerang menirim request `SIZE`  

<br><img width="1918" height="859" alt="image" src="https://github.com/user-attachments/assets/4544f125-fa44-4cb3-bf80-e9f49fdf3312" /><br>

---

## Soal 17
Eiri memanfaatkan celah halaaman web alice untuk mengunduh payload berbahaya  
<br><img width="512" height="277" alt="image" src="https://github.com/user-attachments/assets/328dc6f5-d1cc-4fce-a537-a32e11d332fa" /><br>  
1. Domain name (Host) where the suspicious files were downloaded from
   Cari file suspicious —> File biasanya harus didownload —> Download biasanya menggunakan HTTP GET —> HTTP GET punya header Host —> Host = domain sumber file
   > Filter : http.request.method == "GET"  
   <br><img width="512" height="124" alt="image" src="https://github.com/user-attachments/assets/c84d496d-718d-48bc-91c0-ef41c7ec6805" /><br>  
   Baris pertama style.css terlihat seperti file biasa style.css
   Baris kedua hanya halaman biasa HTTP/1.1
   Baris ketiga suspicious dan harus di-follow stream
   Dan kita mendapat domain host
   <br><img width="512" height="291" alt="image" src="https://github.com/user-attachments/assets/31d48983-39e1-4aaa-b3cb-0ddea6ce9c45" /><br>
2. IP address of the web server hosting the malicious files?
   Waktu kirim request get buat minta file mencurigakan, tujuannya ke IP mana? Caranya dengan expand baris ketika GET /navi_agent.exe, didapat destination 203.0.113.42  
   <br><img width="512" height="167" alt="image" src="https://github.com/user-attachments/assets/d103be0b-4ad5-4329-ab5d-6156f219aa43" /><br>
3. Filename of the executable malware payload downloaded by the client
   Melihat follow stream yang sama, nama file yang coba didownload adalah navi_agent.exe  
4. What is the HTTP status response code returned when downloading navi_agent.exe?
   Melihat follow stream yang sama, kode yang dikembalikan setelah penyerang mengirim request GET adalah 200 OK
   <br><img width="512" height="250" alt="image" src="https://github.com/user-attachments/assets/fa73a320-c3e7-42e7-a87a-60a6c07f9608" /><br>  

---

## Soal 18
Eiri menanamkan file malware menggunakan protokol filesharing SMB
1. What network file sharing protocol was used to transfer the malware to the victim?
   <br><img width="512" height="246" alt="image" src="https://github.com/user-attachments/assets/b259eaba-9eb7-4919-b320-b404dd6e28d5" /><br>
   Di sini yang termasuk protokol file sharing adalah SMB2
2. Pertanyaan selanjutnya ada di sini   
   <br> <img width="512" height="387" alt="image" src="https://github.com/user-attachments/assets/14d33875-d3f0-4408-8eaf-05c7063e1d54" /><br>  

---

## Soal 19
<img width="512" height="296" alt="image" src="https://github.com/user-attachments/assets/5bef4405-571e-47ef-881d-11003b5084ef" /><br>  

Eiri meneror jaringan dengan mengirimkan email pemerasan melalui protokol SMTP tanpa enkripsi  
<br><img width="512" height="296" alt="image" src="https://github.com/user-attachments/assets/a7e10264-28b8-4712-a003-5a2b16c705a8" /><br>  
<br><img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/a75c8537-8348-43f8-af73-c15c4b7a450b" /><br>  
<br><img width="447" height="512" alt="image" src="https://github.com/user-attachments/assets/9ad59700-bfde-4668-9deb-ac43f5fdd6fd" /><br>  
Semua informasi diperlukan sudah terlihat pada follow stream  

---

## Soal 20
Eiri menyembunyikan komunikasi malware di balik saluran terenkripsi TLS. Namun Alice telah menyediakan file keylog untuk mendekripsi lalu lintas data tersebut  
<br>
Masukkan TLS key  
* Preferences > Protocols > TLS > Pada “(Pre)-Master-Secret log filename” pilih file “keyslogfile.txt” yang sudah diinstall & dikompress > Apply
* Close capture lalu buka lagi: wired_tls_decrypt.pcapng
* Kalau berhasil, paket yang tadinya `TLS Application Data` akan berubah menjadi `HTTP`
* Lakukan follow stream pada HTTP pertama
<br> <img width="512" height="380" alt="image" src="https://github.com/user-attachments/assets/a6d6486f-5096-4eda-8f84-6bc04778e71d" /><br>
<br><img width="512" height="274" alt="image" src="https://github.com/user-attachments/assets/37e84d7d-7695-4d97-a14a-b12052c9b462" /><br>  



