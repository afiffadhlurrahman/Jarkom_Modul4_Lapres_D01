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


# Routing
