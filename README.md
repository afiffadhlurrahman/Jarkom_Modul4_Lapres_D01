# Jarkom Materi Subnetting dan Routing

Nama Anggota :
- 05111840000093 Muhammad Afif Fadhlurrahman
- 05111740000091 Affan Ahsanul Habib

### CIDR (Classless Inter Domain Routing)

#### Subnetting
Langkah 1 - Tentukan subnet yang ada dalam topologi dan lakukan labelling netmask terhadap masing-masing subnet </br>
![subnet-langkah-A](/img/gambar.png)

Langkah 2 - Gabungkan subnet paling bawah di dalam topologi. Paling bawah berarti subnet yang paling jauh dari internet (gambar awan) </br>

![subnet-langkah-b](/img/b.jpg)

![subnet-langkah-c](/img/c.jpg)

![subnet-langkah-d](/img/d.jpg)

![subnet-langkah-ef](/img/ef.png)

![subnet-langkah-g](/img/g.jpg)


Langkah 3 - Dari proses penggabungan yang telah dilakukan, didapatkan sebuah subnet besar dengan netmask /16. Kali ini dapat menggunakan NID 192.168.0.0, netmask 255.255.0.0. </br>

Langkah 4 - Hitung pembagian IP dengan pohon berdasarkan penggabungan subnet yang telah dilakukan. </br>

![tree cidr](/img/cidr.png)

Langkah 5 - Berdasarkan penghitungan, maka didapatkan pembagian IP sebagai berikut. </br>

![hitung-a1-a5](/img/hitung-a1-a5.png)

![hitung-a6-a10](/img/hitung-a6-a10.png)

![hitung-a11-s2](/img/hitung-a11-s2.png)


#### Routing

1. SURABAYA

```
0.0.0.0/0 via 10.151.78.9
192.168.128.0/18 via 192.168.192.2
192.168.0.0/19 via 192.168.32.2
10.151.79.16/30 via 192.168.32.2
```

![routing sby 1](/img/sby1.png)

![routing sby 2](/img/sby2.png)

2. PASURUAN

```
0.0.0.0/0 via 192.168.192.1
192.168.128.0/20 via 192.168.144.2
```

![routing pasuruan](/img/pas.png)

3. PROBOLINGGO

```
0.0.0.0/0 via 192.168.144.1
```

![routing probolinggo](/img/probo.png)

4. BATU

```
0.0.0.0/0 via 192.168.32.1
192.168.18.0/28 via 192.168.16.2
192.168.0.0/21 via 192.168.8.2
10.151.79.16/30 via 192.168.8.2
```

![routing batu 1](/img/batu1.png)

![routing batu 2](/img/batu2.png)

5. MADIUN

```
0.0.0.0/0 via 192.168.16.1
```

![routing madiun](/img/madiun.png)

6. KEDIRI

```
0.0.0.0/0 via 192.168.8.1
192.168.0.0/22 via 192.168.4.2
```

![routing kediri](/img/ked.png)

7. BLITAR

```
0.0.0.0/0 via 192.168.4.1
```

![routing blitar](/img/blitar.png)
