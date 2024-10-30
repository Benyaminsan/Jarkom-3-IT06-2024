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
    up echo 192.168.122.1 > /etc/resolv.conf
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

- Ada yang error gabisa connect internet? Cek ``` nano etc/resolv.conf ``` - apakah udah ada ``` nameserver 192.168.122.1 ``` ? Apabila belum, masukkan dan lakukan ulang.
- Jangan lupa, masukkan config berikut. Sesuai dengan nama-namanya. Lewat ``` nano /root/.bashrc ```
- Paradis (DHCP Relay)
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.236.0.0/16
apt-get update
apt-get install isc-dhcp-relay -y
```
- Tybur (DHCP Server)
```
apt-get update
apt-get install isc-dhcp-server -y
```
- Fritz (DNS Server)
```
apt-get update
apt-get install bind9 -y
```
- Beast & Colossal (Load Balancer)
```
apt-get update
apt-get install apache2-utils -y
apt-get install nginx -y
apt-get install lynx -y
```
- Warhammer (DB Server)
```
apt-get update
apt-get install mariadb-server -y
```
- Zeke dan Erwin (Client)
```
apt-get update
apt-get install lynx -y
apt-get install htop -y
apt-get install apache2-utils -y
apt-get install jq -y
```

# PRE-SOAL
Pulau Paradis dan Marley, sama-sama menghadapi ancaman besar dari satu sama lain. Keduanya membangun infrastruktur pertahanan yang kuat untuk melindungi sistem vital mereka. Dengan strategi yang matang, mereka bersiap menghadapi serangan dan mempertahankan wilayah masing-masing.
Bangsa Marley, dipimpin oleh Zeke, telah mempersiapkan Annie, Bertholdt, dan Reiner untuk menyerang menggunakan Laravel Worker. Di sisi lain, Klan Eldia dari Paradis telah mempersiapkan Armin, Eren, dan Mikasa sebagai PHP Worker untuk mempertahankan pulau tersebut. Warhammer bertindak sebagai Database Server, sementara Beast dan Colossal sebagai Load Balancer. 

# NO 0
Pulau Paradis telah menjadi tempat yang damai selama 1000 tahun, namun kedamaian tersebut tidak bertahan selamanya. Perang antara kaum Marley dan Eldia telah mencapai puncak. Kaum Marley yang dipimpin oleh Zeke, me-register domain name marley.yyy.com untuk worker Laravel mengarah pada Annie. Namun ternyata tidak hanya kaum Marley saja yang berinisiasi, kaum Eldia ternyata sudah mendaftarkan domain name eldia.yyy.com untuk worker PHP (0) mengarah pada Armin.

- Masukkan script berikut ke Fritz:
```
echo 'zone "marley.it06.com" { 
        type master; 
        file "/etc/bind/marley/marley.it06.com";
};

zone "eldia.it06.com" {
        type master;
        file "/etc/bind/eldia/eldia.it06.com";
}; ' >> /etc/bind/named.conf.local

