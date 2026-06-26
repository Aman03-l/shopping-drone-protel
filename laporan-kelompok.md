# PROYEK TELEMATIKA GENAP 2025 - 2026

# LAPORAN AKHIR

# DelDrone - Drone Shopping Delivery System

# KELOMPOK [ISI NOMOR]

[NAMA ANGGOTA 1]	NRP. [ISI NRP]

[NAMA ANGGOTA 2]	NRP. [ISI NRP]

[NAMA ANGGOTA 3]	NRP. [ISI NRP]

# DOSEN PENGAMPU

Dr. Ahmad Zaini, S.T., M.T.

Arta Kusuma Hernanda, S.T., M.T.

Dr. Arief Kurniawan, S.T., M.T.

# DEPARTEMEN TEKNIK KOMPUTER

# Fakultas Teknologi Elektro dan Informatika Cerdas

# Institut Teknologi Sepuluh Nopember

# Surabaya 2026

---

# KATA PENGANTAR

Puji syukur kehadirat Tuhan Yang Maha Esa atas rahmat dan karunia-Nya, penulis dapat menyelesaikan Laporan Proyek Telematika dengan judul: **DelDrone - Drone Shopping Delivery System**. Penyusunan laporan ini tidak lepas dari bantuan dan dukungan berbagai pihak. Oleh karena itu, dengan segala kerendahan hati, kami mengucapkan terima kasih kepada:

- Tuhan Yang Maha Esa, atas kelancaran dan berkah yang diberikan selama pelaksanaan proyek telematika ini.
- Bapak Dr. Arief Kurniawan, S.T., M.T. selaku Kepala Departemen Teknik Komputer FTEIC-ITS.
- Bapak Dr. Ahmad Zaini, S.T., M.T., Dr. Arief Kurniawan, S.T., M.T., Arta Kusuma Hernanda, S.T., M.T., dan Prof. Dr. I Ketut Eddy Purnama, S.T., M.T. selaku para Dosen Pengampu Proyek Telematika Departemen Teknik Komputer FTEIC-ITS yang telah memberikan bimbingan dan arahan.
- Rekan-rekan satu tim serta semua pihak terkait yang tidak dapat kami sebutkan satu persatu.

Penulis menyadari bahwa masih terdapat kekurangan dalam pelaksanaan proyek maupun penyusunan laporan ini. Oleh karena itu, penulis memohon maaf atas segala keterbatasan yang ada. Semoga laporan ini dapat memberikan manfaat bagi para pembaca dan pengembangan ilmu pengetahuan.

Surabaya, Juni 2026

Penulis

---

# DAFTAR ISI

KATA PENGANTAR

DAFTAR ISI

BAB I - PENDAHULUAN
- Latar Belakang
- Rumusan Masalah
- Tujuan
- Manfaat

BAB II - PEMBAHASAN
- Deskripsi Produk
- Spesifikasi
- Fitur
- Arsitektur Sistem
- Proses Pengerjaan
- Pembagian Tugas
- Waktu Pengerjaan Kegiatan

BAB III - PENGUJIAN
- Pemasangan Hardware
- Integrasi Aplikasi

BAB IV - PENUTUP

DAFTAR PUSTAKA

---

# BAB I - PENDAHULUAN

## LATAR BELAKANG

Perkembangan teknologi e-commerce dan layanan pengiriman berbasis drone terus mengalami peningkatan signifikan dalam beberapa tahun terakhir. Kebutuhan masyarakat akan pengiriman barang yang cepat, efisien, dan terjangkau menjadi pendorong utama inovasi di bidang logistik udara. Di sisi lain, keterbatasan sistem pengiriman konvensional yang bergantung pada kurir darat seringkali menghadapi kendala kemacetan lalu lintas, jarak tempuh yang jauh, dan keterbatasan waktu operasional. Kondisi ini membuka peluang bagi pengembangan sistem pengiriman berbasis drone yang dapat beroperasi secara otonom, melintasi rute udara langsung, dan memberikan pengalaman belanja yang lebih modern bagi masyarakat.

