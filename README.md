# **Praktikum 4 Jaringan Komputer**
<div align=justify>

Berikut repository dari Kelompok E30 Praktikum Modul 4 Jaringan Komputer.

# **Anggota Kelompok**

| Nama                      | NRP        | Kelas                |
| ------------------------- | ---------- | ----------------     |
| Hana Maheswari            | 5025211182 | Jaringan Komputer E  |
| Meyroja Jovancha Firoos   | 5025211204 | Jaringan Komputer E  |

# **Soal**
<div align=justify>

Berikut adalah topologi yang digunakan. 

![Topologi_Soal](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/e6ceac35-9055-475d-8e2a-2f035e3944bc)

- Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda.
  Keterangan: Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau sebaliknya
- Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR dan DAPAT DIKERJAKAN.
- Untuk di GNS3 CLOUD merupakan NAT1 jangan sampai salah agar bisa terkoneksi internet.
- Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan
- Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.

### List

1. [VLSM](#VLSM)
2. [CIDR](#CIDR)

## **VLSM**

### Pembagian Subnet
Pertama, dibuat plotting subnettingnya.

![VLSM_Subnet](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/befd5a8f-9ecb-4d00-9ec8-0f0a712d238b)

Kemudian dilakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan.

![VLSM_Rute](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/c7d505e9-28b8-47a8-b635-a02629984714)

### Tree
Selanjutnya dilakukan pembagian IP Address menggunakan tree sesuai dengan kebutuhan masing-masing subnet yang ada. Dimulai dari 192.221.0.0/19 kemudian bagi menjadi dua bagian, lakukan cara yang sama hingga 192.221.x.x/30.

![VLSM_Tree](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/947061b6-be93-4606-951e-69bfc1f1d008)

### VLSM-IP

![VLSM_PembagianIP](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/7e48d07c-da58-4097-8132-55336fc5484f)

### Konfigurasi Node

![VLSM_Config](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/68fdeacd-33e8-433f-9350-8a34e184499a)

- **Aura**
  ```
  auto eth0
  iface eth0 inet dhcp
  
  #A16 Aura-Frieren
  auto eth1
  iface eth1 inet static
  	address 192.221.0.17
  	netmask 255.255.255.252
  
  #A17 Aura-Denken
  auto eth2
  iface eth2 inet static
  	address 192.221.0.21
  	netmask 255.255.255.252
  
  #A18 Aura-Eisen
  auto eth3
  iface eth3 inet static
  	address 192.221.0.25
  	netmask 255.255.255.252
  ```
- **Frieren**
  ```
  #A16 Frieren-Aura
  auto eth0
  iface eth0 inet static
  	address 192.221.0.18
  	netmask 255.255.255.252
  	gateway 192.221.0.17
  
  #A15 Frieren-Flamme
  auto eth1
  iface eth1 inet static
  	address 192.221.0.13
  	netmask 255.255.255.252
  
  #A4 Frieren-PCLakeKorridor
  auto eth2
  iface eth2 inet static
  	address 192.221.0.65
  	netmask 255.255.255.224
  ```
- **Flamme**
  ```
  #A15 Flamme-Frieren
  auto eth0
  iface eth0 inet static
  	address 192.221.0.14
  	netmask 255.255.255.252
  	gateway 192.221.0.13
  
  #A13 Flamme-Fern
  auto eth1
  iface eth1 inet static
  	address 192.221.0.5
  	netmask 255.255.255.252
  
  #A2 Flamme-PCRohrRoad
  auto eth2
  iface eth2 inet static
  	address 192.221.8.1
  	netmask 255.255.252.0
  
  #A14 Flamme-Himmel
  auto eth3
  iface eth3 inet static
  	address 192.221.0.9
  	netmask 255.255.255.252
  ```
- **Fern**
  ```
  #A13 Fern-Flamme
  auto eth0
  iface eth0 inet static
  	address 192.221.0.6
  	netmask 255.255.255.252
  	gateway 192.221.0.5
  
  #A1 Fern-Switch4
  #PCLaubHills, PCAppetitRegion
  auto eth1
  iface eth1 inet static
  	address 192.221.24.1
  	netmask 255.255.248.0
  ```
- **Himmel**
  ```
  #A15 Himmel-Flamme
  auto eth0
  iface eth0 inet static
  	address 192.221.0.10
  	netmask 255.255.255.252
  	gateway 192.221.0.9
  
  #A3 Himmel-PCSchwerMountains
  auto eth1
  iface eth1 inet static
  	address 192.221.0.41
  	netmask 255.255.255.248
  ```
- **Denken**
  ```
  #A17 Denken-Aura
  auto eth0
  iface eth0 inet static
  	address 192.221.0.22
  	netmask 255.255.255.252
  	gateway 192.221.0.21
  
  #A9 Denken-Switch2 
  #PCRoyalCapital, PCWilleRegion
  auto eth1
  iface eth1 inet static
  	address 192.221.2.1
  	netmask 255.255.255.0
  ```
- **Eisen**
  ```
  #A18 Eisen-Aura
  auto eth0
  iface eth0 inet static
  	address 192.221.0.26
  	netmask 255.255.255.252
  	gateway 192.221.0.25
  
  #A10 Eisen-Switch1
  #ServerRitcher, ServerRevolte
  auto eth1
  iface eth1 inet static
  	address 192.221.0.49
  	netmask 255.255.255.248
  
  #A12 Eisen-Stark
  auto eth2
  iface eth2 inet static
  	address 192.221.0.1
  	netmask 255.255.255.252
  
  #A21 Eisen-Lugner
  auto eth3
  iface eth3 inet static
  	address 192.221.0.37
  	netmask 255.255.255.252
  
  #A19 Eisen-Linie
  auto eth4
  iface eth4 inet static
  	address 192.221.0.29
  	netmask 255.255.255.252
  ```
- **Lugner**
  ```
  #A21 Lugner-Eisen
  auto eth0
  iface eth0 inet static
  	address 192.221.0.38
  	netmask 255.255.255.252
  	gateway 192.221.0.37
  
  #A8 Lugner-PCTurkRegion
  auto eth1
  iface eth1 inet static
  	address 192.221.12.1
  	netmask 255.255.252.0
  
  #A7 Lugner-PCGrobeForest
  auto eth2
  iface eth2 inet static
  	address 192.221.1.1
  	netmask 255.255.255.0
  ```
- **Linie**
  ```
  #A19 Linie-Eisen
  auto eth0
  iface eth0 inet static
  	address 192.221.0.30
  	netmask 255.255.255.252
  	gateway 192.221.0.29
  
  #A20 Linie-Lawine
  auto eth1
  iface eth1 inet static
  	address 192.221.0.33
  	netmask 255.255.255.252
  
  #A6 Linie-PCGranzChannel
  auto eth2
  iface eth2 inet static
  	address 192.221.4.1
  	netmask 255.255.254.0
  ```
- **Lawine**
  ```
  #A20 Lawine-Linie
  auto eth0
  iface eth0 inet static
  	address 192.221.0.34
  	netmask 255.255.255.252
  	gateway 192.221.0.33
  
  #A5 Lawine-Switch7
  #PCBredtRegion, Heiter
  auto eth1
  iface eth1 inet static
  	address 192.221.0.129
  	netmask 255.255.255.192
  ```
- **Heiter**
  ```
  #A5 Heiter-Lawine
  auto eth0
  iface eth0 inet static
  	address 192.221.0.131
  	netmask 255.255.255.192
  	gateway 192.221.0.129
  
  #A11 Heiter-Switch8
  #ServerSein, PCRiegelCanyon
  auto eth1
  iface eth1 inet static
  	address 192.221.16.1
  	netmask 255.255.252.0
  ```
- **PC LakeKorridor (24 Host)**
  ```
  #A4 PCLakeKorridor-Frieren
  auto eth0
  iface eth0 inet static
  	address 192.221.0.66
  	netmask 255.255.255.224
  	gateway 192.221.0.65
  ```
- **PC RohrRoad (1000 Host)**
  ```
  #A1 PCRohrRoad-Flamme
  auto eth0
  iface eth0 inet static
  	address 192.221.8.2
  	netmask 255.255.252.0
  	gateway 192.221.8.1
  ```
- **PC LaubHills (397 Host)**
  ```
  #A1 LaubHills-Fern
  auto eth0
  iface eth0 inet static
  	address 192.221.24.2
  	netmask 255.255.248.0
  	gateway 192.221.24.1
  ```
- **PC AppetitRegion (625 Host)**
  ```
  #A1 PCAppetitRegion-Fern
  auto eth0
  iface eth0 inet static
  	address 192.221.24.3
  	netmask 255.255.248.0
  	gateway 192.221.24.1
  ```
- **PC SchwerMountains (5 Host)**
  ```
  #A3 PCSchwerMountains-Himmel
  auto eth0
  iface eth0 inet static
  	address 192.221.0.42
  	netmask 255.255.255.248
  	gateway 192.221.0.41
  ```
- **PC RoyalCapital (63 Host)**
  ```
  #A9 PCRoyalCapital-Denken
  auto eth0
  iface eth0 inet static
  	address 192.221.2.2
  	netmask 255.255.255.0
  	gateway 192.221.2.1
  ```
- **WilleRegion (63 Host)**
  ```
  #A9 PC WilleRegion-Denken
  auto eth0
  iface eth0 inet static
  	address 192.221.2.3
  	netmask 255.255.255.0
  	gateway 192.221.2.1
  ```
- **Server Richter**
  ```
  #A10 ServerRitcher-Eisen
  auto eth0
  iface eth0 inet static
  	address 192.221.0.50
  	netmask 255.255.255.248
  	gateway 192.221.0.49
  ```
- **Server Revolte**
  ```
  #A10 ServerRitcher-Eisen
  auto eth0
  iface eth0 inet static
  	address 192.221.0.51
  	netmask 255.255.255.248
  	gateway 192.221.0.49
  ```
- **Server Stark**
  ```
  #A12 Stark-Eisen
  auto eth0
  iface eth0 inet static
  	address 192.221.0.2
  	netmask 255.255.255.252
  	gateway 192.221.0.1
  ```
- **PC TurkRegion (1000 Host)**
  ```
  #A8 PCTurkRegion-Lugner
  auto eth0
  iface eth0 inet static
  	address 192.221.12.2
  	netmask 255.255.252.0
  	gateway 192.221.12.1
  ```
- **PC GrobeForest (250 Host)**
  ```
  #A7 PCGrobeForest-Lugner
  auto eth0
  iface eth0 inet static
  	address 192.221.1.2
  	netmask 255.255.255.0
  	gateway 192.221.1.1
  ```
- **PC GranzChannel (254 Host)**
  ```
  #A6 PCGranzChannel-Linie
  auto eth0
  iface eth0 inet static
  	address 192.221.4.2
  	netmask 255.255.254.0
  	gateway 192.221.4.1
  ```
- **PC BredtRegion (29 Host)**
  ```
  #A5 PCBredtRegion-Lawine
  auto eth0
  iface eth0 inet static
  	address 192.221.0.130
  	netmask 255.255.255.192
  	gateway 192.221.0.129
  ```
- **Server Sein**
  ```
  #A11 ServerSein-Heiter
  auto eth0
  iface eth0 inet static
  	address 192.221.16.2
  	netmask 255.255.252.0
  	gateway 192.221.16.1
  ```
- **PC RiegelCanyon (510 Host)**
  ```
  #A11 PC RiegelCanyon-Heiter
  auto eth0
  iface eth0 inet static
  	address 192.221.16.3
  	netmask 255.255.252.0
  	gateway 192.221.16.1
  ```
  
### Konfigurasi Routing

![VLSM_Routing](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/a3b89a39-745d-4844-8331-010d5103f827)

- **Fern**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.5			#default A1,A13
  ```
- **Himmel**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.9			#default A3,A14
  ```
- **Flamme**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.13			#default A2,A13,A14,A15
  route add -net 192.221.24.0 netmask 255.255.248.0 gw 192.221.0.6	#A1LaubHills,AppetitRegion
  route add -net 192.221.0.40 netmask 255.255.255.248 gw 192.221.0.10	#A3SchwerMountains
  ```
- **Frieren**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.17			#default A4,A15,A16
  route add -net 192.221.24.0 netmask 255.255.248.0 gw 192.221.0.14	#A1LaubHills,AppetitRegion
  route add -net 192.221.0.4 netmask 255.255.255.252 gw 192.221.0.14	#A13Flamme-Fern
  route add -net 192.221.8.0 netmask 255.255.252.0 gw 192.221.0.14	#A2RohrRoad
  route add -net 192.221.0.40 netmask 255.255.255.248 gw 192.221.0.14	#A3SchwerMountains
  route add -net 192.221.0.8 netmask 255.255.255.252 gw 192.221.0.14	#A14Flamme-Himmel
  ```
- **Denken**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.21			#default A9,A17
  ```
- **Lugner**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.37			#default A8,A7,A21
  ```
- **Heiter**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.129			#default A11,A5
  ```
- **Lawine**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.33			#default A20,A5
  route add -net 192.221.16.0 netmask 255.255.252.0 gw 221.221.0.131	#A11Sein,RiegelCanyon
  ```
- **Linie**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.29			#default A19,A6,A20
  route add -net 192.221.0.128 netmask 255.255.255.192 gw 192.221.0.34	#A5BredtRegion,Heiter
  route add -net 192.221.16.0 netmask 255.255.252.0 gw 192.221.0.34	#A11Sein,RiegelCanyon
  ```
- **Eisen**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.25			#default A18,A10,A12,A21,A19
  route add -net 192.221.0.128 netmask 255.255.255.192 gw 192.221.0.30	#A5BredtRegion,Heiter
  route add -net 192.221.16.0 netmask 255.255.252.0 gw 192.221.0.30	#A11Sein,RiegelCanyon
  route add -net 192.221.0.32 netmask 255.255.255.252 gw 192.221.0.30	#A20Linie-Lawine
  route add -net 192.221.4.0 netmask 255.255.254.0 gw 192.221.0.30	#A6GranzChannel
  route add -net 192.221.12.0 netmask 255.255.252.0 gw 192.221.0.38	#A8TurkRegion
  route add -net 192.221.1.0 netmask 255.255.255.0 gw 192.221.0.38	#A7GrobeForest
  ```
- **Aura**
  ```
  iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.221.0.0/16
  
  route add -net 192.221.24.0 netmask 255.255.248.0 gw 192.221.0.18	#A1LaubHills,AppetitRegion
  route add -net 192.221.0.4 netmask 255.255.255.252 gw 192.221.0.18	#A13Flamme-Fern
  route add -net 192.221.8.0 netmask 255.255.252.0 gw 192.221.0.18	#A2RohrRoad
  route add -net 192.221.0.40 netmask 255.255.255.248 gw 192.221.0.18	#A3SchwerMountains
  route add -net 192.221.0.8 netmask 255.255.255.252 gw 192.221.0.18	#A14Flamme-Himmel
  route add -net 192.221.0.12 netmask 255.255.255.252 gw 192.221.0.18	#A15Frieren-Flamme
  route add -net 192.221.0.64 netmask 255.255.255.224 gw 192.221.0.18	#A4LakeKorridor
  
  route add -net 192.221.2.0 netmask 255.255.255.0 gw 192.221.0.22	#A9RoyalCapital,WilleRegion
  
  route add -net 192.221.0.48 netmask 255.255.255.248 gw 192.221.0.26	#A10Ritcher,Revolte
  route add -net 192.221.0.0 netmask 255.255.255.252 gw 192.221.0.26	#A12Eisen-Stark
  route add -net 192.221.0.36 netmask 255.255.255.252 gw 192.221.0.26	#A21Eisen-Lugner
  route add -net 192.221.12.0 netmask 255.255.252.0 gw 192.221.0.26	#A8TurkRegion
  route add -net 192.221.1.0 netmask 255.255.255.0 gw 192.221.0.26	#A7GrobeForest
  route add -net 192.221.0.28 netmask 255.255.255.252 gw 192.221.0.26	#A19Eisen-Linie
  route add -net 192.221.4.0 netmask 255.255.254.0 gw 192.221.0.26	#A6GranzChannel
  route add -net 192.221.0.32 netmask 255.255.255.252 gw 192.221.0.26	#A20Linie-Lawine
  route add -net 192.221.0.128 netmask 255.255.255.192 gw 192.221.0.26	#A5BredtRegion,Heiter
  route add -net 192.221.16.0 netmask 255.255.252.0 gw 192.221.0.26	#A11Sein,RiegelCanyon
  ```
- **All Except Aura**
  ```
  echo nameserver 192.168.122.1 > /etc/resolv.conf
  ```

### Testing
Testing dari Server ke Server

- Sein-Richter

  <img width="423" alt="Screenshot (507)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/9cb3d4cb-8a45-41da-97c8-b2904037b7e7">

Testing dari Client ke Client

- GranzChannel-TurkRegion

  <img width="423" alt="Screenshot (506)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/4818f852-1666-4d66-bfb2-5a793f3bc361">

- RoyalCapital-LaubHills

  <img width="423" alt="Screenshot (503)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/35b49712-37e5-4939-be4b-eef444426f61">

Testing dari Client ke Router

- RiegelCanyon-Aura

  <img width="423" alt="Screenshot (505)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/95a08c7b-a57c-4aa9-84e6-1610d3a0c6f8">

- SchwerMountains-Lugner

  <img width="423" alt="Screenshot (501)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/c3aa7c7f-dae7-4f65-a9bb-6a5812efc615">

Testing dari Router ke Router

- Fern-Linie

  <img width="423" alt="Screenshot (504)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/4d3d023a-8b84-4c54-9cfe-15c6936c58b1">

- Heiter-Denken

  <img width="423" alt="Screenshot (502)" src="https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/108173681/0a8ec948-fe68-4cca-abcc-a2b1f20372a5">

## CIDR

CIDR atau biasa dikenal Classless Inter-Domain Routing adalah suatu metode pengalamatan dan pengelompokan alamat IP yang memungkinkan penggunaan lebih efisien dari ruang alamat IP yang tersedia di Internet.

### Topologi PKT 

![topologi pkt](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/145383781/a19bbf3d-1aa6-41c5-849d-45d13286fd80)

Disini alamat IP kelompok kami adalah 
```
192.221
```

### Penggabungan IP 

Hasil Penggabungan Subnet untuk CIDR ialah 

![topologii](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/145383781/899f5c13-006f-442e-838b-926ef36ff6e6)

### Tabel Penggabungan IP

Disini kami memakai 2 penggabungan subnet. Penggabungan 2 subnet ini menghasilkan 11 penggabungan dengan hasil akhir yaitu /11.


![penggabungan 1](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/145383781/62d5d2e1-7820-4631-bfa0-787558383f5d)

![penggabungan 2](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/145383781/dfa2fbf3-4a28-4f98-8b4f-76865f562757)


### Tree

Hasil Tree CIDR ialah

 ![FIXBGTTREE](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/145383781/5191c4fe-0155-4013-a7b8-62da58e985e3)

 Berdasarkan Prefix IP kami yaitu 192.221 , dilakukan pembuatan tree CIDR dan penentuan Network ID berdasarkan penggabungan IP sebagai berikut.

 ### Pembagian IP

 ![pembagian](https://github.com/hanamahes78/Jarkom-Modul-4-E30-2023/assets/145383781/c83a2ee2-4816-4597-b7b3-a40bc1e493ec)

### Testing
```
https://drive.google.com/drive/folders/1-bpsOqEj6Wvo-4aBPEIfYkjsnjLOGWin
```
