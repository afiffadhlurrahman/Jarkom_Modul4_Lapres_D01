# Modul 4 : Subnetting dan Routing

Nama Anggota :
- 05111840000093 Muhammad Afif Fadhlurrahman
- 05111740000091 Affan Ahsanul Habib

###  VLSM (Variable Length Subnet Masking)
- [Subnetting](#subnetting)
- [Routing](#routing)

# Subnetting

Langkah 1 - Tentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan lakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan.

![vlsm](/pic/vlsm.png)

| Subnet | Jumlah IP | Netmask |
| --- | --- | --- |
| A1 | 2 | /30 |
| A2 | 1001 | /22 |
| A3 | 2 | /30 |
| A4 | 2 | /30 |
| A5 | 701 | /22 |
| A6 | 2 | /30 |
| A7 | 2021 | /21 |
| A8 | 101 | /25 |
| A9 | 502 | /23 |
| A10 | 13 | /28 |
| A11 | 521 | /22 |
| A12 | 2 | /30 |
| A13 | 2 | /30 |
| A14 | 252 | /24 |
| A15 | 721 | /22 |
| **Total** | **5845** | **/19** |

Langkah 2 - Subnet besar yang dibentuk memiliki NID 192.168.0.0 dengan netmask /19. Hitung pembagian IP berdasarkan NID dan netmask tersebut menggunakan pohon seperti gambar di bawah.

![tree vlsm](/pic/tree.png)

Dari pohon dari pohon tersebut akan mendapat pembagian IP sebagai berikut.

![perhitungan a1-a10](/pic/hitung-a1-a10.png)

![perhitung-a11-a15](/pic/hitung-a11-a15.png)

# Pada UML

### File topo.sh
```
# Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch6 > /dev/null < /dev/null &
uml_switch -unix switch12 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &

# Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.78.9 eth1=daemon,,,switch13 eth2=daemon,,,switch1 eth3=daemon,,,switch3 eth4=daemon,,,switch4 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch4 eth1=daemon,,,switch19 eth2=daemon,,,switch6 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch6 eth1=daemon,,,switch16 eth2=daemon,,,switch15 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch3 eth1=daemon,,,switch22 eth2=daemon,,,switch21 eth3=daemon,,,switch12 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch12 eth1=daemon,,,switch18 eth2=daemon,,,switch17 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &

# Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &

# Klien
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
```

### Router
```
# Router
SURABAYA
auto eth0
iface eth0 inet static
address 10.151.78.10
netmask 255.255.255.252
gateway 10.151.78.9

auto eth1
iface eth1 inet static
address 10.151.79.17
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.8.1
netmask 255.255.252.0

auto eth3
iface eth3 inet static
address 192.168.4.97
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 192.168.4.101
netmask 255.255.255.252

PASURUAN
auto eth0
iface eth0 inet static
address 192.168.4.102
netmask 255.255.255.252
gateway 192.168.4.101

auto eth1
iface eth1 inet static
address 192.168.12.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.168.4.105
netmask 255.255.255.252

PROBOLINGGO
auto eth0
iface eth0 inet static
address 192.168.4.106
netmask 255.255.255.252
gateway 192.168.4.105

auto eth1
iface eth1 inet static
address 192.168.24.1
netmask 255.255.248.0

auto eth2
iface eth2 inet static
address 192.168.4.129
netmask 255.255.255.128

BATU
auto eth0
iface eth0 inet static
address 192.168.4.98
netmask 255.255.255.252
gateway 192.168.4.97

auto eth1
iface eth1 inet static
address 192.168.6.1
netmask 255.255.254.0

auto eth2
iface eth2 inet static
address 192.168.16.1
netmask 255.255.252.0

auto eth3
iface eth3 inet static
address 192.168.4.109
netmask 255.255.255.252

MADIUN
auto eth0
iface eth0 inet static
address 192.168.6.2
netmask 255.255.254.0
gateway 192.168.6.1

auto eth1
iface eth1 inet static
address 192.168.4.113
netmask 255.255.255.240

KEDIRI
auto eth0
iface eth0 inet static
address 192.168.4.110
netmask 255.255.255.252
gateway 192.168.4.109

auto eth1
iface eth1 inet static
address 10.151.79.21
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.5.1
netmask 255.255.255.0

BLITAR
auto eth0
iface eth0 inet static
address 192.168.5.2
netmask 255.255.255.0
gateway 192.168.5.1

auto eth1
iface eth1 inet static
address 192.168.20.1
netmask 255.255.252.0
```

### Server
```
# Server
MOJOKERTO
auto eth0
iface eth0 inet static
address 10.151.79.18
netmask 255.255.255.252
gateway 10.151.79.17

MALANG
auto eth0
iface eth0 inet static
address 10.151.79.22
netmask 255.255.255.252
gateway 10.151.79.21
```

### Client
```
# Klien
SAMPANG
auto eth0
iface eth0 inet static
address 192.168.8.2
netmask 255.255.252.0
gateway 192.168.8.1

SIDOARJO
auto eth0
iface eth0 inet static
address 192.168.12.2
netmask 255.255.252.0
gateway 192.168.12.1

BANYUWANGI
auto eth0
iface eth0 inet static
address 192.168.24.2
netmask 255.255.248.0
gateway 192.168.24.1

JEMBER
auto eth0
iface eth0 inet static
address 192.168.27.237
netmask 255.255.248.0
gateway 192.168.24.1

BONDOWOSO
auto eth0
iface eth0 inet static
address 192.168.4.130
netmask 255.255.255.128
gateway 192.168.4.129

JOMBANG
auto eth0
iface eth0 inet static
address 192.168.6.3
netmask 255.255.254.0
gateway 192.168.6.1

BOJONEGORO
auto eth0
iface eth0 inet static
address 192.168.4.114
netmask 255.255.255.240
gateway 192.168.4.113

NGANJUK
auto eth0
iface eth0 inet static
address 192.168.16.2
netmask 255.255.252.0
gateway 192.168.16.1

LUMAJANG
auto eth0
iface eth0 inet static
address 192.168.5.3
netmask 255.255.255.0
gateway 192.168.5.1

TULUNGAGUNG
auto eth0
iface eth0 inet static
address 192.168.20.2
netmask 255.255.252.0
gateway 192.168.20.1
```

# Routing
```
SURABAYA
route add -net 192.168.12.0 netmask 255.255.252.0 gw 192.168.4.102
route add -net 192.168.4.104 netmask 255.255.255.252 gw 192.168.4.102
route add -net 192.168.24.0 netmask 255.255.248.0 gw 192.168.4.102
route add -net 192.168.4.128 netmask 255.255.255.128 gw 192.168.4.102
route add -net 192.168.6.0 netmask 255.255.254.0 gw 192.168.4.98
route add -net 192.168.4.112 netmask 255.255.255.240 gw 192.168.4.98
route add -net 192.168.16.0 netmask 255.255.252.0 gw 192.168.4.98
route add -net 192.168.4.108 netmask 255.255.255.252 gw 192.168.4.98
route add -net 10.151.79.20 netmask 255.255.255.252 gw 192.168.4.98
route add -net 192.168.5.0 netmask 255.255.255.0 gw 192.168.4.98
route add -net 192.168.20.0 netmask 255.255.252.0 gw 192.168.4.98

PASURUAN
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.4.101
route add -net 192.168.24.0 netmask 255.255.248.0 gw 192.168.4.106
route add -net 192.168.4.128 netmask 255.255.255.128 gw 192.168.4.106

PROBOLINGGO
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.4.105

BATU
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.4.97
route add -net 192.168.4.112 netmask 255.255.255.240 gw 192.168.6.2
route add -net 10.151.79.20 netmask 255.255.255.252 gw 192.168.4.110
route add -net 192.168.5.0 netmask 255.255.255.0 gw 192.168.4.110
route add -net 192.168.20.0 netmask 255.255.252.0 gw 192.168.4.110

MADIUN
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.6.1

KEDIRI
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.4.108
route add -net 192.168.20.0 netmask 255.255.252.0 gw 192.168.5.2

BLITAR
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.5.1
```