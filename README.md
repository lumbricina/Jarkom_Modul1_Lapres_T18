# Jarkom Modul1 Praktikum T18

### Soal
Terdapat tiga buah file *.pcapng yang mendukung soal-soal display filter, yaitu:
- [File pertama](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/pcapng/soal_jarkom_modul1_no1-5%2C10.pcapng) untuk menjawab soal nomor 1-5 dan nomor 10.
- [File kedua](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/pcapng/soal_jarkom_modul1_no6%2C7%2C9.pcapng) untuk menjawab soal nomor 6, 7, dan 9.
- [File ketiga](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/pcapng/soal_jarkom_modul1_no8.pcapng) untuk menjawab soal nomor 8.

##### A. Display Filter
1. Sebutkan webserver yang digunakan pada "testing.mekanis.me"!
2. Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!
3. Cari username dan password ketika login di "ppid.dpr.go.id"!
4. Temukan paket dari web-web yang menggunakan basic authentication method!
5. Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!
6. Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut).
7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut.
Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"
8. Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!
9. Cari username dan password ketika login FTP pada localhost!
10. Cari file .pdf di wireshark lalu download dan buka file tersebut!
clue: "25 50 44 46" 

##### B. Capture Filter
11. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
12. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
14. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
15. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!

-------------------------
### Jawaban
1. Webserver yang digunakan pada "testing.mekanis.me" adalah nginx/1.14.0 (Ubuntu). Didapat menggunakan filter '''http.host=="testing.mekanis.me"'''. Kemudian dicek menggunakan TCP Stream.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/1.png)

2. Mengeksport http kemudian filter dengan nama file yang sudah diberi tahu di soal.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/2.png)
Tampilan “Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg”:
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg)

3. Untuk mencari semua yang menggunakan username dan password menggunakan filter "http.request.method == POST". Setelah itu cek detail nya menggunakan TCP Stream. 
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/3.png)

4. 
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/4.png)

5.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/5a.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/5b.png)

6.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6a.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6b.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6c.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6d.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6e.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6f.png)

7. Ubah Yes.pdf menjadi hex menggunakan calculator -> 59 65 73 2e 70 64 66.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/7a.png)
Cari menggunakan hex value
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/7b.png)

8.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/8a.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/8b.png)

9.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/9.png)

10.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/10a.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/10b.png)
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/10c.png)

11.

12.

13.

14.

15.

