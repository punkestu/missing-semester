# HTTP

## Pengertian
HTTP adalah salah satu struktur protokol yang dapat digunakan untuk transaksi data antar 2 endpoint yang berbentuk request dan response. 

HTTP dijalankan menggunakan protokol TCP dimana data akan dijamin terkirim secara sempurna tapi harus mengorbankan waktu pengiriman.

HTTP hanya akan berjalan 1 kali dimana setelah request dan response selesai dijalankan, maka koneksi akan langsung ditutup dan kita harus melakukan request dari awal lagi jika ingin membuat koneksi baru.

## Struktur
HTTP punya 2 struktur khusus yang sudah menjadi standar selama ini yaitu struktur untuk request dan response.

untuk Request:
```
METHOD /ENDPOINT HTTP/VERSI_HTTP
HEADER
<<LINE KOSONG>>
BODY
```

untuk Response:
```
HTTP/VERSI_HTTP KODE_STATUS STATUS
HEADER
<<LINE KOSONG>>
BODY
```

- METHOD: method yang digunakan untuk request (misal: GET, POST, PUT, dll).
- ENDPOINT: path untuk mengakses server (misal: http://facebook.com/user maka ENDPOINTnya adalah /user).
- KODE_STATUS & STATUS: menggambarkan status dari sebuah request dimana setiap status akan memiliki kode masing-masing (misal: jika request berhasil dilakukan maka STATUSnya adalah OK dan KODE nya adalah 200. akses ini untuk lihat lebih lengkap [https://developer.mozilla.org/en-US/docs/Web/HTTP/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)).
- HEADER: data-data penunjang request yang sebaiknya dipisah dari BODY dan akan dibaca terlebih dahulu sebelum BODY (misal: data tentang response seperti apa yang seharusnya dikembalikan server, data tentang jenis BODY yang kita kirim, atau data tentang authentikasi).
- BODY: data-data yang akan kita kirim ke server ketika melakukan request (misal: data email dan password untuk melakukan login akan disimpan di BODY). BODY harus dipisah 1 enter dengan header.

## Cara melakukan Request HTTP
Cara mudahnya kita bisa menggunakan aplikasi yang dibangun khusus untuk melakukan request misalnya CURL, WGET, atau Postman jika ingin yang lebih praktis.

Apapun aplikasi yang digunakan, yang utama adalah kita harus menyiapkan semua komponen yang dibutuhkan untuk melakukan request HTTP terutama METHOD dan ADDRESS/DOMAIN+ENDPOINT.

## Cara menghandle Request HTTP
Untuk menghandle request HTTP kita hanya perlu memisahkan komponen-komponen sesuai dengan struktur HTTP sebelumnya sehingga nantinya kita bisa memetakan handler atau program mana yang akan dikerjakan sesuai dengan request yang diberikan.

Ketika request sudah dikerjakan, untuk melakukan response kita hanya perlu menyusun hasil yang didapatkan sesuai struktur response sebelumnya.