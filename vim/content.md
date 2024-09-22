# VIM

## Pengertian
Vim merupakan text editor (jika dikonfigurasi dengan benar bisa menjadi IDE) yang berbasis terminal. Karena berbasis terminal, Vim cukup sering digunakan saat melakukan konfigurasi pada server karena umumnya OS yang digunakan pada server hanya akan memberikan iterface CLI (CPanel tidak dihitung).

Namun diluar itu, Vim juga bisa digunakan sebagai IDE seperti vscode dan semacamnya. Kita bisa menginstall plugin-plugin yang dapat membantu dalam proses koding misal linter, lsp, dan semacamnya. Kelebihan menggunakan Vim sebagai IDE adalah kita tidak perlu menggunakan mouse lagi karena dalam Vim semua perintah bisa dijalankan hanya dengan keyboard saja.

## Cara penggunaan
Pada beberapa OS, Vim sudah terinstall bersama dengan OS nya misal pada beberapa distro linux. Namun untuk beberapa OS lain, Vim tidak diinstall secara built in.

- Untuk menjalankan Vim, kita bisa menjalankan perintah `vim` pada terminal
- Setelah masuk ke tampilan Vim, maka ada 1 hal yang perlu diperhatikan yaitu mode yang aktif saat ini
- Ada 3 mode yang ada di Vim yaitu ***NORMAL***, ***INSERT***, dan ***VISUAL***. Umumnya mode yang aktif ketika kita baru membuka Vim adalah NORMAL
- Pada mode ***NORMAL*** kita bisa melakukan perintah-perintah tertentu menggunakan keyboard kita misal menekan key 'u' akan melakukan undo, key 'i' untuk masuk ke mode INSERT dengan kursor akan berada pada posisi kursor terakhir. 
- Selain itu kita juga bisa menjalankan command vim ketika berada di mode NORMAL dengan menekan ':' lalu menginputkan command yang ingin dijalankan contohnya command `w` untuk save, `q` untuk menutup vim atau tab vim yang aktif, `wq` untuk save dan quit.
- Pada mode ***INSERT*** kita bisa melakukan input pada file yang kita edit. Pada mode ini kita tidak bisa menggunakan perintah-perintah yang ada pada mode NORMAL. 
- Untuk masuk ke mode INSERT ada beberapa cara yang bisa dilakukan contohnya menekan key 'i' untuk masuk mode INSERT dan kursor berada pada kursor terakhir saat mode NORMAL, key 'a' maka kursor akan berada didepan kursor terakhir, key 'o' maka akan dibuatkan 1 line dibawah kursor terakhir dan kursor akan berpindah ke line tersebut.
- Pada mode ***VISUAL*** kita bisa melakukan selection atau blocking pada text tertentu. Untuk masuk mode ini kita hanya perlu menekan key 'v' maka selection akan dimulai dari kursor terakhir kita. Pada mode ini kita juga bisa menjalankan perintah untuk modifikasi text misal copy, cut, delete dan semacamnya.

## Sumber belajar
- [https://www.vim.org/docs.php](https://www.vim.org/docs.php)