# How to Install and Configure SSH

# Step 1: Prepare linux mint
![step1](https://github.com/user-attachments/assets/7049e30b-6785-4071-9fe8-3965b3b08024)
- sudo apt update: Sistem memperbarui daftar paket dari repository.
- sudo apt upgrade: Sistem memeriksa paket yang sudah diinstal dan memperbaruinya ke versi terbaru jika ada versi yang lebih baru.
- Operator && digunakan untuk menggabungkan dua perintah. Artinya, perintah kedua (sudo apt upgrade) hanya akan dijalankan jika perintah pertama (sudo apt update) berhasil tanpa kesalahan. Jika sudo apt update gagal, maka sudo apt upgrade tidak akan dijalankan.

# Step 2: Install SSH on linux mint
![step2](https://github.com/user-attachments/assets/ab2d6575-3eeb-4398-b36d-9add59d83560)
- sudo adalah singkatan dari SuperUser DO, yang digunakan untuk menjalankan perintah dengan hak akses administrator (root).
- apt (Advanced Package Tool) adalah manajer paket yang digunakan untuk mengelola perangkat lunak pada sistem berbasis Debian.
- dengan perintah install, memberi tahu APT untuk menginstal paket yang disebut setelahnya, dalam hal ini adalah openssh-server.
- openssh-server adalah paket yang berisi OpenSSH Server, yang memungkinkan komputer Anda bertindak sebagai server SSH.

#### sudo apt install openssh-server menginstal OpenSSH Server, yang memungkinkan sistem Anda menjadi server SSH untuk menerima koneksi jarak jauh yang aman.

# Step 3: Start SSH
![step3](https://github.com/user-attachments/assets/c894ac79-1bd2-4188-a953-7ba6be6e2d8d)

enable :
- Opsi enable digunakan untuk mengaktifkan layanan secara otomatis setiap kali sistem dinyalakan (boot).
- Ketika sebuah layanan di-enable, sistem akan secara otomatis menjalankan layanan tersebut pada startup atau booting berikutnya.

-- now :
- Opsi --now adalah tambahan untuk perintah enable yang berarti memulai layanan sekarang juga setelah diaktifkan.
- Tanpa --now, perintah enable hanya akan mengaktifkan layanan untuk dijalankan saat boot, tetapi tidak memulainya langsung pada saat perintah tersebut dijalankan.

#### sudo systemctl enable --now ssh memastikan bahwa layanan SSH:
- Diaktifkan untuk memulai secara otomatis saat boot.
- Dimulai segera pada saat perintah tersebut dijalankan, sehingga sistem segera bisa menerima koneksi SSH.


#### sudo systemctl status ssh
- sudo adalah singkatan dari SuperUser DO, yang digunakan untuk menjalankan perintah dengan hak akses administrator (root).
- systemctl digunakan untuk memulai, menghentikan, mengaktifkan, menonaktifkan, dan memeriksa status dari layanan yang berjalan di sistem.
- Saat menjalankan status, systemd akan menampilkan informasi tentang apakah layanan sedang berjalan (aktif), berhenti (mati), atau mengalami kesalahan.
- SSH : Jika layanan ini aktif, sistem akan siap menerima koneksi SSH dari komputer atau perangkat lain.

#### sudo systemctl status ssh digunakan untuk memeriksa apakah layanan OpenSSH Server sedang aktif, berhenti, atau mengalami masalah.

# Step 4: Configure the firewall
![step4](https://github.com/user-attachments/assets/0a5bcb71-1a85-4a29-9c52-58c987b8e670)
- UFW adalah singkatan dari Uncomplicated Firewall, yaitu alat yang digunakan untuk mengelola firewall di Linux dengan cara yang lebih sederhana dan mudah dibandingkan menggunakan iptables secara langsung.
- sudo adalah singkatan dari SuperUser DO, yang digunakan untuk menjalankan perintah dengan hak akses administrator (root).
- Opsi status digunakan untuk memeriksa status saat ini dari firewall UFW, termasuk apakah firewall sedang aktif atau nonaktif.
- Status: inactive: Ini berarti firewall tidak aktif dan tidak ada aturan firewall yang diterapkan. Sistem tidak memblokir atau mengizinkan lalu lintas jaringan secara khusus melalui UFW.

#### Setelah menjalankan perintah sudo ufw status, mungkin akan melihat beberapa jenis output tergantung pada konfigurasi firewall saat ini.

- sudo ufw allow ssh : Mengizinkan akses jarak jauh: Jika Anda mengelola server atau sistem secara jarak jauh melalui SSH, perintah ini memungkinkan Anda untuk membuka firewall dan menerima koneksi tersebut.

# Step 5: Connect to the server
![ifconfig](https://github.com/user-attachments/assets/7fbd25fb-ca59-49d3-a9fe-da46f81bca6f)
![step5](https://github.com/user-attachments/assets/34a837b9-db41-4ea1-b43e-bc92bed5d7ec)
- rayyisptiany adalah nama pengguna di server.
- Simbol @ memisahkan nama pengguna dari alamat IP atau hostname dari server tujuan.
- 10.8.141.251 adalah alamat IP dari server yang akan diakses.

#### setelah perintah dijalankan maka:
 
  Koneksi SSH Dimulai:
- Perintah ini akan mencoba menghubungkan komputer Anda ke server jarak jauh yang beralamat IP atau hostname yang telah ditentukan.
- Jika ini adalah pertama kalinya Anda menghubungkan ke server tersebut, Anda akan menerima pesan peringatan terkait host authenticity.
  Anda perlu menjawab yes untuk melanjutkan koneksi.
  
#### Memasukkan kata sandi :
- Setelah mengonfirmasi koneksi, Anda akan diminta memasukkan kata sandi untuk pengguna yang Anda tentukan.
- Jika berhasil, Anda akan masuk ke sesi SSH dan bisa mulai berinteraksi dengan server jarak jauh melalui terminal.

# Step 6: Configure SSH
![step6](https://github.com/user-attachments/assets/4f78b033-3bc8-472c-8487-827f8d5aaf67)
- sudo: Memberikan hak akses administrator yang diperlukan untuk menyalin file di direktori sistem.
- cp: Perintah untuk menyalin file atau direktori.
- /etc/ssh/sshd_config: Lokasi file konfigurasi utama OpenSSH server. File ini berisi pengaturan-pengaturan yang mengontrol perilaku server SSH.
- /etc/ssh/sshd_config.initial: Nama file cadangan yang akan dibuat. Dengan menambahkan .initial, Anda menandakan bahwa ini adalah salinan awal dari konfigurasi asli.

![step6 1](https://github.com/user-attachments/assets/4b976cf5-74ea-41cd-9920-a59b501b5a11)
- sudo: Memberikan hak akses administrator untuk mengedit file sistem.
- nano: Perintah ini membuka editor teks Nano di terminal. Nano adalah editor teks berbasis terminal yang sederhana dan mudah digunakan.
- /etc/ssh/sshd_config: Lokasi file konfigurasi SSH yang akan diedit.

#### sudo systemctl restart ssh
- sudo: Menjalankan perintah dengan hak akses administratif.
- systemctl: Alat manajemen layanan yang digunakan untuk mengontrol layanan pada sistem yang menggunakan systemd.
- restart: Tindakan untuk menghentikan dan memulai kembali layanan.
- ssh: Nama layanan SSH yang akan direstart.

#### ssh -p 49532 rayyiseptiany@10.8.141.251
- ssh: Perintah untuk memulai sesi SSH (Secure Shell), yang memungkinkan Anda untuk terhubung secara aman ke server jarak jauh.
- -p port_number: Opsi -p digunakan untuk menentukan nomor port khusus yang akan digunakan untuk koneksi SSH. port_number harus diganti dengan nomor port baru yang telah dikonfigurasi dalam file konfigurasi SSH server (sshd_config).
- Secara default, SSH menggunakan port 22. Jika port ini diubah ke port lain untuk keamanan, perintah ini menginstruksikan SSH untuk menggunakan port yang baru.
- username: Nama pengguna yang digunakan untuk masuk ke server jarak jauh. Harus disesuaikan dengan akun pengguna yang ada di server tujuan.
- IP_address: Alamat IP dari server yang ingin diakses. Alternatifnya, Anda juga bisa menggunakan nama domain server.

![gambarstep6](https://github.com/user-attachments/assets/f33467c9-5a85-49dc-8649-047e82729288)
- Menentukan nomor port baru yang akan digunakan oleh layanan SSH. Port ini berada dalam rentang dinamis (49152 - 65535), yang lebih aman dibandingkan port standar (22).

![gambarstep6 1](https://github.com/user-attachments/assets/495f35a1-d94d-412d-b756-ab2b5355411e)
- PermitRootLogin no: Menonaktifkan login langsung sebagai superuser (root) melalui SSH. Ini memastikan bahwa pengguna harus login menggunakan akun pengguna biasa, kemudian menggunakan perintah sudo untuk menjalankan perintah sebagai superuser.
- PubkeyAuthentication yes: Mengonfigurasi server SSH untuk hanya menerima otentikasi kunci publik, meningkatkan keamanan dengan mencegah penggunaan kata sandi yang lebih rentan terhadap serangan.

# Download Putty
## 1. Tambahkan repository universe
![putty1](https://github.com/user-attachments/assets/48c4d37c-2b23-4ea0-a922-acb890a9f093)
## 2. Update setelah menambahkan repository
![putty2](https://github.com/user-attachments/assets/e49bdea5-1a2d-4715-8acb-8a8f63a61eeb)
## 3. Install PuTTY
![putty3](https://github.com/user-attachments/assets/5754d379-99eb-40c3-873c-90409454d78b)
## 4. Menampilkan versi PuTTY
![putty4](https://github.com/user-attachments/assets/dd0e7af4-fa4f-4483-910a-5b14b1c417ea)
## 5. Tampilan pada saat PuTTY dibuka
![tampilanputty](https://github.com/user-attachments/assets/48fef00d-60d2-4f92-a423-bc58450e9cbd)

