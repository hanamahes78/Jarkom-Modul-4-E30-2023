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

Kemudian dilakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan.


### Tree
Selanjutnya dilakukan pembagian IP Address menggunakan tree sesuai dengan kebutuhan masing-masing subnet yang ada. Dimulai dari 192.221.0.0/19 kemudian bagi menjadi dua bagian, lakukan cara yang sama hingga 192.221.x.x/30.


### VLSM-IP

### Konfigurasi Node

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

- **Fern**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.5	#default A1,A13
  ```
- **Himmel**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.9	#default A3,A14
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
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.21	#default A9,A17
  ```
- **Lugner**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.37	#default A8,A7,A21
  ```
- **Heiter**
  ```
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.221.0.129	#default A11,A5
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

### Testing


## CIDR
