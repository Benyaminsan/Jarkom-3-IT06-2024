# Jarkom-3-IT06-2024

Laporan Resmi Jarkom Modul 3
Buat Praktikan Jarkom IT06 yang masih pemula

| Nama | NRP |
| ---- | ---- |
| Callista Meyra Azizah | 5027231060 |
| Renjamin Khawarizmi Habibi | 5027231078 |

IP Prefix untuk IT06

| IT06 | 192.236 |
|----|----|

# Membuat Topologi

![image](https://github.com/user-attachments/assets/0871f0db-45ef-481a-82d4-d7f7f1edbc53)

Dengan Ketentuan berikut :

| Node | Kategori | Konfigurasi IP |
| ---- | ----- | ---- |
| Paradis | Router (DHCP Relay) | Dynamic | 
| Tybur | DHCP Server | Static | 
| Fritz | DNS Server | Static |
| Warhammer | Database Server | Static |
|Beast | Load Balancer (Laravel) | Static |
|Colossal | Load Balancer (PHP) | Static |
| Annie | Laravel Worker | Static | 
| Bertholdt | Laravel Worker | Static |
| Reiner| Laravel Worker | Static | 
| Armin | PHP Worker | Static |
| Eren | PHP Worker | Static |
| Mikasa | PHP Worker | Static | 
| Zeke | Client | Dynamic | 
| Erwin | Client | Dynamic | 

# CONFIG NODE
- Paradis
```
#Paradis (DHCP Relay)
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.236.1.1
    netmask 255.255.255.0

auto eth2
iface eth2 inet static
    address 192.236.2.1
    netmask 255.255.255.0

auto eth3
iface eth3 inet static
    address 192.236.3.1
    netmask 255.255.255.0

auto eth4
iface eth4 inet static
    address 192.236.4.1
    netmask 255.255.255.0
```

- Annie
```
auto eth0
iface eth0 inet static
    address 192.236.1.2
    netmask 255.255.255.0
    gateway 192.236.1.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Bertholdt
```
auto eth0
iface eth0 inet static
    address 192.236.1.3
    netmask 255.255.255.0
    gateway 192.236.1.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Reinier
```
auto eth0
iface eth0 inet static
    address 192.236.1.4
    netmask 255.255.255.0
    gateway 192.236.1.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Zeke
```
auto eth0
iface eth0 inet dhcp
```

- Armin
```
auto eth0
iface eth0 inet static
    address 192.236.2.2
    netmask 255.255.255.0
    gateway 192.236.2.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Mikasa
```
auto eth0
iface eth0 inet static
    address 192.236.2.3
    netmask 255.255.255.0
    gateway 192.236.2.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Eren
```
auto eth0
iface eth0 inet static
    address 192.236.2.4
    netmask 255.255.255.0
    gateway 192.236.2.1
```

- Erwin
```
auto eth0
iface eth0 inet dhcp
```

- Beast
```
auto eth0
iface eth0 inet static
    address 192.236.3.2
    netmask 255.255.255.0
    gateway 192.236.3.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Colossal
```
auto eth0
iface eth0 inet static
    address 192.236.3.3
    netmask 255.255.255.0
    gateway 192.236.3.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Warhammer
```
auto eth0
iface eth0 inet static
    address 192.236.3.4
    netmask 255.255.255.0
    gateway 192.236.3.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Tybur
```
auto eth0
iface eth0 inet static
    address 192.236.4.2
    netmask 255.255.255.0
    gateway 192.236.4.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

- Fritz
```
auto eth0
iface eth0 inet static
    address 192.236.4.3
    netmask 255.255.255.0
    gateway 192.236.4.1
    up echo 192.168.122.1 > /etc/resolv.conf
```

# PRE-SOAL
Pulau Paradis dan Marley, sama-sama menghadapi ancaman besar dari satu sama lain. Keduanya membangun infrastruktur pertahanan yang kuat untuk melindungi sistem vital mereka. Dengan strategi yang matang, mereka bersiap menghadapi serangan dan mempertahankan wilayah masing-masing.
Bangsa Marley, dipimpin oleh Zeke, telah mempersiapkan Annie, Bertholdt, dan Reiner untuk menyerang menggunakan Laravel Worker. Di sisi lain, Klan Eldia dari Paradis telah mempersiapkan Armin, Eren, dan Mikasa sebagai PHP Worker untuk mempertahankan pulau tersebut. Warhammer bertindak sebagai Database Server, sementara Beast dan Colossal sebagai Load Balancer. 
---------------------






