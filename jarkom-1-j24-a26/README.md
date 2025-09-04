[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/8b_y5Av8)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Abillidya Nofianto Putri | 5025221164 | Jaringan Komputer (A) |
| Rhenaldy Chandra | 5025221190 | Jaringan Komputer (A) |

## Task 1

> a. Berapa banyak packet yang terekam pada file pcapng?

> _a. How many packets are recorded in the pcapng file?_

**Answer:**

- Flag

  `JARKOM24{K4mu_K3r3n_C45OOBALFOOGSR34R8CYI1A94ZMML50xL4ugh1hgppw7apa9oqsgk1pr7aa4}`

- Filter expression

- Explanation
  ![Screenshot 2024-09-13 174223](https://github.com/user-attachments/assets/a1bfcaa1-e2c6-4dc3-b46e-76303b278eff)

  Ketika file dibuka, pada bagian footer terdapat jumlah packets yang ter-capture, yaitu 1089

- Output result

  ![Screenshot 2024-09-11 184527](https://github.com/user-attachments/assets/18426ec1-110b-432c-87a4-7b5bcbbf12ef)

<br>
<br>

> b. Ada berapa jenis protocol yang terekam pada traffic

> _b. How many types of protocols are recorded in the traffic?_

**Answer:**

- Flag

  `JARKOM24{K4mu_K3r3n_C45OOBALFOOGSR34R8CYI1A94ZMML50xL4ugh1hgppw7apa9oqsgk1pr7aa4}`

- Filter expression
  
- Explanation
  ![Screenshot 2024-09-13 174637](https://github.com/user-attachments/assets/d1c7c455-b210-4874-a6d2-e478075d70cb)
  Pada bagian Statistics>Protocol Hierarcy, akan terdisplay statistic protocol yang ada pada file tersebut, yaitu `Multi Domain Name System`, `Hypertext Transfer Protocol`, `User Datagram Protocol`, dan `Transmission Control Protocol`, maka didapatkan hasil akhir sebanyak 4 jenis protocol.

- Output result

  ![Screenshot 2024-09-11 184527](https://github.com/user-attachments/assets/18426ec1-110b-432c-87a4-7b5bcbbf12ef)

> c. Sebutkan secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: protocol1,protocol2

> _c. List the protocols in descending alphabetical order, separated by commas. Example: protocol1,protocol2_

**Answer:**

- Flag

  `JARKOM24{K4mu_K3r3n_C45OOBALFOOGSR34R8CYI1A94ZMML50xL4ugh1hgppw7apa9oqsgk1pr7aa4}`

- Filter expression
  
- Explanation
  ![Screenshot 2024-09-13 174637](https://github.com/user-attachments/assets/d1c7c455-b210-4874-a6d2-e478075d70cb)
  
  Sama seperti sebelumnya, pada bagian Statistics>Protocol Hierarcy, akan terdisplay statistic protocol yang ada pada file tersebut, yaitu `Multi Domain Name System`, `Hypertext Transfer Protocol`, `User Datagram Protocol`, dan `Transmission Control Protocol`.

- Output result

  ![Screenshot 2024-09-11 184527](https://github.com/user-attachments/assets/18426ec1-110b-432c-87a4-7b5bcbbf12ef)


## Task 2

> a. Berapa banyak packet berbasis TCP yang memiliki flag [RST, ACK]

> _a. How many TCP based packets have the flags [RST, ACK]?_

**Answer:**

- Flag

  `JARKOM24{W0w_4nother_Sh0t_SCUTDOKYDPH0mptyqbsuyefsyiyqijblvuahM4r197101614943839180614}`

- Filter expression

  `tcp.flags.reset == 1 && tcp.flags.ack == 1`
  
- Explanation

  Pertama-tama untuk mencari packet berbasis TCP dengan flag [RST, ACK] yang kami lakukan adalah memasukkan query `tcp.flags.reset == 1 && tcp.flags.ack == 1` yang artinya akan melakukan filter sesuai dengan objektif dari soal yaitu packet berbasis TCP dengan flag [RST, ACK]

  ![Explanation2A](https://github.com/user-attachments/assets/8b3dc135-a3f2-4ea8-bddc-7fd68af73b55)

  Setelah query dimasukkan akan diperoleh jumlah packet sebanyak 411 yang dapat dilihat pada bagian kanan bawah dari gambar diatas.

- Output result

  ![FlagNo2](https://github.com/user-attachments/assets/545180c9-2e43-4219-b6ad-032c376c9b59)

  
<br>
<br>

> b. How many TCP based packets have only the [SYN] flag?

> _b. How many TCP based packets have only the [SYN] flag?_

**Answer:**

- Flag

  `JARKOM24{W0w_4nother_Sh0t_SCUTDOKYDPH0mptyqbsuyefsyiyqijblvuahM4r197101614943839180614}`

- Filter expression

  `tcp.flags.reset == 0 && tcp.flags.ack == 0 && tcp.flags.syn == 1`
  
- Explanation

  Pertama-tama untuk mencari packet berbasis TCP dengan flag [SYN] saja, yang kami lakukan adalah memasukkan query `tcp.flags.reset == 0 && tcp.flags.ack == 0 && tcp.flags.syn == 1` yang artinya akan melakukan filter sesuai dengan objektif dari soal yaitu packet berbasis TCP dengan flag [SYN] saja, tanpa [RST], ataupun [ACK] yang dapat dilihat dari query bagian `tcp.flags.reset == 0 && tcp.flags.ack == 0`.

  ![Explanation2B](https://github.com/user-attachments/assets/c40273fd-0426-4755-8761-f2f5dfb42399)

  Setelah query dimasukkan akan diperoleh jumlah packet sebanyak 412 yang dapat dilihat pada bagian kanan bawah dari gambar diatas.

- Output result

  ![FlagNo2](https://github.com/user-attachments/assets/545180c9-2e43-4219-b6ad-032c376c9b59)

<br>
<br>

> c. How many TCP based packets have the ACK flag but do not have SYN or RST?

> _c. How many TCP based packets have the ACK flag but do not have SYN or RST?_

**Answer:**

- Flag

  `JARKOM24{W0w_4nother_Sh0t_SCUTDOKYDPH0mptyqbsuyefsyiyqijblvuahM4r197101614943839180614}`

- Filter expression

  `tcp.flags.ack == 1 && tcp.flags.syn == 0 && tcp.flags.reset == 0`
  
- Explanation

  Pertama-tama untuk mencari packet berbasis TCP yang mempunyai flag [ACK], tetapi tidak mempunyai flag SYN atau RST , yang kami lakukan adalah memasukkan query `tcp.flags.ack == 1 && tcp.flags.syn == 0 && tcp.flags.reset == 0` yang artinya akan melakukan filter sesuai dengan objektif dari soal yaitu packet berbasis TCP  yang mempunyai flag [ACK], tetapi tidak mempunyai flag SYN atau RST , query yang digunakan kurang lebih sama seperti bagian b sebelumnya hanya diganti sedikit saja untuk menyesuaikan permintaan pada soal.

  ![Explanation2C](https://github.com/user-attachments/assets/0aa05d00-57f2-4753-b94d-dab351acaa18)

  Setelah query dimasukkan akan diperoleh jumlah packet sebanyak 217 yang dapat dilihat pada bagian kanan bawah dari gambar diatas.
- Output result

  ![FlagNo2](https://github.com/user-attachments/assets/545180c9-2e43-4219-b6ad-032c376c9b59)

<br>
<br>

## Task 3

> a. Pada port berapa server http terbuka?

> _a. On which port is the HTTP server open?_


**Answer:**

- Flag

  `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_7GLC7L1tsvfxza248gp11girawmmzde}`

- Filter expression

  `http`
  
- Explanation
  Ketika pada filter dilakukan query `http` maka akan menunjukkan semua packets dengan protocol http. 
  ![Screenshot 2024-09-13 180944](https://github.com/user-attachments/assets/dd0d0380-5474-4918-af63-741282c869b4)

  Kemudian pada bagian details akan terdisplay port `http server` yaitu 9282
  ![Screenshot 2024-09-13 180933](https://github.com/user-attachments/assets/a070ef6d-14bd-4f17-9d99-7d1978562e0f)

- Output result

  !![Screenshot 2024-09-11 191546](https://github.com/user-attachments/assets/dfa1e95a-5877-4adf-9595-16c0adc1c4a7)

<br>
<br>

> b. Berapa byte file response yang dikirim dari server

> _b. How many bytes of file response are sent from the server?_


**Answer:**

- Flag

   `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_7GLC7L1tsvfxza248gp11girawmmzde}`

- Filter expression
  `http`
  
- Explanation

  ![Screenshot 2024-09-13 180944](https://github.com/user-attachments/assets/503ca836-2a1e-4a22-8e97-e231ed28e997)
  Ketika pada filter dilakukan query `http`, maka akan terdisplay `length` dari packets dengan respons `200 OK` yang menandakan request succeeded dengan length bytes sebanyak 427.

- Output result

  ![Screenshot 2024-09-11 191546](https://github.com/user-attachments/assets/dfa1e95a-5877-4adf-9595-16c0adc1c4a7)

<br>
<br>

> c. Berapa jumlah file yang terdapat pada server?

> _c. How many files are there on the server?_


**Answer:**

- Flag

   `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_7GLC7L1tsvfxza248gp11girawmmzde}`

- Filter expression
  `http`

- Explanation

  Ketika packets yang telah diquery pada nomor sebelumnya diclick `pada packet>follow>http stream` maka akan terlihat details pada packet tersebut. Pada file html yang tercapture, terdapat 4 file didalamnya, yaitu
  file.pdf, hello.html, lion.jpg, dan present.pptx
  ![Screenshot 2024-09-13 181759](https://github.com/user-attachments/assets/932bf21e-d63c-42bd-b765-1d7d4ebfcddb)

- Output result

  ![Screenshot 2024-09-11 191546](https://github.com/user-attachments/assets/dfa1e95a-5877-4adf-9595-16c0adc1c4a7)

<br>
<br>

> d. Sebutkan nama file secara berurutan berdasarkan alfabet menurun dengan koma sebagai separator, contoh: file1,file2

> _c. List the filenames in descending alphabetical order, separated by commas. Example: file1,file2_


**Answer:**

- Flag

   `JARKOM24{Y0u_4r3_4_g00d_4nalyz3r_7GLC7L1tsvfxza248gp11girawmmzde}`

- Filter expression
  `http`
  
- Explanation

  Ketika packets yang telah diquery pada nomor sebelumnya diclick `pada packet>follow>http stream` maka akan terlihat details pada packet tersebut. Pada file html yang tercapture, terdapat 4 file didalamnya, yaitu
  file.pdf, hello.html, lion.jpg, dan present.pptx
  ![Screenshot 2024-09-13 181759](https://github.com/user-attachments/assets/932bf21e-d63c-42bd-b765-1d7d4ebfcddb)

- Output result

  ![Screenshot 2024-09-11 191546](https://github.com/user-attachments/assets/dfa1e95a-5877-4adf-9595-16c0adc1c4a7)

<br>
<br>

## Task 4

> Protokol apa yang paling banyak terdapat di file hasil capture traffic?

> _Which protocol is the most frequent in the traffic capture file?_


**Answer:**

- Flag

  `JARKOM24{M4ster_4n4lyzer_30235t1k1SWNACERUATR41sbpla5w1x6i}`

- Filter expression

  `Tidak menggunakan Filter expression`
  
- Explanation

  Pertama-tama untuk mencari protokol yang paling banyak di file hasil capture traffic yang kami lakukan yaitu membuka tab `Statistics` -> `Protocol Hierarchy` seperti pada gambar berikut:

  ![Explanation4-1](https://github.com/user-attachments/assets/1d9b91b6-3bc6-4524-ae70-32c55201c016)

  Kemudian dapat kita lihat pada gambar dibawah ini, bahwa protokol yang paling banyak yaitu FTP dengan jumlah 392.

  ![Explanation4-2](https://github.com/user-attachments/assets/0abf3455-9500-4342-b3f0-d45c7a9f1e76)

- Output result

  ![FlagNo4](https://github.com/user-attachments/assets/ebb1b2b9-7834-4c54-8c0b-7a16c72e6263)


<br>
<br>

## Task 5

> Berdasarkan hasil bruteforce, apa user yang tepat dari hasil bruteforce?

> _Based on the brute force results, what is the correct username?_


**Answer:**

- Flag

  `JARKOM24{He_1s_g3d4g3d1g3d4g3d40_CLBQTHZMAMDZXTOMLSUEMunskyyplyxyxdtrt453242133200}`

- Filter expression

  `frame contains "Login"`
  
- Explanation

  Untuk mencari user yang tepat, pertama-tama kami melakukan filter expression dengan kata Login, kemudian mencari bagian dimana terdapat tulisan `Login succesful` seperti gambar berikut:

  ![Explanation5-1](https://github.com/user-attachments/assets/09c369c7-2f7b-4ba6-9b0d-c1ad6fed29f6)

  Setelah itu kami melakukan Follow TCP Stream dan memperoleh informasi sebagai berikut:

  ![Explanation5-2](https://github.com/user-attachments/assets/5468ac7e-f226-4c3d-8483-2d5ee05185c9)

  Disini dapat terlihat dengan jelas bahwa user yang tepat yaitu `gedagedigedagedao`.


- Output result

  ![FlagNo5](https://github.com/user-attachments/assets/b9c6e57d-dba1-481a-b02b-7b41edb4a2d5)

<br>
<br>

## Task 6

> Apa password yang tepat?

> _What is the correct password?_


**Answer:**

- Flag

  `JARKOM24{h1s_fr1end_1s_g3d4g3d1g3d4g3d03_TE0ERIK90AyksnUmbhhdkwimzwB4Sur1BJHGGIQVYB}`

- Filter expression

  `frame contains "Login"`
  
- Explanation

  Untuk mencari password yang tepat, pertama-tama kami melakukan filter expression dengan kata Login, kemudian mencari bagian dimana terdapat tulisan `Login succesful` seperti yang kami lakukan untuk soal sebelumnya.

  ![Explanation6-1](https://github.com/user-attachments/assets/09c369c7-2f7b-4ba6-9b0d-c1ad6fed29f6)

   Setelah itu kami melakukan Follow TCP Stream lagi seperti soal sebelumnya dan memperoleh informasi sebagai berikut:
   
  ![Explanation6-2](https://github.com/user-attachments/assets/5468ac7e-f226-4c3d-8483-2d5ee05185c9)

  Disini dapat terlihat dengan jelas bahwa password yang tepat yaitu `gedagedigedagedoe`.

- Output result

  ![FlagNo6](https://github.com/user-attachments/assets/b3145583-788e-4c3a-b799-4f3cdc3b1e9c)


<br>
<br>

## Task 7

> Pada port berapa telnet yang bisa diakses?

> _On which port is Telnet accessible?_


**Answer:**

- Flag

  `JARKOM24{Gr34t_Sn1ff3r_3DO24yksnUmhzcmzf9ij2T3t0t2ZFgRSug8U}`

- Filter expression

  `frame contains "telnet"`
  
- Explanation

  Ketika dilakukan query dengan memasukkan filter `frame contains "telnet"`
  ![Screenshot 2024-09-13 182744](https://github.com/user-attachments/assets/d803de41-82e5-49b4-9d97-7e8f3cb226a1)
  Pada bagian info akan terdisplay port yang mengandung telnet, yaitu port `2423'

- Output result

  ![Screenshot 2024-09-11 193702](https://github.com/user-attachments/assets/a37cc447-0f23-45d2-868f-467e983b6000)

<br>
<br>

## Task 8

> Ada berapa file di dalam server?

> _How many files are on the server?_


**Answer:**

- Flag

  `JARKOM24{P4ck3t_4n4lyz3r_kzw6supn9g3112zmrvlmfmwyS1SZONOMLQOFN}`

- Filter expression

  `Tidak menggunakan Filter expression`
  
- Explanation

  Disini, pertama-tama kami membuka tab `Statistics` -> `Conversation` akan muncul tampilan seperti berikut ini:

  ![Explanation8-1](https://github.com/user-attachments/assets/0bedff55-dc94-4248-a49b-05b966458dff)

  Kemudian kami menaruh sedikit kecurigaan pada bagian FTP karena berjumlah lebih banyak dari yang lainnya, lalu kami memutuskan untuk melakukan `Follow Stream` pada bagian TCP yang memiliki jumlah Packet paling banyak karena mencurigakan.

  ![Explanation8-2](https://github.com/user-attachments/assets/5634b8b4-6874-4575-b673-4c93cfb67dfa)

  Setelah itu kami memperoleh sebuah aktivitas user yang sedang mencoba untuk login ke dalam server ubuntu, lalu kami merubah tampilannya agar dapat lebih mudah dibaca dengan cara seperti pada gambar berikut:

  ![Explanation8-3](https://github.com/user-attachments/assets/5cddc34b-cdc0-4188-aebc-2643d6171f4e)

  Setelah itu kami perlahan-lahan menelusuri semua aktivitas yang sedang dilakukan oleh user pada server tersebut sampai memperoleh aktivitas dimana user melakukan command `ls` untuk menampilkan beberapa file seperti gambar berikut ini:

  ![Explanation8-4](https://github.com/user-attachments/assets/993d05ae-ade6-4617-8454-807ee43e5d83)

  Dari gambar diatas kami memperoleh jumlah file yang muncul ada `7` yaitu [chakra.txt], [code07.txt], [djumanto.txt], [dongsoo.txt], [echo], [gendra.txt], [junggoo.txt]. Sehingga kami memperoleh jawaban untuk flagnya yaitu berjumlah `7` file.

- Output result

  ![FlagNo8](https://github.com/user-attachments/assets/99a209c6-a327-4320-a242-0a636f8b8026)

<br>
<br>

## Task 9

> Apa nama file yang dieksekusi oleh user?

> _What is the name of the file executed by the user?_


**Answer:**

- Flag

  `JARKOM24{333ch000_us3r_458434898612XeXmGfsccrd33dDKFGYLYKI4}`

- Filter expression

  `Tidak menggunakan Filter Expression`
  
- Explanation

  Disini langkah-langkah yang kami lakukan sama persis dengan yang sudah kami lakukan untuk soal no 8, setelah melakukan Follow Stream dan mengecek aktivitas yang dilakukan oleh user pada sebuah server, kami menemukan bagian saat user sedang mengeksekusi sebuah file

  ![Explanation9-1](https://github.com/user-attachments/assets/34ca49a0-145b-421d-b6ed-308a4c370281)

  Pada gambar diatas user sedang mengeksekusi sebuah file dengan command `./` untuk sebuah file dengan nama `echo`. Sehingga kami memperoleh nama file yang dieksekusi oleh user adalah `echo`.

- Output result

  ![FlagNo9](https://github.com/user-attachments/assets/496c74ca-5b0a-4f2b-b499-7db0ce8c8457)

  Note: 
  
  Mohon Maaf, flag yang kami masukkan tidak sama dikarenakan lupa untuk melakukan Screenshot pada saat pertama kali memperoleh flagnya.

<br>
<br>

## Task 10

> Apa output dari file dalam bentuk base64 decode?

> _What is the output of the file in base64-decoded form?_


**Answer:**

- Flag

  `JARKOM24{tH4ts_1t_w3ll_d0n3_12131670961337o7zn8l79eb1231421421DF3SXX4919KT885}`

- Filter expression

  `Tidak menggunakan Filter Expression`
  
- Explanation

  Sama seperti yang sudah kami lakukan di no 8, dan no 9 sebelumnya, setelah melakukan Follow Stream dan mengecek aktivitas yang dilakukan oleh user pada sebuah server, kami menemukan kejadian user sedang mengeksekusi sebuah file dengan nama `echo` lalu kami menemukan sebuah string yang mencurigakan

  ![Explanation10-1](https://github.com/user-attachments/assets/b4eb67dd-90c9-4606-83de-c90efd764ab4)

  Selanjutnya, kami segera meng-copy string tersebut dan melakukan decode dengan base64 menggunakan bantuan website yang tersedia secara online yaitu `https://www.base64decode.org/`

  ![image](https://github.com/user-attachments/assets/0c1b7ac0-67fa-46e8-8685-817508fdf0b0)

  Setelah itu kami memperoleh jawaban untuk mendapatkan flag dari no 10 yaitu `Djumanto mencoba menenangkan kuda kesayangannya, Glukgluk, yang tiba-tiba melompat-lompat di kandang sambil berteriak, 'Tenang, Glukgluk, ini cuma payung, bukan alien!'`.

- Output result

  ![FlagNo10](https://github.com/user-attachments/assets/a1c5c8f4-2fa5-4d29-9846-54e03f322159)


<br>
<br>

## Summary
Overall soal praktikum dapat kami kerjakan dengan lancar, meskipun ada 1-2 kendala yang terjadi. Praktikum modul pertama ini menurut kami cukup seru karena tidak hanya CTF, kami juga belajar menjadi anak elektro saat praktikum crimping kabel.

## Problems

Pada saat mengerjakan soal no 8,9,10 kami sangat kesusahan untuk memahami apa maksud dari soal dikarenakan kurangnya penjelasan deskripsi soal serta kata-kata yang sedikit ambigu, pada akhirnya setelah menyelesaikan soal no 8, kami dapat menyelesaiakan soal no 9 kemudian no 10 dengan lancar.  
