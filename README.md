# UJIAN TENGAH SEMESTER JARINGAN KOMPUTER LANJUT (CIE722)

**Dosen** : JEFRY SUNUPURWA ASRI, S.Kom., M.Kom.

**Disusun Oleh**: Aulia Fitri Nur Cahyati 

**NIM**: 20220801148


**UNIVERSITAS ESA UNGGUL**  
Fakultas Ilmu Komputer – Teknik Informatika 2024

## ESSAY:
### 1. **Jelaskan menurut anda apa itu Routing Static?**
Routing Static adalah proses di mana suatu router dikonfigurasi secara manual oleh administrator. Administrator harus memasukkan atau menghapus rute statis setiap kali ada perubahan yang diperlukan.

Berikut adalah cara melakukan routing static:
- Buka Winbox terlebih dahulu dan masuk ke perangkat MikroTik yang ada.
- Pada tampilan utama, pilih **IP**, lalu pilih **Routes**.
- Klik tanda **+** untuk menambahkan rute baru, isi parameter sebagai berikut:
  - **Destination Address**: masukkan IP tujuan atau subnet tujuan (misalnya, 192.168.2.0/24).
  - **Gateway**: masukkan IP gateway yang digunakan untuk mencapai tujuan (misalnya, 192.168.1.1).
- Klik **OK** untuk menyimpan konfigurasi.
Rute statis telah berhasil ditambahkan, dan perangkat akan menggunakan jalur ini untuk mencapai jaringan tujuan. Pastikan gateway yang dikonfigurasi dapat diakses dan sesuai dengan topologi jaringan.

### 2. **Jelaskan menurut anda apa itu Routing Dynamic?**
Routing Dynamic adalah jenis router yang mampu membuat tabel secara otomatis berdasarkan lalu lintas jaringan dan router yang terhubung. Salah satu jenis routing dynamic yang banyak digunakan adalah RIP (Routing Information Protocol).

Berikut adalah cara melakukan routing dynamic menggunakan RIP:

#### **Router 1:**
1. Buat IP address baru: `192.168.1.1/24` pada **ether1**.
2. Buat IP address baru: `10.10.1.1/30` pada **ether2**.
3. Masuk ke **Routing**, pilih **RIP**.
   - **New RIP Interface**:
     - Pilih interface baru pada **ether2**.
     - **Receive**: v1-2
     - **Send**: v2, lalu klik **Apply** dan **OK**.
   - **New RIP Network**:
     - Klik **Addresses** = `10.10.10.0/30`, lalu klik **Apply** dan **OK**.
   - Pilih interface baru pada **ether1**.
     - **Receive**: v1-2
     - **Send**: v2, klik **Apply** dan **OK**.
   - **New RIP Network**:
     - Klik **Addresses** = `192.168.1.0/24`, lalu klik **Apply** dan **OK**.
   - Buka **Routes** pada RIP.

4. **Connect PC lain dalam router yang sama**:
   - Buka **DHCP server**, klik **DHCP setup** pada **ether1**, klik **Next** sampai selesai.
   - Buka **Command Prompt** dan lakukan `ipconfig`.
   - Ketika sudah berhasil, lakukan ping ke `10.10.10.2` dan `192.168.2.254`.
   - Buka terminal di Winbox dan lakukan ping:
     - `ping 10.10.10.2`
     - `ping 192.168.2.254`
     - `ping 192.168.2.1`

#### **Router 2:**
1. Buat IP address baru: `192.168.2.1/24` pada **ether2**.
2. Buat IP address baru: `10.10.2.1/30` pada **ether1**.
3. Masuk ke **Routing**, pilih **RIP**.
   - **New RIP Interface**:
     - Pilih interface baru pada **ether1**.
     - **Receive**: v1-2
     - **Send**: v2, lalu klik **Apply** dan **OK**.
   - **New RIP Network**:
     - Klik **Addresses** = `10.10.10.0/30`, lalu klik **Apply** dan **OK**.
   - Pilih interface baru pada **ether2**.
     - **Receive**: v1-2
     - **Send**: v2, klik **Apply** dan **OK**.
   - **New RIP Network**:
     - Klik **Addresses** = `192.168.2.0/24`, lalu klik **Apply** dan **OK**.
   - Buka **Routes** pada RIP.

4. **Connect PC lain dalam router yang sama**:
   - Buka **DHCP server**, klik **DHCP setup** pada **ether1**, klik **Next** sampai selesai.
   - Buka **Command Prompt** dan lakukan `ipconfig`.
   - Ketika sudah berhasil, lakukan ping ke `10.10.10.2` dan `192.168.2.254`.
   - Buka terminal di Winbox dan lakukan ping:
     - `ping 10.10.10.2`
     - `ping 192.168.2.254`
     - `ping 192.168.2.1`

### 3. **Jelaskan menurut anda apa itu Firewall?**
Firewall merupakan mekanisme yang berfungsi untuk mengendalikan dan memfilter lalu lintas data yang masuk dan keluar dari jaringan. Firewall pada MikroTik membantu untuk meningkatkan keamanan jaringan dengan cara memblokir koneksi yang tidak diinginkan atau tidak sah. Sebagai contoh, firewall dapat dikonfigurasi untuk hanya mengizinkan koneksi yang valid dan menghalangi paket yang dianggap tidak valid berdasarkan koneksi, seperti “established” atau “invalid”. Selain itu, firewall juga digunakan untuk kontrol aliran data antar jaringan, baik itu dari jaringan publik ke jaringan lokal atau sebaliknya.

### 4. **Jelaskan menurut anda apa itu NAT?**
NAT (Network Address Translation) adalah sebuah teknik yang digunakan untuk mengubah alamat IP sumber atau tujuan dalam paket data yang melewati router atau firewall. Dalam MikroTik, NAT digunakan untuk menghubungkan jaringan lokal (private) dengan jaringan publik (internet), serta mengelola komunikasi antar alamat IP yang berbeda.