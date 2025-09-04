[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/s7OBVfDF)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Abillidya Nofianto Putri | 5025221164 | Jaringan Komputer (A) |
| Rhenaldy Chandra | 5025221190 | Jaringan Komputer (A) |

## Put your topology config image here!

![GNS3-Topology](https://github.com/user-attachments/assets/7fa59dd9-c6d9-49a5-a8a9-25c3b1bfff41)

## Put your VLSM calculation here!

![VLSM-Calculation](https://github.com/user-attachments/assets/1801fbe5-bf5c-4e0a-90be-8c2b91b8fba0)

<b>Tree:</b>

![VLSM-Tree](https://github.com/user-attachments/assets/7bd8cbcc-7958-45d3-ada6-0cb3683d6420)

## Put your IP route & config here!

![IP-Route](https://github.com/user-attachments/assets/d5f36493-55b5-49f6-b0ab-3d516d83d4bb)

### Subnetting and Routing

Configuration to every router, client, and server for subnetting + routing.

#### Right Side :

- Heiji :
    ```
    auto eth0
    iface eth0 inet dhcp

    #A1
    auto eth2
    iface eth2 inet static
    address 192.181.0.1
    netmask 255.255.255.252

    #A6
    auto eth1
    iface eth1 inet static
    address 192.181.0.13
    netmask 255.255.255.252

    #Routing

    up route add -net 192.181.0.4/30 gw 192.181.0.2
    up route add -net 192.181.0.8/30 gw 192.181.0.2
    up route add -net 192.181.8.0/21 gw 192.181.0.2
    up route add -net 192.181.4.0/22 gw 192.181.0.2

    up route add -net 192.181.0.128/25 gw 192.181.0.14
    up route add -net 192.181.0.16/30 gw 192.181.0.14
    up route add -net 192.181.0.20/30 gw 192.181.0.14
    up route add -net 192.181.2.0/23 gw 192.181.0.14
    ```


- Agasa :
    ```
    #A1
    auto eth0
    iface eth0 inet static
    address 192.181.0.2
    netmask 255.255.255.252
    gateway 192.181.0.1

    #A2
    auto eth1
    iface eth1 inet static
    address 192.181.0.5
    netmask 255.255.255.252

    #A5
    auto eth2
    iface eth2 inet static
    address 192.181.4.1
    netmask 255.255.252.0

    #Routing

    up route add -net 192.181.8.0/21 gw 192.181.0.6
    up route add -net 192.181.0.8/30 gw 192.181.0.6
    ```

- Kazuha :
    ```
    #A2
    auto eth0
    iface eth0 inet static
    address 192.181.0.6
    netmask 255.255.255.252
    gateway 192.181.0.5

    #A3
    auto eth2
    iface eth2 inet static
    address 192.181.8.1
    netmask 255.255.248.0

    #A4
    auto eth1
    iface eth1 inet static
    address 192.181.0.9
    netmask 255.255.255.252
    ```

- Haibara :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.8.2
    netmask 255.255.248.0
    gateway 192.181.8.1
    ```

- Sonoko :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.0.10
    netmask 255.255.255.252
    gateway 192.181.0.9
    ```

- Ran :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.4.2
    netmask 255.255.252.0
    gateway 192.181.4.1
    ```

#### Left Side :

- Ayumi :
    ```
    #A6
    auto eth0
    iface eth0 inet static
    address 192.181.0.14
    netmask 255.255.255.252
    gateway 192.181.0.13

    #A7
    auto eth1
    iface eth1 inet static
    address 192.181.0.129
    netmask 255.255.255.128

    #A8
    auto eth2
    iface eth2 inet static
    address 192.181.0.17
    netmask 255.255.255.252

    #Routing

    up route add -net 192.181.0.20/30 gw 192.181.0.18
    up route add -net 192.181.2.0/23 gw 192.181.0.18
    ```

- Mitsuhiko :
    ```
    #A8
    auto eth0
    iface eth0 inet static
    address 192.181.0.18
    netmask 255.255.255.252
    gateway 192.181.0.17

    #A9
    auto eth2
    iface eth2 inet static
    address 192.181.0.21
    netmask 255.255.255.252

    #A10
    auto eth1
    iface eth1 inet static
    address 192.181.2.1
    netmask 255.255.254.0

    ```

- Conan :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.0.130
    netmask 255.255.255.128
    gateway 192.181.0.129
    ```

- Shinichi :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.0.131
    netmask 255.255.255.128
    gateway 192.181.0.129
    ```

- Megure :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.0.22
    netmask 255.255.255.252
    gateway 192.181.0.21
    ```

- Kogoro :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.2.2
    netmask 255.255.254.0
    gateway 192.181.2.1
    ```

- Genta :
    ```
    auto eth0
    iface eth0 inet static
    address 192.181.2.3
    netmask 255.255.254.0
    gateway 192.181.2.1
    ```
    




## Soal 1

> Bagaimana cara mengkonfigurasi iptables pada router bernama 'Heiji' agar memungkinkan jaringan mengakses internet melalui interface eth0 menggunakan SNAT tanpa menggunakan MASQUERADE?

> _How to configure iptables on a router named ‘Heiji’ to allow the network to access the internet through interface eth0 using SNAT without using MASQUERADE?_

**Answer:**

- Screenshot

    ![No1-1](https://github.com/user-attachments/assets/cb7d4a85-ab0f-4474-af29-5d9b10706f79)

- Configuration

    ```
    IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"
    iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source "$IPETH0" -s 192.181.0.0/20
    ```

- Explanation

    #### Menentukan Alamat IP pada Interface `eth0`
    Untuk mendapatkan alamat IP yang terpasang pada interface `eth0`, gunakan perintah berikut:

    ```
    IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"
    ```
    - `ip -br a`: Menampilkan daftar IP dan interface secara singkat.
    - `grep eth0`: Memilih baris yang hanya berisi informasi tentang eth0.
    - `awk '{print $NF}'`: Mengambil kolom terakhir yang berisi alamat IP dan subnet.
    - `cut -d'/' -f1`: Menghapus bagian subnet (misalnya /20), hanya menyisakan alamat IP saja.

    #### Menambahkan Aturan SNAT pada `iptables`
    Setelah mendapatkan alamat IP pada interface `eth0`, tambahkan aturan SNAT untuk mengganti alamat IP sumber paket yang keluar melalui `eth0`:

    ```
    iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source "$IPETH0" -s 192.181.0.0/20
    ```

    - `iptables -t nat`: Menggunakan tabel NAT (Network Address Translation) untuk pengubahan alamat IP pada paket.
    - `-A POSTROUTING`: Menambahkan aturan pada chain POSTROUTING, yang berlaku pada paket setelah routing (untuk paket yang keluar).
    - `-o eth0`: Aturan ini hanya berlaku untuk paket yang keluar melalui interface eth0.
    - `-j SNAT`: Menggunakan aksi Source Network Address Translation (SNAT), untuk mengubah alamat IP sumber paket.
    - `--to-source "$IPETH0"`: Mengubah alamat IP sumber paket menjadi IP yang ada pada eth0, yang telah disimpan di variabel IPETH0.
    - `-s 192.181.0.0/20`: Aturan ini hanya berlaku untuk paket yang berasal dari jaringan 192.181.0.0/20.

<br>

## Soal 2

> Kalian diminta untuk melakukan drop semua paket masuk TCP kecuali pada port 1744 pada node Shinichi.

> _You are asked to drop all incoming TCP packets except on port 1744 on Shinichi's node_

**Answer:**

- Screenshot

    Port 1744:
    ![No2-1](https://github.com/user-attachments/assets/a9c061c6-b647-42b3-8dcb-88062b2285d6)

    Port Selain 1744:
    ![No2-2](https://github.com/user-attachments/assets/10ed1917-ae9b-45f7-ba2f-fe8f43a7a323)

- Configuration

    Pada Node Shinichi :
    ```
    iptables -A INPUT -p tcp --dport 1744 -j ACCEPT
    iptables -A INPUT -p tcp -j DROP
    ```

- Explanation

    Konfigurasi ini berfungsi untuk membatasi akses TCP pada node Shinichi, dengan penjelasan sebagai berikut:

    - `-A INPUT`: Menambahkan aturan ke chain INPUT (rantai yang digunakan untuk lalu lintas yang menuju ke sistem).
    - `-p tcp`: Menentukan protokol yang digunakan, dalam hal ini TCP. - --dport 1744: Menentukan port tujuan, dalam hal ini port 1744.
    - `-j ACCEPT`: Menentukan tindakan yang diambil jika paket memenuhi kriteria aturan, dalam hal ini menerima paket.
    - `-j DROP`: Menentukan tindakan yang diambil jika paket memenuhi kriteria aturan, dalam hal ini menolak (DROP) paket.

    ```
    iptables -A INPUT -p tcp --dport 1744 -j ACCEPT:
    ```

    Aturan ini menerima (ACCEPT) semua paket TCP yang ditujukan ke port 1744. Jadi, hanya koneksi yang mengarah ke port ini yang akan diizinkan.

    ```
    iptables -A INPUT -p tcp -j DROP:
    ```

    Aturan ini akan menolak (DROP) semua paket TCP lainnya yang masuk ke node Shinichi, yang tidak ditujukan ke port 1744.

    


<br>

## Soal 3

> Lakukan pembatasan sehingga koneksi SSH pada semua Web Server hanya dapat dilakukan oleh user yang berada pada node Ran.

> _Make restrictions so that SSH connections to all Web Servers can only be made by users who are on the Ran node._

**Answer:**

- Screenshot
    Pada Node Ran:
    ![No3-1](https://github.com/user-attachments/assets/c149ca4d-370f-4818-b1fa-2ddc553ae722)

    Selain Node Ran:
    ![No3-2](https://github.com/user-attachments/assets/757e6944-65f4-472c-8bb0-32d32504d833)

- Configuration

    Semua Web Server :
    ```
    iptables -A INPUT -p tcp --dport 22 -s 192.181.4.0/25 -j ACCEPT
    iptables -A INPUT -p tcp --dport 22 -j DROP
    ```

- Explanation

    Konfigurasi ini membatasi akses SSH (port 22) ke Web Server hanya untuk user yang berasal dari node Ran, dengan penjelasan sebagai berikut:
    ```
    iptables -A INPUT -p tcp --dport 22 -s 192.181.4.0/25 -j ACCEPT:
    ```
    Aturan ini menerima (ACCEPT) semua koneksi SSH (port 22) yang datang dari jaringan `192.181.4.0/25` (yang diasumsikan sebagai alamat jaringan node Ran).
    Hanya alamat IP yang berada dalam rentang tersebut yang diizinkan mengakses SSH pada Web Server.
    ```
    iptables -A INPUT -p tcp --dport 22 -j DROP:
    ```
    Aturan ini menolak (DROP) semua koneksi SSH yang datang ke Web Server selain dari jaringan `192.181.4.0/25`.
    Semua koneksi SSH lainnya yang tidak berasal dari jaringan node Ran akan diblokir.

    Jadi, Web Server hanya menerima koneksi SSH dari node Ran dengan alamat IP `192.181.4.0/25` (Subnet A5) dan menolak koneksi SSH lainnya dari sumber IP + Subnet yang berbeda.


<br>

## Soal 4

> Semua subnet hanya dapat mengakses Web Server pada port 80 dan 443 (Conan, Sonoko, dan Megure) pada hari Senin-Jumat, pukul 07:00- 19:00.

> _All subnets can access the Web Server (Conan, Sonoko, and Megure) only on ports 80 and 443, from Monday to Friday, between 07:00-19:00._

**Answer:**

- Screenshot

    Pada port 80
  
    ![Testing sukses pada port 80 di Shinici](https://github.com/user-attachments/assets/fe1b1709-f000-4667-9fce-c3b4b79bbf94)
  
    ![Testing sukses pada port 80 di conan](https://github.com/user-attachments/assets/f01ea222-1473-46f5-8caf-1864f77af4bf)

    Pada port 443
  
    ![Testing sukses pada port 443](https://github.com/user-attachments/assets/5e1e2d5a-7445-4623-82d4-e1d8eef7e7e7)
  
    ![Testing pada megumi port 443](https://github.com/user-attachments/assets/f507b18c-10b5-4abe-83b6-bfeafecab086)

    Testing Gagal
  
    ![Testing gagal karena salah waktu](https://github.com/user-attachments/assets/5444523e-75f2-44af-b9d1-bb0291849ffc)
  
    ![testing 443 gagal di megumi](https://github.com/user-attachments/assets/8f5c0f36-b5df-4766-b4c6-a762c7262316)
  
    ![testing port gagal](https://github.com/user-attachments/assets/47e0cd6d-7788-4961-b59d-6bae4f0444b2)
  
    ![testing port gagal](https://github.com/user-attachments/assets/8834517f-9846-4402-95ea-2141e0b81734)

- Configuration

    Semua Web Server:
    ```
        iptables -A INPUT -p tcp --dport 80 -m time --timestart 07:00 --timestop 19:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
        iptables -A INPUT -p tcp --dport 443 -m time --timestart 07:00 --timestop 19:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
        iptables -A INPUT -j DROP
    ```

- Explanation

  Karena webserver hanya dapat diakses pada hari tertentu pada waktu tertentu, maka kami melakukan `iptables` pada node webserver yaitu Conan, Sonoko, dan Megure dengan command match `m` pada modul `time`. Kami menambahkan hari yang diizinkan untuk access dengan command `--weekdays Mon,Tue,Wed,Thu,Fri`. Lalu, kami melakukan command `--timestart` untuk menentukan waktu mulai akses, yaitu `07:00` dan `--timestop` untuk waktu batas akhir akses, yaitu `19:00`. Selain itu, webserver hanya dapat diakses melalui port 80 dan 443 (http dan https) maka kami menambahkan command untuk paket tipe `tcp` dengan port `--dport 80` dan `--dport 443`. Semua input paket tersebut akan diterima ke dalam webserver dengan command `-j ACCEPT`.
    Kami menambahkan command `-j DROP` untuk membatasi semua input `-A INPUT` yang masuk selain input yang telah ditentukan.

<br>

## Soal 5

> Ternyata subnet Haibara memiliki akses tambahan, yaitu dapat mengakses Web Server pada port 80 dan 443 di luar hari Senin-Jumat (hari Sabtu dan Minggu), tanpa pembatasan waktu.

> _The Haibara subnet has additional access, allowing it to access the Web Server on ports 80 and 443 outside of Monday to Friday (on Saturday and Sunday), with no time restrictions._

**Answer:**

- Screenshot

    ![haibara access 80 on sunday](https://github.com/user-attachments/assets/7ae2c747-93ce-4d55-96c8-0ffccd1858e5)
  
    ![another client cant access](https://github.com/user-attachments/assets/1855b85a-e555-41c9-a2ba-c594a7a0ea93)


- Configuration

    Semua Web Server
    ```
        iptables -A INPUT -s 192.181.8.2/21 -p tcp --dport 80 -m time --weekdays Sat,Sun -j ACCEPT
        iptables -A INPUT -s 192.181.8.2/21 -p tcp --dport 443 -m time --weekdays Sat,Sun -j ACCEPT
    ```

- Explanation
    Kami menambahkan command `-s 192.181.8.2/21` untuk memfilter input yang berasal dari source IP Haibara. Selanjutnya kami menambahkan hari yang diizinkan untuk access dengan command `--weekdays Sat,Sun`. Kemudian kami tambahkan port yang diizinkan yaitu `--dport 80` dan `--dport 443` dengan protocol `p tcp`. 

<br>

## Soal 6

> Akses ke Web Server Conan, Sonoko, dan Megure pada port 80 dan 443 dilarang pada hari Jumat, pukul 11:00-13:00 (maklum, Jumatan rek).

> _Access to the Web Server (Conan, Sonoko, and Megure) on ports 80 and 443 is prohibited on Fridays between 11:00-13:00 (It's Friday prayer time)._

**Answer:**

- Screenshot

    ![Connection Refused](https://github.com/user-attachments/assets/cd93e16c-059e-4abf-abf8-614c0069e3e1)

- Configuration

    Semua Web Server
    ```
        iptables -A INPUT -p tcp --dport 80 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT
        iptables -A INPUT -p tcp --dport 443 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT
    ```

- Explanation

    Kami menggunakan command `-m time` untuk melakukan `match` pada modul `time` dan menambahkan hari yang akan di-reject akses dengan command `--weekdays Friday`. Kemudian kami menambahkan batas waktu dengan command `--timestart 11:00 --timestop 13:00` untuk melakukan reject `-j REJECT`. Semua request yang masuk pada jam tersebut pada port `--dport 80` dan `--dport 443` dengan protocol `-p tcp` hari Jumat akan direject.

<br>

## Soal 7

> Tambahkan logging paket yang di-drop di setiap node server dan router.

> _Enable logging for dropped packets on every server node and router._

**Answer:**

- Screenshot

    ![image](https://github.com/user-attachments/assets/5b7acaa4-3cbb-412a-bcd5-e5b1dc4515b8)


- Configuration

    Pada semua router dan webserver
    ```
        iptables -A INPUT -p tcp --dport 22 -j NFLOG
        iptables -A INPUT -p tcp --dport 22 -j DROP
        iptables -A INPUT -p tcp --dport 80 -j NFLOG
        iptables -A INPUT -p tcp --dport 80 -j REJECT
        iptables -A INPUT -p tcp --dport 443 -j NFLOG
        iptables -A INPUT -p tcp --dport 443 -j REJECT
    ```
    Untuk capture paket
    `tcdump -i nflog -l > root/logfile.txt`

- Explanation

    ```
        iptables -A INPUT -p tcp --dport 22 -j NFLOG
        iptables -A INPUT -p tcp --dport 22 -j DROP
    ```
    Semua paket yang masuk ke port `--dport 22` akan di log menggunakan NFLOG lalu paket tersebut akan di drop.
    ```
        iptables -A INPUT -p tcp --dport 80 -j NFLOG
        iptables -A INPUT -p tcp --dport 80 -j REJECT
        iptables -A INPUT -p tcp --dport 443 -j NFLOG
        iptables -A INPUT -p tcp --dport 443 -j REJECT
    ```
    Sedangkan semua paket yang masuk ke port `--dport 80` dan `--dport 443` akan di catat dengan `NFLOG` lalu akan di `REJECT`.

    Untuk menangkap paket kami menggunakan
    `tcdump -i nflog -l > root/logfile.txt`
    `tcdump` akan digunakan untuk menangkap jaringan yang telah dicatat di `-i nflog`. Kemudian paket yang tercapture aka dimasukan ke dalam `root/logfile.txt`.
  
<br>

## Soal 8

> Untuk keperluan maintenance, pilih salah satu Subnet dan lakukan blokir terhadap semua request protokol ICMP (ping) dari luar subnet terhadap subnet tersebut.

> _For maintenance purposes, select one Subnet and block all ICMP (ping) protocol requests from outside the subnet to that subnet._

**Answer:**

- Screenshot

    ![image](https://github.com/user-attachments/assets/8a9880d4-5b94-4c7d-aeb0-33108587d638)


- Configuration

    Pada Subnet Mitsuhiko
    ```
        iptables -A INPUT -p icmp -s 192.181.2.0/23 -d 192.181.2.0/23 -j ACCEPT
        iptables -A INPUT -p icmp -s 0.0.0.0/0 -d 192.181.2.0/23 -j DROP
        iptables -A FORWARD -p icmp -s 0.0.0.0/0 -d 192.181.2.0/23 -j DROP
    ```

- Explanation

    Di sini kami melakukan blok pada subnet A10, yaitu subnet `Mitsuhiko-Switch2-Kogoro-Switch2-Genta` dengan prefix IP `192.181.2.0/23`.
  
    `iptables -A INPUT -p icmp -s 0.0.0.0/0 -d 192.181.2.0/23 -j DROP`
    Kami melakukan DROP paket dari semua source IP address ipv 4 (`0.0.0.0/0`) yang mencoba akses subnet `-d 192.18.2.0/23` dengan menambahkan `iptables` pada gateway yaitu node `Mitsuhiko` dengan protocol `p icmp` ping.

    `iptables -A FORWARD -p icmp -s 0.0.0.0/0 -d 192.181.2.0/23 -j DROP`
    Kami melakukan DROP chain `FORWARD` dari semua source IP address ipv 4 (`0.0.0.0/0`) yang mencoba akses subnet `-d 192.18.2.0/23` melalui gateway `Mitsuhiko`. Drop ini bertujuan agar semua paket yang berada di subnet A10 tidak dapat diteruskan oleh Mitsuhiko.

    `ptables -A INPUT -p icmp -s 192.181.2.0/23 -d 192.181.2.0/23 -j ACCEPT`
    Kami menambah rules input packet `-A INPUT` untuk semua paket yang berasal dari subnet itu sendiri (Matsuhiko) agar tetap di `Accept`. 
  
<br>

## Soal 9

> Untuk meningkatkan keamanan, setiap Web Server harus bisa melakukan blok terhadap IP yang melakukan scanning port dalam jumlah yang tidak wajar (maksimal 10 scan port) di dalam selang waktu 1 menit. 

> _To enhance security, each Web Server must be able to block IP addresses that perform an excessive number of port scans (a maximum of 10 port scans) within a 1-minute interval._

**Answer:**

- Screenshot

    ![image](https://github.com/user-attachments/assets/954b2afe-0a59-4478-b4fa-085ca0bc3f81)


- Configuration

    ```
        iptables -N portscan

        iptables -A INPUT -m recent --name portscan --update --seconds 60 --hitcount 10 -j DROP
        iptables -A FORWARD -m recent --name portscan --update --seconds 60 --hitcount 10 -j DROP
        
        iptables -A INPUT -m recent --name portscan --set -j ACCEPT
        iptables -A FORWARD -m recent --name portscan --set -j ACCEPT
    ```

- Explanation

    Kami membuat sebuah aturan CHAINS `-N` bernama `portscan` untuk menyimpan aturan mengenai port scanning.

    `iptables -A INPUT -m recent --name portscan --update --seconds 60 --hitcount 10 -j DROP`
  
    Kemudian akan dilakukan `match` untuk menggunakan modul `recent` untuk semua paket/koneksi. Lalu, kami menggunakan command `--update` untuk mengupdate informasi paket. Jika paket berada dalam jangkan waktu `--seconds 60` dan melakukan `hit` sebanyak `--hitcount 10` maka paket akan di drop.

    `iptables -A FORWARD -m recent --name portscan --update --seconds 60 --hitcount 10 -j DROP`

    Sama seperti sebelumnya namun kami menambahkan aturan chain FORWARD dimana semua packet yang melewati sistem akan di drop jika melebihi ketentuan.

    `iptables -A INPUT -m recent --name portscan --set -j ACCEPT`
    `iptables -A FORWARD -m recent --name portscan --set -j ACCEPT`
    Menggunakan modul `recent` untuk melacak paket dan jika paket memenuhi aturan maka paket akan di accept.
  
<br>

## Soal 10

> Akses dari client ke WebServer Conan pada port 80 akan didistribusikan bergantian antara WebServer Conan dan Sonoko. Buatlah Load Balancer Node pada Kogoro dan beri firewall pada node Kazuha (misalnya, permintaan pertama dengan curl menghasilkan konten dari WebServer Conan, dan permintaan kedua menghasilkan konten dari WebServer Sonoko). Lakukan evaluasi menggunakan Jmeter atau Apache Benchmark terhadap metode load balancing Round-Robin serta lakukan testing firewall antara kedua WebServer menggunakan curl.

> _Access from the client to the WebServer Conan on port 80 will be alternately distributed between the WebServer Conan and Sonoko. Create a Load Balancer Node on Kogoro and apply a firewall on the Kazuha node (e.g., the first request with curl retrieves content from WebServer Conan, and the second request retrieves content from WebServer Sonoko). Perform an evaluation using JMeter or Apache Benchmark on the Round-Robin load balancing method, and conduct firewall testing between both WebServers using curl._

**Answer:**

- Screenshot

    Kami melakukan testing pada client `Haibara`
  
    Testing ke LB Kogoro
  
    ![image](https://github.com/user-attachments/assets/12042ab1-e800-4d8d-ab70-e35b6cca2448)
  
    Testing ke Kazuha
  
    ![image](https://github.com/user-attachments/assets/86f7a2be-1439-449f-b289-dee4fc29d7ec)

    Testing menggunakan Apache Benchmark pada load balancer `Kogoro`
    ![image](https://github.com/user-attachments/assets/322d1cb8-6b2a-4e1a-b78c-1904d08398d0)
    ![image](https://github.com/user-attachments/assets/d6059c10-9989-445a-80e8-8e20aa12cf88)
    ![image](https://github.com/user-attachments/assets/d3c7fbff-fcb5-49d5-998e-1bd7660e285e)

- Configuration

    Kogoro
    Pada `/etc/nginx/sites-available/default`
    ```
        upstream load_balancer {
            server 192.181.0.130:80; # WebServer Conan
            server 192.181.0.10:80;  # WebServer Sonoko
        }
        
        server {
            listen 80;
            server_name 192.181.2.2; # IP Kogoro
        
            location / {
                proxy_pass http://load_balancer;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            }
        }
    ```
    
    Conan
    Pada `/etc/nginx/sites-available/default`
    ```
        server {
            listen 80 default_server;
            listen [::]:80 default_server;
        
            root /var/www/html;
            index index.html;
        
            server_name 192.181.0.130;
        
            location / {
                try_files $uri $uri/ =404;
            }
        }
    ```
    
    `echo 'Conan' > /var/www/html/index.html`

    Sonoko
    Pada `/etc/nginx/sites-available/default`
    ```
        server {
            listen 80 default_server;
            listen [::]:80 default_server;
        
            root /var/www/html;
            index index.html;
        
            server_name 192.181.0.10;
        
            location / {
                try_files $uri $uri/ =404;
            }
        }
    ```
    `echo 'Sonoko' > /var/www/html/index.html`

    Kazuha
    ```
        iptables -t nat -A PREROUTING -p tcp --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.181.0.130:80
        iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.181.0.10:80
    ```

- Explanation

    Pada soal ini Kogoro dan Kazuha akan berperan sebagai load balancer. Pada Kogoro kami menambahkan konfigurasi load balancer round robin sebagai berikut:
    ```
        upstream load_balancer {
            server 192.181.0.130:80; # WebServer Conan
            server 192.181.0.10:80;  # WebServer Sonoko
        }
        
        server {
            listen 80;
            server_name 192.181.2.2; # IP Kogoro
        
            location / {
                proxy_pass http://load_balancer;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            }
        }
    ```
    Kami menambahkan IP webserver Conan `server 192.181.0.130:80` dan webserver Sonoko `server 192.181.0.10:80` pada block `upstream load_balancer`.

    Pada Conan dan Sonoko kami menambahkan konfigurasi menggunakan nginx
    ```
        server {
            listen 80 default_server;
            listen [::]:80 default_server;
        
            root /var/www/html;
            index index.html;
        
            server_name 192.181.0.130;
        
            location / {
                try_files $uri $uri/ =404;
            }
        }
    ```
    Dimana server akan menerima request `listen 80` pada port 80.
    Pada bagian file `index.html` kami mengisi konten berupa text `Conan` dan `Sonoko`.

    Karena Kazuha juga berperan sebagai firewall, maka kami menambahkan rules
    ```
        iptables -t nat -A PREROUTING -p tcp --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.181.0.130:80
        iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.181.0.10:80
    ```
    Dimana pada chain `PREROUTING`, pada setiap request yang dilakukan dengan protocol `-p tcp` pada `--dport 80` akan dilakukan match dengan module `-m statistic`. Pada command berikut `--mode nth --every 2` setiap 2 packet maka packet `--packet 0` akan dikirimkan ke destination `DNAT --to destination 192.181.0.130:80` yang merupakan IP `Conan`

  Kemudian untuk setiap packet yang tidak dikirimkan ke tujuan `192.181.0.130:80` akan dikirimkan ke `DNAT --to-destination 192.181.0.10:80` yang merupakan IP `Sonoko`.

  Lalu lakukan testing dengan `curl http://192.181.0.10:80/` dan `ab -n 500 -c 100 http://192.181.0.10:80/`

<br>
  
## Problems

## Revisions (if any)
