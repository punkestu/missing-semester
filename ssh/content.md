# SSH

## Pengertian
SSH (Secure Shell) adalah protokol yang digunakan untuk mengakses dan mengelola komputer atau server secara remote melalui jaringan dengan koneksi terenkripsi. SSH memastikan keamanan komunikasi antara client dan server dengan mengenkripsi data yang dikirimkan.

## Contoh Penggunaan
- **Akses Remote:** Mengelola server secara aman dari jarak jauh.
- **Transfer File Aman:** Menggunakan **SCP** atau **SFTP** untuk mentransfer file antara dua komputer.
- **Tunneling (Port Forwarding):** Mengamankan koneksi aplikasi melalui SSH dengan meneruskan port dari satu mesin ke mesin lainnya.

## Cara Penggunaan

- **Menghubungkan ke server:**
  ```bash
  ssh username@hostname_or_ip
  ```
  Contoh:
  ```bash
  ssh bima@192.168.1.100
  ```

- **Menggunakan kunci SSH (Key Pair) untuk login tanpa password:**
  1. **Buat key pair:**
     ```bash
     ssh-keygen -t rsa
     ```
  2. **Salin kunci publik ke server:**
     ```bash
     ssh-copy-id username@hostname_or_ip
     ```

- **Transfer file menggunakan SCP:**
  ```bash
  scp local_file username@hostname_or_ip:/remote/directory/
  ```

- **SSH Tunneling (Port Forwarding):**
  ```bash
  ssh -L local_port:remote_host:remote_port username@hostname_or_ip
  ```

## Alternatif SSH

Salah satu alternatif dari SSH adalah `Telnet` dimana protokol ini adalah akses remote yang lebih tua, tetapi tidak aman karena tidak mengenkripsi data.

## Kesimpulan
SSH adalah alat utama untuk mengakses server dan mentransfer file secara aman. Alternatif seperti Telnet atau RDP dapat digunakan, tetapi dengan kelebihan dan kelemahan masing-masing, di mana SSH tetap menjadi pilihan paling aman untuk akses jarak jauh di lingkungan berbasis teks atau terminal.