mkdir /etc/bind/marley
mkdir /etc/bind/eldia

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     marley.it06.com. root.marley.it06.com. (
                  2024102619        ; Serial
                         604800         ; Refresh
                          86400          ; Retry
                        2419200        ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      marley.it06.com.
@       IN      A       192.236.1.2     ; IP Annie' > /etc/bind/marley/marley.it06.com

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     eldia.it06.com. root.eldia.it06.com. (
                   2024102619       ; Serial
                         604800         ; Refresh
                          86400          ; Retry
                        2419200        ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      eldia.it06.com.
@       IN      A       192.236.2.2    ; IP Armin' > /etc/bind/eldia/eldia.it06.com

service bind9 restart

```

- Misal belum bisa, maka lakukan berikut:
```
nano /etc/bind/named.conf.local
```
- Terus masukkan ini:
```
zone "marley.it06.com" { 
    type master; 
    file "/etc/bind/marley/marley.it06.com";
};

zone "eldia.it06.com" {
    type master;
    file "/etc/bind/eldia/eldia.it06.com";
};

```
- Verify dengan ini:
```
cat /etc/bind/named.conf.local
```
- Misal masih belum bisa, cek dengan command ini:
```
cat /etc/bind/marley/marley.it06.com
```
- Terus hasilnya harusnya ada ini:
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     marley.it06.com. root.marley.it06.com. (
                  2024102619        ; Serial
                         604800         ; Refresh
                          86400          ; Retry
                        2419200        ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      marley.it06.com.
@       IN      A       192.236.1.2     ; IP Annie
```
- Belum ada lagi? Maka lanjutkan dengan cara manual. Gunakan command berikut buat bikin foldernya:
```
mkdir -p /etc/bind/marley
mkdir -p /etc/bind/eldia
```
- Masukkan ini ke marley.it06.com:
```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     marley.it06.com. root.marley.it06.com. (
                  2024102619        ; Serial
                         604800         ; Refresh
                          86400          ; Retry
                        2419200        ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      marley.it06.com.
@       IN      A       192.236.1.2     ; IP Annie' | tee /etc/bind/marley/marley.it06.com

```
- Dan ini ke eldia.it06.com:
```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     eldia.it06.com. root.eldia.it06.com. (
                   2024102619       ; Serial
                         604800         ; Refresh
                          86400          ; Retry
                        2419200        ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      eldia.it06.com.
@       IN      A       192.236.2.2    ; IP Armin' | tee /etc/bind/eldia/eldia.it06.com

```
- Terus, cek dengan ini:
```
cat /etc/bind/marley/marley.it06.com
cat /etc/bind/eldia/eldia.it06.com
```
- Lalu restart BIND service-nya.
```
sudo systemctl restart bind9
```
# NO 1
Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.
# NO 1.1 - 1.5
Jauh sebelum perang dimulai, ternyata para keluarga bangsawan, Tybur dan Fritz, telah membuat kesepakatan sebagai berikut:
Semua Client harus menggunakan konfigurasi ip address dari keluarga Tybur (dhcp).
Client yang melalui bangsa marley mendapatkan range IP dari [prefix IP].1.05 - [prefix IP].1.25 dan [prefix IP].1.50 - [prefix IP].1.100 (2)
Client yang melalui bangsa eldia mendapatkan range IP dari [prefix IP].2.09 - [prefix IP].2.27 dan [prefix IP].2 .81 - [prefix IP].2.243 (3)
Client mendapatkan DNS dari keluarga Fritz dan dapat terhubung dengan internet melalui DNS tersebut (4)
Dikarenakan keluarga Tybur tidak menyukai kaum eldia, maka mereka hanya meminjamkan ip address ke kaum eldia selama 6 menit. Namun untuk kaum marley, keluarga Tybur meminjamkan ip address selama 30 menit. Waktu maksimal dialokasikan untuk peminjaman alamat IP selama 87 menit. (5)

- Pertama, kita setup Paradis dulu agar dhcpnya lancar:
```
nano etc/root/.bashrc
```
```
apt-get update
apt install isc-dhcp-relay -y

service isc-dhcp-relay start 

# What servers should the DHCP relay forward requests to? (Disini kita masukkan IP Tybur)
SERVERS="192.236.4.2" 

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3 eth4"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```
lalu buka ```nano /etc/sysctl.conf``` dan masukkan:
```
net.ipv4.ip_forward=1
```
Lalu jalankan:
```
service isc-dhcp-relay restart

```
- Selanjutnya, buka /etc/dhcp/dhcpd.conf di Tybur dengan:
```
nano /etc/dhcp/dhcpd.conf
```
- Lalu, masukkan script dibawah ke dalamnya - Ada beberapa detail mengenai nomor berapa yang dikerjakan:

```
# NO 1 cuma assign ip address
# NO 2 benerin subnet buat client Marley
subnet 192.236.1.0 netmask 255.255.255.0 {
    range 192.236.1.5 192.236.1.25; 
    range 192.236.1.50 192.236.1.100;
    option routers 192.236.1.1;
    option broadcast-address 192.236.1.255;
    option domain-name-servers 192.236.4.3;  # Fritz DNS Server - NO 4
    default-lease-time 1800;  # Lease time 30 menit untuk Marley - NO 5
    max-lease-time 5220;      # Lease time maksimal 87 menit - NO 5
}
# NO 3 subnet client Eldia
subnet 192.236.2.0 netmask 255.255.255.0 {
    range 192.236.2.9 192.236.2.27;
    range 192.236.2.81 192.236.2.243;
    option routers 192.236.2.1;
    option broadcast-address 192.236.2.255;
    option domain-name-servers 192.236.4.3;  # Fritz DNS Server - N0 4
    default-lease-time 360;   # Lease time 6 menit untuk Eldia - NO 5
    max-lease-time 5220;      # Lease time maksimal 87 menit - NO 5
}

subnet 192.236.3.0 netmask 255.255.255.0 {
    option routers 192.236.3.1;
}

subnet 192.236.4.0 netmask 255.255.255.0 {
    option routers 192.236.4.1;
}
```

# DOKUMENTASI NO 1.2 [IP ZEKE]
![WhatsApp Image 2024-10-30 at 20 12 41_c7bc2530](https://github.com/user-attachments/assets/6ec69f23-c3c2-439e-8c9e-e2c38ae38da0)

# DOKUMENTASI NO 1.3 [IP ERWIN]
![WhatsApp Image 2024-10-30 at 20 13 02_1b5984f4](https://github.com/user-attachments/assets/d9a43b04-6d9c-48a9-9933-4a753708b923)

# DOKUMENTASI NO 1.4 [PING ELDIA.ITO6.COM DAN PING MARLET.IT06.COM]
![WhatsApp Image 2024-10-30 at 20 07 03_6be7e50a](https://github.com/user-attachments/assets/10493cdd-3b14-47eb-b3c5-deb5f02ef7c2)

![WhatsApp Image 2024-10-30 at 20 06 15_0b6ed45a](https://github.com/user-attachments/assets/acb1e907-ad03-41ae-ad1a-77cbde1ab762)

# DOKUMENTASI 1.5 [LEASE TIME]
![WhatsApp Image 2024-10-30 at 20 06 48_f0507c84](https://github.com/user-attachments/assets/f24bd7c9-af40-4c3e-be8e-5f2ed3a1d545)

![WhatsApp Image 2024-10-30 at 20 07 21_bca7c5f5](https://github.com/user-attachments/assets/86154169-b53f-4550-a2af-b29bbea6899f)







