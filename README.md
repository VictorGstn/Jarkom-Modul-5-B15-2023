# Jarkom-Modul-4-B15-2023

## Area Subnet
![Mind Map](https://github.com/VictorGstn/Jarkom-Modul-4-B15-2023/assets/125529445/b6e254ef-84ac-4081-b922-c9ba06a9d814)

| Subnet   | Lenght  | Jumlah IP | SubNetmask      |   Nid       | Broadcast   |
|----------|---------|-----------|-----------------|-------------|-------------|
| A1       | /30     | 2         | 255.255.255.252 | 10.16.0.0   | 10.16.0.3   |
| A2       | /30     | 2         | 255.255.255.252 | 10.16.0.4   | 10.16.0.7   |
| A3       | /25     | 66        | 255.255.255.128 | 10.16.0.128 | 10.16.0.255 |
| A4       | /23     | 256       | 255.255.254.0   | 10.16.2.0   | 10.16.3.255 |
| A5       | /30     | 2         | 255.255.255.252 | 10.16.0.8   | 10.16.0.11  |
| A6       | /30     | 2         | 255.255.255.252 | 10.16.0.12  | 10.16.0.15  |
| A7       | /30     | 2         | 255.255.255.252 | 10.16.0.16  | 10.16.0.19  |
| A8       | /30     | 2         | 255.255.255.252 | 10.16.0.20  | 10.16.0.23  |
| A9       | /21     | 1023      | 255.255.248.0   | 10.16.8.0   | 10.16.15.255|
| A10      | /22     | 514       | 255.255.252.0   | 10.16.4.0   | 10.16.7.255 |
| Total    |  /20    | 1871      | 255.255.240.0   |             |             |

![All](https://github.com/VictorGstn/Jarkom-Modul-4-B15-2023/assets/125529445/d2eb6a28-3851-4d00-8908-f84460d36c80)

## Network config
```sh
---Aura---
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#A8
auto eth1
iface eth1 inet static
address 10.16.0.21
netmask 255.255.255.252

#A6
auto eth2
iface eth2 inet static
address 10.16.0.13
netmask 255.255.255.252


---Heiter---
auto lo
iface lo inet loopback

#A8
auto eth0
iface eth0 inet static
address 10.16.0.22
netmask 255.255.255.252
gateway 10.16.0.21

#A9
auto eth1
iface eth1 inet static
address 10.16.8.1
netmask 255.255.248.0

#A10
auto eth2
iface eth2 inet static
address 10.16.4.1
netmask 255.255.252.0

---Frieren---
auto lo
iface lo inet loopback

#A6
auto eth0
iface eth0 inet static
address 10.16.0.14
netmask 255.255.255.252
gateway 10.16.0.13

#A7
auto eth1
iface eth1 inet static
address 10.16.0.17
netmask 255.255.255.252

#A5
auto eth2
iface eth2 inet static
address 10.16.0.9
netmask 255.255.255.252

---Himmel---
auto lo
iface lo inet loopback

#A5
auto eth0
iface eth0 inet static
address 10.16.0.10
netmask 255.255.255.252
gateway 10.16.0.9

#A4
auto eth1
iface eth1 inet static
address 10.16.2.1
netmask 255.255.254.252

#A3
auto eth2
iface eth2 inet static
address 10.16.0.129
netmask 255.255.255.128

---Fern---
auto lo
iface lo inet loopback

#A3
auto eth0
iface eth0 inet static
address 10.16.0.130
netmask 255.255.255.128
gateway 10.16.0.129

#A2
auto eth1
iface eth1 inet static
address 10.16.0.5
netmask 255.255.255.252

#A1
auto eth2
iface eth2 inet static
address 10.16.0.1
netmask 255.255.255.252

---DHCP Client--
auto eth0
iface eth0 inet dhcp

---Sein---
auto eth0
iface eth0 inet static
address 10.16.4.2
netmask 255.255.252.0
gateway 10.16.4.1

---Stark---
auto eth0
iface eth0 inet static
address 10.16.0.18
netmask 255.255.255.252
gateway 10.16.0.17

---Richter---
auto eth0
iface eth0 inet static
address 10.16.0.6
netmask 255.255.255.252
gateway 10.16.0.5

---Revolte---
auto eth0
iface eth0 inet static
address 10.16.0.2
netmask 255.255.255.252
gateway 10.16.0.1
```


## Routing

```sh
#A9
route add -net 10.16.8.0 netmask 255.255.248.0 gw 10.16.0.22
#A10
route add -net 10.16.4.0 netmask 255.255.252.0 gw 10.16.0.22

#A7
route add -net 10.16.0.16 netmask 255.255.255.252 gw 10.16.0.14
#A5
route add -net 10.16.0.8 netmask 255.255.255.252 gw 10.16.0.14
#A4
route add -net 10.16.2.0 netmask 255.255.254.0 gw 10.16.0.14
#A3
route add -net 10.16.0.128 netmask 255.255.255.128 gw 10.16.0.14
#A2
route add -net 10.16.0.4 netmask 255.255.255.252 gw 10.16.0.14
#A1
route add -net 10.16.0.0 netmask 255.255.255.252 gw 10.16.0.14

--Heiter--
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.16.0.21

--Frieren--
#A4
route add -net 10.16.2.0 netmask 255.255.254.0 gw 10.16.0.10
#A3
route add -net 10.16.0.128 netmask 255.255.255.128 gw 10.16.0.10
#A2
route add -net 10.16.0.4 netmask 255.255.255.252 gw 10.16.0.10
#A1
route add -net 10.16.0.0 netmask 255.255.255.252 gw 10.16.0.10

--Himmel--
#A2
route add -net 10.16.0.4 netmask 255.255.255.252 gw 10.16.0.130
#A1
route add -net 10.16.0.0 netmask 255.255.255.252 gw 10.16.0.130

--Fern--
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.16.0.129
```
## DHCP
### DHCP Server
```sh
apt-get update -y
apt-get install isc-dhcp-server -y

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo '
subnet 10.16.0.0 netmask 255.255.255.252 {
}
subnet 10.16.0.4 netmask 255.255.255.252 {
}
subnet 10.16.0.128 netmask 255.255.255.128 {
	range 10.16.0.132 10.16.0.254;
    	option routers 10.16.0.130;
    	option broadcast-address 10.16.0.255;
    	option domain-name-servers 10.16.0.6;
    	default-lease-time 3600;
    	max-lease-time 5760;

}
subnet 10.16.2.0 netmask 255.255.254.0 {
	range 10.16.2.4 10.16.2.254;
    	option routers 10.16.2.1;
    	option broadcast-address 10.16.3.255;
    	option domain-name-servers 10.16.0.6;
    	default-lease-time 3600;
    	max-lease-time 5760;
}
subnet 10.16.0.8 netmask 255.255.255.252 {
}
subnet 10.16.0.12 netmask 255.255.255.252 {
}
subnet 10.16.0.20 netmask 255.255.255.252 {
}
subnet 10.16.8.0 netmask 255.255.248.0 {
	range 10.16.8.4 10.16.8.254;
    	option routers 10.16.8.1;
    	option broadcast-address 10.16.15.255;
    	option domain-name-servers 10.16.0.6;
    	default-lease-time 3600;
    	max-lease-time 5760;

}
subnet 10.16.4.0 netmask 255.255.252.0 {
	range 10.16.4.4 10.16.4.254;
    	option routers 10.16.4.1;
    	option broadcast-address 10.16.7.255;
    	option domain-name-servers 10.16.0.6;
    	default-lease-time 3600;
    	max-lease-time 5760;

}
' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server stop
service isc-dhcp-server start
```

### DHCP Relay
```sh
apt-get update
apt-get install isc-dhcp-relay -y

echo '
SERVERS="10.16.0.2"
INTERFACES="eth0 eth1 eth2"
OPTIONS=
' > etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' > /etc/sysctl.conf
```

## DNS
```sh
apt-get update
apt-get install bind9 -y

echo '
options {
	directory "/var/cache/bind";
	forwarders {
		192.168.122.1;
	};
	// dnssec-validation auto;
	allow-query{any;};
	auth-nxdomain no;
	listen-on-v6 { any; };
};
' > /etc/bind/named.conf.options

service bind9 start
```
## Nomor 1
```sh
ip=$(ip -o addr show up primary scope global eth0 |
      while read -r num dev fam addr rest; do echo ${addr%/*}; done)
echo $ip

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to $ip
```
Perintah tersebut akan mengambil IP dinamis yang didapatkan oleh aura. IP tersebut akan digunakan untuk mengatur destinasi SNAT.

## Nomor 2
```sh
# Allow incoming TCP traffic on port 8080
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT

# Drop all other incoming TCP traffic
iptables -A INPUT -p tcp -j DROP

# Drop all other incoming UDP traffic
iptables -A INPUT -p udp -j DROP
```
Perintah pertama akan menerima koneksi yang berasal dari port 8080. Perintah kedua dan ketiga masing-masing akan mendrop koneksi tcp dan udp lain.

## Nomor 3
```sh
iptables -A INPUT -p icmp --icmp-type echo-request -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
Perintah akan menerima koneksi icmp(ping) sebanyak 3. Jika 3 koneksi sudah terhubung maka koneksi selanjutnya akan didrop. Perintah kedua akan memastikan untuk koneksi yang sudah jalan sebelumnya dapat tetap jalan.

## Nomor 4
```sh
# Allow SSH (TCP port 22) from hosts in subnet 
iptables -A INPUT -p tcp --dport 22 -s 10.16.4.0/22 -j ACCEPT

# Drop SSH (TCP port 22) from all other sources
iptables -A INPUT -p tcp --dport 22 -j DROP
```
Perintah akan mengaccept koneksi port 22(SSH) dari subnet grobeforest. Koneksi dari source lainnya akan didrop.

## Nomor 5
```sh
iptables -A INPUT -m time --weekdays Mon,Tue,Wed,Thu,Fri --timestart 08:00 --timestop 16:00 -j ACCEPT

iptables -A INPUT -j DROP
```
Perintah akan menggaccept koneksi pada weekdaus(senin-jumat) mulai dari jam 08:00 hingga jam 16:00. Koneksi lainnya akan didrop.

## Nomor 6
```sh
iptables -A INPUT -m time --weekdays Mon,Tue,Wed,Thu --timestart 12:00 --timestop 13:00 -j DROP

iptables -A INPUT -m time --weekdays Fri --timestart 11:00 --timestop 13:00 -j DROP

iptables -A INPUT -j DROP

iptables -A INPUT -m time --weekdays Mon,Tue,Wed,Thu,Fri --timestart 08:00 --timestop 16:00 -j ACCEPT
```
Perintah intinya sama dengan nomor sebelumnya. Akan tetapi disini ditambahkan aturan baru yakni larangan koneksi saat jam istirahat dan sholat jumat. Karena jam tersebut terdapat dalam jadwal accept sebelumnya maka kita taruh perintah drop di atas perintah accept agar packet tidak di accept terlebih dahulu.


## Nomor 7
```sh
iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.16.4.2 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.16.0.18:80
iptables -A PREROUTING -t nat -p tcp --dport 443 -d 10.16.0.18 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.16.4.2:443
```
Perintah akan mengarahkan route koneksi ke destinasi dan port yang diinginkan. Mode nth membantu untuk mengatur setiap berapa paket koneksi akan diarahkan.

## Nomor 8
```sh
iptables -A INPUT -s 10.16.0.0/30 -m time --datestart 2023-01-01T00:00 --datestop 2024-06-26T23:59 -j DROP
```
Perintah akan mengatur koneksi input pada subnet DHCP berada (10.16.0.0/30) dimana dari tanggal 1 Januari 2023 hingga 26 Juli 2024 semua koneksi masuk akan didrop.

## Nomor 9
```sh
iptables -N PORTSCAN
iptables -A INPUT -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP
iptables -A FORWARD -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP
iptables -A INPUT -m recent --name portscan --set -j ACCEPT
iptables -A FORWARD -m recent --name portscan --set -j ACCEPT
```
Perintah akan menghitung koneksi yang masuk dan memasukkannya ke chain bernama portscan. Jika suatu IP melakukan ping atau koneksi sebanyak 20 kali dalam 10 menit maka koneksi selanjutnya dari IP tersebut akan didrop. IP lain dapat tetap berkoneksi dengan webserver.

## Nomor 10
```sh
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-level 6 --log-prefix "INPUT:DROP: "
iptables -A LOG_DROP -j DROP

iptables -A INPUT -j LOG_DROP
iptables -A OUTPUT -j LOG_DROP
```
Perintah akan membuat sebuah chain bernama LOG_DROP. Koneksi yang masuk melalui chain tersebut akan dilakukan log lalu didrop. Dua perintah paling bawah menggunakan contoh penggunaannya. Perintah tersebut akan memasukkan koneksi masuk dan keluar pada LOG_DROP yang nantinya akan dilog dan drop. 
