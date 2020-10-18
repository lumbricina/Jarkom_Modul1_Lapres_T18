# LapresJarkom Modul1 Praktikum T18

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

###### 1. Webserver yang digunakan pada "testing.mekanis.me" adalah nginx/1.14.0 (Ubuntu). Didapat menggunakan filter `'http.host=="testing.mekanis.me"`. Kemudian dicek menggunakan TCP Stream.
![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/1.png)

###### 2. Mengeksport http kemudian filter dengan nama file yang sudah diberi tahu di soal.

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/2.png)

Tampilan “Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg”:

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg)

###### 3. Untuk mencari semua yang menggunakan username dan password menggunakan filter `http.request.method == POST`. Setelah itu cek detail nya menggunakan TCP Stream. 

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/3.png)

###### 4. Menggunakan `http.authbasic` untuk memfilter semua yang menggunakan basic authentication method

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/4.png)

###### 5. Untuk mendapatkan Nama pengguna dan sandi, pertama menggunakan filter `http.host=="aku.pengen.pw"`. Kemudian pilih salah satu, lihat pada bagian authorization dan credentials

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/5a.png)

Nama pengguna : kakakgamtenk
Sandi         : hartatahtabermuda

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/5b.png)

###### 6. Menggunakan `follow tcp stream`

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6a.png)

Lihat pada stream 12 -> show and save data as RAW -> save as ZIP file

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6b.png)

File zip akan terlihat sebagai berikut :

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6c.png)

Untuk membuka file `Open This.pdf` dibutuhkan password. Untuk mencari password tersebut, dicari yang ada zipkey.txt kemudian follow tcp stream

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6d.png)

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6e.png)

Muncul password, gunakan, dan tampilan isi pdf adalah sebagai berikut

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/6f.png)

###### 7. Menggunakan `ftp-data contains "Yes.pdf"`

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/7a.png)

Follow tcp stream dan save file as raw dalam bentuk zip

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/7b.png)

Tampilan Yes.pdf adalah sebagai berikut

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/7c.png)

###### 8. Menggunakan `ftp.request.command == RETR`

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/8e.png)

Kemudian follow tcp stream dan dapat terlihat bahwa menggunakan Microsoft FTP Service

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/8c.png)

###### 9. Menggunakan `ftp contains "USER"` dan `ftp contains "PASS"
USER dhana
PASS dhana123

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/9a.png)


![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/9b.png)

###### 10. Mencari menggunakan hex value dari hint yang diberikan

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/10a.png)

Follow tcp stream dan didapat link dari file yang dimaksud

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/10b.png)

Buka link tersebut dan terlihat seperti gambar berikut

![](https://github.com/lumbricina/Jarkom_Modul1_Praktikum_T18/blob/main/img/10c.png)

###### 11. port 21

###### 12. src port 80

###### 13. dst port 443

###### 14. `src host 192.168.0.15` -> IP dari komputer

###### 15. Pertama melakukan ping ke http://monta.if.its.ac.id/ untuk mendapatkan ip addressnya. Didapatkan IP 103.94.190.11, gunakan `capture filter` ini untuk mengambil paket yang tujuannya ke monta.if.its.ac.id
`dst host 103.94.190.11`

## Kendala
tidak ada kendala yang signifikan atau kompleks selama mengerjakan, hanya kendala penyesuaian waktu pengerjaan, serta pada display capture yang sedikit ada kesalahan

