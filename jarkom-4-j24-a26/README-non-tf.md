| Name           | NRP        | Class     |
| ---            | ---        | ----------|
| Abillidya Nofianto Putri | 5025221164 | Jaringan Komputer (A) |
| Rhenaldy Chandra | 5025221190 | Jaringan Komputer (A) |

<br>

<b> Letakkan link excel hasil perhitungan di sini </b>
<br>
<b> _Place the excel calculation results link here_ </b>
```
https://docs.google.com/spreadsheets/d/1rfoKddHbqkkezp1W6Nu4CYTdl9PYTE3sQBoPxTDPajs/edit?usp=drivesdk
```

# Laporan Praktikum Modul 4 Non Terraform

## Prefix IP
Letakkan prefix IP yang digunakan di bawah:

_Put IP prefix used below:_
```
192.181.x.x
```

## Topology

- GNS3

  ![Topology-GNS3](https://github.com/user-attachments/assets/4e613413-63d4-44ff-aac2-03cfcc8117df)


- CPT

  ![Topology-CPT](https://github.com/user-attachments/assets/f8b99715-7b6a-40ec-af88-48a2f142e4b8)


<br>

## Routing

- Routing table

  ![Routing-table-A26](https://github.com/user-attachments/assets/3999beaa-cdae-4510-bf21-3f3ec9cb1209)

- Route visualization in topology
  
  ![Route subnet_topologi_A26](https://github.com/user-attachments/assets/550fa389-186e-4014-9631-dccaef6a6b51)

  

<br>

## VLSM

### Tree

- Tree image

  ![Tree-GNS3-CPT-GNS3 - VLSM drawio](https://github.com/user-attachments/assets/a6af9bb4-2c6b-487c-abfa-86272b380484)

- IP distribution table

  ![IP-Distribution-Table](https://github.com/user-attachments/assets/6c0f28b2-275b-4964-a069-ff77305c412c)

### Subnetting (If you use GNS3)

Configuration to every router, client, and server for subnetting.

- Kamachi:

  ```
  auto eth0
  iface eth0 inet dhcp

  #A1
  auto eth1
  iface eth1 inet static
  address 192.181.0.1
  netmask 255.255.255.252

  #A4
  auto eth2
  iface eth2 inet static
  address 192.181.0.5
  netmask 255.255.255.252

  #A7
  auto eth3
  iface eth3 inet static
  address 192.181.0.13
  netmask 255.255.255.252

  #A14
  auto eth4
  iface eth4 inet static
  address 192.181.0.33
  netmask 255.255.255.252

  #A17
  auto eth5
  iface eth5 inet static
  address 192.181.0.37
  netmask 255.255.255.252
  ```

- Fiamma:

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
  address 192.181.2.1
  netmask 255.255.254.0
  ```

- GoldenDawn:

  ```
  #A4
  auto eth0
  iface eth0 inet static
  address 192.181.0.6
  netmask 255.255.255.252
  gateway 192.181.0.5

  #A5
  auto eth1
  iface eth1 inet static
  address 192.181.8.1
  netmask 255.255.248.0

  #A6
  auto eth2
  iface eth2 inet static
  address 192.181.0.9
  netmask 255.255.255.252
  ```

- Necessarius:

  ```
  #auto lo
  #iface lo inet loopback

  #A7
  auto eth0
  iface eth0 inet static
  address 192.181.0.14
  netmask 255.255.255.252
  gateway 192.181.0.13

  #A8
  auto eth1
  iface eth1 inet static
  address 192.181.0.17
  netmask 255.255.255.252

  #A12
  auto eth2
  iface eth2 inet static
  address 192.181.0.29
  netmask 255.255.255.252
  ```

- Alice:

  ```
  #A14
  auto eth0
  iface eth0 inet static
  address 192.181.0.34
  netmask 255.255.255.252
  gateway 192.181.0.33

  #A15
  auto eth1
  iface eth1 inet static
  address 192.181.6.1
  netmask 255.255.254.0
  ```

- Kihara:

  ```
  #A17
  auto eth0
  iface eth0 inet static
  address 192.181.0.38
  netmask 255.255.255.252
  gateway 192.181.0.37

  #A19
  auto eth1
  iface eth1 inet static
  address 192.181.0.45
  netmask 255.255.255.252

  #A18
  auto eth2
  iface eth2 inet static
  address 192.181.0.41
  netmask 255.255.255.252
  ```

- Vento:

  ```
  #A2
  auto eth0
  iface eth0 inet static
  address 192.181.2.3
  netmask 255.255.254.0
  gateway 192.181.2.1

  #A3
  auto eth1
  iface eth1 inet static
  address 192.181.0.65
  netmask 255.255.255.224
  ```

- Terra:

  ```
    auto eth0
  iface eth0 inet static
  address 192.181.0.66
  netmask 255.255.255.224
  gateway 192.181.0.65
  ```

- Acqua:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.2.2
  netmask 255.255.254.0
  gateway 192.181.2.1
  ```

- Aiwass:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.9.1
  netmask 255.255.248.0
  gateway 192.181.8.1
  ```

- Aleister:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.10.1
  netmask 255.255.248.0
  gateway 192.181.8.1
  ```

- Mathers:

  ```
  auto eth0
  iface eth0 inet static  
  address 192.181.0.10
  netmask 255.255.255.252
  gateway 192.181.0.9
  ```

- Coronzon:

  ```
  #A8
  auto eth0
  iface eth0 inet static
  address 192.181.0.18
  netmask 255.255.255.252
  gateway 192.181.0.17

  #A9
  auto eth1
  iface eth1 inet static
  address 192.181.0.21
  netmask 255.255.255.252

  #A10
  auto eth2
  iface eth2 inet static
  address 192.181.0.25
  netmask 255.255.255.252
  ```

- Elizard:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.0.22
  netmask 255.255.255.252
  gateway 192.181.0.21
  ```

- Index:

  ```
  #A10
  auto eth0
  iface eth0 inet static
  address 192.181.0.26
  netmask 255.255.255.252
  gateway 192.181.0.25

  #A11
  auto eth1
  iface eth1 inet static
  address 192.181.0.49
  netmask 255.255.255.240
  ```

- Magnus:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.0.50
  netmask 255.255.255.240
  gateway 192.181.0.49
  ```

- Gremlin:

  ```
  #A12
  auto eth0
  iface eth0 inet static
  address 192.181.0.30
  netmask 255.255.255.252
  gateway 192.181.0.29

  #A13
  auto eth1
  iface eth1 inet static
  address 192.181.4.1
  netmask 255.255.254.0
  ```

- Thor:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.4.2
  netmask 255.255.254.0
  gateway 192.181.4.1
  ```

- Othinus:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.4.3
  netmask 255.255.254.0
  gateway 192.181.4.1
  ```

- LastOrder:

  ```
  #A15
  auto eth0
  iface eth0 inet static
  address 192.181.6.3
  netmask 255.255.254.0
  gateway 192.181.6.1

  #A16
  auto eth1
  iface eth1 inet static
  address 192.181.0.129
  netmask 255.255.255.128
  ```

- Leivinia:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.0.130
  netmask 255.255.255.128
  gateway 192.181.0.129
  ```

- Fuze:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.6.2
  netmask 255.255.254.0
  gateway 192.181.6.1
  ```

- Accel:

  ```
  #A19
  auto eth0
  iface eth0 inet static
  address 192.181.0.46
  netmask 255.255.255.252
  gateway 192.181.0.45

  #A20
  auto eth1
  iface eth1 inet static
  address 192.181.1.1
  netmask 255.255.255.128
  ```

- Railgun:

  ```
  #A20
  auto eth0
  iface eth0 inet static
  address 192.181.1.3
  netmask 255.255.255.128
  gateway 192.181.1.1

  #A21
  auto eth1
  iface eth1 inet static
  address 192.181.0.97
  netmask 255.255.255.224
  ```

- MeltDowner:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.0.99
  netmask 255.255.255.224
  gateway 192.181.0.97
  ```

- MentalOut:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.0.98
  netmask 255.255.255.224
  gateway 192.181.0.97
  ```

- DarkMatter:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.1.2
  netmask 255.255.255.128
  gateway 192.181.1.1
  ```

- Noukan:

  ```
  auto eth0
  iface eth0 inet static
  address 192.181.0.42
  netmask 255.255.255.252
  gateway 192.181.0.41
  ```

### Routing

Configuration to every router for routing.

- Kamachi:

  ```
  # Fiamma ( A1, A2, A3 )

  # Setting Acqua (A2) Subnet
  up route add -net 192.181.2.0/23 gw 192.181.0.2
  # Setting Terra (A3) Subnet
  up route add -net 192.181.0.64/27 gw 192.181.0.2

  # GoldenDawn ( A4, A5, A6 )

  # Setting Aiwass & Aleister (A5) Subnet
  up route add -net 192.181.0.8/30 gw 192.181.0.6
  # Setting Mathers (A6) Subnet
  up route add -net 192.181.8.0/21 gw 192.181.0.6

  # Necessarius ( A7, A8, A9, A10, A11, A12, A13 )


  up route add -net 192.181.4.0/23 gw 192.181.0.14
  up route add -net 192.181.0.20/30 gw 192.181.0.14
  up route add -net 192.181.0.48/28 gw 192.181.0.
  
  #Jika mau ke Gremlin, maka harus lewat Necessarius dulu
  up route add -net 192.181.0.28/30 gw 192.181.0.14
  #Jika mau ke Coronzon, maka harus lewat Necessarius dulu
  up route add -net 192.181.0.16/30 gw 192.181.0.14
  #Jika mau ke Index, maka harus lewat Necessarius dulu
  up route add -net 192.181.0.24/30 gw 192.181.0.14

  #Alice ( A14, A15, A16 )

  up route add -net 192.181.6.0/23 gw 192.181.0.34
  up route add -net 192.181.0.128/25 gw 192.181.0.34

  #Kihara ( A17, A18, A19, A20, A21 )

  #Jika mau ke Accel, maka harus lewat Kihara dulu
  up route add -net 192.181.0.44/30 gw 192.181.0.38

  up route add -net 192.181.1.0/25 gw 192.181.0.38
  up route add -net 192.181.0.40/30 gw 192.181.0.38
  up route add -net 192.181.0.96/27 gw 192.181.0.38
  ```

- Fiamma:

  ```
  # Setting Terra(A3) Subnet via Vento
  up route add -net 192.181.0.64/27 gw 192.181.2.3

  # reverse all traffic back to Kamachi
  up route add -net 0.0.0.0/0 gw 192.181.0.1
  ```

- GoldenDawn:

  ```
  up route add -net 0.0.0.0/0 gw 192.181.0.5
  ```

- Necessarius:

  ```
  #A13
  up route add -net 192.181.4.0/23 gw 192.181.0.30
  #A9
  up route add -net 192.181.0.20/30 gw 192.181.0.18
  #A11
  up route add -net 192.181.0.48/28 gw 192.181.0.18
  # A10 Jika mau ke Index, maka harus lewat Coronzon dulu
  up route add -net 192.181.0.24/30 gw 192.181.0.18

  up route add -net 0.0.0.0/0 gw 192.181.0.13
  ```

- Alice:

  ```
  # Setting LastOrder
  up route add -net 192.181.0.128/25 gw 192.181.6.3

  # reverse all traffic back to Kamachi
  up route add -net 0.0.0.0/0 gw 192.181.0.33
  ```

- Kihara:

  ```
  up route add -net 192.181.1.0/25 gw 192.181.0.46
  up route add -net 192.181.0.96/27 gw 192.181.0.46
  up route add -net 0.0.0.0/0 gw 192.181.0.37
  ```

- Vento:

  ```
  # reverse all traffic back to Fiamma
  up route add -net 0.0.0.0/0 gw 192.181.2.1
  ```

- Coronzon:

  ```
  #A11
  up route add -net 192.181.0.48/28 gw 192.181.0.26
  ```

- Index:

  ```
    up route add -net 0.0.0.0/0 gw 192.181.0.25
  ```

- Gremlin:

  ```
  route add -net 0.0.0.0/0 gw 192.181.0.29
  ```

- LastOrder:

  ```
  up route add -net 0.0.0.0/0 gw 192.181.6.1
  ```

- Accel:

  ```
  up route add -net 192.181.0.96/27 gw 192.181.1.3

  up route add -net 0.0.0.0/0 gw 192.181.0.45
  ```

- Railgun:

  ```
  up route add -net 0.0.0.0/0 gw 192.181.1.1
  ```

### Testing

- Client - client

  Terra (15 Host) -> Magnus (12 Host)
  ![C - C](https://github.com/user-attachments/assets/65f105c1-b0f9-497c-80d4-12a3dd3bfb3c)


- Client - Server

  Terra (15 Host) -> MentalOut
  ![C - S](https://github.com/user-attachments/assets/463d63dd-a418-4b5f-9dd0-762faa550328)


- Client - Router
  
  Terra (15 Host) -> LastOrder
  ![C - R](https://github.com/user-attachments/assets/de81f4ff-65e0-41cd-8f4e-abdab63819fc)


- Server - Server
  
  Othinus -> Noukan
  ![S - S](https://github.com/user-attachments/assets/803340fb-7e8d-4e26-9246-34ea1f78e8ba)


- Server - Router

  Othinus -> Vento
  
  ![S - R](https://github.com/user-attachments/assets/02e46537-5d34-478c-bb3e-6666af4cb373)
  

- Router - Router

  Railgun -> LastOrder
  ![R - R](https://github.com/user-attachments/assets/ee458810-5014-4fb9-8bd4-3daa5bc7ca65)


<br>

## CIDR

### Tree

- Tree image

  ![cidr-tree-a26](https://github.com/user-attachments/assets/b474731f-c374-4c13-a8bb-fe7cd40093e9)


- IP distribution table

  ![ip-table-cidr-a26](https://github.com/user-attachments/assets/5d36b688-a892-4513-b25b-06dcd35f5a7c)


### Subnet Merging Iteration

- Iteration 1

  ![cidr-1](https://github.com/user-attachments/assets/165a7a85-9496-46da-a11b-d6ed68aae617)

  ![iteration-1](https://github.com/user-attachments/assets/b8626bc6-3cfb-44c6-b392-251142bc0c36)


- Iteration 2

  ![cidr-2](https://github.com/user-attachments/assets/a785e22a-d026-4466-bb03-6b52a00fc1b2)

  ![iteration-2](https://github.com/user-attachments/assets/23c14a46-e430-43c8-9197-02f6f31ccd3a)

  
- Iteration 3

  ![cidr-3](https://github.com/user-attachments/assets/9d0d77e9-37bc-4068-b66e-6a99c05b7cd3)
  
  ![iteration-5](https://github.com/user-attachments/assets/fb28f114-5a50-4bd3-83c4-e397e869915d)

  
- Iteration 4

  ![cidr-4](https://github.com/user-attachments/assets/519d320b-4486-4264-b5b2-a7202e832634)
  
  ![iteration-4](https://github.com/user-attachments/assets/ec347e44-0888-4994-a9c0-db746ef0700b)


- Iteration 5

  ![cidr-5](https://github.com/user-attachments/assets/855c470c-a50a-46e7-8371-05d495672f41)
  
  ![iteration-5](https://github.com/user-attachments/assets/cdad8bd6-fbf0-469c-8eeb-797c98bf752c)


- Iteration 6

  ![cidr-6](https://github.com/user-attachments/assets/a41311ad-81b1-4f8d-a149-4e4493888230)
  
  ![iteration-6](https://github.com/user-attachments/assets/9cf5966f-be4e-4d16-b4ae-a6b3346797f9)


- Iteration 7

  ![cidr-7](https://github.com/user-attachments/assets/58a2eaa7-3813-4b7e-b4e1-a01336ec46f1)
  
  ![iteration-7](https://github.com/user-attachments/assets/2d7c3a39-a183-4fdd-a56d-961a9f324268)


- Iteration 8

  ![cidr-8](https://github.com/user-attachments/assets/23e8f507-bb4b-4134-acc2-1cef8efd81d3)
  
  ![iteration-8](https://github.com/user-attachments/assets/a6cf0bd5-5a73-4443-b960-0ea0678e771f)


### Subnetting (If you use CPT)
- Kamachi

  ![Kamachi-Config](https://github.com/user-attachments/assets/b3c41f1c-20d4-4491-8dd4-3797065a2790)

- Kihara

  ![Kihara-Config](https://github.com/user-attachments/assets/d9fd89b6-d9e1-4191-aeb6-3cbf8c7c7e99)

- Noukan

  ![Noukan-Config](https://github.com/user-attachments/assets/3a4b308f-8f09-4102-97a6-118df8e25384)

- Accel

  ![Accel-Config](https://github.com/user-attachments/assets/2d68e9f0-5ec1-42be-997f-9f2db008c621)

- DarkMatter

  ![DarkMatter-Config](https://github.com/user-attachments/assets/e1b0d765-3a26-4a77-ad46-73cb8b6c2d97)

- Railgun

  ![Railgun-Config](https://github.com/user-attachments/assets/78c352a4-06bb-4ad4-a246-26a719be5f5a)

- MentalOut

  ![MentalOut-Config](https://github.com/user-attachments/assets/7feae1b2-2824-4a3e-a3d7-cc42b7aa1a4f)

- MeltDowner

  ![MeltDowner-Config](https://github.com/user-attachments/assets/a434b7ca-002d-4b74-9727-3c8c2d54ab9a)

- Alice

  ![Alice-Config](https://github.com/user-attachments/assets/8bf1108a-b03c-410e-b947-60dd4622c91a)

- Fuze

  ![Fuze-Config](https://github.com/user-attachments/assets/dfb7b6ee-d57e-4072-acf6-1684c73e5b0a)

- LastOrder

  ![LastOrder-Config](https://github.com/user-attachments/assets/e96e4f31-6894-44b3-b56f-dfc48182b999)

- Leivinia

  ![Leivinia](https://github.com/user-attachments/assets/083c120a-2978-420b-bcad-1f1052555a47)

- Elizard

  ![Elizard-Config](https://github.com/user-attachments/assets/4e9ab590-b943-4314-bc0b-e56b759dd4ad)

- Magnus

  ![Magnus-Config](https://github.com/user-attachments/assets/b16bbb6c-3f2a-4b1a-bfe7-53c31c6f54a6)

  
- Coronzon

  ![Coronzon-Config](https://github.com/user-attachments/assets/c49feb1b-71ee-46e4-aacf-20ca22ad4b2e)

- Index

  ![Index-Config](https://github.com/user-attachments/assets/7305f33e-64e4-442d-a494-ebdb4670a267)

- Othinus

  ![Othinus-Config](https://github.com/user-attachments/assets/ee7b93f8-53e6-4e2a-b718-015c42b51f9f)

- Gremlin

  ![Gremlin-Config](https://github.com/user-attachments/assets/83a73f14-fe91-4535-abf0-5f98c283b6ed)

- Necessarius

  ![Necessarius-Config](https://github.com/user-attachments/assets/34aa5f3f-2c06-494d-b641-00a740459f05)

- Thor

  ![Thor-Config](https://github.com/user-attachments/assets/b6003a91-37a7-4d39-bfd9-5f7068ac7f4a)

- Mathers

  ![Mathers-Config](https://github.com/user-attachments/assets/cc6fafb6-c47c-45d6-84bf-3e969494bf7b)

- Aleister

  ![Aleister-Config](https://github.com/user-attachments/assets/100effa1-5489-451d-a6a8-5181bf20be2b)

- Aiwass

  ![Aiwass-Config](https://github.com/user-attachments/assets/a0e0589e-b05b-41e4-bcfe-bcd890a1868f)

- GoldenDawn

  ![GoldenDawn-Config](https://github.com/user-attachments/assets/6d6f218f-9edd-46d9-8119-38ae3e7a805f)

- Terra

  ![Terra-Config](https://github.com/user-attachments/assets/0af70836-d44b-4e47-96b5-3bd2e75ceae5)

- Vento

  ![Vento-Config](https://github.com/user-attachments/assets/925e1238-a8e0-4d43-8841-7ba8140b7194)

- Acqua

  ![Acqua-Config](https://github.com/user-attachments/assets/092e5d52-f5ac-4fa9-ba10-956be24f5b69)

- Fiamma

  ![Fiamma-Config](https://github.com/user-attachments/assets/5e5e0730-cfc6-41ce-80c6-7e9eebb66b24)



### Routing

Configuration to every router for routing.

- Kamachi:

  ```
   #Necessarius (A12, A13, A8, A10, A11,A9)
   ip route 192.181.2.0 255.255.255.252 192.181.8.2
   ip route 192.181.4.64 255.255.255.252 192.181.8.2
   ip route 192.181.0.0 255.255.254.0 192.181.8.2
   ip route 192.181.4.16 255.255.255.252 192.181.8.2
   ip route 192.181.4.0 255.255.255.240 192.181.8.2
   ip route 192.181.4.32 255.255.255.252 192.181.8.2

   #Alice (A15, A16)
   ip route 192.181.16.0 255.255.254.0 192.181.20.2
   ip route 192.181.18.0 255.255.255.128 192.181.20.2

   #GoldenDawn (A5, A6)
   ip route 192.181.64.0 255.255.248.0 192.181.80.2
   ip route 192.181.72.0 255.255.255.252 192.181.80.2

   #Fiamma (A2, A3)
   ip route 192.181.96.0 255.255.254.0 192.181.100.2
   ip route 192.181.98.0 255.255.255.224 192.181.100.2

   #Kihara (A18, A19, A20, A21)
   ip route 192.181.33.0 255.255.255.252 192.181.36.2
   ip route 192.181.34.0 255.255.255.252 192.181.36.2
   ip route 192.181.32.0 255.255.255.128 192.181.36.2
   ip route 192.181.32.128 255.255.255.224 192.181.36.2
  ```

- Fiamma:

  ```
   #Default route to Kamachi
   ip route 0.0.0.0 0.0.0.0 192.181.100.1

   #Vento (A3)
   ip route 192.181.98.0 255.255.255.224 192.181.96.3
  ```

- GoldenDawn:

  ```
   #Default route to Kamachi
   ip route 0.0.0.0 0.0.0.0 192.181.80.1
  ```

- Necessarius:

  ```
   #Default route to Kamachi
   ip route 0.0.0.0 0.0.0.0 192.181.8.1
  
   #Gremlin (A13)
   ip route 192.181.0.0 255.255.254.0 192.181.2.2
  
   #Coronzon (A11, A10, A9)
   ip route 192.181.4.16 255.255.255.252 192.181.4.66
   ip route 192.181.4.0 255.255.255.240 192.181.4.66
   ip route 192.181.4.32 255.255.255.252 192.181.4.66
  ```

- Alice:

  ```
   #LastOrder (A16)
   ip route 192.181.18.0 255.255.255.128 192.181.16.3
  
   #Default route to Kamachi
   ip route 0.0.0.0 0.0.0.0 192.181.20.1
  ```

- Kihara:

  ```
   #Accel (A20, A21)
   ip route 192.181.32.0 255.255.255.128 192.181.33.2
   ip route 192.181.32.128 255.255.255.224 192.181.33.2

   #Default route to Kamachi
   ip route 0.0.0.0 0.0.0.0 192.181.36.1
  ```

- Vento:

  ```
   #Default route to Fiamma
   ip route 0.0.0.0 0.0.0.0 192.181.96.1
  ```

- Coronzon:

  ```
   #Default route to Necessarius
   ip route 0.0.0.0 0.0.0.0 192.181.4.65

   #Index (A11)
   ip route 192.181.4.0 255.255.255.240 192.181.4.18
  ```
  
- Index:

  ```
   #Default route
   ip route 0.0.0.0 0.0.0.0 192.181.4.17
  ```

- Gremlin:

  ```
    #Default route
    ip route 0.0.0.0 0.0.0.0 192.181.2.1
  ```

- LastOrder:

  ```
    #Default route
    ip route 0.0.0.0 0.0.0.0 192.181.2.1
  ```

- Accel:

  ```
    #Default route
    ip route 0.0.0.0 0.0.0.0 192.181.33.1

    #Railgun (A21)
    ip route 192.181.32.128 255.255.255.224 192.181.32.3
  ```

- Railgun:

  ```
    #Default route
    ip route 0.0.0.0 0.0.0.0 192.181.32.1
  ```

### Testing

- Client - client

  Leivinia -> Terra
  
  ![Client-Client](https://github.com/user-attachments/assets/37a12cf8-4a3c-4e23-bcfa-d852af0df3ed)

- Client - Server

  Aiwass -> MentalOut
  
  ![Client-Server](https://github.com/user-attachments/assets/e748c129-4e4f-46a4-8814-65ff0da2403a)

- Client - Router

  DarkMatter -> Gremlin
  
  ![Client-Router](https://github.com/user-attachments/assets/43ad47bd-11e6-4474-b8f4-82dd855c06b4)

- Server - Server

  Elizard -> Noukan
  
  ![Server-Server](https://github.com/user-attachments/assets/1598a528-ca84-4e03-8cc7-b0025917deb6)

- Server - Router

  Othinus -> Vento
  
  ![Server-Router](https://github.com/user-attachments/assets/3a61a6fa-db98-4bd4-9fa9-ce96045f511e)

- Router - Router

  Railgun -> Coronzon
  
  ![Router-Router](https://github.com/user-attachments/assets/34442f31-e627-477a-a0da-54c9815f7cda)


<br>
  
## Problems

<br>

## Revisions (if any)
