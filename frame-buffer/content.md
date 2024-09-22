# Frame Buffer

## Missing in 
- semester: 2
- matkul: Sistem Operasi

## Pengertian
Frame buffer adalah area memori yang digunakan untuk menyimpan data representasi piksel dari suatu gambar atau tampilan yang akan ditampilkan di layar. 

Frame buffer berfungsi sebagai tempat penyimpanan sementara untuk data visual sebelum dikirim ke perangkat output, seperti monitor. 

Dalam komputer grafis, frame buffer biasanya digunakan oleh kartu grafis atau sistem operasi untuk menyimpan informasi mengenai setiap piksel, termasuk warna dan intensitas cahaya.

Setiap piksel pada layar memiliki informasi yang tersimpan di frame buffer, yang sering kali disusun dalam bentuk matriks. Data ini diperbarui secara teratur ketika terjadi perubahan tampilan.

Ukuran frame buffer tergantung pada resolusi layar dan kedalaman warna (jumlah bit per piksel yang menyatakan warna). **Misalnya** layar dengan resolusi 1920x1080 dan kedalaman warna 24-bit per piksel memerlukan frame buffer yang lebih besar dibandingkan layar dengan resolusi dan kedalaman warna yang lebih kecil.

## Penggunaan

Frame buffer mendukung operasi rendering dan penggambaran grafis pada sistem operasi berbasis GUI, video games, aplikasi multimedia, dan lain sebagainya.

## Cara menggunakan

Pada dasarnya frame buffer pasti ada pada sistem operasi yang memiliki akses ke graphic interface. Berikut cara menggunakannya:
1. Memeriksa Ketersediaan Frame Buffer

    Periksa apakah perangkat frame buffer tersedia di sistem:

    ```
    ls /dev/fb0
    ```

    Jika output menampilkan /dev/fb0, itu berarti frame buffer aktif dan dapat diakses.

2. Mengakses dan menggambar ke Frame Buffer

    Kita dapat membaca atau menulis langsung ke frame buffer menggunakan file device /dev/fb0. Contoh menggunakan program C untuk mengakses frame buffer:

    ```
    #include <fcntl.h>
    #include <linux/fb.h>
    #include <sys/mman.h>
    #include <unistd.h>
    #include <stdio.h>
    #include <stdlib.h>

    int main() {
        int fb_fd = open("/dev/fb0", O_RDWR);
        if (fb_fd == -1) {
            perror("Error membuka /dev/fb0");
            return 1;
        }

        struct fb_var_screeninfo vinfo;
        if (ioctl(fb_fd, FBIOGET_VSCREENINFO, &vinfo)) {
            perror("Error mendapatkan informasi layar");
            close(fb_fd);
            return 1;
        }

        long screensize = vinfo.yres_virtual * vinfo.xres_virtual * vinfo.bits_per_pixel / 8;
        unsigned char *fbptr = (unsigned char *)mmap(0, screensize, PROT_READ | PROT_WRITE, MAP_SHARED, fb_fd, 0);
        if ((long)fbptr == -1) {
            perror("Error mmap frame buffer");
            close(fb_fd);
            return 1;
        }

        // Menggambar piksel pada koordinat (100,100) dengan warna merah (RGB)
        int x = 100, y = 100;
        long location = (x + vinfo.xoffset) * (vinfo.bits_per_pixel / 8) +
                        (y + vinfo.yoffset) * vinfo.line_length;

        *(fbptr + location) = 255;        // Biru
        *(fbptr + location + 1) = 0;      // Hijau
        *(fbptr + location + 2) = 0;      // Merah
        *(fbptr + location + 3) = 0;      // Transparansi (jika 32-bit)

        munmap(fbptr, screensize);
        close(fb_fd);
        return 0;
    }
    ```
3. Tips

    - Kedalaman warna (bits per pixel): Pastikan Kita menyesuaikan jumlah byte yang ditulis untuk setiap piksel berdasarkan kedalaman warna layar (misalnya, 32-bit = 4 byte per piksel, 24-bit = 3 byte per piksel).
    - Manajemen memori: Biasanya, frame buffer di-mmap (memory-mapped) agar lebih efisien. Ini menghindari overhead dari operasi I/O disk.
4. Membersihkan Layar

    Untuk membersihkan layar, Kita dapat mengisi seluruh frame buffer dengan nilai nol, yang akan membuat layar menjadi hitam.
    ```
    memset(fbptr, 0, screensize);
    ```
5. Menggunakan Frame Buffer dalam Pemrograman Grafis

    Kita juga dapat menggunakan pustaka grafis seperti SDL atau DirectFB untuk mempermudah interaksi dengan frame buffer, terutama saat membuat aplikasi grafis yang lebih kompleks.

## Kesimpulan
Dengan memahami bagaimana mengakses dan menulis ke frame buffer, Kita dapat langsung menggambar di layar tanpa melalui sistem grafis tingkat tinggi. Ini bermanfaat dalam sistem embedded, low-level programming, atau aplikasi yang membutuhkan kontrol langsung terhadap layar.