Sebagai solusi atas permasalahan tersebut, dikembangkanlah **DelDrone (DroneMart)** — sebuah platform belanja dan pengiriman berbasis drone yang mengintegrasikan aplikasi mobile untuk pelanggan, dashboard manajemen untuk penjual, serta perangkat keras drone yang dikendalikan melalui komunikasi MQTT (Message Queuing Telemetry Transport) dan protokol MAVLink. Aplikasi pelanggan dibangun menggunakan framework Flutter untuk memberikan pengalaman lintas platform (Android dan iOS) yang responsif, sementara perangkat drone menggunakan mikrokontroler LilyGO T-Call A7670E yang terintegrasi dengan flight controller Pixhawk 2.4.8 untuk navigasi otonom berbasis GPS.

Keunggulan utama DelDrone terletak pada arsitektur komunikasi real-time yang memungkinkan pemantauan posisi drone secara langsung (live tracking) melalui peta interaktif, pengiriman perintah penerbangan jarak jauh, serta notifikasi status pengiriman yang diperbarui secara kontinu. Sistem ini juga dilengkapi dashboard penjual yang memungkinkan pengelolaan produk, pemrosesan pesanan, pengiriman drone, dan pemantauan laporan penjualan dalam satu antarmuka terpadu. Dengan integrasi Firebase untuk autentikasi pengguna dan sinkronisasi data, serta broker MQTT berbasis cloud (HiveMQ) untuk komunikasi dengan drone, DelDrone menghadirkan solusi end-to-end untuk ekosistem belanja dan pengiriman udara modern.

Melalui implementasi proyek ini, diharapkan DelDrone dapat menjadi purwarupa (prototype) sistem logistik udara yang aplikatif, mendorong efisiensi pengiriman barang kebutuhan sehari-hari, dan membuka wawasan tentang integrasi teknologi IoT, mobile development, dan sistem kendali drone dalam satu kesatuan arsitektur yang solid.

## RUMUSAN MASALAH

Berdasarkan latar belakang di atas, permasalahan utama yang diselesaikan dalam proyek ini meliputi:

1. Bagaimana merancang dan membangun aplikasi mobile multiplatform menggunakan Flutter yang menyediakan layanan belanja produk kebutuhan sehari-hari dengan fitur pelacakan pengiriman drone secara real-time?

2. Bagaimana mengimplementasikan sistem komunikasi dua arah antara aplikasi mobile dan perangkat drone menggunakan protokol MQTT yang handal, responsif, dan mampu menangani perintah penerbangan serta data telemetri secara kontinu?

3. Bagaimana mengintegrasikan flight controller Pixhawk 2.4.8 dengan mikrokontroler LilyGO T-Call A7670E agar drone dapat menerima perintah penerbangan (arm, takeoff, goto, land, RTL) melalui jaringan seluler 4G LTE dan mengirimkan data lokasi GPS, status baterai, serta attitude secara berkala?

4. Bagaimana membangun dashboard manajemen bagi penjual yang mencakup fitur pengelolaan produk, pemrosesan pesanan masuk, pengiriman drone, dan laporan penjualan dalam satu antarmuka yang terpadu dan intuitif?

5. Bagaimana memastikan sinkronisasi data yang konsisten antara aplikasi pelanggan, dashboard penjual, dan perangkat drone melalui integrasi Firebase (autentikasi & database) dan broker MQTT cloud?

## TUJUAN

Adapun tujuan dari proyek ini adalah sebagai berikut:

1. Merancang dan membangun aplikasi mobile multiplatform berbasis Flutter (DelDrone Customer App) yang menyediakan fitur katalog produk, keranjang belanja, checkout, dan pelacakan pengiriman drone secara real-time dengan visualisasi peta interaktif menggunakan Flutter Map dan OpenStreetMap.

