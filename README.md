# Jarkom-Modul-1-A13-2021
**Modul 1: Wireshark dan Crimping**

|Nama|NRP|
|----|-----|
|Afifah Nur Sabrina Syamsudin|05111940000022|
|James Rafferty Lee|05111940000055|
|Zulfiqar Fauzul Akbar|05111940000101|

### Soal No. 1
### Soal No. 2
### Soal No. 3
### Soal No. 4
### Soal No. 5
### Soal No. 6
### Soal No. 7
### Soal No. 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!

**Penyelesaian**

wireshark filter expression: `ftp.request.command == STOR`.
![soal8](https://user-images.githubusercontent.com/75364000/134761082-bea106c2-0677-42e9-945b-7ec58c9309ce.jpg)

### Soal No. 9
Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

**Penyelesaian**

gunakan ctrl + f untuk mengextend display filter, kemudian ubah filter menjadi string dan gunakan wireshark filter expression: `secret.zip ftp`.
pilih paket dengan protocol `FTP-DATA` dan info `STOR secret.zip`,  lalu follow dan pilih `TCP Stream`.
![soal9](https://user-images.githubusercontent.com/75364000/134764729-30c7792d-ff6e-49d3-b549-c062f5556cca.jpg)

ubah data dari ASCII ke Raw, selanjutnya save as dengan penamaan `secret.zip` ke komputer.
![soal9 (2)](https://user-images.githubusercontent.com/75364000/134764725-7d0db9d0-1da0-4fc7-ab32-aa8e6475d00a.jpg)

buka zip file dan terdapat file Wanted.pdf yang memerlukan password.
![soal9 (3)](https://user-images.githubusercontent.com/75364000/134764726-06e81246-9e4e-4b83-9423-b0cf15147414.jpg)

### Soal No. 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

**Penyelesaian**

gunakan ctrl + f untuk mengextend display filter, kemudian ubah filter menjadi string dan gunakan wireshark filter expression: `history.zip ftp`.
pilih paket dengan protocol `FTP-DATA` dan info `STOR history.zip`,  lalu follow dan pilih `TCP Stream`. 
ditemukan clue yaitu file selanjutnya pada, line ke `289` dengan penamaan `bukanapaapa.txt`.
![soal10](https://user-images.githubusercontent.com/75364000/134764918-0fbaad72-057b-4017-90a1-f2f9a0f8c077.jpg)

gunakan wireshark filter expression: `bukanapaapa.zip ftp`.
pilih paket dengan protocol `FTP-DATA` dan info `STOR bukanapaapa.zip`,  lalu follow dan pilih `TCP Stream`. 
ditemukan password : **dibilangbukanapaapajugagapercaya**
![soal10 (2)](https://user-images.githubusercontent.com/75364000/134764955-434c5ede-7ee2-4ac0-8927-2b6b0675cdc7.jpg)

isi dari file Wanted.pdf
![soal10 (3)](https://user-images.githubusercontent.com/75364000/134764985-420edbac-1f57-4ee1-80e3-b6a138df6b63.jpg)

### Soal No. 11
### Soal No. 12
### Soal No. 13
### Soal No. 14
### Soal No. 15

### Kendala yang Dialami
