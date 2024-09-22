# Unix Domain Socket (UDS)

## Pengertian

Unix Domain Socket (UDS) adalah mekanisme komunikasi antar proses (IPC) di sistem operasi berbasis Unix, memungkinkan dua proses dalam satu mesin untuk berkomunikasi secara langsung.

Berbeda dengan TCP/IP socket yang beroperasi melalui jaringan, UDS menggunakan file di sistem file sebagai endpoint komunikasi, yang lebih cepat dan efisien karena tidak melibatkan protokol jaringan.

## Penggunaan

Contoh penggunaan UDS adalah pada database dimana jika kita ingin menggunakan database secara lokal, maka kita harus menginstall 2 aplikasi yaitu aplikasi client dan server.

Aplikasi server ini nantinya akan berjalan di background (daemon) dan dengan aplikasi client, kita bisa mengontrol aplikasi server tersebut dengan menggunakan mekanisme komunikasi UDS.

## Cara Menggunakan UDS
Untuk menggunakan UDS kita hanya perlu membuat sebuah file socket yang akan menjadi jalur komunikasi antar aplikasi daemon yang berjalan di background dengan aplikasi client yang bisa kita kontrol secara langsung.

**di sini contoh file socket tersebut adalah "/tmp/my_socket"*

1. Server UDS

```c
#include <sys/socket.h>
#include <sys/un.h>
#include <unistd.h>

int main() {
    int server_fd = socket(AF_UNIX, SOCK_STREAM, 0);
    struct sockaddr_un addr;
    addr.sun_family = AF_UNIX;
    strcpy(addr.sun_path, "/tmp/my_socket");
    bind(server_fd, (struct sockaddr*)&addr, sizeof(addr));
    listen(server_fd, 5);
    int client_fd = accept(server_fd, NULL, NULL);
}
```

2. Client UDS

```c
#include <sys/socket.h>
#include <sys/un.h>
#include <unistd.h>

int main() {
    int client_fd = socket(AF_UNIX, SOCK_STREAM, 0);
    struct sockaddr_un addr;
    addr.sun_family = AF_UNIX;
    strcpy(addr.sun_path, "/tmp/my_socket");
    connect(client_fd, (struct sockaddr*)&addr, sizeof(addr));
}
```

## Kesimpulan

Unix Domain Socket (UDS) menyediakan komunikasi antar proses yang cepat dan aman di dalam satu mesin, tanpa melibatkan protokol jaringan. Ini sangat efisien untuk aplikasi yang berjalan secara lokal, seperti server database atau microservices.