2. Mengimplementasikan sistem komunikasi MQTT dua arah antara aplikasi Flutter dan perangkat drone (LilyGO T-Call A7670E) melalui broker cloud HiveMQ, yang menangani topik perintah (command), permintaan data (request), status, lokasi GPS, dan telemetri drone secara efisien.

3. Mengintegrasikan flight controller Pixhawk 2.4.8 dengan mikrokontroler LilyGO T-Call A7670E menggunakan protokol MAVLink, sehingga drone dapat dikendalikan dari jarak jauh melalui jaringan seluler 4G LTE (SIM by.U) untuk misi pengiriman otonom.

4. Membangun dashboard penjual (Seller Dashboard) berbasis Flutter yang mencakup halaman dashboard statistik, pengelolaan produk, manajemen pesanan, pengiriman drone, dan laporan penjualan dalam satu aplikasi terpadu.

5. Mengintegrasikan layanan Firebase Authentication untuk autentikasi pengguna (pelanggan dan penjual) serta Firebase Firestore untuk penyimpanan data produk, pesanan, dan profil pengguna secara real-time.

## MANFAAT

Adapun manfaat dari proyek ini adalah sebagai berikut:

### Bagi Pelanggan

- **Kemudahan Belanja:** Pelanggan dapat menjelajahi katalog produk kebutuhan sehari-hari (makanan ringan, minuman, perawatan diri, kebutuhan rumah) melalui antarmuka yang intuitif dengan pencarian dan filter kategori.
- **Pengiriman Cepat dan Transparan:** Fitur live tracking memungkinkan pelanggan memantau posisi drone secara real-time di peta, lengkap dengan estimasi waktu tiba, status pengiriman, dan indikator baterai drone.
- **Notifikasi Status Pengiriman:** Pelanggan menerima notifikasi perubahan status pengiriman (persiapan, mengudara, menuju lokasi, sampai) secara langsung di aplikasi.

### Bagi Penjual

- **Manajemen Toko Terpadu:** Dashboard terpadu untuk mengelola produk (tambah/edit/hapus), memantau pesanan masuk, mengirim drone, dan melihat laporan penjualan dalam satu aplikasi.
- **Otomatisasi Pengiriman:** Fitur "Kirim Drone" memungkinkan penjual mengirimkan drone ke lokasi pelanggan hanya dengan satu klik, dengan konfirmasi status pengiriman yang real-time.
- **Modernisasi Bisnis:** Membangun citra toko sebagai pelaku usaha yang modern dan adaptif terhadap teknologi logistik udara, meningkatkan daya saing di era digital.

### Bagi Bidang Keilmuan dan Pengembangan Teknologi

- **Implementasi Arsitektur IoT Terintegrasi:** Proyek ini memberikan kontribusi praktis mengenai integrasi mobile development (Flutter), Internet of Things (ESP32 + MQTT), sistem kendali drone (Pixhawk + MAVLink), dan layanan cloud (Firebase + HiveMQ) ke dalam satu solusi arsitektur end-to-end.
- **Referensi Pengembangan Drone Delivery:** Dokumentasi teknis dan kode sumber proyek dapat menjadi referensi bagi pengembang lain yang ingin membangun sistem pengiriman berbasis drone menggunakan teknologi open-source.

---

# BAB II - PEMBAHASAN

## DESKRIPSI PRODUK

DelDrone (DroneMart) adalah platform belanja dan pengiriman berbasis drone yang terdiri dari tiga komponen utama: (1) **Aplikasi Pelanggan** (Flutter) untuk menjelajahi dan membeli produk kebutuhan sehari-hari, (2) **Dashboard Penjual** (Flutter) untuk mengelola toko, produk, pesanan, dan pengiriman drone, serta (3) **Perangkat Keras Drone** (LilyGO T-Call A7670E + Pixhawk 2.4.8) yang menjalankan misi pengiriman otonom ke lokasi pelanggan. Seluruh komponen terhubung melalui infrastruktur komunikasi MQTT (HiveMQ Cloud) dan Firebase untuk sinkronisasi data real-time.

