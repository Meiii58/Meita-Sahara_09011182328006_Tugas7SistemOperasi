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
- systemctl digunakan untuk memulai, menghentikan, mengaktifkan, menonaktifkan, dan memeriksa status dari layanan yang berjalan di sistem.
- Saat menjalankan status, systemd akan menampilkan informasi tentang apakah layanan sedang berjalan (aktif), berhenti (mati), atau mengalami kesalahan.
- SSH : Jika layanan ini aktif, sistem akan siap menerima koneksi SSH dari komputer atau perangkat lain.

#### sudo systemctl status ssh digunakan untuk memeriksa apakah layanan OpenSSH Server sedang aktif, berhenti, atau mengalami masalah.

# Step 4: Configure the firewall
![step4](https://github.com/user-attachments/assets/0a5bcb71-1a85-4a29-9c52-58c987b8e670)
- UFW adalah singkatan dari Uncomplicated Firewall, yaitu alat yang digunakan untuk mengelola firewall di Linux dengan cara yang lebih sederhana dan mudah dibandingkan menggunakan iptables secara langsung.
- Opsi status digunakan untuk memeriksa status saat ini dari firewall UFW, termasuk apakah firewall sedang aktif atau nonaktif.
- Status: inactive: Ini berarti firewall tidak aktif dan tidak ada aturan firewall yang diterapkan. Sistem tidak memblokir atau mengizinkan lalu lintas jaringan secara khusus melalui UFW.

#### Setelah menjalankan perintah sudo ufw status, mungkin akan melihat beberapa jenis output tergantung pada konfigurasi firewall saat ini.

- sudo ufw allow ssh : Mengizinkan akses jarak jauh: Jika Anda mengelola server atau sistem secara jarak jauh melalui SSH, perintah ini memungkinkan Anda untuk membuka firewall dan menerima koneksi tersebut.

# Step 5: Connect to the server
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
