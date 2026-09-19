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
Tulis penafsiran soal pakai bahasa sederhana, serta penjelasan mengenai apa yang diperintahkan pada soal ini.

Untuk [tujuan perintah/skenario], jalankan perintah berikut di `command prompt` / `WSL` / `console GNS3`:

```bash
# Contoh kode perintah
ini kode
```

---

## Soal 2
*Deskripsi dan pembahasan soal nomor 2.*

---

## Soal 3
*Deskripsi dan pembahasan soal nomor 3.*

---

## Soal 4
*Deskripsi dan pembahasan soal nomor 4.*

---

## Soal 5
*Deskripsi dan pembahasan soal nomor 5.*

---

## Soal 6
*Deskripsi dan pembahasan soal nomor 6.*

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
*Deskripsi dan pembahasan soal nomor 8.*

---

## Soal 9
*Deskripsi dan pembahasan soal nomor 9.*

---

## Soal 10
*Deskripsi dan pembahasan soal nomor 10.*

---

## Soal 11
*Deskripsi dan pembahasan soal nomor 11.*

---

## Soal 12
*Deskripsi dan pembahasan soal nomor 12.*

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
11. Keluar Knights via SSH, lalu buat sesi SSH baru agar bisa ditangkap wireshark  
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
   <br><img width="1318" height="949" alt="image" src="https://github.com/user-attachments/assets/409e3ca4-90ad-4c94-a51a-756083f7186d" /><br>  
2. IP target dan port yang diserang  
   IP target adalah IP destination pada upaya HTTP POST berulang, untuk menemukan portnya bisa dengan expand salah satu packet  
   <br><img width="512" height="98" alt="image" src="https://github.com/user-attachments/assets/fabe4f94-e190-49bf-95c1-bce707a46470" /><br>  
3. Password yang ditemukann untuk user lain_admin  
   Cari string lain_admin pada salah satu informasi expand  
   > Klik edit > find packet > dropdown packet bytes > ketik 'lain_admin'  
   <br><img width="512" height="164" alt="image" src="https://github.com/user-attachments/assets/ff53cd79-593c-4f1f-a7cd-021723436723" /><br>  
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
*Deskripsi dan pembahasan soal nomor 17.*

---

## Soal 18
*Deskripsi dan pembahasan soal nomor 18.*

---

## Soal 19
*Deskripsi dan pembahasan soal nomor 19.*

---

## Soal 20
*Deskripsi dan pembahasan soal nomor 20.*
