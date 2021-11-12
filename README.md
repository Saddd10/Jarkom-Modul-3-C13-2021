# Jarkom-Modul-3-C13-2021

## Anggota Kelompok :

| Anggota              | NRP            |
| -------------------- | -------------- |
| M. Auliya Mirzaq R.  | 05111940000065 |
| M. Akmal Joedhiawan  | 05111940000125 |
| M. Arsyad Ardiansyah | 05111940000228 |

## Soal
Luffy yang sudah menjadi Raja Bajak Laut ingin mengembangkan daerah kekuasaannya dengan membuat peta seperti berikut:

![image](https://user-images.githubusercontent.com/73766214/140846386-977685f5-1f96-4b60-983e-e27c152e2ace.png)

Luffy bersama Zoro berencana membuat peta tersebut dengan kriteria EniesLobby sebagai DNS Server, Jipangu sebagai DHCP Server, Water7 sebagai Proxy Server (1), dan Foosha sebagai DHCP Relay (2). Luffy dan Zoro menyusun peta tersebut dengan hati-hati dan teliti.

Ada beberapa kriteria yang ingin dibuat oleh Luffy dan Zoro, yaitu:
- Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server.
- Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.20 - [prefix IP].1.99 dan [prefix IP].1.150 - [prefix IP].1.169 (3)
- Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.30 - [prefix IP].3.50 (4)
- Client mendapatkan DNS dari EniesLobby dan client dapat terhubung dengan internet melalui DNS tersebut. (5)
- Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch1 selama 6 menit sedangkan pada client yang melalui Switch3 selama 12 menit. Dengan waktu maksimal yang dialokasikan untuk peminjaman alamat IP selama 120 menit. (6)
	
Luffy dan Zoro berencana menjadikan Skypie sebagai server untuk jual beli kapal yang dimilikinya dengan alamat IP yang tetap dengan IP [prefix IP].3.69 (7). Loguetown digunakan sebagai client Proxy agar transaksi jual beli dapat terjamin keamanannya, juga untuk mencegah kebocoran data transaksi.

Pada Loguetown, proxy harus bisa diakses dengan nama jualbelikapal.yyy.com dengan port yang digunakan adalah 5000 (8). Agar transaksi jual beli lebih aman dan pengguna website ada dua orang, proxy dipasang autentikasi user proxy dengan enkripsi MD5 dengan dua username, yaitu luffybelikapalyyy dengan password luffy_yyy dan zorobelikapalyyy dengan password zoro_yyy (9). Transaksi jual beli tidak dilakukan setiap hari, oleh karena itu akses internet dibatasi hanya dapat diakses setiap hari Senin-Kamis pukul 07.00-11.00 dan setiap hari Selasa-Jum’at pukul 17.00-03.00 keesokan harinya (sampai Sabtu pukul 03.00) (10).

Agar transaksi bisa lebih fokus berjalan, maka dilakukan redirect website agar mudah mengingat website transaksi jual beli kapal. Setiap mengakses google.com, akan diredirect menuju super.franky.yyy.com dengan website yang sama pada soal shift modul 2. Web server super.franky.yyy.com berada pada node Skypie (11).

Saatnya berlayar! Luffy dan Zoro akhirnya memutuskan untuk berlayar untuk mencari harta karun di super.franky.yyy.com. Tugas pencarian dibagi menjadi dua misi, Luffy bertugas untuk mendapatkan gambar (.png, .jpg), sedangkan Zoro mendapatkan sisanya. Karena Luffy orangnya sangat teliti untuk mencari harta karun, ketika ia berhasil mendapatkan gambar, ia mendapatkan gambar dan melihatnya dengan kecepatan 10 kbps (12). Sedangkan, Zoro yang sangat bersemangat untuk mencari harta karun, sehingga kecepatan kapal Zoro tidak dibatasi ketika sudah mendapatkan harta yang diinginkannya (13).

Keterangan :
- yyy adalah nama kelompok Anda
- Untuk nomor 9, harus htpasswd yang melakukan enkripsi
- Bisa melakukan wget https://raw.githubusercontent.com/FeinardSlim/Praktikum-Modul-2-Jarkom/main/super.franky.zip untuk mendapatkan file untuk super.franky.yyy.com

## Soal 1

Luffy bersama Zoro berencana membuat peta tersebut dengan kriteria EniesLobby sebagai DNS Server, Jipangu sebagai DHCP Server, Water7 sebagai Proxy Server.

Setting network configuration pada semua node sesuai dengan Prefix IP dari kelompok C13 yaitu `192.190`

#### Foosha

```
```

#### EniesLobby (DNS Master)

```
```

#### Water7 (Proxy Server)

```
```

#### Jipangu (DHCP Server)

```
```

## Soal 2

Dan Foosha sebagai DHCP Relay.

#### Node Foosha

- Lakukan update dengan `apt-get update`

- Install `isc-dhcp-relay` dengan perintah `apt-get install isc-dhcp-relay`

- Edit file DHCP relaynya dengan perintah `vim /etc/default/isc-dhcp-relay` lalu tambahkan `eth1 eth2 eth3` pada kolom `INTERFACES= `.

- Memasukkan IP Jipangu sebagai DHCP Servernya, yaitu `192.190.2.4`.

- Kosongkan kolom berikutnya.

## Soal 3

Ada beberapa kriteria yang ingin dibuat oleh Luffy dan Zoro, yaitu:
- Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server.
- Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.20 - [prefix IP].1.99 dan [prefix IP].1.150 - [prefix IP].1.169h ke Skypie.

#### Node Jipangu

- Ketik `vim /etc/dhcp/dhcpd.conf` untuk mengedit file `dhcpd.conf`, lalu tambahkan beris berikut

  ```
  ```
- Restart service isc-dhcp-server dengan perintah `service isc-dhcp-server restart`

## Soal 4

Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.30 - [prefix IP].3.50.

#### Node Jipangu

- Ketik `vim /etc/dhcp/dhcpd.conf` untuk mengedit file `dhcpd.conf`, lalu tambahkan beris berikut

  ```
  ```
- Restart service isc-dhcp-server dengan perintah `service isc-dhcp-server restart`

## Soal 5

Client mendapatkan DNS dari EniesLobby dan client dapat terhubung dengan internet melalui DNS tersebut.

#### Node Loguetown

- Edit file `interfaces` dengan perintah `vim /etc/network/interfaces` seperti berikut.

  ```
  ```
  
- Cek nameserver pada file `vim /etc/resolv.conf`.

#### Node Alabasta

- Edit file `interfaces` dengan perintah `vim /etc/network/interfaces` seperti berikut.

  ```
  ```
  
- Cek nameserver pada file `vim /etc/resolv.conf`.

#### Node Tottoland

- Edit file `interfaces` dengan perintah `vim /etc/network/interfaces` seperti berikut.

  ```
  ```
  
- Cek nameserver pada file `vim /etc/resolv.conf`.

#### Node Skypie

- Edit file `interfaces` dengan perintah `vim /etc/network/interfaces` seperti berikut.

  ```
  ```
  
- Cek nameserver pada file `vim /etc/resolv.conf`.

## Soal 6

Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch1 selama 6 menit sedangkan pada client yang melalui Switch3 selama 12 menit. Dengan waktu maksimal yang dialokasikan untuk peminjaman alamat IP selama 120 menit.

#### Node Jipangu

- Edit file `dhcpd.conf` dengan perintah `vim /etc/dhcp/dhcpd.conf`
- Ubah kode `default-lease-time 600;` menjadi `default-lease-time 360;` pada subnet `192.190.1.0` (Switch1).
- Ubah kode `default-lease-time 600;` menjadi `default-lease-time 720;` pada subnet `192.190.3.0` (Switch3)

## Soal 7

Luffy dan Zoro berencana menjadikan Skypie sebagai server untuk jual beli kapal yang dimilikinya dengan alamat IP yang tetap dengan IP [prefix IP].3.69.

#### Node Jipangu

- Edit file `dhcpd.conf` dengan perintah `vim /etc/dhcp/dhcpd.conf` menjadi seperti berikut.
- Cek `link/ether` `eth0` di Node Skypie dengan menjalankan perintah `ip a` untuk mendapatkan Hardware Ethernet.
- Restart service DHCP Server dengan perintah `service isc-dhcp-server restart`.

#### Node Skypie

- Edit file `interfaces` dengan perintah `vim /etc/network/interfaces` menjadi seperti berikut.
- Restart Node Skypie.
- Cek apakah IP sudah berubah dengan perintah `ip a`.

## Soal 8

Loguetown digunakan sebagai client Proxy agar transaksi jual beli dapat terjamin keamanannya, juga untuk mencegah kebocoran data transaksi.Pada Loguetown, proxy harus bisa diakses dengan nama jualbelikapal.yyy.com dengan port yang digunakan adalah 5000.

#### Node Water7

- Lakukan update dengan perintah `apt-get update`.
- Install Squid dengan perintah `apt-get install squid`.
- Edit file `squid.conf` dengan perintah `vim /etc/squid/squid.conf` seperti berikut.

```
```

- Restart service DHCP Server dengan perintah `service isc-dhcp-server restart`.

## Soal 9

Agar transaksi jual beli lebih aman dan pengguna website ada dua orang, proxy dipasang autentikasi user proxy dengan enkripsi MD5 dengan dua username, yaitu luffybelikapalyyy dengan password luffy_yyy dan zorobelikapalyyy dengan password zoro_yyy.

#### Node Water7

- Lakukan update dengan perintah `apt-get update`.
- Install `Apache Utils` dengan perintah `apt-get install apache2-utils`.
- Ketikkan perintah dibawah untuk menambahkan username dan password. Agar bisa terenkripsi MD5 maka tambahkan `-m` dan hilangan `-c` untuk menghindari membuat file baru.

```
```

- Edit file `squid.conf` dengan perintah `vim /etc/squid/squid.conf` seperti berikut.

```
```

- Cek apakah password sudah terenkripsi di file ``.
- Restart service DHCP Server dengan perintah `service isc-dhcp-server restart`.

## Soal 10

Transaksi jual beli tidak dilakukan setiap hari, oleh karena itu akses internet dibatasi hanya dapat diakses setiap hari Senin-Kamis pukul 07.00-11.00 dan setiap hari Selasa-Jum’at pukul 17.00-03.00 keesokan harinya (sampai Sabtu pukul 03.00).

#### Node Water7

- Edit file `acl.conf` dengan perintah `vim /etc/squid/acl.conf` seperti berikut.

```
```

- Restart service DHCP Server dengan perintah `service isc-dhcp-server restart`.

## Soal 11

Agar transaksi bisa lebih fokus berjalan, maka dilakukan redirect website agar mudah mengingat website transaksi jual beli kapal. Setiap mengakses google.com, akan diredirect menuju super.franky.yyy.com dengan website yang sama pada soal shift modul 2. Web server super.franky.yyy.com berada pada node Skypie.

#### Node Water7

- Ubah nameserver untuk menyambungkan Node Water7 dengan Node Enieslobby pada file `/etc/resolv.conf`.

#### Node Enieslobby

#### Node Skypie

## Soal 12

Saatnya berlayar! Luffy dan Zoro akhirnya memutuskan untuk berlayar untuk mencari harta karun di super.franky.yyy.com. Tugas pencarian dibagi menjadi dua misi, Luffy bertugas untuk mendapatkan gambar (.png, .jpg), sedangkan Zoro mendapatkan sisanya. Karena Luffy orangnya sangat teliti untuk mencari harta karun, ketika ia berhasil mendapatkan gambar, ia mendapatkan gambar dan melihatnya dengan kecepatan 10 kbps.

#### Node Water7

- Tambahkan perintah berikut ke dalam file `/etc/squid/squid.conf` seperti gambar dibawah ini
- Restart service squid

#### Node Loguetown

- Uji dengan mendownload file berekstensi `.png` atau `.jpg` terlihat seperti gambar dibawah ini apabila delay bandwith berhasil

## Soal 13

Sedangkan, Zoro yang sangat bersemangat untuk mencari harta karun, sehingga kecepatan kapal Zoro tidak dibatasi ketika sudah mendapatkan harta yang diinginkannya.

#### Node Water7

- Tambahkan perintah berikut ke dalam file `/etc/squid/squid.conf` seperti gambar dibawah ini
- Restart service squid

#### Node Loguetown

- Uji dengan mendownload file selain berekstensi `.png` atau `.jpg` terlihat seperti gambar dibawah ini
