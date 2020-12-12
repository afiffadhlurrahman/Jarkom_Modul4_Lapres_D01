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
