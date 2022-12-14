# Jarkom-Modul-5-E06-2022

Repositori Jarkom Modul 5 kelompok E06

<details><summary>Anggota kelompok(click to show)</summary>
<p>

### Kelompok E06 :

1. Billy Brianto 5025201080
2. Atha Dzaky Hidayanto 5025201269
3. Naily Khairiya 5025201244
</p>
</details>

## SOAL
semua aturan iptables harus disimpan pada sistem atau paling tidak kalian menyediakan script sebagai backup.

### A. Membuat topologi jaringan sesuai dengan rancangan
![image](https://user-images.githubusercontent.com/92420947/206388562-bdb3a339-5508-4506-9198-d62431bf82b6.png)
<details><summary>Details(click to show)</summary>

### Keterangan :	
- Eden adalah DNS Server
- WISE adalah DHCP Server
- Garden dan SSS adalah Web Server
- Jumlah Host pada Forger adalah 62 host
- Jumlah Host pada Desmond adalah 700 host
- Jumlah Host pada Blackbell adalah 255 host
- Jumlah Host pada Briar adalah 200 host

</details>

### B. Untuk menjaga perdamaian dunia, Loid ingin meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM setelah melakukan subnetting.
Kelompok kami menggunakan teknik VLSM.

<img width="525" alt="image" src="https://user-images.githubusercontent.com/72675854/206854142-c5bf133f-5d9d-44d2-8cd8-b30ab310873a.png">

Didapatkan,

<img width="231" alt="image" src="https://user-images.githubusercontent.com/72675854/206854177-8ace4cca-f76c-4175-9bf8-58a33196e2a8.png">


Kemudian dibuat tree sebagai berikut,

![image](https://user-images.githubusercontent.com/72675854/206854223-dd18d382-ab8e-48f7-8b61-10fa94cc8414.png)


Sehingga didapatkan pembagian IP sebagai berikut,

<img width="520" alt="image" src="https://user-images.githubusercontent.com/72675854/206854239-8b41c3d7-4f13-4c18-ac2f-1ab5f42dc532.png">


### C. Anya, putri pertama Loid, juga berpesan kepada anda agar melakukan Routing agar setiap perangkat pada jaringan tersebut dapat terhubung.

Lakukan routing pada,

#### Strix

```
route add -net 192.195.4.0 netmask 255.255.252.0 gw 192.195.0.14
route add -net 192.195.2.0 netmask 255.255.254.0 gw 192.195.0.10
route add -net 192.195.1.0 netmask 255.255.255.0 gw 192.195.0.10
route add -net 192.195.0.128 netmask 255.255.255.128 gw 192.195.0.14
route add -net 192.195.0.24 netmask 255.255.255.248 gw 192.195.0.14
route add -net 192.195.0.16 netmask 255.255.255.248 gw 192.195.0.10
```

### D. Tugas berikutnya adalah memberikan ip pada subnet Forger, Desmond, Blackbell, dan Briar secara dinamis menggunakan bantuan DHCP server
1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Strix menggunakan iptables, tetapi Loid tidak ingin menggunakan MASQUERADE.
2. Kalian diminta untuk melakukan drop semua TCP dan UDP dari luar Topologi kalian pada server yang merupakan DHCP Server demi menjaga keamanan.
3. Loid meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 2 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.
4. Akses menuju Web Server hanya diperbolehkan disaat jam kerja yaitu Senin sampai Jumat pada pukul 07.00 - 16.00.
5. Karena kita memiliki 2 Web Server, Loid ingin Ostania diatur sehingga setiap request dari client yang mengakses Garden dengan port 80 akan didistribusikan secara bergantian pada SSS dan Garden secara berurutan dan request dari client yang mengakses SSS dengan port 443 akan didistribusikan secara bergantian pada Garden dan SSS secara berurutan.
6. Karena Loid ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level.