Sistem ini mengadopsi arsitektur client-server dengan pola komunikasi publish-subscribe melalui broker MQTT. Drone secara berkala mempublikasikan data telemetri (GPS, baterai, attitude) ke topik MQTT yang dilanggan oleh aplikasi Flutter untuk ditampilkan di peta interaktif. Sebaliknya, perintah penerbangan (arm, takeoff, goto, land, RTL) dikirim dari dashboard penjual ke drone melalui topik command MQTT. Integrasi protokol MAVLink antara LilyGO dan Pixhawk memungkinkan penerjemahan perintah MQTT menjadi instruksi penerbangan yang dipahami oleh flight controller.

## SPESIFIKASI

Produk DelDrone dibangun menggunakan spesifikasi perangkat lunak dan perangkat keras sebagai berikut:

### Spesifikasi Perangkat Lunak (Software)

- **Framework Frontend:** Flutter 3.x (Dart SDK >= 2.17.0 < 4.0.0) untuk aplikasi pelanggan dan dashboard penjual yang berjalan di Android dan iOS.
- **State Management:** Provider (ChangeNotifier) untuk manajemen state pengguna, kategori, restoran, produk, dan keranjang belanja.
- **Peta Interaktif:** Flutter Map v8.3.0 dengan tile layer OpenStreetMap untuk visualisasi rute dan posisi drone secara real-time.
- **Komunikasi MQTT:** Library mqtt_client v10.1.0 untuk koneksi aplikasi mobile ke broker MQTT cloud (HiveMQ dan CrystalMQ).
- **Backend & Autentikasi:** Firebase Authentication untuk login/registrasi pengguna dan Firebase Firestore untuk penyimpanan data terpusat.
- **HTTP Client:** Library http v1.6.0 untuk komunikasi REST API.
- **UI/UX:** Google Fonts (Poppins, Ubuntu, Dancing Script), simple_animations, flutter_spinkit, showcaseview, carousel_slider, transparent_image.
- **Firmware Drone:** Arduino IDE dengan board ESP32, library TinyGSM untuk konektivitas 4G LTE, dan MAVLink untuk komunikasi dengan Pixhawk.
- **Broker MQTT:** HiveMQ Cloud (SSL/TLS port 8883) dan CrystalMQ (port 1883) untuk menjembatani komunikasi antara aplikasi dan drone.

### Spesifikasi Perangkat Keras (Hardware)

- **Mikrokontroler:** LilyGO T-Call A7670E (ESP32 + modem 4G LTE A7670E) sebagai onboard computer drone.
- **Flight Controller:** Pixhawk 2.4.8 dengan firmware ArduPilot untuk kendali penerbangan otonom.
- **Konektivitas:** SIM Card by.U (APN: byu) untuk akses internet seluler 4G LTE pada drone.
- **GPS:** Modul GPS internal pada Pixhawk 2.4.8 untuk navigasi waypoint.
- **Perangkat Pengguna:** Smartphone Android/iOS untuk menjalankan aplikasi pelanggan dan dashboard penjual.

## FITUR

DelDrone memiliki serangkaian fitur yang dirancang untuk pengalaman belanja dan pengiriman drone yang seamless:

### Fitur Aplikasi Pelanggan (Customer App)

1. **Autentikasi Pengguna:** Login dan registrasi akun pelanggan dengan email dan password melalui Firebase Authentication.
2. **Katalog Produk Interaktif:** Tampilan grid produk dengan gambar, nama, harga, rating, dan tombol "Beli" cepat. Dilengkapi fitur pencarian teks dan filter berdasarkan kategori (Makanan Ringan, Minuman, Perawatan Diri, Kebutuhan Rumah).
3. **Keranjang Belanja:** Manajemen item belanja dengan fitur tambah, kurang, hapus item, dan ringkasan total harga.
4. **Live Drone Tracking:** Peta interaktif (Flutter Map) yang menampilkan posisi drone secara real-time, rute penerbangan, status pengiriman (persiapan → mengudara → menuju lokasi → sampai), estimasi jarak dan waktu tiba, serta indikator baterai drone.
5. **Profil Pengguna:** Halaman profil dengan informasi akun dan akses ke pengaturan.

