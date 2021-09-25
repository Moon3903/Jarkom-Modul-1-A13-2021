# Jarkom-Modul-1-A13-2021
**Modul 1: Wireshark dan Crimping**

|Nama|NRP|
|----|-----|
|Afifah Nur Sabrina Syamsudin|05111940000022|
|James Rafferty Lee|05111940000055|
|Zulfiqar Fauzul Akbar|05111940000101|

### Soal No. 1
Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

**Penyelesaian**

wireshark filter expression:0 `http.host == "ichimarumaru.tech"`<br>
Setelah itu pilih follow http stream dan muncul seperti berikut :

![eb0fcc1a422290d9910eafc9231ce0e2](https://user-images.githubusercontent.com/62832487/134772604-b4bf9ccd-e0c9-4664-b5f4-794ed8d24062.png)

### Soal No. 2
Temukan paket dari web-web yang menggunakan basic authentication method!

**Penyelesaian**

wireshark filter expression: `http.authbasic`<br>
di dapat : basic.ichimarumaru.tech

![57d70422263e3060de886a8f7f035fce](https://user-images.githubusercontent.com/62832487/134772688-2c645b91-fb93-4a87-8fa8-ae30972e27cb.png)

### Soal No. 3
Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!

**Penyelesaian**

Wireshark filter expression : `http.host == "basic.ichimarumaru.tech"`<br>
Lalu dapat dilihat pada isi package pada credential<br>
USER : kuncimenujulautan<br>
PASS : tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN<br>

![cc0c8e2485966f6347bd2e796dc3ac93](https://user-images.githubusercontent.com/62832487/134772725-6c2aaa6e-2acb-4681-a7f7-f7f059177b0f.png)

setelah itu log in pada webnya dan menjawab pertanyaan disana

![c904194b00589eb2caed6e6788b462e1](https://user-images.githubusercontent.com/62832487/134772782-8e1df55a-fc17-473c-8f58-88bef19a233f.png)

### Soal No. 4
Temukan paket mysql yang mengandung perintah query select!

**Penyelesaian**

Wireshark filter : `mysql contains "SELECT" || mysql contains "select"`<br>
Maka didapat command sql yg berisi SELECT atau select

![cd1b746ece835698fc828c8ef75fa110](https://user-images.githubusercontent.com/62832487/134772820-3124ec6c-7eed-4e1f-8bb4-253dd6456e68.png)

### Soal No. 5
Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

**Penyelesaian**

Wireshark filter : `mysql contains "INSERT"`<br>
maka di dapat id dan password nya<br>

Username : akakanomi<br>
Password : pemisah4lautan

![472a31472cfebb2af2b7f09ce004900b](https://user-images.githubusercontent.com/62832487/134772873-6948ff57-9fb0-46a6-a2ea-9da53d856154.png)

dan menyelesaikan soal pada web tersebut :

![74e28251ca816ceec051b5046302de7f](https://user-images.githubusercontent.com/62832487/134772899-790e00b4-babf-461c-be59-f4736059ce3f.png)

### Soal No. 6
Cari username dan password ketika melakukan login ke FTP Server!

**Penyelesaian**
Dengan menggunakan `ftp.request.command == USER || ftp.request.command == PASS` 
Di dapat <br>
USER : secretuser<br>
PASS : aku.pengen.pw.aja

![194ad03da9114c856abcd47e5e11e845](https://user-images.githubusercontent.com/62832487/134772921-c68a328c-1d81-48b1-8561-e0c3b9497a30.png)

### Soal No. 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

**Penyelesaian**
Pertama cari ftp yang mengandung “Real.pdf” dengan menggunakan `frame contains “Real.pdf”`, dan pilih follow tcp stream

![f30e3533819833217344b1029827a50c](https://user-images.githubusercontent.com/62832487/134772956-9c6c44b1-4cac-42e4-96d5-3df3f01623ba.png)

Setelah itu data diubah menjadi raw dan di save sebagai zip setelah itu di ekstrak

![b2a8f03b9bd7c66d12a3a3d0ce93eb13](https://user-images.githubusercontent.com/62832487/134772975-cf4cc75b-1b51-4094-b9ab-f3aff92a7976.png)

File real.pdf :

![0cf0478cd2f3ebb2f0a959decd276d3b](https://user-images.githubusercontent.com/62832487/134773009-6c42c8c6-5771-40fb-b861-129fa9813d73.png)


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

Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80! 

**Penyelesaian**

Wireshark capture filter : src port 80
![image](https://user-images.githubusercontent.com/68369091/134773171-b0fa9095-8698-4d4c-ba5c-63fced4c5207.png)

### Soal No. 12

Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

**Penyelesaian**

Wireshark capture filter : port 21

![image](https://user-images.githubusercontent.com/68369091/134773184-bd17c4b3-0843-4c12-9515-a7b2b8f67eb2.png)

### Soal No. 13

Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

**Penyelesaian**

Karena disuruh menampilkan, bukan mengambil, menggunakan display filter.

Wireshark display filter : tcp.dstport == 443

![image](https://user-images.githubusercontent.com/68369091/134773198-e4e03bd2-8cbb-43f1-9771-7295e681b2bd.png)


### Soal No. 14

Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

**Penyelesaian**

Wireshark capture filter : dst kemenag.go.id

![image](https://user-images.githubusercontent.com/68369091/134773208-870e484f-5392-4491-9865-8ec84dae544e.png)


### Soal No. 15

Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

**Penyelesaian**

Wireshark capture filter: ip src 192.168.0.10

![image](https://user-images.githubusercontent.com/68369091/134773223-00c7b8a1-a75d-4bf3-b9aa-c12d6fa220cf.png)


### Kendala yang Dialami
- Kurang teliti dalam membaca soal yang mengakibatkan salah satu soal menjadi revisi
