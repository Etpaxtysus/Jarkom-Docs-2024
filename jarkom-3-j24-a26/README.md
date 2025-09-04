[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1zoHyFGp)
| Name           | NRP        | Kelas     |
| ---            | ---        | ----------|
| Abillidya Nofianto Putri | 5025221164 | Jaringan Komputer (A) |
| Rhenaldy Chandra | 5025221190 | Jaringan Komputer (A) |

## Put your topology config image here!

![Topology](https://github.com/user-attachments/assets/a3e8d470-2532-487b-8d06-a39fd9b0d5a5)


<br>

> Template testing report: https://docs.google.com/document/d/17T0fsnh_4zZTrG-lELDJ88intrc9mkwCzZ_s-23JLCc/edit?usp=sharing

## Put your testing report here! 
> The report is sent in PDF format, uploaded to Drive, and set to public view.

[Link Report](https://drive.google.com/drive/folders/1gQDlYkbEUXw1njY3Se11t0-De_HorpJ0?usp=sharing)

## Soal 0

> Pada perlombaan akhir tahun kali ini, semua worker dan client ikut serta di dalamnya sebagai perwakilan dari masing-masing asrama. Persiapan yang dilakukan untuk perlombaan ini adalah dengan setup semua network configuration yang sesuai dengan tabel peran diatas. Khusus untuk client menggunakan konfigurasi dari DHCP Server.

> _For the end-of-year competition, all the workers and clients participate, representing their respective houses. The preparation includes setting up the network configuration as per the table above, with clients using DHCP Server configuration_

**Answer**

- Dumbledore (DHCP Relay):

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

  auto eth5
  iface eth5 inet static
    address 192.181.5.1
    netmask 255.255.255.0

  auto eth6
  iface eth6 inet static
    address 192.181.6.1
    netmask 255.255.255.0

  up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.181.0.0/16
  ```

- SeverusSnape (DHCP Server):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.3.2
    netmask 255.255.255.0
    gateway 192.181.3.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- McGonagall (DNS Server):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.3.3
    netmask 255.255.255.0
    gateway 192.181.3.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- Hagrid (Database Server):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.4.2
    netmask 255.255.255.0
    gateway 192.181.4.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- Voldemort (Load Balancer):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.4.3
    netmask 255.255.255.0
    gateway 192.181.4.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- Dementor (Load Balancer):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.4.4
    netmask 255.255.255.0
    gateway 192.181.4.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- HarryPotter (PHP Worker):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.1.2
    netmask 255.255.255.0
    gateway 192.181.1.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  hwaddress ether f6:83:1a:aa:75:9d
  ```

- RonWeasley (PHP Worker):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.1.3
    netmask 255.255.255.0
    gateway 192.181.1.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  hwaddress ether 4e:d4:76:4b:e7:19
  ```

- HermioneGranger (PHP Worker):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.1.4
    netmask 255.255.255.0
    gateway 192.181.1.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  hwaddress ether 72:2e:fc:68:18:cb
  ```

- LunaLovegood (Laravel Worker):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.6.2
    netmask 255.255.255.0
    gateway 192.181.6.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  hwaddress ether c2:6d:9b:06:84:a7
  ```

- FiliusFlitwick (Laravel Worker):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.6.3
    netmask 255.255.255.0
    gateway 192.181.6.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  hwaddress ether 9a:e3:e6:cb:f2:e3
  ```

- ChoChang (Laravel Worker):

  ```
  auto eth0
  iface eth0 inet static
    address 192.181.6.4
    netmask 255.255.255.0
    gateway 192.181.6.1
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  hwaddress ether 06:6a:b2:3d:ac:dc
  ```

- DracoMalfoy (Client):

  ```
  auto eth0
  iface eth0 inet dhcp
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- AstoriaGreengrass (Client):

  ```
  auto eth0
  iface eth0 inet dhcp
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- SusanBones (Client):

  ```
  auto eth0
  iface eth0 inet dhcp
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```

- HannahAbbott (Client):

  ```
  auto eth0
  iface eth0 inet dhcp
  up echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  ```
  
## Soal 1

> Melakukan registrasi subdomain untuk PHP worker bernama gryffindor.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Voldemort dan untuk laravel worker bernama ravenclaw.hogwarts.yyy.com yang mengarah ke alamat IP load balancer Dementor. Seluruh domain ini berkumpul dalam suatu ruang atau folder bernama hogwarts

> _Registering subdomains for the PHP workers named gryffindor.hogwarts.yyy.com, pointing to the IP Voldemort load balancer, and for the Laravel workers named ravenclaw.hogwarts.yyy.com, pointing to the IP Dementor load balancer. All domains are gathered in a folder named "hogwarts."_

**Answer:**

- Screenshot

![No1-1](https://github.com/user-attachments/assets/947dc3e4-2b4d-4024-a253-b55ea30ce302)

- Configuration

  McGonagall (DNS Server):
  ```
  echo 'zone "hogwarts.A26.com" {
        type master;
        file "/etc/bind/hogwarts/hogwarts.A26.com";
  };

  zone "3.181.192.in-addr.arpa" {
      type master;
      file "/etc/bind/hogwarts/3.181.192.in-addr.arpa";
  };' > /etc/bind/named.conf.local

  mkdir -p /etc/bind/hogwarts
  cp /etc/bind/db.local /etc/bind/hogwarts/hogwarts.A26.com
  cp /etc/bind/db.local /etc/bind/hogwarts/3.181.192.in-addr.arpa

  echo '
  ;
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     hogwarts.A26.com. root.hogwarts.A26.com. (
                            2024102326      ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
  ;
  @               IN      NS      hogwarts.A26.com.
  @               IN      A       192.181.3.3     ; IP DNS SERVER
  www             IN      CNAME   hogwarts.A26.com.
  gryffindor      IN      A       192.181.4.3     ; IP Voldemort as subdomain
  ravenclaw       IN      A       192.181.4.4     ; IP Dementor' > /etc/bind/hogwarts/hogwarts.A26.com

  echo '
  ;
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     hogwarts.A26.com. root.hogwarts.A26.com. (
                            2024102226      ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
  ;
  3.181.192.in-addr.arpa.       IN      NS        hogwarts.A26.com.
  3                               IN      PTR     hogwarts.A26.com.' > /etc/bind/hogwarts/3.181.192.in-addr.arpa

  echo 'options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
  };' >/etc/bind/named.conf.options

  echo 'nameserver 192.181.3.3' >> /etc/resolv.conf

  service named restart

  ```

- Explanation

  Pertama-tama kita install `bind9` terlebih dahulu lalu start dengan command:
  ```
  service named start
  ```

  Lalu edit pada `/etc/bind/named.conf.local` :
  ``` 
  zone "hogwarts.A26.com" {
        type master;
        file "/etc/bind/hogwarts/hogwarts.A26.com";
  };

  zone "3.181.192.in-addr.arpa" {
      type master;
      file "/etc/bind/hogwarts/3.181.192.in-addr.arpa";
  };
  ```
  Buar direktori baru, lalu copy file `db.local` tadi ke direktori `hogwarts`:
  ```
  mkdir -p /etc/bind/hogwarts
  cp /etc/bind/db.local /etc/bind/hogwarts/hogwarts.A26.com
  cp /etc/bind/db.local /etc/bind/hogwarts/3.181.192.in-addr.arpa
  ```
  Lalu edit `/etc/bind/hogwarts/hogwarts.A26.com`:
  ```
  ;
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     hogwarts.A26.com. root.hogwarts.A26.com. (
                            2024102326      ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
  ;
  @               IN      NS      hogwarts.A26.com.
  @               IN      A       192.181.3.3     ; IP DNS SERVER
  www             IN      CNAME   hogwarts.A26.com.
  gryffindor      IN      A       192.181.4.3     ; IP Voldemort as subdomain
  ravenclaw       IN      A       192.181.4.4     ; IP Dementor
  ```
  Pada `/etc/bind/hogwarts/3.181.192.in-addr.arpa`:
  ```
  ;
  ; BIND data file for local loopback interface
  ;
  $TTL    604800
  @       IN      SOA     hogwarts.A26.com. root.hogwarts.A26.com. (
                            2024102226      ; Serial
                            604800         ; Refresh
                              86400         ; Retry
                            2419200         ; Expire
                            604800 )       ; Negative Cache TTL
  ;
  3.181.192.in-addr.arpa.       IN      NS        hogwarts.A26.com.
  3                               IN      PTR     hogwarts.A26.com.
  ```

  Lalu pada `/etc/bind/named.conf.options`:
  ```
  options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
  };
  ```

  Terakhir, restart nginx dan tambahkan nameserver untuk internetnya:
  ```
  echo 'nameserver 192.181.3.3' >> /etc/resolv.conf

  service named restart
  ```
  Tes menggunakan command berikut:
  ```
  ping gryffindor.hogwarts.A26.com
  ping ravenclaw.hogwarts.A26.com
  ```

<br>

## Soal 2

> Memberikan ketentuan khusus untuk DracoMalfoy dan AstoriaGreengrass yang mendapat range IP dari [Prefix IP].2.64 - [Prefix IP].2.65 dan [Prefix IP].2.100 - [Prefix IP].2.101

> Selain itu, untuk HannahAbbott dan SusanBones mendapat range IP dari [Prefix IP].5.50 - [Prefix IP].5.51 dan [Prefix IP].5.155 - [Prefix IP].5.156.


> _Special provisions are given to DracoMalfoy and AstoriaGreengrass, who are assigned the IP range from [Prefix IP].2.64 - [Prefix IP].2.65 and [Prefix IP].2.100 - [Prefix IP].2.101._

> _Additionally, HannahAbbott and SusanBones are assigned the IP range from [Prefix IP].5.50 - [Prefix IP].5.51 and [Prefix IP].5.155 - [Prefix IP].5.156._

**Answer:**

- Screenshot

  ![No2-1](https://github.com/user-attachments/assets/bec402d0-f452-4059-9d41-25a171632d5f)


- Configuration

  SeverusSnape (DHCP Server):
  ```
  echo '
  INTERFACESv4="eth0"
  INTERFACESv6=""
  ' > /etc/default/isc-dhcp-server
  echo '

  subnet 192.181.1.0 netmask 255.255.255.0 {
  }

  subnet 192.181.2.0 netmask 255.255.255.0 {
    range 192.181.2.64 192.181.2.65;
    range 192.181.2.100 192.181.2.101;
    option routers 192.181.2.1;
  }

  subnet 192.181.3.0 netmask 255.255.255.0 {
  }

  subnet 192.181.4.0 netmask 255.255.255.0 {
  }

  subnet 192.181.5.0 netmask 255.255.255.0 {
    range 192.181.5.50 192.181.5.51;
    range 192.181.5.155 192.181.5.156;
    option routers 192.181.5.1;
  }

  subnet 192.181.6.0 netmask 255.255.255.0 {
  }
  ' > /etc/dhcp/dhcpd.conf

  service isc-dhcp-server restart
  service isc-dhcp-server status
  ```

- Explanation

  Pertama install dhcp server pada Severus Snape: 
  ```
  apt-get update
  apt-get install isc-dhcp-server -y
  ```

  Ganti pada `/etc/default/isc-dhcp-server`:
  ```
  INTERFACESv4="eth0"
  INTERFACESv6=""
  ```

  Pada `/etc/dhcp/dhcpd.conf`:
  ```
  subnet 192.181.1.0 netmask 255.255.255.0 {
  }

  subnet 192.181.2.0 netmask 255.255.255.0 {
    range 192.181.2.64 192.181.2.65;
    range 192.181.2.100 192.181.2.101;
    option routers 192.181.2.1;
  }

  subnet 192.181.3.0 netmask 255.255.255.0 {
  }

  subnet 192.181.4.0 netmask 255.255.255.0 {
  }

  subnet 192.181.5.0 netmask 255.255.255.0 {
    range 192.181.5.50 192.181.5.51;
    range 192.181.5.155 192.181.5.156;
    option routers 192.181.5.1;
  }

  subnet 192.181.6.0 netmask 255.255.255.0 {
  }
  ```
  Lalu restart dan cek status nya:
  ```
  service isc-dhcp-server restart
  service isc-dhcp-server status
  ```


<br>

## Soal 3

> Khusus untuk HermioneGranger yang berada di switch 1 mendapat range IP dari
[Prefix IP].1.10 - [Prefix IP].1.15 dan [Prefix IP].1.20 - [Prefix IP].1.25

> Khusus untuk ChoChang yang berada di switch 6 mendapat range IP dari 
[Prefix IP].6.10 - [Prefix IP].6.15 dan [Prefix IP].6.20 - [Prefix IP].6.25


> _HermioneGranger, who is on switch 1, is assigned the IP range from [Prefix IP].1.10 - [Prefix IP].1.15 and [Prefix IP].1.20 - [Prefix IP].1.25._

> _ChoChang, who is on switch 6, is assigned the IP range from [Prefix IP].6.10 - [Prefix IP].6.15 and [Prefix IP].6.20 - [Prefix IP].6.25._

**Answer:**

- Screenshot

  ![No3-1](https://github.com/user-attachments/assets/927b4970-e24f-4923-989c-25dab285e323)


- Configuration

  SeverusSnape (DHCP Server):
  ```
  echo '
  INTERFACESv4="eth0"
  INTERFACESv6=""
  ' > /etc/default/isc-dhcp-server
  echo '

  class "HermioneGranger" {
    match if hardware = 72:2e:fc:68:18:cb;  # MAC address HermioneGranger
  }

  subnet 192.181.1.0 netmask 255.255.255.0 {
      pool {
          allow members of "HermioneGranger";
          range 192.181.1.10 192.181.1.15;
          range 192.181.1.20 192.181.1.25;
          option routers 192.181.1.1;
      }
  }

  subnet 192.181.2.0 netmask 255.255.255.0 {
    range 192.181.2.64 192.181.2.65;
    range 192.181.2.100 192.181.2.101;
    option routers 192.181.2.1;
  }

  subnet 192.181.3.0 netmask 255.255.255.0 {
  }

  subnet 192.181.4.0 netmask 255.255.255.0 {
  }

  subnet 192.181.5.0 netmask 255.255.255.0 {
    range 192.181.5.50 192.181.5.51;
    range 192.181.5.155 192.181.5.156;
    option routers 192.181.5.1;
  }

  class "ChoChang" {
    match if hardware = 06:6a:b2:3d:ac:dc;  # MAC address ChoChang
  }

  subnet 192.181.6.0 netmask 255.255.255.0 {
      pool {
          allow members of "ChoChang";
          range 192.181.6.10 192.181.6.15;
          range 192.181.6.20 192.181.6.25;
          option routers 192.181.6.1;
      }
  }

  ' > /etc/dhcp/dhcpd.conf

  service isc-dhcp-server restart
  service isc-dhcp-server status
  ```

- Explanation

  Sama seperti pada no sebelumnya, edit `/etc/dhcp/dhcpd.conf`:
  ```
  class "HermioneGranger" {
    match if hardware = 72:2e:fc:68:18:cb;  # MAC address HermioneGranger
  }

  subnet 192.181.1.0 netmask 255.255.255.0 {
      pool {
          allow members of "HermioneGranger";
          range 192.181.1.10 192.181.1.15;
          range 192.181.1.20 192.181.1.25;
          option routers 192.181.1.1;
      }
  }

  subnet 192.181.2.0 netmask 255.255.255.0 {
    range 192.181.2.64 192.181.2.65;
    range 192.181.2.100 192.181.2.101;
    option routers 192.181.2.1;
  }

  subnet 192.181.3.0 netmask 255.255.255.0 {
  }

  subnet 192.181.4.0 netmask 255.255.255.0 {
  }

  subnet 192.181.5.0 netmask 255.255.255.0 {
    range 192.181.5.50 192.181.5.51;
    range 192.181.5.155 192.181.5.156;
    option routers 192.181.5.1;
  }

  class "ChoChang" {
    match if hardware = 06:6a:b2:3d:ac:dc;  # MAC address ChoChang
  }

  subnet 192.181.6.0 netmask 255.255.255.0 {
      pool {
          allow members of "ChoChang";
          range 192.181.6.10 192.181.6.15;
          range 192.181.6.20 192.181.6.25;
          option routers 192.181.6.1;
      }
  }
  ```

<br>

## Soal 4

> Menetapkan batasan waktu untuk DHCP server dalam peminjaman alamat IP untuk client melalui switch 2 selama 5 menit sedangkan client yang melalui switch 5 selama 20 menit. Untuk switch 1 dan switch 6 memiliki batas waktu 10 menit. Alokasi waktu maksimal peminjaman alamat IP selama 100 menit. 

> _The DHCP server's lease time for IP addresses is set as follows: Clients connected through switch 2 have a lease time of 5 minutes, Clients connected through switch 5 have a lease time of 20 minutes, Switches 1 and 6 have a lease time of 10 minutes, The maximum lease time for IP addresses is set at 100 minutes._

**Answer:**

- Screenshot

  ![No4-1](https://github.com/user-attachments/assets/927b4970-e24f-4923-989c-25dab285e323)

- Configuration

  SeverusSnape (DHCP Server):
  ```
  echo '
  INTERFACESv4="eth0"
  INTERFACESv6=""
  ' > /etc/default/isc-dhcp-server
  echo '

  class "HermioneGranger" {
    match if hardware = 72:2e:fc:68:18:cb;  # MAC address HermioneGranger
  }

  subnet 192.181.1.0 netmask 255.255.255.0 {
      pool {
          allow members of "HermioneGranger";
          range 192.181.1.10 192.181.1.15;
          range 192.181.1.20 192.181.1.25;
          option routers 192.181.1.1;
          default-lease-time 600;  # 600 detik = 10 menit
          max-lease-time 6000;     # 6000 detik = 100 menit
      }
  }

  subnet 192.181.2.0 netmask 255.255.255.0 {
    range 192.181.2.10 192.181.2.100;
    option routers 192.181.2.1;
    default-lease-time 300;  # 300 detik = 5 menit
    max-lease-time 6000;     # 6000 detik = 100 menit
  }

  subnet 192.181.3.0 netmask 255.255.255.0 {
  }

  subnet 192.181.4.0 netmask 255.255.255.0 {
  }

  subnet 192.181.5.0 netmask 255.255.255.0 {
    range 192.181.5.50 192.181.5.200;
    option routers 192.181.5.1;
    default-lease-time 1200; # 1200 detik = 20 menit
    max-lease-time 6000;     # 6000 detik = 100 menit
  }

  class "ChoChang" {
    match if hardware = 06:6a:b2:3d:ac:dc;  # MAC address ChoChang
  }

  subnet 192.181.6.0 netmask 255.255.255.0 {
      pool {
          allow members of "ChoChang";
          range 192.181.6.10 192.181.6.15;
          range 192.181.6.20 192.181.6.25;
          option routers 192.181.6.1;
          default-lease-time 600;  # 600 detik = 10 menit
          max-lease-time 6000;     # 6000 detik = 100 menit
      }
  }

  ' > /etc/dhcp/dhcpd.conf

  service isc-dhcp-server restart
  service isc-dhcp-server status
  ```
- Explanation

 Sama seperti pada no sebelumnya, edit `/etc/dhcp/dhcpd.conf`:
  ```
  class "HermioneGranger" {
    match if hardware = 72:2e:fc:68:18:cb;  # MAC address HermioneGranger
  }

  subnet 192.181.1.0 netmask 255.255.255.0 {
      pool {
          allow members of "HermioneGranger";
          range 192.181.1.10 192.181.1.15;
          range 192.181.1.20 192.181.1.25;
          option routers 192.181.1.1;
          default-lease-time 600;  # 600 detik = 10 menit
          max-lease-time 6000;     # 6000 detik = 100 menit
      }
  }

  subnet 192.181.2.0 netmask 255.255.255.0 {
    range 192.181.2.10 192.181.2.100;
    option routers 192.181.2.1;
    default-lease-time 300;  # 300 detik = 5 menit
    max-lease-time 6000;     # 6000 detik = 100 menit
  }

  subnet 192.181.3.0 netmask 255.255.255.0 {
  }

  subnet 192.181.4.0 netmask 255.255.255.0 {
  }

  subnet 192.181.5.0 netmask 255.255.255.0 {
    range 192.181.5.50 192.181.5.200;
    option routers 192.181.5.1;
    default-lease-time 1200; # 1200 detik = 20 menit
    max-lease-time 6000;     # 6000 detik = 100 menit
  }

  class "ChoChang" {
    match if hardware = 06:6a:b2:3d:ac:dc;  # MAC address ChoChang
  }

  subnet 192.181.6.0 netmask 255.255.255.0 {
      pool {
          allow members of "ChoChang";
          range 192.181.6.10 192.181.6.15;
          range 192.181.6.20 192.181.6.25;
          option routers 192.181.6.1;
          default-lease-time 600;  # 600 detik = 10 menit
          max-lease-time 6000;     # 6000 detik = 100 menit
      }
  }
  ```

<br>

## Soal 5

> Memastikan bahwa semua CLIENT, HermioneGranger, dan ChoChang harus menggunakan konfigurasi dari DHCP server, menerima DNS dari Professor McGonagall dan dapat akses internet. Khusus untuk HermioneGranger dan ChoChang mendapatkan IP Statis dari DHCP dengan [Prefix IP].x.14. hint: fixed address


> _Ensure that all CLIENT, HermioneGranger, and ChoChang use DHCP server configurations, receive DNS from Professor McGonagall, and can access the internet. HermioneGranger and ChoChang must receive static IPs from DHCP with the address [Prefix IP].x.14 (hint: fixed address)._

**Answer:**

- Screenshot

  ![No5-1](https://github.com/user-attachments/assets/b5de408a-5f18-426d-aeea-e08931a66fc2)

  ![No5-2](https://github.com/user-attachments/assets/a78544aa-00d5-4c77-9677-dea2559b3bff)

  ![No5-3](https://github.com/user-attachments/assets/1cf524c0-46a7-4cb1-8eaf-9ff9069b8eae)

- Configuration
  Dumbledore (DHCP Relay):
  ```
  echo '
  SERVERS="192.181.3.2" # IP SeverusSnape (DHCP Server)
  INTERFACES="eth1 eth2 eth3 eth4 eth5 eth6"
  OPTIONS=' > /etc/default/isc-dhcp-relay

  echo '
  net.ipv4.ip_forward=1
  ' > /etc/sysctl.conf

  service isc-dhcp-relay restart
  ```

  SeverusSnape (DHCP Server):
  ```
  echo '
  INTERFACESv4="eth0"
  INTERFACESv6=""
  ' > /etc/default/isc-dhcp-server
  echo '
  subnet 192.181.1.0 netmask 255.255.255.0 {
      range 192.181.1.10 192.181.1.15;
      range 192.181.1.20 192.181.1.25;
      option routers 192.181.1.1;                 # Router Dumbledore
      option broadcast-address 192.181.1.255;
      option domain-name-servers 192.181.3.3;     # DNS McGonagall
      default-lease-time 600;                     # 10 menit
      max-lease-time 6000;                        # 100 menit
    }

    host HermioneGranger {
        hardware ethernet 72:2e:fc:68:18:cb;      # MAC address HermioneGranger
        fixed-address 192.181.1.14;               # IP statis untuk HermioneGranger
        option routers 192.181.1.1;               # Router Dumbledore
        option broadcast-address 192.181.1.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
    }

    subnet 192.181.2.0 netmask 255.255.255.0 {
        range 192.181.2.64 192.181.2.65;
        range 192.181.2.100 192.181.2.101;
        option routers 192.181.2.1;               # Router Dumbledore
        option broadcast-address 192.181.2.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
        default-lease-time 300;                   # 5 menit
        max-lease-time 6000;                      # 100 menit
    }

    subnet 192.181.3.0 netmask 255.255.255.0 {
    }

    subnet 192.181.4.0 netmask 255.255.255.0 {
    }

    subnet 192.181.5.0 netmask 255.255.255.0 {
        range 192.181.5.50 192.181.5.51;
        range 192.181.5.155 192.181.5.156;
        option routers 192.181.5.1;               # Router Dumbledore
        option broadcast-address 192.181.5.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
        default-lease-time 1200;                  # 20 menit
        max-lease-time 6000;                      # 100 menit
    }

    subnet 192.181.6.0 netmask 255.255.255.0 {
        range 192.181.6.10 192.181.6.15;
        range 192.181.6.20 192.181.6.25;
        option routers 192.181.6.1;               # Router Dumbledore
        option broadcast-address 192.181.6.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
        default-lease-time 600;                   # 10 menit
        max-lease-time 6000;                      # 100 menit
    }

    host ChoChang {
        hardware ethernet 06:6a:b2:3d:ac:dc;    # MAC address ChoChang
        fixed-address 192.181.6.14;             # IP statis untuk ChoChang
        option routers 192.181.6.1;             # Router Dumbledore
        option broadcast-address 192.181.6.255;
        option domain-name-servers 192.181.3.3; # DNS McGonagall
    }

    ' > /etc/dhcp/dhcpd.conf

    service isc-dhcp-server restart
    service isc-dhcp-server status
  ```
  HermioneGranger (Client) :
  ```
  echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  echo 'auto eth0
  iface eth0 inet dhcp' > /etc/network/interfaces
  hwaddress ether 72:2e:fc:68:18:cb
  ```

  ChoChang (Client):
  ```
  echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  echo 'auto eth0
  iface eth0 inet dhcp
  hwaddress ether 06:6a:b2:3d:ac:dc
  ' > /etc/network/interfaces
  ```

  All Client:
  ```
  echo 'nameserver 192.168.122.1' > /etc/resolv.conf
  echo 'auto eth0
  iface eth0 inet dhcp' > /etc/network/interfaces

  ```

- Explanation

 Pertama edit pada Dumbledore (DHCP Relay) di `/etc/default/isc-dhcp-relay`:
 ```
 SERVERS="192.181.3.2" # IP SeverusSnape (DHCP Server)
 INTERFACES="eth1 eth2 eth3 eth4 eth5 eth6"
 OPTIONS=
 ```
 lalu pada `/etc/sysctl.conf`:
 ```
 net.ipv4.ip_forward=1
 ```
Lalu restart:
```
service isc-dhcp-relay restart
```

Selanjutnya pada SeverusSnape (DHCP Server), edit :
```
 subnet 192.181.1.0 netmask 255.255.255.0 {
      range 192.181.1.10 192.181.1.15;
      range 192.181.1.20 192.181.1.25;
      option routers 192.181.1.1;                 # Router Dumbledore
      option broadcast-address 192.181.1.255;
      option domain-name-servers 192.181.3.3;     # DNS McGonagall
      default-lease-time 600;                     # 10 menit
      max-lease-time 6000;                        # 100 menit
    }

    host HermioneGranger {
        hardware ethernet 72:2e:fc:68:18:cb;      # MAC address HermioneGranger
        fixed-address 192.181.1.14;               # IP statis untuk HermioneGranger
        option routers 192.181.1.1;               # Router Dumbledore
        option broadcast-address 192.181.1.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
    }

    subnet 192.181.2.0 netmask 255.255.255.0 {
        range 192.181.2.64 192.181.2.65;
        range 192.181.2.100 192.181.2.101;
        option routers 192.181.2.1;               # Router Dumbledore
        option broadcast-address 192.181.2.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
        default-lease-time 300;                   # 5 menit
        max-lease-time 6000;                      # 100 menit
    }

    subnet 192.181.3.0 netmask 255.255.255.0 {
    }

    subnet 192.181.4.0 netmask 255.255.255.0 {
    }

    subnet 192.181.5.0 netmask 255.255.255.0 {
        range 192.181.5.50 192.181.5.51;
        range 192.181.5.155 192.181.5.156;
        option routers 192.181.5.1;               # Router Dumbledore
        option broadcast-address 192.181.5.255;
        option domain-name-servers 192.181.3.3;   # DNS McGonagall
        default-lease-time 1200;                  # 20 menit
        max-lease-time 6000;                      # 100 menit
    }

    subnet 192.181.6.0 netmask 255.255.255.0 {
      range 192.181.6.10 192.181.6.15;
      range 192.181.6.20 192.181.6.25;
      option routers 192.181.6.1;               # Router Dumbledore
      option broadcast-address 192.181.6.255;
      option domain-name-servers 192.181.3.3;   # DNS McGonagall
      default-lease-time 600;                   # 10 menit
      max-lease-time 6000;                      # 100 menit
    }

    host ChoChang {
        hardware ethernet 06:6a:b2:3d:ac:dc;    # MAC address ChoChang
        fixed-address 192.181.6.14;             # IP statis untuk ChoChang
        option routers 192.181.6.1;             # Router Dumbledore
        option broadcast-address 192.181.6.255;
        option domain-name-servers 192.181.3.3; # DNS McGonagall
    }
```

<br>

## Soal 6

> Dimulai dari asrama Gryffindor yang menjadi PHP worker, mereka harus melakukan deployment untuk website berikut menggunakan PHP 7.4.

> _The Gryffindor house, represented by the PHP workers, must deploy the following website using PHP 7.4._

**Answer:**

- Screenshot

  ![deployment](https://github.com/user-attachments/assets/1655d8bf-9a70-4ce2-9279-5b1c0ed97e5c)


- Configuration
  ```
    cp /etc/nginx/sites-available/A26-9 /etc/nginx/sites-available/gryffindor.hogwarts.a26.com
    ln -s /etc/nginx/sites-available/gryffindor.hogwarts.a26.com /etc/nginx/sites-enabled/
  ```

  ```
    server {
      listen 80;
      server_name gryffindor.hogwarts.a26.com;

      root /var/www/hogwarts/gryffindor.hogwarts.a26.com;
      index index.php index.html index.htm;

      location / {
          try_files $uri $uri/ /index.php?$query_string;
      }

      location ~ \.php$ {
          include snippets/fastcgi-php.conf;
          fastcgi_pass unix:/run/php/php7.4-fpm.sock;
          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
          include fastcgi_params;
      }
    }
  ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 7

> Khusus perlombaan ini, Voldemort sudah jinak dan dia menjadi load balancer untuk para penghuni asrama Gryffindor yang menjadi worker PHP. Aturlah agar Voldemort dapat membagi pekerjaan kepada worker PHP secara optimal. Sebagai pengetesan awal, terapkan algoritma round robin dan lakukan test index.php menggunakan apache benchmark dengan 1000 request dan 100 request/second. Lakukan test sebanyak 3 kali lalu hitung rata-rata dan standar deviasi dari time/request

> _Voldemort, who is now reformed, becomes the load balancer for the Gryffindor PHP workers. Optimize Voldemort to distribute tasks to the PHP workers. For the initial test, apply the round-robin algorithm and test it to the index.php page using Apache Benchmark with 1,000 requests and 100 requests/second. Do the test 3 times and calculate the mean and standard deviation of time/request._

- Screenshot

![image](https://github.com/user-attachments/assets/b1ccaf95-91d5-47bc-acbb-9fa6cdc6583d)
![image](https://github.com/user-attachments/assets/f9a4c47e-dece-4616-a825-3dcb7b3b6ecd)
![image](https://github.com/user-attachments/assets/46b24059-03de-49b8-9f02-b95ad9994a16)

- Configuration
  ```
    upstream worker {
        server 192.181.1.2;
        server 192.181.1.3;
        server 192.181.1.14;
    }

    server {
        listen 80;
        server_name gryffindor.hogwarts.a26.com;

        root /var/www/html;

        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
            proxy_pass http://worker;
        }
    } 
  ```

  `ab -n 1000 -c 100 http://gryffindor.hogwarts.a26.com/index.php`

- Explanation

  `Put your explanation in here`

<br>

## Soal 8

> Dalam penilaian akhir tahun ini, dibutuhkan algoritma terbaik, cobalah tes 3 algoritma load balancer dengan menggunakan jmeter. Jmeter perlu melakukan login, akses home, dan terakhir logout. Lakukan test dengan 300 thread dan 3 sec ramp up period. Lakukan test sebanyak 3 kali per algoritma, lalu hitung rata-rata dan standar deviasi dari response time. (username: wingardium, password: leviosa)


> _For the final assessment, try three different load-balancing algorithms using JMeter with 300 threads and a 3-second ramp-up period. Jmeter have to be able to login, access homepage, and logout. Do the test 3 times for each algorithm, then calculate the mean and standard deviation of response time. (username: wingardium, password: leviosa)_

**Answer:**

- Screenshot

![image](https://github.com/user-attachments/assets/b1ccaf95-91d5-47bc-acbb-9fa6cdc6583d)
![image](https://github.com/user-attachments/assets/f9a4c47e-dece-4616-a825-3dcb7b3b6ecd)
![image](https://github.com/user-attachments/assets/46b24059-03de-49b8-9f02-b95ad9994a16)

- Configuration
  ```
    upstream worker {
        server 192.181.1.2;
        server 192.181.1.3;
        server 192.181.1.14;
    }

    server {
        listen 80;
        server_name gryffindor.hogwarts.a26.com;

        root /var/www/html;

        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
            proxy_pass http://worker;
        }
    } 
  ```

  `ab -n 1000 -c 100 http://gryffindor.hogwarts.a26.com/index.php`

- Explanation

  `Put your explanation in here`

<br>

## Soal 9

> Tidak semua IP dapat akses asrama Gryffindor melalui IP Load balancer Voldemort. Untuk itu, berikan akses pada load balancer Voldemort. Autentikasi akan memerlukan username: “jarkom” dan password: “modul3”. Simpan file autentikasi pada  /etc/nginx/secretchamber 

> _Not all IPs can access Gryffindor's house through Voldemort’s load balancer. Grant access to the Voldemort load balancer. Authentication will require username: “jarkom” and password: “modul3”. Save the authentication file in /etc/nginx/secretchamber._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/65d0dbfe-0ab4-4bc4-ac04-6fbad2af8525)
  ![image](https://github.com/user-attachments/assets/cfc08139-b0ed-4d13-b99a-fc021f20123c)
  ![image](https://github.com/user-attachments/assets/a300b64d-fa2a-41a0-bb23-da692898cae6)
  ![image](https://github.com/user-attachments/assets/b1084c36-78f3-4556-9d74-f20f13915fe6)

- Configuration

  ```
    mkdir /etc/nginx/secretchamber
    htpasswd -c /etc/nginx/secretchamber/htpasswd jarkom modul3
  ```

  Voldemort (Load Balancer):
  ```
    upstream backend {
      server 192.181.1.2;
      server 192.181.1.3;
      server 192.181.1.14;
    }

    server {
      listen 80;
      server_name gryffindor.hogwarts.A26.com;

      location / {
          auth_basic "Restricted Content";
          auth_basic_user_file /etc/nginx/secretchamber/htpasswd;

          proxy_pass http://backend;
          proxy_set_header Host $host;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      }

      proxy_next_upstream error timeout http_500 http_502 http_503 http_504;
      proxy_next_upstream_timeout 5s;
    }
  ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 10

> Setelah menambahkan autentikasi ke Gryffindor, coba testing ulang dengan menggunakan JMeter (algoritma round robin) serta skenario, thread, dan ramp up period yang sama seperti no 8 (300 thread, 3 sec ramp up period, login-home-logout). Kali ini, coba juga jumlah worker yang berbeda: 3 worker, 2 worker, dan 1 worker. 

> _After adding authentication to Gryffindor, retest using JMeter (round-robin algorithm) with the same scenario, thread, and ramp up period as number 8 (300 thread, 3 sec ramp up period, login-home-logout). This time, test with different numbers of workers: 3 workers, 2 workers, and 1 worker._

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 11

> Hogwarts juga bekerjasama dengan ITS dalam perlombaan ini. Untuk itu, setiap request pada Voldemort yang mengandung /informatika pada akhir url akan di proxy passing menuju halaman https://www.its.ac.id/informatika/id/beranda/ 

> _Hogwarts has also partnered with ITS for this competition. Any request to Voldemort containing /informatika at the end of the URL should be proxied to the page at https://www.its.ac.id/informatika/id/beranda/._


**Answer:**

- Screenshot

  ![No11-1](https://github.com/user-attachments/assets/872a3c01-ed8d-4287-b132-36dff631e6f6)


- Configuration

  
  Voldemort (Load Balancer):
  ```
  upstream backend {
    server 192.181.1.2;
    server 192.181.1.3;
    server 192.181.1.14;
  }

  server {
    listen 80;
    server_name gryffindor.hogwarts.A26.com;

    location / {
        auth_basic "Restricted Content";
        auth_basic_user_file /etc/nginx/secretchamber/htpasswd;

        proxy_pass http://backend;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    location ~* /informatika$ {
        rewrite ^(.*)/informatika$ /informatika/id/beranda/ break;
        proxy_pass https://www.its.ac.id;
        proxy_set_header Host www.its.ac.id;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    proxy_next_upstream error timeout http_500 http_502 http_503 http_504;
    proxy_next_upstream_timeout 5s;
  }
  ```

- Explanation

  Pertama lakukan instalasi seperti nomor sebelumnya, lalu tambahkan script berikut pada `/etc/nginx/sites-available/gryffindor.hogwarts.A26.com`:
  ```
  location ~* /informatika$ {
      rewrite ^(.*)/informatika$ /informatika/id/beranda/ break;
      proxy_pass https://www.its.ac.id;
      proxy_set_header Host www.its.ac.id;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
  }
  ```

  Testing dengan meggunakan command berikut pada `Worker`:

  ```
  lynx gryffindor.hogwarts.A26.com/informatika
  lynx gryffindor.hogwarts.A26.com/sesuatu/apa/pun/itu/informatika

  ```

<br>

## Soal 12

> Selain butuh autentikasi dalam pengaksesan asrama Gryffindor melalui LB Voldemort, juga perlu dibatasi dengan pembatasan IP.  LB Voldemort hanya boleh diakses oleh client dengan IP [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, dan [Prefix IP].5.155. hint: (fixed in dulu clientnya) 


> _In addition to requiring authentication for access to Gryffindor through Voldemort’s load balancer, IP restrictions also need to be enforced. Voldemort's load balancer can only be accessed by clients with IPs: [Prefix IP].2.64, [Prefix IP].2.100, [Prefix IP].5.50, and [Prefix IP].5.155. (hint: fixed client IPs first)._

**Answer:**

- Screenshot

  ![No12-1](https://github.com/user-attachments/assets/b79b9242-a662-43e4-ad56-6af5e0db7f0d)

  ![No12-2](https://github.com/user-attachments/assets/0299418e-cd37-4a84-b7f5-708f0604ab57)

- Configuration
  Voldemort (Load Balancer):
  ```
  upstream backend {
    server 192.181.1.2;
    server 192.181.1.3;
    server 192.181.1.14;
  }

  server {
    listen 80;
    server_name gryffindor.hogwarts.A26.com;

    location / {
        allow 192.181.2.64;
        allow 192.181.2.100;
        allow 192.181.5.50;
        allow 192.181.5.155;
        # allow 192.181.1.14; Untuk Testing Allow IP HermioneGranger

        deny all;
        auth_basic "Restricted Content";
        auth_basic_user_file /etc/nginx/secretchamber/htpasswd;

        proxy_pass http://backend;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    location ~* /informatika$ {
        rewrite ^(.*)/informatika$ /informatika/id/beranda/ break;
        proxy_pass https://www.its.ac.id;
        proxy_set_header Host www.its.ac.id;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    proxy_next_upstream error timeout http_500 http_502 http_503 http_504;
    proxy_next_upstream_timeout 5s;
  }
  ```

- Explanation

  Sama seperti soal sebelumnya kita menambahkan script ini pada `/etc/nginx/sites-available/gryffindor.hogwarts.A26.com`:
  ```
  allow 192.181.2.64;
  allow 192.181.2.100;
  allow 192.181.5.50;
  allow 192.181.5.155;
  deny all;
  ```

  Untuk melakukan testing kita dapat mengubah salah 1 IP pada `Worker` agar sesuai dengan IP yang di allow lalu coba untuk login dengan IP tersebut.

<br>

## Soal 13

> Pengaturan database yang dibutuhkan dalam perlombaan ini wajib diatur di Hagrid. Pastikan pengaturan database tersebut dapat diakses oleh Lunalovegood, FiliusFlitwick, dan ChoChang dengan menggunakan username: kelompokyyy dan password: passwordyyy 

> _Database setup for this competition is managed by Hagrid. Ensure that this database can be accessed by LunaLovegood, FiliusFlitwick, and ChoChang using the username: "kelompokyyy" and password: "passwordyyy”_

**Answer:**

- Screenshot

 ![No13-1](https://github.com/user-attachments/assets/f7110187-1779-46a1-be31-d823fd0260b7)

- Configuration

  Hagrid (Database):
  ```
  apt-get update
  apt-get install mariadb-server -y
  service mysql start

  cp /root/my.cnf /etc/mysql/my.cnf
  cp /root/50-server.cnf /etc/mysql/mariadb.conf.d/50-server.cnf

  service mysql restart

  mysql -u root -p
  Enter password: 

  # Run di dalam database setelah login

  CREATE USER 'kelompokA26'@'%' IDENTIFIED BY 'passwordA26';
  CREATE USER 'kelompokA26'@'localhost' IDENTIFIED BY 'passwordA26';
  CREATE DATABASE dbkelompokA26;
  GRANT ALL PRIVILEGES ON *.* TO 'kelompokA26'@'%';
  GRANT ALL PRIVILEGES ON *.* TO 'kelompokA26'@'localhost';
  FLUSH PRIVILEGES;

  # Test di Laravel Worker :
  mariadb --host=192.181.4.2 --port=3306 --user=kelompokA26 --password=passwordA26 dbkelompokA26 -e "SHOW DATABASES;"
  ```

- Explanation

 Pertama-tama, pada node Hagrid (Database) lakukan update dan install terlebih dahulu:
 ```
apt-get update
apt-get install mariadb-server -y
service mysql start
 ```
Lalu, edit pada `/etc/mysql/my.cnf`:
```
[client-server]

# Import all .cnf files from configuration directory
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mariadb.conf.d/

# Options affecting the MySQL server (mysqld)
[mysqld]
skip-networking=0
skip-bind-address
```
Pada `/etc/mysql/mariadb.conf.d/50-server.cnf` ganti pada bagian ini:
```
bind-address            = 127.0.0.1
```
Lalu jalankan command berikut pada terminal:
```
mysql -u root -p
Enter password: 

# Run di dalam database setelah login

CREATE USER 'kelompokA26'@'%' IDENTIFIED BY 'passwordA26';
CREATE USER 'kelompokA26'@'localhost' IDENTIFIED BY 'passwordA26';
CREATE DATABASE dbkelompokA26;
GRANT ALL PRIVILEGES ON *.* TO 'kelompokA26'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'kelompokA26'@'localhost';
FLUSH PRIVILEGES;
```

Terakhir untuk testing, gunakan salah satu Laravel Worker lalu jalankan script ini :
```
echo 'nameserver 192.181.3.3
nameserver 192.168.122.1' > /etc/resolv.conf

apt-get update
apt-get install lynx -y
apt-get install mariadb-client -y


mariadb --host=192.181.4.2 --port=3306 --user=kelompokA26 --password=passwordA26 dbkelompokA26 -e "SHOW DATABASES;"
```


<br>

## Soal 14

> Selain itu, untuk Lunalovegood, FiliusFlitwick, dan ChoChang memiliki website sesuai dengan https://github.com/lodaogos/laravel-jarkom-modul-3/tree/main  berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer! Pastikan database di Hagrid sudah ada isinya sekarang dan server Laravel sudah running di localhost!

> _Additionally, LunaLovegood, FiliusFlitwick, and ChoChang have websites following this GitHub link: Laravel Jarkom Modul 3. Install PHP 8.0 and Composer! Make sure Hagrid's data storage is populated, and the Laravel servers are running on localhost!_

**Answer:**

- Screenshot

  ![No14-1](https://github.com/user-attachments/assets/41c62399-cd15-494d-b3b6-0b9191a49878)

  ![No14-2](https://github.com/user-attachments/assets/f56adb17-90d9-4eaa-88d3-2144677c666b)

- Configuration

  Script Utama:
  ```
  echo 'nameserver 192.181.3.3
  nameserver 192.168.122.1' > /etc/resolv.conf

  apt-get update
  apt-get install lynx -y
  apt-get install mariadb-client -y
  apt-get install -y lsb-release ca-certificates apt-transport-https 
  software-properties-common gnupg2
  curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
  sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
  apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
  apt-get install nginx -y

  apt-get update
  apt-get install software-properties-common
  add-apt-repository ppa:ondrej/php

  service nginx start
  service php8.0-fpm start

  # Install Composer
  wget https://getcomposer.org/download/2.0.13/composer.phar
  chmod +x composer.phar
  mv composer.phar /usr/local/bin/composer

  # Install + Clone Github Project Laravel
  apt-get install git -y
  cd /var/www && git clone https://github.com/lodaogos/laravel-jarkom-modul-3.git
  cd /var/www/laravel-jarkom-modul-3 && composer update
  ```

  Script untuk Setup Laravel:
  ```
  cd /var/www/laravel-jarkom-modul-3/ && cp .env.example .env
  echo 'APP_NAME=Laravel
  APP_ENV=local
  APP_KEY=
  APP_DEBUG=true
  APP_URL=http://localhost

  LOG_CHANNEL=stack
  LOG_DEPRECATIONS_CHANNEL=null
  LOG_LEVEL=debug

  DB_CONNECTION=mysql
  DB_HOST=192.181.4.2
  DB_PORT=3306
  DB_DATABASE=dbkelompokA26
  DB_USERNAME=kelompokA26
  DB_PASSWORD=passwordA26

  BROADCAST_DRIVER=log
  CACHE_DRIVER=file
  FILESYSTEM_DISK=local
  QUEUE_CONNECTION=sync
  SESSION_DRIVER=file
  SESSION_LIFETIME=120

  MEMCACHED_HOST=127.0.0.1

  REDIS_HOST=127.0.0.1
  REDIS_PASSWORD=null
  REDIS_PORT=6379

  MAIL_MAILER=smtp
  MAIL_HOST=mailpit
  MAIL_PORT=1025
  MAIL_USERNAME=null
  MAIL_PASSWORD=null
  MAIL_ENCRYPTION=null
  MAIL_FROM_ADDRESS="hello@example.com"
  MAIL_FROM_NAME="${APP_NAME}"

  AWS_ACCESS_KEY_ID=
  AWS_SECRET_ACCESS_KEY=
  AWS_DEFAULT_REGION=us-east-1
  AWS_BUCKET=
  AWS_USE_PATH_STYLE_ENDPOINT=false

  PUSHER_APP_ID=
  PUSHER_APP_KEY=
  PUSHER_APP_SECRET=
  PUSHER_HOST=
  PUSHER_PORT=443
  PUSHER_SCHEME=https
  PUSHER_APP_CLUSTER=mt1

  VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
  VITE_PUSHER_HOST="${PUSHER_HOST}"
  VITE_PUSHER_PORT="${PUSHER_PORT}"
  VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
  VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"' > /var/www/laravel-jarkom-modul-3/.env


  cd /var/www/laravel-jarkom-modul-3/ && php artisan key:generate
  cd /var/www/laravel-jarkom-modul-3/ && composer install

  cd /var/www/laravel-jarkom-modul-3/ && php artisan migrate:fresh
  cd /var/www/laravel-jarkom-modul-3/ && php artisan db:seed --class=MusicsTableSeeder
  cd /var/www/laravel-jarkom-modul-3/ && php artisan jwt:secret
  ```

  Script Tambahan untuk Deployment:
  ```
  echo 'server {
    listen 8001;

    root /var/www/laravel-jarkom-modul-3/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
      include snippets/fastcgi-php.conf;
      fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
    }

    location ~ /\.ht {
            deny all;
            }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
  }' > /etc/nginx/sites-available/laravel-worker

  ln -s /etc/nginx/sites-available/laravel-worker /etc/nginx/sites-enabled/

  chown -R www-data.www-data /var/www/laravel-jarkom-modul-3/storage

  service php8.0-fpm start

  service nginx restart
  ```

  Testing dengan :
  ```
  lynx localhost:8001 # Di Worker LunaLovegood
  lynx localhost:8002 # Di Worker FiliusFlitwick
  lynx localhost:8003 # Di Worker ChoChang 
  ```

- Explanation
 Pertama-tama, install semua dependensi yang diperlukan menggunakan script berikut:
 ```
  apt-get update
  apt-get install lynx -y
  apt-get install mariadb-client -y
  apt-get install -y lsb-release ca-certificates apt-transport-https 
  software-properties-common gnupg2
  curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
  sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
  apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
  apt-get install nginx -y

  apt-get update
  apt-get install software-properties-common
  add-apt-repository ppa:ondrej/php

  service nginx start
  service php8.0-fpm start
 ```

 Lalu Install Composer dan Git sekaligus clone project laravelnya:
 ```
  # Install Composer
  wget https://getcomposer.org/download/2.0.13/composer.phar
  chmod +x composer.phar
  mv composer.phar /usr/local/bin/composer

  # Install + Clone Github Project Laravel
  apt-get install git -y
  cd /var/www && git clone https://github.com/lodaogos/laravel-jarkom-modul-3.git
  cd /var/www/laravel-jarkom-modul-3 && composer update
 ```

 Gunakan script ini untuk setup `.env` pada direktori Laravel Project:
 ```
  cd /var/www/laravel-jarkom-modul-3/ && cp .env.example .env
  echo 'APP_NAME=Laravel
  APP_ENV=local
  APP_KEY=
  APP_DEBUG=true
  APP_URL=http://localhost

  LOG_CHANNEL=stack
  LOG_DEPRECATIONS_CHANNEL=null
  LOG_LEVEL=debug

  DB_CONNECTION=mysql
  DB_HOST=192.181.4.2
  DB_PORT=3306
  DB_DATABASE=dbkelompokA26
  DB_USERNAME=kelompokA26
  DB_PASSWORD=passwordA26

  BROADCAST_DRIVER=log
  CACHE_DRIVER=file
  FILESYSTEM_DISK=local
  QUEUE_CONNECTION=sync
  SESSION_DRIVER=file
  SESSION_LIFETIME=120

  MEMCACHED_HOST=127.0.0.1

  REDIS_HOST=127.0.0.1
  REDIS_PASSWORD=null
  REDIS_PORT=6379

  MAIL_MAILER=smtp
  MAIL_HOST=mailpit
  MAIL_PORT=1025
  MAIL_USERNAME=null
  MAIL_PASSWORD=null
  MAIL_ENCRYPTION=null
  MAIL_FROM_ADDRESS="hello@example.com"
  MAIL_FROM_NAME="${APP_NAME}"

  AWS_ACCESS_KEY_ID=
  AWS_SECRET_ACCESS_KEY=
  AWS_DEFAULT_REGION=us-east-1
  AWS_BUCKET=
  AWS_USE_PATH_STYLE_ENDPOINT=false

  PUSHER_APP_ID=
  PUSHER_APP_KEY=
  PUSHER_APP_SECRET=
  PUSHER_HOST=
  PUSHER_PORT=443
  PUSHER_SCHEME=https
  PUSHER_APP_CLUSTER=mt1

  VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
  VITE_PUSHER_HOST="${PUSHER_HOST}"
  VITE_PUSHER_PORT="${PUSHER_PORT}"
  VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
  VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"' > /var/www/laravel-jarkom-modul-3/.env


  cd /var/www/laravel-jarkom-modul-3/ && php artisan key:generate
  cd /var/www/laravel-jarkom-modul-3/ && composer install

  cd /var/www/laravel-jarkom-modul-3/ && php artisan migrate:fresh
  cd /var/www/laravel-jarkom-modul-3/ && php artisan db:seed --class=MusicsTableSeeder
  cd /var/www/laravel-jarkom-modul-3/ && php artisan jwt:secret
 ```

 Selanjutnya, gunakan script ini untuk mengatur agar Websitr Laravel yang dideploy dapat dijalankan pada port 8001,8002,8003 di masing-masing Laravel Worker:
 ```
  server {
    listen 8001;

    root /var/www/laravel-jarkom-modul-3/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files $uri $uri/ /index.php?$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php$ {
      include snippets/fastcgi-php.conf;
      fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
    }

    location ~ /\.ht {
            deny all;
            }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
  }'
 ```
 Lakukan symlink dan restart php dan nginx:
 ```
  ln -s /etc/nginx/sites-available/laravel-worker /etc/nginx/sites-enabled/

  chown -R www-data.www-data /var/www/laravel-jarkom-modul-3/storage

  service php8.0-fpm start

  service nginx restart
 ```
 Terakhir testing dengan :
  ```
  lynx localhost:8001 # Di Worker LunaLovegood
  lynx localhost:8002 # Di Worker FiliusFlitwick
  lynx localhost:8003 # Di Worker ChoChang 
  ```

<br>

## Soal 15

> Lakukan testing endpoint /register sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Kenapa failed 99x? Jelaskan! 

> _Test the /register endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Why did 99 tests fail? Explain!_

**Answer:**

- Screenshot

  ![No15-2](https://github.com/user-attachments/assets/410f0636-83fc-452e-bae2-16797fbfd6e9)

  ![No15-2](https://github.com/user-attachments/assets/40e377a5-ebc1-4a64-baf6-283c7f94920a)



- Configuration

  apt-get update
  apt install apache2-utils -y

  echo '
  {
      "username": "username",
      "password": "password"
  }
  ' > registerdata.json

  ab -n 100 -c 10 -p registerdata.json -T application/json http://192.181.6.2:8001/api/auth/register

- Explanation

  Pertama, install update dan install dependensi yang diperlukan:
  ```
  apt-get update
  apt install apache2-utils -y
  ```
  Lalu, tambahkan perintah berikut pada `registerdata.json`:
  ```
  {
      "username": "username",
      "password": "password"
  }
  ```

  Setelah itu lakukan testing dengan command berikut:
  ```
  ab -n 100 -c 10 -p registerdata.json -T application/json http://192.181.6.2:8001/api/auth/register
  ```
<br>

## Soal 16

> Lakukan juga testing pada endpoint /login sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Dapatkan token melalui responsenya juga!

> _Test the /login endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Collect the token from the response!_

**Answer:**

- Screenshot

  ![No16-1](https://github.com/user-attachments/assets/66a9c0a2-ace1-4658-93f7-a19a2555e3d8)

  ![No16-2](https://github.com/user-attachments/assets/cad8cdcd-687e-4aad-adb1-12bcc1dafd05)


- Configuration

  ```
  apt-get update
  apt install apache2-utils -y

  echo '
  {
      "username": "username",
      "password": "password"
  }
  ' > logindata.json

  ab -n 100 -c 10 -v 4 -p registerdata.json -T application/json http://192.181.6.2:8001/api/auth/login

  # Untuk mendapatkan token : ab -n 100 -c 10 -v 4 -p registerdata.json -T application/json http://192.181.6.2:8001/api/auth/login > response.log cat
  # response.log | grep -o '"token":"[^"]*' | grep -o '[^"]*$' >> tokens.txt
  # cat response.log | grep -o '"token":"[^"]*' | grep -o '[^"]*$' | sed 's/$/\n/' >> tokens.txt


  ```

- Explanation
  Sama seperti soal sebelumnya, update dan install dependesi yang diperlukan:
  ```
  apt-get update
  apt install apache2-utils -y

  echo '
  {
      "username": "username",
      "password": "password"
  }
  ' > logindata.json

  ```

  Lalu testing dengan menggunakan:
  ```
  ab -n 100 -c 10 -v 4 -p registerdata.json -T application/json http://192.181.6.2:8001/api/auth/login

  ```

  Untuk mendapatkan token dan memasukkannya pada file `tokens.txt`:
  ```
  ab -n 100 -c 10 -v 4 -p registerdata.json -T application/json http://192.181.6.2:8001/api/auth/login > response.log cat
  response.log | grep -o '"token":"[^"]*' | grep -o '[^"]*$' >> tokens.txt
  cat response.log | grep -o '"token":"[^"]*' | grep -o '[^"]*$' | sed 's/$/\n/' >> tokens.txt

  ```
  Berikut ini adalah token yang kami dapat:
  ```
  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6InBrOUV3THVjY21wRjdaTDgiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.EzHOWqDZXe6NErs7qWBlUsIuxjOqI1fWMObJYopnMoM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6IkdnVU9wMUpWQUt5YmszTngiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.ATibHTz5wjSM0J1I9pD_E4zjcErn9j939NFUbSOeXxo

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6IjhMcUdCS0lpSDNNMWtGOVkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.LiVfAu_T9kaxUEa5xAx-LCvQXyBRhfeu7jKFTeOTiZk

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6Ilhwc29vdTRIYW1UTU1NVmUiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.b6OlVexQoSY0eNUlGRRdfvR_55VD_HK6SP_5peLQZ_k

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6ImtyRElCRzA5R3UzdWkyUmciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.9pg5qyDuFZQYHb3XRt0Vivt_2vHJfVk7mpHsJZqGBoY

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6Ik5TUmlsOXVKMEMwSkNUV1kiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.qRPNo-eSRs-6y_ILBLnLt1EKOnY2yLEKB-f7DXqeSyw

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6InBxVHRnekdHUENYNmh2ZEIiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.iviSrdRv7uv1ylOTtlxTiQI1_OgwdU59lJDeTAIQiSk

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMSwiZXhwIjoxNzI5ODI5MzIxLCJuYmYiOjE3Mjk4MjU3MjEsImp0aSI6IjBLVHJRamV2OEVLTWlPOTAiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.FuSq6Fwa76G7uCGHWcDHsmA_rXq6Blz8yBnv7LE8JpE

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6IlJLNVRQdVpaeDlUNGlncHIiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.v3vHRC-QU5klxGX925UoyFCN98GNMSqD-AphUHuEKsQ

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6Ik15b2h2d0c4VkhlUGMxQ2IiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.gp-BxTK0Kdw-gslgCAdBia6D4REFHqJ-O-CPlKpna7o

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6InVUS1luYXBqOUc0bzlzZ00iLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.Et4NyNgba_JWV8v5ggFz_tuTT8kvHgi8Ff3q9pTM81Q

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6ImVvZnZBWG9sTmk2MTNBemQiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.t4_SRVWimg9AufPYC4-RBpGakMEVGN3E2SuwLnirLes

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6InBMWUtsSHhjaER2OUJDMWkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.XsUD7PP5KTYjCIiLaq_uvL3BFSyGxarj9Uj5ZcWXfto

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6IlZXdGVKcG5LRWxZYjEzZm0iLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.ice2tJxjvVRz-dmqWyG2jGeDGmrMTgN80QWy_PTvaDI

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6IlhrZ2ZXZXk2VHc0VzFBT1oiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.MX8pdBJZT7Qnm80MkCrr1D9Kh4z3g-eGbiMs8nxcbgM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6Im5lMUVsbFVYSWdHMTBqMnQiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.XpeW28HaKnp8gZwwlpapTcv5IDEbN54w5tH2BzMoOX8

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6IkNPOEJjZ0VjSEhLNU9tYTkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.rrhJNT8TNHGZOr-ZRbf9hwSl_jMk4HLTZjWXOxJFBMc

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6Ik1uZk9LaEpka1ZQMjN0d3kiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.DjoTlwVuSO0_uiYT5PNSXYwlL-hN1i34bAkYKAIz16o

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6IjJlZ29jYk9CVWltelcwMGsiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.SG5_BBb5grb3kZc71DNHe4tzL5dXt6R2knlrrXyrMfs

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6InlkUVJPVnJXSEVaVW9HZ0siLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.sPgCZ59aSRgaAYhiuSG0T4eV_IZGeKPHn-v9A4Y_Zp8

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6ImpHcVA1cVBUS0p6c1JDS0wiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.1VDsZUko_3FRoaBGMi3nMQr4RNyWdifW5XZKV1NRyDA

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6IlRxUm9CcVhjVXVjRnM2QnciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.oD4ROnS9CKTzqY8Syh44Gyzk0UY3jRaTLI7k-4xeRb8

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6InFnd0lzR1Jab2pSU1RUbUEiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.Aaf8cC3oLG0eYsK9-KBOf9NohYvd38IFR4Y9y-pK-fA

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMiwiZXhwIjoxNzI5ODI5MzIyLCJuYmYiOjE3Mjk4MjU3MjIsImp0aSI6ImJQNHVuc3RQSkhkaWVZTFoiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.pC9llcE_yMN1UqK3CFQeTDtL2kw054g_aLpyOXO_zEI

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IklhRWNNQWx0Y3JBN2x4QTciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.X8JPDO_Oxjvo8HiuJmPHjQIEAatjSHXkKyARXDLKshA

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IjQzZUp2cUFCUEUxMUUxeXUiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.f3otCCmC3VxHfg2z8ldLedbQT_nVoaxJFOjd5lKSBxw

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6ImxOOUljSFdFZVNLY2VlTWQiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.qr3ZduYXY7_TRX99TDPCRCcsCfjOMD78F3YhS1gahsc

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6ImtpbjdaQk5hQzJVcTNpcHkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.0kbldDN6XC3-NB9X2vKB7TTC7sMScHbXg5BcF_mdZhw

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IlpNM0ZxQmdqVDlESWNITDQiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.K_rxKOyyPcMPnyZTBqMb02CraXF5Cd8mfHdz8iuHDsA

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IlBYRkdweVJZWWlkWnkzd1giLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.h3FLyfWqh4fXMchPSsbT9uusqzjl-w6epoKnkej9e70

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IkR5UFFJWkpiOVRma2k3cnYiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.bpnngyKObjgBJNTRS5sn5llALxuEMEn4wtfCyHhx0VM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IkNGdXczRGVaZHR6YmpQdWciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.6pikIMsPuBjq9-VAE_zKsHuwrLA_l4a7wFA9R-CPOuQ

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IldDaU03bTBxbTIzUDhzSmoiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.lp2cLA2SLwjHIPm3AOSwge_4em7Ive8orPfBfMD0qTA

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IlpxOGNHSU1Sc3htWXBBcEkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.OwU4PuAscT9FAhnnNH4gfU1A595Mb5AiXBejlPhTsIE

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IkVnWUNBbFo0VkJUNzZ0cVoiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.PKbTNKK8MgjtVpysBuhwhLOLdQAFsDwkRh59vBa1sbM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IlprTUt4bDBjTzBlamExajgiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.c_uJoGSiibQR5gXNv_eBj-HjENGeqj2ZbP2JYUahrXA

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6Iko0UGNjNEZnVDlnbld3cHYiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.MT9ooO9F4XJ0v9nVV1JDjPmWLMOAJj9x2b3-hGen6oM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6Ik5HWWI1UFlKSTdGenFsb1giLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.63WyTwXwSMWPGNFMpl0TN5NoKFRlT8AkZZnaNcpGoMw

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6IndyWWJDVTJaa2I5QWhjcHMiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.TvVctiqZka5PSbZ8mavm5YnSGiQa1z045lYP25_Yass

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyMywiZXhwIjoxNzI5ODI5MzIzLCJuYmYiOjE3Mjk4MjU3MjMsImp0aSI6ImFoTHc0THlmT1hnMjI2cjEiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.jIHXfIfk_iDWgs-WicReY7jTuE00NQkKMh5aVgIBCw8

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6InNjNHhxZFV2NWx6U1haczUiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.Qjm_fhTv_bDRwVql_i_8QwxRGzpr4tK0PyM7AI7nVHU

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6IlVKdDJEZ3FLalJ5T21YMlciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.0NTAdYe_-pJ_EFuB8Twqa5Jm5WAVsSTnIpRo8LDqRPI

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6ImJSc1RkSjJiNGtkZ2VHREIiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.OK5e52iS5FI4se8qYFMzIyBm3t3ao5S6eOdhm4mZmsg

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6IjNlS3BYeFpjS0RmSlhHaHAiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.Jt-t1ILraPgCKSDG7zWCID4krjb4tpIwafW-rwXw3rU

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6ImJvUkNEWGJKVWVKdldrdjkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.4AAkygYTgFaMlxpbxSgBTpAB0RVAwTBXiklxZEUXkCI

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6ImloeTNCanc4QUgxd3NES1QiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.AHZ726MM3o8G6sS4TALJjwfxxcKnHF4ZoxRBLgXiXps

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6InF3U000SGhxWEVRTUdQVWUiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.ETg8r7bQvfnF1DDaKlGIeOjTu8sCV9fedyfvXSx1KG0

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6IjNQQTlJWVRUVFdwdHFaRlYiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.b1fGfbwVoAKl44n99HKzvfWD31rtaw4zvGo96Uhjitc

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6Im5SQnlRejBpbzlaNUZvSmoiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.c3hYsoewjudmvVRlqWhLTDNIce9eXp_NrjkJ1xJi06M

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6ImNxMmdmRWE1QXpnUGFYS2UiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.RUUklFYPwf31fIYIEX836s3I7y7-Xl8A6N_CEZra3Bs

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6ImM1RW85MzR2M0hlcUNqRmwiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.nsHp3n2JAdCkbC9h0oESaiyQC7yhPczY85n2dcIMsvw

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6IkEzTjBoUDQzR0Y3M3Z2cUciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.fx7t37wcVbfoExaKeFkuPXWX8Defla69AQktatMVRx8

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6InZCRDRlZ2pYbGxVcVh2VWgiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.v5KTmxg_9Vr7vf-cXFbA6opkqlY6EFRIswlrZXrbTIo

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6IlZkSnlTdVZxSG1ZYnZRckoiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.FzOxx87Nqhgutm2agGZ8tY-OZsxlQLO2bH2yjrjoJxs

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI0LCJuYmYiOjE3Mjk4MjU3MjQsImp0aSI6InlWeHRGSk1yWk03Z1FSenciLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.W6rd_QhSKYWG5jiLddpoypSklsCu9zfr0acCFMXJSlg

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNCwiZXhwIjoxNzI5ODI5MzI1LCJuYmYiOjE3Mjk4MjU3MjUsImp0aSI6InB6dHM1ZzdpbXhXbnc1YWkiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.x-GHnpqpJbx2qcfM37wb28RK5QDviSb7JjJfVkevTfk

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNSwiZXhwIjoxNzI5ODI5MzI1LCJuYmYiOjE3Mjk4MjU3MjUsImp0aSI6Im9Wc04zc2twbGd2QXZqQk4iLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.UjQmkjgtbAwwOxJPYPJic-QnQIt_WxM5SSf_WaCj9dM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNSwiZXhwIjoxNzI5ODI5MzI1LCJuYmYiOjE3Mjk4MjU3MjUsImp0aSI6Ik1XZm80NnQzNmVINlIzNkIiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.kjqcv9vxwRl3EGFdIJn8QWWKnsAOYIyryC7wzFQWpqM

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNSwiZXhwIjoxNzI5ODI5MzI1LCJuYmYiOjE3Mjk4MjU3MjUsImp0aSI6IlRibk5CcldrNXB6MmtveDgiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.IpljtB3vuZCypAKCZgDIqnTUPX-G1o8HmwrWfEi7KOE

  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTkyLjE4MS42LjI6ODAwMS9hcGkvYXV0aC9sb2dpbiIsImlhdCI6MTcyOTgyNTcyNSwiZXhwIjoxNzI5ODI5MzI1LCJuYmYiOjE3Mjk4MjU3MjUsImp0aSI6InY2SWt2cnpMUGNia2U1T1EiLCJzdWIiOiIxIiwicHJ2IjoiMjNiZDVjODk0OWY2MDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyJ9.ML-rsniiv39VEcok_sWFvlZH72Frg9BEPYb0GQWiMsE
  ```
  
<br>

## Soal 17

> Coba testing pada endpont /me sebanyak 100 request dengan 10 request/second di salah satu worker menggunakan apache benchmark dari SusanBones! Periksa responsenya apakah sudah sesuai dengan yang diloginkan? 

> _Test the /me endpoint with 100 requests and 10 requests per second on one of the workers using Apache Benchmark from SusanBones! Check if the response matches the logged-in user!_

**Answer:**

- Screenshot

  ![No17-1](https://github.com/user-attachments/assets/724da9eb-8940-4b3e-8fa5-ef4f8103f950)

  ![No17-2](https://github.com/user-attachments/assets/dc3e661d-f0be-43f7-935f-6cc64f9588f5)

- Configuration

  apt-get update
  apt install apache2-utils -y
  apt-get install jq -y


  
  curl -X POST -H "Content-Type: application/json" -d @logindata.json http://192.181.6.2:8001/api/auth/login > login_output.txt

  token=$(cat login_output.txt | jq -r '.token')

  ab -n 100 -c 10 -H "Authorization: Bearer $token" http://192.181.6.2:8001/api/me

- Explanation

  Pertama update dan install dependensi yang diperlukan :
  ```
  apt-get update
  apt install apache2-utils -y
  apt-get install jq -y
  ```

  Dapatkan tokennya terlebih dahulu sebelum mengakses endpoint `/api/me`:
  ```
  curl -X POST -H "Content-Type: application/json" -d @logindata.json http://192.181.6.2:8001/api/auth/login > login_output.txt
  ```
  Lalu kita set token nya secara global:
  ```
  token=$(cat login_output.txt | jq -r '.token')
  ```
  Terakhir lakukan testing:
  ```
  ab -n 100 -c 10 -H "Authorization: Bearer $token" http://192.181.6.2:8001/api/me
  ```

  

<br>

## Soal 18

> Mendekati tugas akhir perlombaan ini, mari seimbangkan kekuatan LunaLovegood, FiliusFlitwick, dan ChoChang untuk bekerja sama secara adil! Buatkan load balancer Laravel dengan Dementor dan implementasikan Proxy Bind untuk mengaitkan IP dari ketiga worker tersebut!

> _As the competition nears its end, balance the workload of LunaLovegood, FiliusFlitwick, and ChoChang! Create a Laravel load balancer using Dementor and implement Proxy Bind to link the IPs of the three workers!_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  Dementor (Load Balancer):
  ```
  upstream backend {
    server 192.181.6.2:8001;    # IP LunaLovegood
    server 192.181.6.3:8002;    # IP FiliusFlitwick
    server 192.181.6.11:8003;   # IP ChoChang
  }

  server {
      listen 80;
      server_name ravenclaw.hogwarts.A26.com;

      location / {
          
          proxy_pass http://backend;

          proxy_set_header Host $host;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header X-Forwarded-Proto $scheme;

          proxy_bind 192.181.4.4;  # Ganti dengan IP server Nginx jika diperlukan
          
          proxy_connect_timeout 5s;
          proxy_read_timeout 60s;
          proxy_send_timeout 60s;
      }

      # Configure failover for specific errors
      proxy_next_upstream error timeout http_500 http_502 http_503 http_504;
      proxy_next_upstream_timeout 5s;
  }
  ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 19

> Untuk menguatkan para Laravel Worker, coba implementasikan PHP-FPM pada LunaLovegood, FiliusFlitwick, dan ChoChang. Untuk testing kinerja naikkan: 
pm.max_children
pm.start_servers
pm.min_spare_servers
pm.max_spare_servers
sebanyak tiga percobaan dan lakukan analisis testing menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _To strengthen the Laravel workers, implement PHP-FPM on LunaLovegood, FiliusFlitwick, and ChoChang. For performance testing, adjust: pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers. Run the tests three times and analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>

## Soal 20

> Yey terakhir. Menurut Professor Dumbledore, sepertinya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa worker-worker. Implementasikan Least-Conn pada Dementor. Lakukan analisis pada testing kinerja menggunakan apache benchmark sebanyak 100 request dengan 10 request/second atau menggunakan jmeter dengan 100 threads! (Pilih 1 metode testing)

> _Finally, Professor Dumbledore suggests that PHP-FPM might not be enough to improve the workers' performance. Implement the Least-Conn algorithm on Dementor. Analyze the performance by using Apache Benchmark with 100 requests at a rate of 10 requests per second or using JMeter with 100 threads! (Choose 1 testing method)_

**Answer:**

- Screenshot

  `Put your screenshot in here`

- Configuration

  `Put your configuration in here`

- Explanation

  `Put your explanation in here`

<br>
  
## Problems

## Revisions (if any)