### Fitur Dashboard Penjual (Seller Dashboard)

1. **Dashboard Statistik:** Ringkasan jumlah produk, pesanan aktif, dan rating toko dalam tampilan kartu informatif.
2. **Manajemen Produk:** Tambah, edit, dan hapus produk dengan detail nama, kategori, harga, rating, dan gambar.
3. **Manajemen Pesanan:** Daftar pesanan masuk dengan informasi pelanggan, alamat pengiriman, dan status pemrosesan.
4. **Pengiriman Drone:** Antarmuka pengiriman drone dengan daftar pesanan siap kirim. Penjual dapat mengirim drone ke alamat pelanggan dengan satu klik, dengan konfirmasi status pengiriman real-time.
5. **Laporan Penjualan:** Halaman laporan penjualan dengan ringkasan pendapatan dan performa toko.
6. **Informasi Toko:** Pengelolaan profil toko (nama toko, alamat, kontak).

## ARSITEKTUR SISTEM

```
┌──────────────────────────────────────────────────────────────────┐
│                        DelDrone Architecture                     │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────────┐   │
│  │ Customer App │    │ Seller App   │    │ Firebase Cloud   │   │
│  │  (Flutter)   │    │  (Flutter)   │    │ (Auth + DB)      │   │
│  └──────┬───────┘    └──────┬───────┘    └────────┬─────────┘   │
│         │                   │                     │             │
│         └─────────┬─────────┘                     │             │
│                   │                               │             │
│                   ▼                               │             │
│         ┌─────────────────┐                       │             │
│         │  MQTT Broker    │                       │             │
│         │  HiveMQ Cloud   │                       │             │
│         └────────┬────────┘                       │             │
│                  │                                │             │
│                  ▼                                │             │
│         ┌─────────────────────────────────────────┴──────┐      │
│         │          LilyGO T-Call A7670E (ESP32)          │      │
│         │  ┌──────────────┐  ┌──────────────────────┐   │      │
│         │  │ Modem 4G LTE │  │ MQTT Client          │   │      │
│         │  │ (SIM by.U)   │  │ (TinyGSM)            │   │      │
│         │  └──────────────┘  └──────────────────────┘   │      │
│         │                                                │      │
│         │  Serial2 (MAVLink) ◄────► Pixhawk 2.4.8       │      │
│         └────────────────────────────────────────────────┘      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

Diagram di atas menggambarkan arsitektur sistem DelDrone secara keseluruhan. Aplikasi pelanggan dan dashboard penjual (keduanya dibangun dengan Flutter) berkomunikasi dengan broker MQTT HiveMQ Cloud untuk mengirim perintah dan menerima data telemetri drone. LilyGO T-Call A7670E bertindak sebagai onboard computer yang menjembatani komunikasi antara cloud (MQTT) dan flight controller (Pixhawk via MAVLink). Firebase digunakan untuk autentikasi pengguna dan penyimpanan data aplikasi secara terpusat.

## PROSES PENGERJAAN

Proses pengerjaan proyek DelDrone dibagi ke dalam beberapa tahapan utama:

1. **Analisis Kebutuhan & Perancangan Sistem:** Menganalisis alur pengguna (pelanggan dan penjual), menentukan spesifikasi teknis, merancang arsitektur komunikasi MQTT, dan mendesain skema database Firebase.

2. **Pengembangan Aplikasi Flutter (Customer App):** Membangun antarmuka pengguna pelanggan meliputi halaman home (katalog produk), detail produk, keranjang belanja, checkout, pelacakan drone, dan profil pengguna.

3. **Pengembangan Aplikasi Flutter (Seller Dashboard):** Membangun dashboard penjual meliputi halaman dashboard, manajemen produk, manajemen pesanan, pengiriman drone, laporan, dan informasi toko.

4. **Pengembangan Firmware Drone (LilyGO + Pixhawk):** Memprogram mikrokontroler ESP32 menggunakan Arduino IDE, mengimplementasikan koneksi LTE (TinyGSM), MQTT client (publish/subscribe), dan komunikasi MAVLink dengan Pixhawk.

5. **Integrasi MQTT & Firebase:** Menghubungkan aplikasi Flutter dengan broker MQTT (HiveMQ) untuk komunikasi drone, serta integrasi Firebase Authentication dan Firestore untuk manajemen data.

6. **Pengujian & Debugging:** Menguji akurasi tracking drone, responsivitas perintah penerbangan, sinkronisasi data Firebase, dan stabilitas koneksi MQTT.

7. **Dokumentasi & Penyusunan Laporan:** Menyusun dokumentasi teknis, panduan penggunaan, dan laporan akhir proyek.

## PEMBAGIAN TUGAS

Deskripsi tugas dari masing-masing bidang di atas adalah sebagai berikut:

- **Frontend Engineering (Customer App):** Bertanggung jawab merancang antarmuka aplikasi pelanggan (UI/UX) yang intuitif menggunakan Flutter, membangun halaman katalog produk, keranjang belanja, dan integrasi peta interaktif untuk drone tracking.

- **Frontend Engineering (Seller Dashboard):** Mengembangkan dashboard manajemen penjual berbasis Flutter, termasuk halaman dashboard statistik, manajemen produk, pemrosesan pesanan, pengiriman drone, dan laporan penjualan.

- **Backend & IoT Engineering:** Mengembangkan firmware drone pada LilyGO T-Call A7670E (Arduino/C++), mengimplementasikan konektivitas 4G LTE, MQTT client (publish/subscribe topic), dan komunikasi MAVLink dengan Pixhawk 2.4.8.

- **Integrasi & DevOps:** Mengkonfigurasi broker MQTT HiveMQ Cloud (SSL/TLS, topik, autentikasi), mengatur Firebase Authentication dan Firestore, serta memastikan sinkronisasi data real-time antara seluruh komponen sistem.

## WAKTU PENGERJAAN KEGIATAN

Berikut ini merupakan tabel pengerjaan kegiatan:

| No | Kegiatan | Minggu 1-2 | Minggu 3-4 | Minggu 5-6 | Minggu 7-8 | Minggu 9-10 | Minggu 11-12 |
|----|----------|:----------:|:----------:|:----------:|:----------:|:-----------:|:------------:|
| 1 | Analisis & Perancangan | ✓ | | | | | |
| 2 | Dev Customer App | | ✓ | ✓ | ✓ | | |
| 3 | Dev Seller Dashboard | | | ✓ | ✓ | ✓ | |
| 4 | Dev Firmware Drone | | ✓ | ✓ | ✓ | ✓ | |
| 5 | Integrasi MQTT & Firebase | | | | ✓ | ✓ | |
| 6 | Pengujian & Debugging | | | | | ✓ | ✓ |
| 7 | Dokumentasi & Laporan | | | | | | ✓ |

---

# BAB III - PENGUJIAN

## 3.1 PEMASANGAN HARDWARE

Tahap pengujian hardware berfokus pada kesiapan sistem drone untuk misi pengiriman. Konfigurasi perangkat keras meliputi:

**Wiring LilyGO T-Call A7670E ke Pixhawk 2.4.8:**
- GPIO16 (RX2) LilyGO → Pin TX TELEM2 Pixhawk
- GPIO17 (TX2) LilyGO → Pin RX TELEM2 Pixhawk
- GND LilyGO → GND TELEM2 Pixhawk
- Catu daya terpisah untuk LilyGO (USB/baterai) dan Pixhawk (baterai LiPo)

**Konfigurasi Modem 4G LTE:**
- SIM Card by.U dipasang pada slot SIM LilyGO T-Call A7670E
- APN dikonfigurasi: `byu` (tanpa username/password)
- Modem diinisialisasi melalui Serial1 (baud rate 115200) dengan pin RX=25, TX=26

**Pengujian Koneksi:**
- Pengujian AT command untuk verifikasi modem berfungsi (`AT`, `AT+CPIN?`, `AT+CREG?`)
- Pengujian registrasi jaringan 4G LTE (`AT+COPS?`)
- Pengujian koneksi data GPRS (`AT+CGATT?`) dan ping ke server HiveMQ

**Kalibrasi Pixhawk:**
- Kalibrasi akselerometer, giroskop, dan kompas melalui Mission Planner/QGroundControl
- Konfigurasi parameter MAVLink (baud rate TELEM2 = 57600)
- Pengujian GPS fix (jumlah satelit, HDOP)

## 3.2 INTEGRASI APLIKASI

Pengujian integrasi aplikasi memastikan seluruh komponen sistem (Flutter App, MQTT Broker, Firebase, dan Drone) dapat berkomunikasi dengan lancar. Skenario pengujian meliputi:

### Pengujian Autentikasi Firebase

Menguji proses registrasi akun baru (email & password) dan login pengguna. Verifikasi bahwa pengguna dengan role "seller" diarahkan ke dashboard penjual, sedangkan role "buyer" diarahkan ke aplikasi pelanggan. Pengujian mencakup validasi form, error handling (email sudah terdaftar, password salah), dan persistensi sesi login.

### Pengujian MQTT (Aplikasi ke Drone)

Menguji konektivitas broker MQTT HiveMQ Cloud dari aplikasi Flutter:
- Koneksi ke broker dengan kredensial (username, password)
- Subscribe ke topik `protel/drone/status`, `protel/drone/location`, `protel/drone/telemetry`
- Verifikasi penerimaan data telemetri drone (GPS, baterai, attitude) secara real-time
- Pengujian publish command ke topik `protel/drone/command` (PING, STATUS, ARM, TAKEOFF)

### Pengujian MQTT (Drone ke Broker)

Menguji konektivitas MQTT dari sisi drone (LilyGO) ke broker HiveMQ Cloud:
- Koneksi MQTT dengan SSL/TLS (port 8883) menggunakan root CA certificate HiveMQ
- Subscribe ke topik `protel/drone/command` dan `protel/drone/request`
- Publish data GPS setiap 1 detik, status setiap 2 detik, telemetri setiap 5 detik
- Verifikasi publish berhasil melalui Serial Monitor Arduino IDE

### Pengujian Live Tracking

Simulasi pengiriman drone dari hangar (koordinat ITS) ke lokasi pelanggan:
- Verifikasi rute penerbangan divisualisasikan di Flutter Map
- Verifikasi marker drone bergerak secara real-time mengikuti data GPS dari MQTT
- Verifikasi status pengiriman berubah sesuai progress (preparing → flying → arriving → delivered)
- Verifikasi indikator baterai, jarak tersisa, dan estimasi waktu tiba

### Pengujian Dashboard Penjual

- **Manajemen Produk:** Menambahkan produk baru, mengedit detail, dan menghapus produk. Verifikasi perubahan tersimpan di Firebase Firestore.
- **Pengiriman Drone:** Memilih pesanan dan menekan tombol "Kirim" — verifikasi command terkirim ke topik MQTT yang sesuai.
- **Laporan Penjualan:** Verifikasi data laporan ditampilkan dengan benar sesuai data pesanan.

---

# BAB IV - PENUTUP

Sebagai penutup, proyek DelDrone (Drone Shopping Delivery System) yang telah kami kembangkan memberikan wawasan mendalam dan pengalaman praktis dalam penerapan teknologi Internet of Things (IoT), mobile development, dan sistem kendali drone untuk solusi logistik udara modern.

Melalui proyek ini, kami memahami pentingnya integrasi arsitektur perangkat lunak dan perangkat keras yang solid, dimulai dari pengembangan aplikasi mobile multiplatform menggunakan Flutter (dengan state management Provider, integrasi Firebase, dan visualisasi peta Flutter Map), hingga pemrograman mikrokontroler ESP32 (LilyGO T-Call A7670E) yang menjembatani komunikasi antara cloud MQTT dan flight controller Pixhawk melalui protokol MAVLink.

Kami belajar mengenai tantangan nyata dalam merancang sistem komunikasi real-time yang handal — di mana protokol MQTT dengan pola publish-subscribe menjadi tulang punggung pertukaran data antara aplikasi pengguna dan drone. Penggunaan broker MQTT berbasis cloud (HiveMQ) memberikan pemahaman tentang krusialnya infrastruktur message broker yang aman (SSL/TLS), scalable, dan responsif dalam aplikasi IoT. Kami juga menghadapi dan mengatasi tantangan dalam mengintegrasikan dua protokol komunikasi yang berbeda (MQTT untuk cloud-to-device dan MAVLink untuk device-to-flight-controller) ke dalam satu sistem yang koheren.

Dari sisi pengembangan aplikasi, kami mendapatkan pengalaman berharga dalam membangun aplikasi dual-role (pelanggan dan penjual) dalam satu codebase Flutter, mengimplementasikan pattern Provider untuk state management yang efisien, serta merancang antarmuka pengguna yang responsif dengan dukungan Google Fonts, animasi, dan komponen Material Design.

Kami ingin menyampaikan apresiasi kepada semua pihak yang telah mendukung kami dalam proyek ini. Dukungan dari dosen pembimbing, mentor, dan rekan-rekan tim, serta ketersediaan literatur teknis (dokumentasi Flutter, TinyGSM, MAVLink, MQTT, Firebase), telah sangat berharga dalam membantu kami mengatasi berbagai kendala dan mencapai tujuan proyek. Kami yakin bahwa pengalaman dalam mengembangkan DelDrone ini akan menjadi aset berharga dalam karir profesional kami di masa depan, khususnya dalam bidang pengembangan aplikasi mobile (Mobile Development), Internet of Things (IoT), sistem kendali drone (Drone Engineering), dan integrasi sistem cloud (Cloud Integration).

---

# DAFTAR PUSTAKA

Flutter Documentation. (n.d.). Flutter: Build apps for any screen. Retrieved from https://flutter.dev/

Provider Package. (n.d.). A wrapper around InheritedWidget for state management. Retrieved from https://pub.dev/packages/provider

Flutter Map. (n.d.). A versatile mapping package for Flutter. Retrieved from https://pub.dev/packages/flutter_map

MQTT Client for Dart. (n.d.). MQTT client library for Dart/Flutter. Retrieved from https://pub.dev/packages/mqtt_client

Firebase Documentation. (n.d.). Firebase Authentication & Cloud Firestore. Google. Retrieved from https://firebase.google.com/docs

HiveMQ Documentation. (n.d.). HiveMQ Cloud - Managed MQTT Broker. Retrieved from https://www.hivemq.com/docs/

TinyGSM Library. (n.d.). A small Arduino library for GSM modules. Retrieved from https://github.com/vshymanskyy/TinyGSM

MAVLink Protocol. (n.d.). Micro Air Vehicle Link Communication Protocol. Retrieved from https://mavlink.io/en/

ArduPilot Documentation. (n.d.). Open Source Drone Autopilot. Retrieved from https://ardupilot.org/

LilyGO T-Call Series. (n.d.). ESP32 with SIM7000G/SIM800L/A7670E Modem. Retrieved from https://github.com/Xinyuan-LilyGO/LilyGo-T-Call-SIM800

Pixhawk Documentation. (n.d.). Pixhawk 2.4.8 Flight Controller. Retrieved from https://docs.px4.io/

OpenStreetMap. (n.d.). OpenStreetMap Tile Layer. Retrieved from https://www.openstreetmap.org/

Google Fonts for Flutter. (n.d.). Google Fonts package for Flutter. Retrieved from https://pub.dev/packages/google_fonts
