# Jarkom-Modul-5-B03-2023
Berikut adalah laporan resmi untuk praktikum modul 4 jarkom.

| Nama | NRP |
|---------------------------|------------|
|Wan Sabrina Mayzura | 5025211023 |
|Syarifah Talitha Erfany | 5025211175 |

## Daftar Isi
  - [Config](#Config)
  - [Topologi Cisco Packet Tracer CIDR](#topologi-cisco-packet-tracer-cidr)
  - [Rute](#rute)
- [VLSM](#vlsm)
  - [Tree](#tree)
  - [Pembagian IP](#pembagian-ip)
  - [Config GNS3](#config-gns3)
  - [Routing](#routing)
  - [Testing](#testing)
- [CIDR](#cidr)
  - [Penggabungan IP](#penggabungan-ip)
  - [Tree](#tree-1)
  - [Pembagian IP](#pembagian-ip-1)
  - [Routing](#routing-1)
  - [Testing](#testing-1)

## Config

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
```

- TurkRegion (Client)
```
auto eth0
iface eth0 inet static
	address 10.10.0.2
	netmask 255.255.248.0
	gateway 10.10.0.1
```

- Sein (Server)
```
auto eth0
iface eth0 inet static
	address 10.10.8.2
	netmask 255.255.252.0
	gateway 10.10.8.1
```

- GrobeForest (Client)
```
auto eth0
iface eth0 inet static
	address 10.10.8.3
	netmask 255.255.252.0
	gateway 10.10.8.1
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
```

- Stark (Server)
```
auto eth0
iface eth0 inet static
	address 10.10.14.142
	netmask 255.255.255.252
	gateway 10.10.14.141
```

- LaubHills (Client)
```
auto eth0
iface eth0 inet static
	address 10.10.12.2
	netmask 255.255.254.0
	gateway 10.10.12.1
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
```

- Richter (Client)
```
auto eth0
iface eth0 inet static
	address 10.10.14.134
	netmask 255.255.255.252
	gateway 10.10.14.133
```

- SchwerMountains (Client)
```
auto eth0
iface eth0 inet static
	address 10.10.14.3
	netmask 255.255.255.128
	gateway 10.10.14.1
```

- Revolte (Client)
```
auto eth0
iface eth0 inet static
	address 10.10.14.130
	netmask 255.255.255.252
	gateway 10.10.14.129
```