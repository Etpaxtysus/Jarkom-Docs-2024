[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/99wpTe72)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Abillidya Nofianto Putri | 5025221164 | Jaringan Komputer (A) |
| Rhenaldy Chandra | 5025221190 | Jaringan Komputer (A) |

## Find your topology here!

- Link: https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing

- Topology distribution for groups: https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?gid=1757558734#gid=1757558734

## Put your topology config image here!

![Topology](https://github.com/user-attachments/assets/c4a65ba0-3224-4c8d-b2e0-c457b04c1d8d)


<br>

## Soal 1

> Topologi terdiri dari node Wortel yang berupa DNS Master*. Selain itu, terdapat pula node Pokcoy sebagai DNS Slave*, yang bertugas sebagai cadangan dari node Wortel.
> <br> </br>
> Selanjutnya terdapat node Tomat dan Taoge yang bekerja sebagai Client*, tiga buah Web Server* yaitu Bayam, Buncis, dan Brokoli, serta Mayur sebagai Router*. Buatlah topologi sesuai dengan pembagian topologi [di sini](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) dan konfigurasi topologi [di sini](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Pastikan bahwa setiap node dapat terhubung ke Internet.

> _The topology consists of a Wortel node which is a DNS Master*. In addition, there is also a Pokcoy node as a DNS Slave*, which serves as a backup for the Wortel node._
> <br> </br>
> _Furthermore, there are Tomat and Taoge nodes that work as Client*, three Web Servers*, namely Bayam, Buncis, and Brokoli, then finally Mayur as Router*. Make a topology according to the topology division [here](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) and the topology configuration [here](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Make sure that each node can connect to the Internet._

**Answer:**

- Screenshot

  ![No1-1](https://github.com/user-attachments/assets/bf190c89-caba-4a81-893e-fbbef22d6e00)

  ![No1-2](https://github.com/user-attachments/assets/066f3f35-a144-48b5-958b-0b6cd07da5b4)


- Explanation

  Berikut ini adalah konfigurasi network yang kami gunakan pada topologi kami:
  
  Mayur (Router):

  ```
  auto eth0 
  iface eth0 inet dhcp

  auto eth1
  iface eth1 inet static
    address 192.181.1.1
    netmask 255.255.255.0
  
  auto eth2
  iface eth2 inet static
    address 192.181.2.1
    netmask 255.255.255.0

  auto eth3
  iface eth3 inet static
    address 192.181.3.1
    netmask 255.255.255.0

  auto eth4
  iface eth4 inet static
    address 192.181.4.1
    netmask 255.255.255.0

  up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.181.0.0/16

  ```


  Tomat (Client):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.1.2
    netmask 255.255.255.0
    gateway 192.181.1.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Tauge (Client):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.2.2
    netmask 255.255.255.0
    gateway 192.181.2.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Pokcoy (Slave):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.3.2
    netmask 255.255.255.0
    gateway 192.181.3.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Wortel (Master):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.3.3
    netmask 255.255.255.0
    gateway 192.181.3.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Brokoli (WebServer):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.4.2
    netmask 255.255.255.0
    gateway 192.181.4.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Buncis (Webserver):
  ```
  auto eth0
  iface eth0 inet static
    address 192.181.4.3
    netmask 255.255.255.0
    gateway 192.181.4.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Bayam :

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.4.4
    netmask 255.255.255.0
    gateway 192.181.4.1
  
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

  Kami menambahkan `up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.181.0.0/16` pada konfigurasi network di bagian router agar script dapat jalan setelah node di start. Kami juga menambahkan `up echo nameserver 192.168.122.1 > /etc/resolv.conf` pada konfigurasi network tiap node agar dapat terhubung dengan internet.

<br>

## Soal 2

> Tambahkan konfigurasi untuk domain bayam.yyy.com yang mengarah ke IP node Bayam di DNS Master. Dengan cara yang sama, buat konfigurasi domain brokoli.yyy.com yang mengarah ke IP node Brokoli dan domain buncis.yyy.com yang mengarah ke IP node Buncis. Simpan semua konfigurasi dalam folder Jarkom. Selama pengerjaan soal, ubah yyy menjadi kode kelompok masing-masing (contoh: A02).
> <br> </br>
> Jangan lupa update konfigurasi kedua client agar dapat berkomunikasi dengan semua domain tersebut.


> _Add a configuration for bayam.yyy.com domain that points to the Bayam node IP in the DNS Master. In the same way, create a brokoli.yyy.com domain configuration that points to the Brokoli node IP and a buncis.yyy.com domain that points to the Buncis node IP. Save all configurations in a folder called Jarkom. For this practicum, substitute yyy with the code of each group (ex: A02).
> <br> </br> 
> Don't forget to update the configuration of both clients so that they can communicate with the domains._

**Answer:**

 Tomat (Client) :

  ![No2-1](https://github.com/user-attachments/assets/c8485cdc-bf39-4d56-8616-615adc223b05)

  Pokcoy (Client) :

  ![No2-2](https://github.com/user-attachments/assets/67e0f95e-206a-4fa5-b8ce-ad4b538ba52a)


- Explanation

  Hal pertama yang kami lakukan adalah melakukan update dan install bind9 terlebih dahulu dengan command berikut :
  ```
  apt-get update
  apt-get install bind9 -y
  ```
  Selanjutnya kita akan melakukan modifikasi pada file `named.conf.local` sebagai berikut:
  ```
  zone "bayam.A26.com" {
	  type master;
	   file "/etc/bnd/Jarkom/bayam.A26.com";
  };

  zone "buncis.A26.com" {
	  type master;
	  file "/etc/bnd/Jarkom/buncis.A26.com";
  };

  zone "brokoli.A26.com" {
    type master;
    file "/etc/bnd/Jarkom/brokoli.A26.com";
  };
  ```
  Selanjutnya kita buat direktori baru :
  ```
  mkdir /etc/bind/Jarkom
  ```
  Lalu kita juga mengganti file `db.local` untuk setiap domain dengan IP Node yang mengarah ke Buncis, Brokoli, dan Bayam :

  `bayam.A26.com` :
  ```
    $TTL    604800
    @       IN      SOA     bayam.A26.com. root.bayam.A26.com. (
                                  2         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      bayam.A26.com.
    @       IN      A       192.181.4.4
  ```

  `buncis.A26.com` :
  ```
    $TTL    604800
    @       IN      SOA     buncis.A26.com. root.buncis.A26.com. (
                                  2         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      buncis.A26.com.
    @       IN      A       192.181.4.3
  ```
  `brokoli.A26.com` :
    ```
      $TTL    604800
      @       IN      SOA     brokoli.A26.com. root.brokoli.A26.com. (
                                    2         ; Serial
                              604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                              604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      brokoli.A26.com.
      @       IN      A       192.181.4.4

    ```

    Terkhir kita melakukan konfigurasi untuk Client (Tomat & Tauge) pada file `/etc/resolv.conf` seperti berikut :
    ```
    nameserver 192.181.3.3
    ```

<br>

## Soal 3

> Tambahkan domain alias berupa www.bayam.yyy.com pada alamat bayam.yyy.com dan www.brokoli.yyy.com pada alamat brokoli.yyy.com.

> _Add a domain alias in the form of www.bayam.yyy.com to the bayam.yyy.com address and www.brokoli.yyy.com to the brokoli.yyy.com address._

**Answer:**

- Screenshot

  ![No3-1](https://github.com/user-attachments/assets/cb2e7f2c-bfec-4fa0-be07-564ed81b8280)
- Explanation

  Hal pertama yang kami lakukan adalah melakukan update dan install bind9 terlebih dahulu dengan command berikut :
  ```
    apt-get update
    apt-get install bind9 -y
  ```
  Selanjutnya kita buat direktori baru :
  ```
  mkdir /etc/bind/Jarkom
  ```

  Lalu, kita juga mengganti file `db.local` untuk domain dengan IP Node yang mengarah ke Brokoli, dan Bayam untuk kita beri alias :

  `bayam.A26.com` :
  ```
    $TTL    604800
    @       IN      SOA     bayam.A26.com. root.bayam.A26.com. (
                                  2         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      bayam.A26.com.
    @       IN      A       192.181.4.4
    www     IN      CNAME   bayam.A26.com.
  ```

  `brokoli.A26.com` :
    ```
      $TTL    604800
      @       IN      SOA     brokoli.A26.com. root.brokoli.A26.com. (
                                    2         ; Serial
                              604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                              604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      brokoli.A26.com.
      @       IN      A       192.181.4.3
      @       IN      NS      brokoli.A26.com.

    ```
    Terkhir kita melakukan konfigurasi untuk Client (Tomat & Tauge) pada file `/etc/resolv.conf` seperti berikut untuk melakukan testing :
    ```
      echo 'nameserver 192.181.3.3' > /etc/resolv.conf
      ping www.bayam.A26.com -c 5
      ping www.brokoli.A26.com -c 5
    ```
  

<br>

## Soal 4

> Tambahkan record reverse domain untuk domain brokoli.yyy.com dan buncis.yyy.com.

> _Add a reverse domain record for brokoli.yyy.com and buncis.yyy.com domains._

**Answer:**

- Screenshot

  ![No4-1](https://github.com/user-attachments/assets/3f12ed21-79e4-432d-aa69-dc295a0b9928)


- Explanation

  Pertama-tama yang kami lakukan adalah melakukan update dan install bind9 terlebih dahulu dengan command berikut :
  ```
    apt-get update
    apt-get install bind9 -y
  ```
  Lalu ubah `/etc/bind/named.conf.local` :

  ```
    zone "A26.com" {
      type master;
      file "/etc/bind/Jarkom/A26.com";
    };

    zone "bayam.A26.com" {
      type master;
      file "/etc/bind/Jarkom/bayam.A26.com";
    };

    zone "buncis.A26.com" {
      type master;
      file "/etc/bind/Jarkom/buncis.A26.com";
    };
  ```
  Buat direktori baru :
  ```
    mkdir /etc/bind/Jarkom
  ```
  Copykan file db.local pada path /etc/bind ke dalam folder Jarkom yang baru saja dibuat dan ubah namanya menjadi 4.181.192.in-addr.arpa, lalu kami edit seperti berikut:
  `4.181.192.in-addr.arpa`:
  ```
    $TTL  604800
      @     IN  SOA  A26.com. root.localhost. (
                  3        ; Serial
                  604800   ; Refresh
                  86400    ; Retry
                  2419200  ; Expire
                  604800 ) ; Negative Cache TTL

      4.181.192.in-addr.arpa.         IN      NS      brokoli.a26.com.
      3                               IN      PTR     buncis.a26.com.
      4                               IN      PTR     brokoli.a26.com.
  ```

  Kemudian restart bind9 dengan perintah:
  ```
    service bind9 restart
  ```
  Untuk melakukan pengecekan bisa menggunakan command berikut pada node Client (Tomat & Tauge):

  ```
    apt-get update
    apt-get install dnsutils -y
    echo 'nameserver 192.181.3.3' > /etc/resolv.conf
    host -t PTR 192.181.4.3
    host -t PTR 192.181.4.4
  ```
<br>

## Soal 5

> Ubah record SOA dari domain bayam.yyy.com sesuai dengan ketentuan berikut:
> - Lama waktu server slave menunggu untuk mengecek salinan baru server master adalah sebesar 2 jam.
> - Field yang mengatur revisi file zona ini diubah menjadi tanggal awal praktikum (format YYYYMMDD) kemudian diikuti dengan nomor kelompok (contoh untuk kelompok A02 maka nomornya 02).
> - Lamanya waktu server harus menunggu untuk meminta pembaruan lagi dari nameserver master yang tidak responsif sebesar 30 menit.
> - Lama waktu nama domain di-cache secara lokal sebelum kadaluarsa dan kembali ke nameserver otoritatif untuk informasi terbaru sebesar 12 jam.
> - Jika server slave tidak mendapatkan respons dari server master dalam waktu 2 minggu, server tersebut harus berhenti merespons kueri untuk zona tersebut.

> _Change the SOA record of the bayam.yyy.com domain according to the following conditions:_
> - The length of time the slave server waits to check for a new revision of the master server is 2 hours.
> - The field that regulates the revision of this zone file is changed to the start date of the practicum (YYYYMMDD format) then followed by the group number (ex: for A02 the group number would be 02).
> - The length of time the server has to wait to request another update from an unresponsive master nameserver is 30 minutes.
> - The length of time a domain name is cached locally before it expires and returns to an authoritative nameserver for up-to-date information is 12 hours.
> - If the slave server does not get a response from the master server within 2 weeks, it must stop responding to queries for that zone.

**Answer:**

- Screenshot

  ![No5-1](https://github.com/user-attachments/assets/48a96d79-a1bf-46db-bd43-1342014ce43a)

- Explanation

  Pertama-tama, kami mengedit file `/etc/bind/Jarkom/bayam.A26.com` sebagai berikut:

  ```
    $TTL    604800
      @       IN      SOA     bayam.A26.com. root.bayam.A26.com. (
                                  2024100126 ; Serial
                                      7200    ; Refresh
                                      1800    ; Retry
                                      1209600 ; Expire
                                      43200 )     ; Negative Cache TTL

      ;


      @       IN      NS      bayam.A26.com.
      @       IN      A       192.181.4.4
      www     IN      CNAME   bayam.A26.com.
  ```

  Untuk memenuhi permintaan soal kami melakukan edit pada bagian ini :
  ```
    @       IN      SOA     bayam.A26.com. root.bayam.A26.com. (
                                  2024100126 ; Serial
                                      7200    ; Refresh
                                      1800    ; Retry
                                      1209600 ; Expire
                                      43200 )     ; Negative Cache TTL
      ;

  ```
  Pada bagian serial adalah tanggal mulai Praktikum 2 Jarkom yaitu 01-10-2024 lalu diakhir dengan nama kelompok kami yaitu `A26`.
  Pada bagian refresh diganti dengan 7200 yang artinya 7200 detik atau 2 jam.
  Pada bagian retry diganti dengan 1800 yang artinya 1800 detik atau 30 menit.
  Pada bagian expire diganti dengan 1209600 yang artinya 2 minggu.
  Pada bagian negative cache TTL diganti dengan 43200 yang artinya 12 jam.

<br>

## Soal 6

> Untuk menangani request yang berlebih dari client ke ketiga alamat yang tadi dibuat, konfigurasikan node Pokcoy sebagai DNS Slave yang bekerja untuk DNS Master Wortel.

> _To handle excess requests from the client to the three addresses created, configure the Pokcoy node as the DNS Slave that works for Wortel DNS Master._

**Answer:**

- Screenshot

  ![No6-1](https://github.com/user-attachments/assets/4a98eecc-8fdd-4c23-bf15-6005aea519d3)

  ![No6-2](https://github.com/user-attachments/assets/9da6ff79-a9b0-4e17-b8bc-f6c99223fd69)


- Explanation


  Konfigurasi pada Slave (Pokcoy) :

  Pertama seperti biasa lakukan update dan install bind9 terlebih dahulu:
  ```
    apt-get update
    apt-get install bind9 -y
  ```
  Edit pada file `/etc/bind/named.conf.local` pada node Slave (Pokcoy):

  ```
    zone "buncis.A26.com" {
        type slave;
        masters { 192.181.3.3; }; // IP wortel
        file "/var/lib/bind/buncis.A26.com";
    };
    zone "bayam.A26.com" {
        type slave;
        masters { 192.181.3.3; }; // IP wortel
        file "/var/lib/bind/bayam.A26.com";
    };
    zone "brokoli.A26.com" {
        type slave;
        masters { 192.181.3.3; }; // IP wortel
        file "/var/lib/bind/brokoli.A26.com";
    };
  ```
  Lalu restart bind9 :
  ```
    service bind9 restart
  ```

  Selanjutnya untuk konfigurasi pada Master (Wortel)

  Pertama seperti biasa lakukan update dan install bind9 terlebih dahulu:
  ```
    apt-get update
    apt-get install bind9 -y
  ```
  Edit pada file `/etc/bind/named.conf.local` pada node Master (Wortel):
  ```
    zone "bayam.A26.com" {
        type master;
        also-notify { 192.181.3.2; };
        allow-transfer { 192.181.3.2; };
        file "/etc/bind/Jarkom/bayam.A26.com";
    };

    zone "buncis.A26.com" {
        type master;
        also-notify { 192.181.3.2; };
        allow-transfer { 192.181.3.2; };
        file "/etc/bind/Jarkom/buncis.A26.com";
    };
  ```
  Lalu restart bind9 :
  ```
    service bind9 restart
  ```

  Untuk melakukan pengecekan pertama kami mematikan bind9 di node Master (Wortel) :
  ```
    service bind9 stop
  ```
  
  
  Lalu , kami melakukan command berikut ini pada node Client (Tomat & Tauge) :


  ```
    echo 'nameserver 192.181.3.3' > /etc/resolv.conf
    echo 'nameserver 192.181.3.2' >> /etc/resolv.conf

    ping www.bayam.A26.com -c 5
    ping www.buncis.A26.com -c 5

  ``

<br>

## Soal 7

> Karena membutuhkan tempat untuk menyimpan resep brokoli, buatlah subdomain berupa vitamin.brokoli.yyy.com dengan alias www.vitamin.brokoli.yyy.com dengan mendelegasikannya dari Wortel ke Pokcoy dengan alamat IP menuju Brokoli yang diatur di folder Vitamin.

> _Since we need a place to store Brokoli recipes, create a subdomain in the form of vitamin.brokoli.yyy.com with an alias of www.vitamin.brokoli.yyy.com by delegating it from Wortel to Pokcoy with an ip to the Brokoli node in a folder called Vitamin._

**Answer:**

- Screenshot

  ![No7-1](https://github.com/user-attachments/assets/3d2d837e-b7ba-4f70-9682-9bf88f3b1c90)


- Explanation

  Hal pertama yang kami lakukan adalah melakukan update dan install bind9 terlebih dahulu dengan command berikut :
  ```
  apt-get update
  apt-get install bind9 -y

  ```

  Selanjutnya kami mengedit file pada `/etc/bind/Jarkom/brokoli.A26.com` dan file `/etc/bind/named.conf.local` pada DNS Master (Wortel) sebagai berikut:

  `brokoli.A26.com`
  ```
    $TTL    43200
    @       IN      SOA     brokoli.A26.com. root.brokoli.A26.com. (
                                  24100126          ; Serial
                            7200           ; Refresh
                              1800          ; Retry
                            1209600         ; Expire
                            43200 )        ; Negative Cache TTL
    ;
    @       IN      NS      brokoli.A26.com.
    @       IN      A       192.181.4.2
    www     IN      CNAME   brokoli.A26.com.
    ns1     IN      A       192.181.3.2     ; IP Pokcoy
    vitamin IN      NS      ns1
  ```
  `/etc/bind/named.conf.options` :
  ```
    options {
          directory "/var/cache/bind";

          //dnssec-validation auto;
          allow-query { any; };

          auth-nxdomain no;    # conform to RFC1035
          listen-on-v6 { any; };
    };

  ```
 
  `/etc/bind/named.conf.local` :
  ```
    zone "brokoli.A26.com" {
          type master;
          also-notify { 192.181.3.2; };
          allow-transfer { 192.181.3.2; };
          file "/etc/bind/Jarkom/brokoli.A26.com";
    };
  ```

  Restart bind9 :
  ```
  service bind9 restart
  ```

  Kemudian edit file `/etc/bind/Jarkom/brokoli.A26.com` dan file `/etc/bind/named.conf.local` pada DNS Slave (Pokcoy) sebagai berikut :

  `vitamin.brokoli.A26.com`
  ```
    $TTL    604800
    @       IN      SOA     vitamin.brokoli.A26.com. root.vitamin.brokoli.A26.com. (
                                  2         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      vitamin.brokoli.A26.com.
    @       IN      A       192.181.3.2                     ; IP Pokcoy
    www     IN      CNAME   vitamin.brokoli.A26.com.        ; IP Pokcoy
  ```
  `/etc/bind/named.conf.options` :
  ```
    options {
          directory "/var/cache/bind";

          //dnssec-validation auto;
          allow-query { any; };

          auth-nxdomain no;    # conform to RFC1035
          listen-on-v6 { any; };
    };

  ```
  Membuat direktori Vitamin :
  ```
  mkdir /etc/bind/Vitamin
  ```
  `/etc/bind/named.conf.local` :
  ```
    zone "buncis.A26.com" {
      type slave;
      masters { 192.181.3.3; }; // IP wortel
      file "/var/lib/bind/buncis.A26.com";
    };
    zone "bayam.A26.com" {
      type slave;
      masters { 192.181.3.3; }; // IP wortel
      file "/var/lib/bind/bayam.A26.com";
    };
    zone "brokoli.A26.com" {
      type slave;
      masters { 192.181.3.3; }; // IP wortel
      file "/var/lib/bind/brokoli.A26.com";
    };
    zone "vitamin.brokoli.A26.com" {
      type master;
      file "/etc/bind/Vitamin/vitamin.brokoli.A26.com";
    };
  ```
  `/etc/bind/Vitamin/vitamin.brokoli.A26.com` :

  ```
  $TTL    604800
    @       IN      SOA     vitamin.brokoli.A26.com. root.vitamin.brokoli.A26.com. (
                                  2         ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
    ;
    @       IN      NS      vitamin.brokoli.A26.com.
    @       IN      A       192.181.3.2                     ; IP Pokcoy
    www     IN      CNAME   vitamin.brokoli.A26.com.        
  ```

  Restart bind9 :
  ```
  service bind9 restart
  ```
  Terakhir, untuk melihat hasilnya dapat menggunakan command seperti dibawah ini pada Client (Tomat & Tauge) :
  ```
    echo 'nameserver 192.181.3.2' > /etc/resolv.conf

    ping www.vitamin.brokoli.A26.com -c 5

  ```



<br>

## Soal 8

> Buatlah subdomain khusus untuk kandungan brokoli dengan akses k1.vitamin.brokoli.yyy.com dengan alias www.k1.vitamin.brokoli.yyy.com yang mengarah ke IP brokoli dan diatur di folder k1.  

> _Create a special subdomain for Brokoli content called k1.vitamin.brokoli.yyy.com with an alias called www.k1.vitamin.brokoli.yyy.com that point to Brokoli node and are organized in a folder called k1._

**Answer:**

- Screenshot

  ![No8-1](https://github.com/user-attachments/assets/74f5556d-c7b8-4fc4-a227-d769208db24b)


- Explanation

  Pertama-tama yang kami lakukan adalah melakukan update dan install bind9 terlebih dahulu dengan command berikut :
  ```
  apt-get update
  apt-get install bind9 -y
  ```

  Kemudian kita akan memodifikasi file `named.conf.local` :
  ```
    zone "k1.vitamin.brokoli.A26.com" {
        type master;
        file "/etc/bind/k1/k1.vitamin.brokoli.A26.com";
    };
  ```
  Lalu edit file `k1.vitamin.brokoli.A26.com` :
  ```
    $TTL    604800
      @       IN      SOA     k1.vitamin.brokoli.A26.com. root.k1.vitamin.brokoli.A26.com. (
                                    2         ; Serial
                              604800         ; Refresh
                                86400         ; Retry
                              2419200         ; Expire
                              604800 )       ; Negative Cache TTL
      ;
      @       IN      NS      k1.vitamin.brokoli.A26.com.
      @       IN      A       192.181.4.2                     ; IP Pokcoy
      www     IN      CNAME   k1.vitamin.brokoli.A26.com.

  ```
  Selanjutnya edit `/etc/bind/named.conf.options` :

  ```
    options {
        directory "/var/cache/bind";

        //dnssec-validation auto;
        allow-query{any;};

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
    };  
  ```
  Tidak lupa untuk membuat sebuah direktori baru :
  ```
    mkdir /etc/bind/k1
  ```
  Restart bind9 :
  ```
  service bind9 restart
  ```

  Terakhir, untuk melihat hasilnya dapat menggunakan command seperti dibawah ini pada Client (Tomat & Tauge) :
  ```
    echo 'nameserver 192.181.3.2' > /etc/resolv.conf

    ping www.k1.vitamin.brokoli.A26.com -c 5

    ping k1.vitamin.brokoli.A26.com -c 5
  ```


<br>

## Soal 9

> Bayam, Brokoli, dan Buncis masing-masing berfungsi sebagai web server nginx yang menyajikan resep khusus untuk jenis sayuran yang mereka tangani. Untuk mengaktifkan web server pada masing-masing worker, lakukan deployment website menggunakan sumber yang tersedia di sayur_webserver_nginx. Tambahkan konfigurasi untuk log error ke file /var/log/nginx/error.log dan log access ke file /var/log/nginx/access.log.

> _Bayam, Brokoli, and Buncis each function as nginx web servers that serve special recipes for the type of vegetables they handle. To activate the web server on each worker, do the deployment using the resources available in sayur_webserver_nginx. Add configuration for error log to the file /var/log/nginx/error.log and access log to the file /var/log/nginx/access.log._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/b358f14a-421d-4d25-b046-817905f27fcf)
  ![image](https://github.com/user-attachments/assets/02d366bf-569d-4ef9-9a8e-6e4a76c25ea3)
  ![image](https://github.com/user-attachments/assets/6f24a088-2ffe-4bb6-9a32-6e2c74b60b28)

- Explanation

  Pertama, kita mendownload file yang diperlukan dan menaruhnya di root
  ```
    wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1tFDk7pKRQLd3BMUcyvfAfEL-drvIxdSl' -O sayur_webserver_nginx.zip 
  ```
  lalu kita install zip, dan taruh file download di root
  ```
    apt-get update
    apt-get install unzip

    unzip sayur_webserver_nginx.zip -d root
  ```
  selanjutnya, buat script untuk menjalankan deployment di masing masing webserver
  
  pada brokoli
  ``` 
    apt-get update
    apt-get install nginx -y
    apt-get install php
    apt-get install lynx -y
    clear
    php -v
    mkdir -p /var/www/brokoli
    cp root/sayur_webserver_nginx/index.php /var/www/brokoli/
    cp root/sayur_webserver_nginx/resep3.php /var/www/brokoli/
    cp root/A26-9 /etc/nginx/sites-available/brokoli
    ln -s /etc/nginx/sites-available/brokoli /etc/nginx/sites-enabled/
    nginx -t
    service php7.2-fpm restart
    service nginx restart
    lynx http://brokoli.A26.com
  ```
  
  pada bayam
  ``` 
    apt-get update
    apt-get install nginx -y
    apt-get install php
    apt-get install lynx -y
    clear
    php -v
    mkdir -p /var/www/bayam
    cp root/sayur_webserver_nginx/index.php /var/www/bayam/
    cp root/sayur_webserver_nginx/resep1.php /var/www/bayam/
    cp root/A26-9 /etc/nginx/sites-available/bayam
    ln -s /etc/nginx/sites-available/bayam /etc/nginx/sites-enabled/
    nginx -t
    service nginx restart
    service php7.2-fpm restart
    lynx http://bayam.A26.com
  ```
  
  pada buncis
  ``` 
    apt-get update
    apt-get install nginx -y
    apt-get install php
    apt-get install lynx -y
    clear
    php -v
    mkdir -p /var/www/buncis
    cp root/sayur_webserver_nginx/index.php /var/www/buncis/
    cp root/sayur_webserver_nginx/resep2.php /var/www/buncis/
    cp root/A26-9 /etc/nginx/sites-available/buncis
    ln -s /etc/nginx/sites-available/buncis /etc/nginx/sites-enabled/
    nginx -t
    service nginx restart
    service php7.2-fpm restart
    lynx http://buncis.A26.com
  ```
  
  kita perlu menginstall nginx untuk menjalankan deployment dan lynx untuk melihat web. lalu kita juga perlu memindakhkan resep dan index sesuai sayuran. buat file konfigurasi yang perlu ditambahkan di sites-available, yaitu
  ```
    server {
      listen 80;
      server_name buncis.A26.com;

      root /var/www/buncis;
      index index.php;

      location / {
          try_files $uri $uri/ =404;
      }

      location ~ \.php$ {
          include snippets/fastcgi-php.conf;
          fastcgi_pass unix:/run/php/php7.2-fpm.sock;
          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
          include fastcgi_params;
      }

      error_log /var/log/nginx/error.log;
      access_log /var/log/nginx/access.log;
  }
  ```
  lakukan hal yang sama untuk file lain. kemudian jalankan script.
<br>

## Soal 10

> Pada masing masing worker nginx, akan terdapat beberapa hal yang perlu diperbaiki pada resource yang diberikan untuk bisa menampilkan resep saat halaman dimuat. Analisis kesalahan yang ada di resource melalui file /var/log/nginx/error.log dan perbaiki hingga halaman bisa menampilkan resep sesuai dengan worker nya.

> _On each nginx worker, there will be several things that need to be fixed in the resources provided to be able to display recipes when the page is loaded. Analyze the errors in the resource through the /var/log/nginx/error.log file and fix it until the page can display recipes according to its worker._

**Answer:**

- Screenshot

  
![image](https://github.com/user-attachments/assets/eabb7c31-2023-43fb-887e-e1fd2aee243c)
![image](https://github.com/user-attachments/assets/1eea8111-7c9c-48ca-a444-be2067936db7)
![image](https://github.com/user-attachments/assets/c542a39f-c5c4-421f-ab87-909370c75174)

- Explanation

Pada error log diketahui bahwa hostname tidak ditemukan
![image](https://github.com/user-attachments/assets/0380129d-8098-469d-a604-59048e2aae0f)
lalu ketika cat script, dapat diketahui bahwa hostname tidak ditemukan merupakan kesalahan error default akibat perbedaan penulisan hostname dan if-case. Maka, pertama saya mengubah kondisi switch-case agar sama dengan hostname, yaitu bunciswebserver, brokoliwebserver, dan bayamwebserver

terdapat juga kesalahan penulisan resep, dimana resep seharusnya ditulis `resep3.php` namun ditulis `resep_3.php`. lanhkah selanjutnya adalah memperbaiki semua kesalahan
![image](https://github.com/user-attachments/assets/2abdb2a4-445d-4a29-bcf0-0450c456e43e)
lalu resep akan bisa tampil sesuai nodenya.

<br>

## Soal 11

> Setelah website berhasil dideploy pada masing-masing worker (Bayam, Brokoli, dan Buncis) dan halaman dapat menampilkan resep sayuran yang sesuai,  buatlah custom access log ke file /var/log/nginx/access.log di masing-masing web server worker menggunakan format log tertentu seperti di bawah:
> - Tanggal dan waktu akses dalam format standar log.
Nama worker yang sedang dilayani (misalnya: Bayam, Brokoli, atau Buncis).
> - Alamat IP klien yang mengakses website.
> - Metode HTTP dan URI yang diakses oleh klien.
> - Status respons HTTP yang diberikan oleh server.
> - Jumlah byte yang dikirimkan dalam respons.
> - Waktu yang dihabiskan oleh server untuk menangani permintaan.
> <br> </br>
> Contoh format log yang sesuai: 
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned stat


> _After successfully deploying the website on each worker (Bayam, Brokoli, and Buncis) and ensuring the pages display the appropriate vegetable recipes, create a custom access log file at /var/log/nginx/access.log on each web server worker using a specific log format as described below:_
> - _Access date and time in standard log format._
> - _Name of the worker serving the request (e.g., Bayam, Brokoli, or Buncis)._
> - _Client IP address accessing the website._
> - _HTTP method and URI accessed by the client._
> - _HTTP response status provided by the server.__
> - _Number of bytes sent in the response.
> - _Time taken by the server to handle the request._
> <br> </br>
> _Example of the appropriate log format:
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned status 200 with 2567 bytes sent in 0.038 seconds_


**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/1b22df2c-0fa5-4710-8200-20cf25ed9f1f)
  ![image](https://github.com/user-attachments/assets/25492b25-8239-436b-9043-c4bc34ae0f12)
  ![image](https://github.com/user-attachments/assets/34c92efe-8929-4da2-8132-76e61f9899f4)

- Explanation
  
  copy file `/etc/ngin/nginx.conf` pada root, lalu tambahkan kode berikut
  ```
  http { 
    log_format custom_access_log '[$time_local] $node_name Access from $remote_addr using
    "$request" ' 'returned status $status with $body_bytes_sent bytes
    sent in $request_time seconds'; 
  }
  ```
  lalu copy file `nginx.conf` pada `/etc/nginx/nginx.conf`
<br>

## Soal 12

> Informasi vitamin pada sayur brokoli akan ditampilkan pada subdomain vitamin.brokoli.yyy.com di node brokoli, buatlah DocumentRoot yang disimpan pada /var/www/vitamin.brokoli.yyy. Konfigurasikan webserver dengan nama server vitamin.brokoli.yyy.com dan server alias www.vitamin.brokoli.yyy.com. Lakukan konfigurasi Apache Web Server pada Brokoli dengan menggunakan sumber yang tersedia di [sini](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2).

> _For information on vitamins in brokoli will be displayed on the vitamin.brokoli.yyy.com subdomain on the brokoli node, create a DocumentRoot stored in /var/www/vitamin.brokoli.yyy. Configure the web server with the server name vitamin.brokoli.yyy.com and server alias www.vitamin.brokoli.yyy.com. Configure the Apache Web Server on Brokoli using [this resource](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2)._

**Answer:**

- Screenshot

	![No12-1](https://github.com/user-attachments/assets/1f4aeaf3-957d-417e-b1d8-0589e9880692)

- Explanation
 
  Pertama download file resources
  ```
    wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1NhsaTLD4Zk06BZJCqdN_oqoxB3uIg2C7' -O vitamin.brokoli.A26.zip
  ```
  lalu unzip, dan simpan ke dalam root
  ```
    apt-get update
    apt-get install unzip
    unzip vitamin.brokoli.A26.zip
  ```
  
  buat script berikut untuk menjalankan no 12
  ```
  	apt-get update
    apt-get install nginx -y
    apt-get install php
    apt-get install php-fpm
    apt-get install libapache2-mod-php7.0
    clear
    php -v
    mkdir -p /var/www/brokoli
    cp root/brokoli.conf /etc/apache2/sites-available/vitamin.brokoli.A26.conf
    cp -r root/vitamin.brokoli.A26.com/* /var/www/vitamin.brokoli.A26
    cp root/sayur_webserver_nginx/index.php /var/www/brokoli/
    cp root/sayur_webserver_nginx/resep1.php /var/www/brokoli/
    cp root/A26-9 /etc/nginx/sites-available/brokoli
    ln -s /etc/nginx/sites-available/bayam /etc/nginx/sites-enabled/
    nginx -t
    service php7.2-fpm start
    service nginx stop
    service apache2 start
    lynx http://vitamin.brokoli.A26.com
  ```

  pada script, line berikut merupakan line untuk mengcopy semua dir
  ```
    cp -r root/vitamin.brokoli.A26.com/* /var/www/vitamin.brokoli.A26
  ```
  
  buat file `brokoli.conf` lalu isi dengan konfigurasi berikut lalu pindah `/etc/apache2/sites-available/vitamin.brokoli.A26.conf`
  ```
        <VirtualHost *:80>
      ServerAdmin webmaster@localhost
        ServerName vitamin.brokoli.A26.com
        ServerAlias www.vitamin.brokoli.A26.com
        DocumentRoot /var/www/vitamin.brokoli.A26
      <Directory /var/www/vitamin.brokoli.A26>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
      </Directory>
        ErrorLog ${APACHE_LOG_DIR}/vitamin_brokoli_error.log
        CustomLog ${APACHE_LOG_DIR}/vitamin_brokoli_access.log combined
      </VirtualHost>
  ```

<br>

## Soal 13

> Pada subdomain vitamin.brokoli.yyy.com, terdapat subfolder /nutrisi yang menyediakan informasi tentang berbagai vitamin dalam brokoli, seperti Vitamin A, C, dan K. Aktifkan directory listing untuk folder /nutrisi, dan buatlah rewrite rule di Apache untuk memperbaiki URL agar halaman seperti www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php dapat diakses hanya dengan www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Pastikan setiap halaman vitamin dapat diakses langsung melalui url yang telah disederhanakan.

> _On the vitamin.brokoli.yyy.com subdomain, there is a /nutrisi subfolder that provides information about various vitamins in brokoli, such as Vitamin A, C, and K. Activate directory listing for the /nutrisi folder, and create a rewrite rule in Apache to fix the URL so that pages like www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php can be accessed only with www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Make sure each vitamin page can be accessed directly through the simplified url._

**Answer:**

- Screenshot

	![No13-1](https://github.com/user-attachments/assets/3b09a032-5fdd-4abd-9236-c9f9d52da4d3)

	![No13-2](https://github.com/user-attachments/assets/3bfc9dc8-5c62-488f-a3b9-d72fbdae79bf)

	![No13-3](https://github.com/user-attachments/assets/9c4183b0-6b5d-4014-9e3b-3e3aa74a35fb)




- Explanation

  Buat file `.htaccess` di `/var/www/vitamin.brokoli.A26/nutrisi` untuk me-manage settings directory nutrisi.
  Isi file dengan konfigurasi berikut
  ```
    RewriteEngine On
    RewriteRule ^vitamin_a$ /nutrisi/vitamin_a.php [NC,L]
    RewriteRule ^vitamin_c$ /nutrisi/vitamin_c.php [NC,L]
    RewriteRule ^vitamin_k$ /nutrisi/vitamin_k.php [NC,L]
  ```

  lalu tambah konfigurasi berikut pada sites_available
  ```
    <Directory /var/www/vitamin.brokoli.A26/nutrisi>
        Options +FollowSymLinks -Multiviews
        AllowOverride All
    </Directory>

    <Directory /var/www/vitamin.brokoli.A26/nutrisi>
        Options +Indexes
    </Directory>
  ```

  testing dengan konfigurasi berikut
  ```
    lynx http://vitamin.brokoli.A26.com/nutrisi
  ```

<br>

## Soal 14

> Tambahkan alias untuk folder /public/images/ pada subdomain www.vitamin.brokoli.yyy.com agar folder tersebut dapat diakses langsung melalui url www.vitamin.brokoli.yyy.com/img.

> _Add an alias for the /public/images/ folder on the www.vitamin.brokoli.yyy.com subdomain so that the folder can be accessed directly through the url www.vitamin.brokoli.yyy.com/img._

**Answer:**

- Screenshot

	![No14-1](https://github.com/user-attachments/assets/4c63546e-1f9e-403b-a86a-94ebfde234a3)

- Explanation
  tambahkan script berikut pada 
  ```
    Alias /img /var/www/vitamin.brokoli.A26/public/images
  ```
  testing dengan script berikut
  ```
    lynx http://vitamin.brokoli.A26.com/img
  ```

<br>

## Soal 15

> Karena terdapat resep rahasia di file /secret/recipe_secret.txt pada subdomain www.vitamin.brokoli.yyy.com, konfigurasikan folder /secret agar tidak dapat diakses oleh pengguna (dengan menampilkan 403 Forbidden).

> _Because there is a secret recipe in the /secret/recipe_secret.txt file on the www.vitamin.brokoli.yyy.com subdomain, configure the /secret folder so that it cannot be accessed by users (by displaying 403 Forbidden)._

**Answer:**

- Screenshot

  ![No15-1](https://github.com/user-attachments/assets/83ec94d3-8a41-4c7c-9e7e-9f880187709e)


- Explanation
Tambahkan ini di konfigurasi `sites_available`
```
  <Directory /var/www/vitamin.brokoli.A26/secret>
      Require all denied
  </Directory>
```

Testing dengan script berikut
```
  lynx vitamin.brokoli.A26/secret
```

<br>

## Soal 16

> Karena dinilai terlalu panjang coba ubah konfigurasi www.vitamin.brokoli.yyy.com/public/js menjadi www.vitamin.brokoli.yyy.com/js

> _Since it is considered too long, change the configuration from www.vitamin.brokoli.yyy.com/public/js to www.vitamin.brokoli.yyy.com/js._

**Answer:**

- Screenshot

  ![No16-1](https://github.com/user-attachments/assets/1e7f91f8-de29-4e1b-9ee4-beb1c3b47ac4)

- Explanation

  Tambahkan ini di konfigurasi `sites_available`
  ```
    Alias "/js" "/var/www/vitamin.brokoli.A26/public/js"
    <Directory /var/www/vitamin.brokoli.A26/public/js>
        Require all granted
    </Directory>
  ```
  Lalu testing dengan 
  ```
    lynx www.vitamin.brokoli.A26.com/js
  ```

<br>

## Soal 17

> Supaya Web kita aman terkendali maka ubah konfigurasi www.k1.vitamin.brokoli.yyy.com menjadi hanya bisa di akses oleh port 9696 dan 8888

> _To keep our web secure, configure www.k1.vitamin.brokoli.yyy.com to only be accessible through ports 9696 and 8888._

**Answer:**

- Screenshot

  ![No17-1](https://github.com/user-attachments/assets/22e38c37-6092-47f7-8cdf-603834b883ae)

- Explanation

  Pertama, download dan unzip file ke `/var/www/k1.vitamin.brokoli.A26.com`
  Kemudian pada `PokcoyDNSSlaves` jalankan `script-no-8.sh`.
  
  Lalu, ubah file `resolv.conf` dengan mengisi kode berikut
  ```
  nameserver 192.181.3.3
  nameserver 192.181.3.2
  ```

  Lalu, edit konfigurasi file `/etc/apache2/sites-available/` dengan menambahkan kode berikut
  ```
      <VirtualHost *:9696>
              ServerAdmin webmaster@localhost
              ServerName k1.vitamin.brokoli.A26.com
              ServerAlias www.k1.vitamin.brokoli.A26.com
              DocumentRoot /var/www/k1.vitamin.brokoli.A26
      <Directory /var/www/k1.vitamin.brokoli.A26>
              Options Indexes FollowSymLinks
              AllowOverride All
              Require all granted
      </Directory>
      </VirtualHost>

      <VirtualHost *:8888>
              ServerAdmin webmaster@localhost
              ServerName k1.vitamin.brokoli.A26.com
              ServerAlias www.k1.vitamin.brokoli.A26.com
              DocumentRoot /var/www/k1.vitamin.brokoli.A26
      <Directory /var/www/k1.vitamin.brokoli.A26>
              Options Indexes FollowSymLinks
              AllowOverride All
              Require all granted
      </Directory>
      </VirtualHost>
  ```
  Selanjutnya, edit `/etc/apache2/ports.conf` agar dapat listen port 8888 dan 9696:
  ```
    Listen 80
    Listen 9696
    Listen 8888

    <IfModule ssl_module>
            Listen 443
    </IfModule>

    <IfModule mod_gnutls.c>
            Listen 443
    </IfModule>
  ```
  Lakukan testing dengan cara berikut pada client node:

  ```
    lynx http://www.k1.vitamin.brokoli.A26.com:8888
    lynx http://www.k1.vitamin.brokoli.A26.com:9696 
  ```

<br>

## Soal 18

> Lanjutkan dari nomor sebelumnya buatlah autentikasi dengan username “Seblak” dan password “sehatyyy” dengan yyy adalah kode kelompok. Letakkan Document Root pada /var/www/k1.vitamin.brokoli.yyy.

> _Continuing from the previous point, create authentication with the username “Seblak” and the password “sehatyyy” where yyy is the group code. Set the Document Root to /var/www/k1.vitamin.brokoli.yyy._

**Answer:**

- Screenshot

  
  ![No18-1](https://github.com/user-attachments/assets/de649f45-a733-4652-95cc-9f9d416e243a)
  ![No18-2](https://github.com/user-attachments/assets/ee22d45a-314e-4a7f-94b6-0aae8f822917)
  ![No18-3](https://github.com/user-attachments/assets/bdcb5ef9-4141-41bc-959b-dff10ee7d893)


- Explanation

  Untuk melakukan autentikasi pada sebuah server, diperlukan AuthType dan Require Valid-User. Lalu untuk AuthUserFile sendiri adalah tempat yang ingin kita gunakan untuk melakukan write. Sedangkan untuk AuthName adalah content-type Autentikasi pada apache2
  Selanjutnya kita dapat melakukan edit konfigurasi file `/etc/apache2/sites-available/` seperti berikut:

  ```
    <VirtualHost *:8888>
          ServerAdmin webmaster@localhost
          ServerName k1.vitamin.brokoli.A26.com
          ServerAlias www.k1.vitamin.brokoli.A26.com
          DocumentRoot /var/www/k1.vitamin.brokoli.A26
      <Directory /var/www/k1.vitamin.brokoli.A26>
          AuthType Basic
          AuthName "Restricted Content"
          AuthUserFile /etc/apache2/.htpasswd
          Require valid-user
      </Directory>
          ErrorLog ${APACHE_LOG_DIR}/vitamin_brokoli_error.log
          CustomLog ${APACHE_LOG_DIR}/vitamin_brokoli_access.log combined
    </VirtualHost>

    <VirtualHost *:9696>
          ServerAdmin webmaster@localhost
          ServerName k1.vitamin.brokoli.A26.com
          ServerAlias www.k1.vitamin.brokoli.A26.com
          DocumentRoot /var/www/k1.vitamin.brokoli.A26
      <Directory /var/www/k1.vitamin.brokoli.A26>
          AuthType Basic
          AuthName "Restricted Content"
          AuthUserFile /etc/apache2/.htpasswd
          Require valid-user
      </Directory>
          ErrorLog ${APACHE_LOG_DIR}/vitamin_brokoli_error.log
          CustomLog ${APACHE_LOG_DIR}/vitamin_brokoli_access.log combined
    </VirtualHost>
  ```
 
  Lalu kami menambahkan command berikut untuk dijalankan :

  ```
    htpasswd -c -b /etc/apache2/.htpasswd Seblak sehatA26
  ```
  Perintah `htpasswd` digunakan untuk  menambahkan username dan password ke dalamnya. Perintah pertama htpasswd dengan opsi -c digunakan untuk membuat file .htpasswd di direktori /etc/apache2/ jika belum ada, lalu menambahkan username "Seblak" dan password "sehatA26". Command -b yang merupakan bcrypt agar password yang kita isi akan dilakukan hash terlebih dahulu sebelum disimpan.

  Untuk melakukan testing :
  ```
    lynx k1.vitamin.brokoli.A26.com:9696
    lynx k1.vitamin.brokoli.A26.com:8888
  ```




<br>

## Soal 19

> Konfigurasikan agar setiap kali IP Brokoli diakses dengan lynx, secara otomatis akan dialihkan ke www.brokoli.yyy.com (alias).

> _Configure it so that every time Brokoli's IP is accessed using lynx, it is automatically redirected to www.brokoli.yyy.com (alias)._

**Answer:**

- Screenshot

  ![No19-1](https://github.com/user-attachments/assets/eabb7c31-2023-43fb-887e-e1fd2aee243c)

- Explanation

  Tambahkan server block baru pada `/etc/nginx/sites_availabe/brokoli`
  ```
    server {
      listen 80;
      server_name brokoli.A26.com;

      # Redirect all requests from test.com to www.test.com
      return 301 http://www.brokoli.A26.com$request_uri;
    }
  ```
  lalu ubah main servername menjadi
  ```
    server_name  www.brokoli.A26.com;
  ```
  jalankan dengan 
  `lynx http://brokoli.A26.com;`

<br>

## Soal 20

> Karena jumlah pengunjung website www.vitamin.brokoli.yyy.com semakin meningkat dan terdapat banyak gambar random, ubah permintaan gambar yang mengandung substring "vitamin" agar diarahkan ke file vitamin.png.

> _Since the number of visitors to www.vitamin.brokoli.yyy.com is increasing and there are many random images, redirect image requests that contain the substring "vitamin" to the file vitamin.png._

**Answer:**

  ![No20-1](https://github.com/user-attachments/assets/08d52d75-d94d-4fe6-8e69-ce0fbf261444)
  ![No20-2](https://github.com/user-attachments/assets/e549dc3f-1dec-4111-b1aa-0de3480fb818)
  ![No20-3](https://github.com/user-attachments/assets/894d9beb-da21-4bbb-abfd-adb8169c8434)

- Explanation

  Pertama, tambah line berikut pada .htaccess
  ```
    RewriteCond %{REQUEST_URI} vitamin [NC]
    RewriteRule \.(jpg|jpeg|png|gif)$ /var/www/vitamin.brokoli.A26/public/images/vitamin.png [L,R=301]
  ```

  Lalu jalankan dengan command berikut
  ```
    lynx vitamin.brokoli.a26.com/public/images/sayur-vitamin-k.jpg
  ```

<br>
  
## Problems
  Problem yang kami temukan pada soal modul 2 ini cukup banyak. Kami kurang memahami maksud dari soal nomor 2 yang ternyata harus membuat file berbeda, sedangkan kami memasukkan ketiga domainnya ke dalam file yang sama, sehingga harus mengulang nomor 2-6.

  Pada awalnya saya kurang memahami bagaimana cara menyimpan script sehingga harus banyak mengulang.

  Node di GNS3 kadang terputus jaringan dengan internet sehingga harus restart node --> restart vm.
  Masalah pada wifi, jika saya menggunakan wifi (saya memakai gns3 di vmware) maka ip address pada bayam.A26.com dan alamat lainnya mengarah ke random IP. Kemudian, jika saya run no 9, saya diarahkan ke situs mercubuana. Problem fixed ketika saya menggunkan hotspot pribadi.

## Revisions (if any)
