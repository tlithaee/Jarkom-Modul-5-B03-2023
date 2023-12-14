# Jarkom-Modul-5-B03-2023
Berikut adalah laporan resmi untuk praktikum modul 5 jarkom.

| Nama | NRP |
|---------------------------|------------|
|Wan Sabrina Mayzura | 5025211023 |
|Syarifah Talitha Erfany | 5025211175 |

## Daftar Isi
  - [Topologi dan Pembagian Subnet](#topologi-dan-pembagian-subnet)
  - [Rute](#rute)
  - [Tree](#tree)
  - [Config GNS3](#config-gns3)
  - [Pembagian IP](#pembagian-ip)
  - [Routing](#routing)
  - [Testing](#testing)

## Topologi dan Pembagian Subnet
![Alt text](TopologiPrak5.png)

## Rute
![Alt text](image.png)

## Tree
![Alt text](TreeVLSM.png)

## Config GNS3

- Aura (Router)
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.10.14.149
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.10.14.145
	netmask 255.255.255.252
```

- Heiter (Router)
```
auto eth0
iface eth0 inet static
	address 10.10.14.150
	netmask 255.255.255.252
	gateway 10.10.14.149

auto eth1
iface eth1 inet static
    address 10.10.0.1
    netmask 255.255.248.0

auto eth2
iface eth2 inet static
    address 10.10.8.1
    netmask 255.255.252.0

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- TurkRegion (Client)
```
auto eth0
iface eth0 inet dhcp
	gateway 10.10.0.1

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Sein (Server)
```
auto eth0
iface eth0 inet static
	address 10.10.8.2
	netmask 255.255.252.0
	gateway 10.10.8.1

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- GrobeForest (Client)
```
auto eth0
iface eth0 inet dhcp
	gateway 10.10.8.1

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Frieren (Router)
```
auto eth0
iface eth0 inet static
	address 10.10.14.146
	netmask 255.255.255.252
	gateway 10.10.14.145

auto eth1
iface eth1 inet static
    address 10.10.14.137
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.10.14.141
    netmask 255.255.255.252

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Stark (Server)
```
auto eth0
iface eth0 inet static
	address 10.10.14.142
	netmask 255.255.255.252
	gateway 10.10.14.141

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- LaubHills (Client)
```
auto eth0
iface eth0 inet dhcp
	gateway 10.10.12.1

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Himmel (Router)
```
auto eth0
iface eth0 inet static
	address 10.10.14.138
	netmask 255.255.255.252
	gateway 10.10.14.137

auto eth1
iface eth1 inet static
    address 10.10.12.1
    netmask 255.255.254.0

auto eth2
iface eth2 inet static
    address 10.10.14.1
    netmask 255.255.255.128

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Fern (Router)
```
auto eth0
iface eth0 inet static
	address 10.10.14.2
	netmask 255.255.255.128
	gateway 10.10.14.1

auto eth1
iface eth1 inet static
    address 10.10.14.133
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.10.14.129
    netmask 255.255.255.252

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Richter (Server)
```
auto eth0
iface eth0 inet static
	address 10.10.14.134
	netmask 255.255.255.252
	gateway 10.10.14.133

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- SchwerMountains (Client)
```
auto eth0
iface eth0 inet dhcp
	gateway 10.10.14.1

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Revolte (Server)
```
auto eth0
iface eth0 inet static
	address 10.10.14.130
	netmask 255.255.255.252
	gateway 10.10.14.129
	
up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

## Pembagian IP
Sesuai config network, maka pembagian IP untuk tiap nodenya adalah sebagai berikut:
| Node               | Subnet | Interface | IP Address    | Netmask         | Gateway        |
|--------------------|--------|-----------|---------------|-----------------|----------------|
| Aura (Router)      |   -    | eth0      | DHCP          | -               | -              |
|                    |   A8   | eth1      | 10.10.14.149  | 255.255.255.252 | -              |
|                    |   A7   | eth2      | 10.10.14.145  | 255.255.255.252 | -              |
| Heiter (Router)    |   A8   | eth0      | 10.10.14.150  | 255.255.255.252 | 10.10.14.149   |
|                    |   A9   | eth1      | 10.10.0.1     | 255.255.248.0   | -              |
|                    |  A10   | eth2      | 10.10.8.1     | 255.255.252.0   | -              |
| TurkRegion         |   A9   | eth0      | DHCP          | -               | -              |
| Sein (Server)      |  A10   | eth0      | 10.10.8.2     | 255.255.252.0   | 10.10.8.1      |
| GrobeForest        |  A10   | eth0      | DHCP          | -               | -              |
| Frieren (Router)   |   A7   | eth0      | 10.10.14.146  | 255.255.255.252 | 10.10.14.145   |
|                    |   A5   | eth1      | 10.10.14.137  | 255.255.255.252 | -              |
|                    |   A6   | eth2      | 10.10.14.141  | 255.255.255.252 | -              |
| Stark (Server)     |   A6   | eth0      | 10.10.14.142  | 255.255.255.252 | 10.10.14.141   |
| LaubHills (Client) |   A4   | eth0      | DHCP          | -               | -              |
| Himmel (Router)    |   A5   | eth0      | 10.10.14.138  | 255.255.255.252 | 10.10.14.137   |
|                    |   A4   | eth1      | 10.10.12.1    | 255.255.254.0   | -              |
|                    |   A3   | eth2      | 10.10.14.1    | 255.255.255.128 | -              |
| Fern (Router)      |   A3   | eth0      | 10.10.14.2    | 255.255.255.128 | 10.10.14.1     |
|                    |   A2   | eth1      | 10.10.14.133  | 255.255.255.252 | -              |
|                    |   A1   | eth2      | 10.10.14.129  | 255.255.255.252 | -              |
| Richter (Server)   |   A2   | eth0      | 10.10.14.134  | 255.255.255.252 | 10.10.14.133   |
| SchwerMountains (Client) |   A3   | eth0 | DHCP          | -               | -              |
| Revolte (Client)   |   A1   | eth0      | 10.10.14.130  | 255.255.255.252 | 10.10.14.129   |

## Routing

- Aura
```
# ke arah Frieren
# gateway menggunakan eth0 dari Frieren
# Routing for subnets A1, A2, A3, A4, A5, A6
up route add -net 10.10.14.128 netmask 255.255.255.252 gw 10.10.14.146
up route add -net 10.10.14.132 netmask 255.255.255.252 gw 10.10.14.146
up route add -net 10.10.14.0 netmask 255.255.255.128 gw 10.10.14.146
up route add -net 10.10.12.0 netmask 255.255.254.0 gw 10.10.14.146
up route add -net 10.10.14.136 netmask 255.255.255.252 gw 10.10.14.146
up route add -net 10.10.14.140 netmask 255.255.255.252 gw 10.10.14.146

# ke arah Heiter
# gateway menggunakan eth0 dari Heiter
# Routing for subnets A9, A10 
up route add -net 10.10.0.0 netmask 255.255.248.0 gw 10.10.14.150
up route add -net 10.10.8.0 netmask 255.255.252.0 gw 10.10.14.150
```

- Frieren
```
# ke arah Himmel
# gateway menggunakan eth0 dari Himmel
# Routing for subnets A1, A2, A3, A4
up route add -net 10.10.14.128 netmask 255.255.255.252 gw 10.10.14.138
up route add -net 10.10.14.132 netmask 255.255.255.252 gw 10.10.14.138
up route add -net 10.10.14.0 netmask 255.255.255.128 gw 10.10.14.138
up route add -net 10.0.12.0 netmask 255.255.255.0 gw 10.10.14.138
```

- Himmel
```
# ke arah Fern
# gateway menggunakan eth0 dari Fern
# Routing for subnets A1, A2
up route add -net 10.10.14.128 netmask 255.255.255.252 gw 10.10.14.2
up route add -net 10.10.14.132 netmask 255.255.255.252 gw 10.10.14.2
```

- DHCP Server (Aura)
	- .bashrc
	```
	apt-get update -y
	apt-get install isc-dhcp-server -y
	```

	- start.sh
	```
	echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

	echo '
	subnet 10.10.14.128 netmask 255.255.255.252 {
	}
	subnet 10.10.14.132 netmask 255.255.255.252 {
	}
	subnet 10.10.14.0 netmask 255.255.255.128 {
		range 10.10.14.1 10.10.14.126;
			option routers 10.10.14.130;
			option broadcast-address 10.10.14.127;
			option domain-name-servers 10.10.14.6;
			default-lease-time 3600;
			max-lease-time 5760;
	}
	subnet 10.10.12.0 netmask 255.255.254.0 {
		range 10.10.12.1 10.10.13.254;
			option routers 10.10.12.1;
			option broadcast-address 10.10.13.255;
			option domain-name-servers 10.10.14.6;
			default-lease-time 3600;
			max-lease-time 5760;
	}
	subnet 10.10.14.136 netmask 255.255.255.252 {
	}
	subnet 10.10.14.140 netmask 255.255.255.252 {
	}
	subnet 10.10.0.0 netmask 255.255.248.0 {
		range 10.10.0.1 10.10.7.254;
			option routers 10.10.0.1;
			option broadcast-address 10.10.7.255;
			option domain-name-servers 10.10.14.6;
			default-lease-time 3600;
			max-lease-time 5760;

	}
	subnet 10.10.8.0 netmask 255.255.252.0 {
		range 10.10.8.1 10.10.11.254;
			option routers 10.10.8.1;
			option broadcast-address 10.10.11.255;
			option domain-name-servers 10.10.14.6;
			default-lease-time 3600;
			max-lease-time 5760;

	}
	' > /etc/dhcp/dhcpd.conf

	service isc-dhcp-server stop
	service isc-dhcp-server start
	```

- DHCP Relay (Fern - Heiter - Himmel)
	- .bashrc
	```
	apt-get update
	apt-get install isc-dhcp-relay -y
	```

	- start.sh
	```
	echo '
	SERVERS="10.10.0.2"
	INTERFACES="eth0 eth1 eth2"
	OPTIONS=
	' > etc/default/isc-dhcp-relay

	echo 'net.ipv4.ip_forward=1' > /etc/sysctl.conf

	service isc-dhcp-relay restart
	```

- DNS Server (Richter)	
	- .bashrc
	```
	apt-get update
	apt-get install bind9 -y
	```

	- start.sh
	```
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

	## Number 1