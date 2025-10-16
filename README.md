# 🐳 Odoo Development with Docker

Repository ini menyediakan **lingkungan pengembangan Odoo** berbasis **Docker**, sehingga kamu dapat menjalankan, menguji, dan mengembangkan modul Odoo dengan cepat tanpa perlu instalasi manual.

## 🚀 Fitur Utama

- ⚙️ Setup cepat & otomatis menggunakan Docker Compose  
- 🧩 Mendukung custom modules di folder `addons/`  
- 🗄 Database PostgreSQL terpisah  
- 🔄 Persistent volume — data tidak hilang meskipun container dimatikan  
- 🧠 Ideal untuk kebutuhan **development** dan **testing**


## 📂 Struktur Folder

```
.
├── addons/                 # Tempat untuk modul kustom 
├── config/                 # File konfigurasi Odoo (odoo.conf)
│   └── odoo.conf
├── docker-compose.yml      # Konfigurasi utama Docker Compose
└── odoo_pg_pass            # File berisi password PostgreSQL
```

> 💡 **Catatan:**  
> Letakkan modul kustom di folder `addons/`.  
> Misalnya: `addons/my_custom_module/`


## ⚙️ Persiapan

Sebelum menjalankan, pastikan kamu sudah menginstal:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)



## ▶️ Cara Menjalankan

1. **Clone repository ini**
   ```bash
   git clone https://github.com/redoranged/odoo-docker.git
   cd odoo-docker
	 ```

2.	**Jalankan layanan**
	```bash
	docker-compose up -d
	```
3.	**Akses Odoo**
	-	Buka browser ke: http://localhost:8069
	-	Buat database baru sesuai kebutuhan
	
4.	Hentikan layanan
	```bash
	docker-compose down
	```


## 🧩 Pengembangan Modul

Untuk membuat modul baru:
	
1.	Buat folder modul di:
	```bash
	addons/my_module/
	```
2.	Setelah menambahkan atau mengubah modul, restart layanan Odoo: 
	```bash
	docker-compose restart odoo
	```
3.	Aktifkan Developer Mode di antarmuka Odoo untuk memuat modul baru.

## 🧠 Konfigurasi

File konfigurasi Odoo terdapat di:
```bash
config/odoo.conf
```

Contoh isi minimal:

```bash
[options]
addons_path = /mnt/extra-addons,/mnt/custom-addons
db_host = db
db_port = 5432
db_user = odoo
db_password = odoo
```

## 🗄 Database	
- Layanan database otomatis dibuat oleh docker-compose.yml
-	Password database diatur dalam file odoo_pg_pass
-	Data disimpan di volume Docker agar tetap aman meskipun container dihentikan

## 💡 Perintah Berguna


Perintah	Keterangan

`docker-compose up -d`	Jalankan semua service di background

`docker-compose logs -f`	Lihat log secara real-time

`docker-compose down`	Hentikan semua container

`docker exec -it odoo bash`	Masuk ke dalam container Odoo

`docker-compose restart odoo`	Restart service Odoo saja


---
© 2025 redoranged