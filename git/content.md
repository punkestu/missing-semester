# GIT

## Pengertian
Git adalah tool yang digunakan untuk memisahkan kode-kode yang kita buat dalam satu projek. Misal jika kita sudah membuat sebuah aplikasi atau fitur atau fungsi yang berjalan dengan baik, maka kita bisa simpan kode atau kondisi tersebut kedalam sebuah state yang disebut commit (atau bisa disebut versi jika skalanya lebih besar). 

Dengan begitu ketika kita merubah kode tersebut dan ternyata apa yang kita rubah ternyata malah merusak aplikasi kita, kita tinggal kembali ke commit terakhir yang kita buat sebelumnya dan akan menghilangkan semua perubahaan yang telah kita lakukan.

## Penggunaan
Seperti yang telah disebutkan diatas, git bisa digunakan untuk membuat versi atau memisahkan kode-kode yang telah kita buat dengan perubahan yang kita tambahkan. Namun selain itu git juga bisa digunakan ketika kita ingin melakukan kolaborasi kode dengan orang lain. Hal ini bisa dilakukan karena kita bisa memisahkan kode kita dengan kode teman kita sehingga tidak akan saling merusak satu sama lain.

## Cara penggunaan
*Pastikan kalian sudah menginstall Git di komputer kalian sebelum melanjutkan

Untuk memulai menggunakan Git, kita bisa melakukan sebuah inisialisasi. Caranya adalah kalian bisa mengakses terminal dan masuk ke folder yang ingin diinisialisasi lalu jalankan perintah yang ``git init`` maka folder tersebut dan seluruh isinya akan terintegrasi dengan git.

Lalu kalian bisa menuliskan kode yang kalian butuhkan di dalam folder tersebut dan jika kalian rasa sudah cukup untuk menulis kode dan sudah saatnya menyimpan kondisi yang sudah ada, maka kalian bisa melakukan ***commit***. Untuk melakukan commit ada beberapa langkah yang perlu dilakukan antara lain:
1. tambahkan kondisi yang sekarang ke dalam staging dengan perintah ``git add <nama-file-yang-ingin-di-commit>`` atau bisa dengan ``git add .`` jika ingin melakukan commit dengan semua file yang telah diubah.
2. commit kondisi yang ada pada staging dengan perintah ``git commit -m "pesan commit"``.

Dengan begitu maka perubahan yang kalian lakukan sudah tersimpan dan dapat diakses kembali suatu saat ketika kalian ingin kembali ke kondisi tersebut.

## Kolaborasi
Untuk melakukan kolaborasi kalian bisa menggunakan fitur yang bernama branch. Dengan begitu maka kalian dan teman kalian bisa mengerjakan kode yang sama tanpa harus bersinggungan satu sama lain.

Untuk membuat branch kalian bisa menjalankan perintah ``git branch <nama-branch>`` lalu masuk ke branch tersebut dengan ``git checkout <nama-branch>``. Dengan membuat branch, maka jika kalian dan teman kalian melakukan commit di waktu yang sama, maka tidak akan terjadi tabrakan atau biasa disebut ***conflict***.

Namun dengan branch, maka kode kalian dan teman kalian tidak akan bergabung dan tidak akan bisa dijalankan secara bersamaan. Untuk itu kalian perlu menggabungkan kedua branch tersebut atau biasa disebut dengan ***merge***. Perintah yang digunakan untuk melakukan merge adalah ``git merge <nama-branch-yang-ingin-digabung>``. Namun kalian perlu berhati-hati jika melakukan merge karena ada kemungkinan terjadi conflict ketika merge.

## Sumber belajar git
- [https://www.w3schools.com/git/default.asp](https://www.w3schools.com/git/default.asp)
- [https://learngitbranching.js.org/](https://learngitbranching.js.org/)
