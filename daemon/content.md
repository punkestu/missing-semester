# Daemon

## Pengertian Daemon
Daemon adalah proses latar belakang di sistem operasi Unix/Linux yang berjalan secara terus-menerus tanpa interaksi langsung dari pengguna. Daemon biasanya menjalankan tugas-tugas otomatis atau melayani permintaan sistem tanpa terhubung ke terminal.

## Contoh Penggunaan
- **`cron`:** Menjalankan tugas yang dijadwalkan, seperti backup data atau menjalankan skrip pada waktu tertentu.
- **`sshd`:** Melayani koneksi SSH jarak jauh.
- **`httpd`:** Server web yang melayani permintaan HTTP.

Semua aplikasi tersebut berjalan di background.

## Cara Penggunaan Daemon
Daemon biasanya dimulai saat sistem booting dan dapat dikelola menggunakan sistem `systemd` atau `init` (jika aplikasi daemon tersebut sudah diregistrasi kedalam `systemd`). Untuk mengelola daemon di Linux, gunakan perintah `systemctl`:

- **Memulai daemon:**
  ```bash
  sudo systemctl start nama_daemon
  ```

- **Menghentikan daemon:**
  ```bash
  sudo systemctl stop nama_daemon
  ```

- **Melihat status daemon:**
  ```bash
  sudo systemctl status nama_daemon
  ```

- **Mengaktifkan daemon agar otomatis berjalan saat boot:**
  ```bash
  sudo systemctl enable nama_daemon
  ```

## Kesimpulan
Daemon adalah proses yang berjalan di latar belakang untuk menangani tugas-tugas otomatis atau layanan sistem. Ini sangat penting untuk operasi sistem yang membutuhkan pengelolaan berkelanjutan tanpa interaksi langsung dari pengguna.