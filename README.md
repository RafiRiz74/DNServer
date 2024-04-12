# Membuat DNS Server
sebelum memulai langkahnya, masukkan user ke root dengan menggunakan
```sh
sudo su
```
## 1. Update dan Install Bind9
sebelum menginstall lakukan update terlebih dahulu menggunakan perintah berikut
```sh
apt update
```
setelah update, install bind9 menggunakan perintah berikut
```sh
apt install bind9
```
![1.png](https://github.com/RafiRiz74/DNServer/blob/main/1.png)
## 2. Konfigurasi
lakukan pengecekan agar bisa mengetahui berapa ip server menggunakan perintah
```sh
ip a
```
kemudian masukkan ke repositori bind menggunakan perintah
```sh
cd /etc/bind
```
### 2.1 Konfigurasi named.conf.local
Ubah konfigurasi pada named.conf.local menggunakan perintah
```sh
nano named.conf.local
```
Ubah konfigurasinya seperti gambar dibawah ini
![2.png](https://github.com/RafiRiz74/DNServer/blob/main/2.png)

### 2.2 Konfigurasi db.rafiriz
disini saya menduplikasi db.local dan mengubahnya menjadi db.rafiriz menggunakan perintah
```sh
cp db.local db.rafiriz
```
ubah konfigurasi db.rafiriz menggunakan perintah
```sh
nano db.rafiriz
```
Ubah konfigurasinya seperti gambar dibawah ini
![3.png](https://github.com/RafiRiz74/DNServer/blob/main/3.png)

### 2.3 Konfigurasi db.192
disini saya menduplikasi db.255 dan mengubahnya menjadi db.192 menggunakan perintah
```sh
cp db.255 db.192
```
ubah konfigurasi db.192 menggunakan perintah
```sh
nano db.192
```
Ubah konfigurasinya seperti gambar dibawah ini
![4.png](https://github.com/RafiRiz74/DNServer/blob/main/4.png)

### 2.4 Konfigurasi resolv.conf
Ubah konfigurasi pada named.conf.local menggunakan perintah
```sh
nano /etc/resolv.conf
```
Ubah konfigurasinya seperti gambar dibawah ini
![5.png](https://github.com/RafiRiz74/DNServer/blob/main/5.png)

## 3. Pengecekkan pada server
sebelum melakukan pengecekkan, jalankan perintah berikut agar konfigurasi dapat berjalan
```sh
systemctl restart bind9
```
### 3.1 Cek keaktifan bind9
disini saya melakukan pengecekkan keaktifan bind9 menggunakan perintah sebagai berikut
```sh
systemctl status bind9
```
dapat dilihat status dari bind9 pada gambar berikut
![6.png](https://github.com/RafiRiz74/DNServer/blob/main/6.png)

### 3.2 Cek domain yang telah dibuat
yang pertama saya menggunakan dig untuk melakukan pengecekkan seperti dibawah ini
![7.png](https://github.com/RafiRiz74/DNServer/blob/main/7.png)

kemudian saya menggunakan nslookup untuk mengeceknya


![8.png](https://github.com/RafiRiz74/DNServer/blob/main/8.png)

## 4. Pengecekkan pada client
saya melakukan pengecekkan menggunakan 2 client pada windows dan linux

### 4.1 Windows
![9.png](https://github.com/RafiRiz74/DNServer/blob/main/9.png)
dapat dilihat bahwa pada windows berhasil di ping domain yang telah dibuat tadi

### 4.2 Linux
![10.png](https://github.com/RafiRiz74/DNServer/blob/main/10.png)


pada linux juga domain yang telah dibuat dapat di ping
