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
- **LakeKorridor (24 Host)**
  ```
  #A4 PCLakeKorridor-Frieren
  auto eth0
  iface eth0 inet static
  	address 192.221.0.66
  	netmask 255.255.255.224
  	gateway 192.221.0.65
  ```

### Konfigurasi Routing

- **ThePerformance**
  ```
  ```


### Testing


## CIDR
