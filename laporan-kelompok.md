# PROYEK TELEMATIKA GENAP 2025 - 2026

# LAPORAN AKHIR

# Shopping Drone - Drone Shopping Delivery System

# KELOMPOK 3

Salman Al Ghifary	NRP. 5024221003

Farhan Abdurrahman Muthohhar	NRP. 5024221050

Andika Fathurrahman Achiral	NRP. 5024221065

# DOSEN PENGAMPU

Prof. Dr. I Ketut Eddy Purnama, S.T., M.T.

Ahmad Zaini, S.T., M.T.

# DEPARTEMEN TEKNIK KOMPUTER

# Fakultas Teknologi Elektro dan Informatika Cerdas

# Institut Teknologi Sepuluh Nopember

# Surabaya 2026

---

# KATA PENGANTAR

Puji syukur kehadirat Tuhan Yang Maha Esa atas rahmat dan karunia-Nya, penulis dapat menyelesaikan Laporan Proyek Telematika dengan judul: **Shopping Drone - Drone Shopping Delivery System**. Penyusunan laporan ini tidak lepas dari bantuan dan dukungan berbagai pihak. Oleh karena itu, dengan segala kerendahan hati, kami mengucapkan terima kasih kepada:

- Tuhan Yang Maha Esa, atas kelancaran dan berkah yang diberikan selama pelaksanaan proyek telematika ini.
- Bapak Dr. Arief Kurniawan, S.T., M.T. selaku Kepala Departemen Teknik Komputer FTEIC-ITS.
- Bapak Prof. Dr. I Ketut Eddy Purnama, S.T., M.T. dan Ahmad Zaini, S.T., M.T. selaku Dosen Pengampu Proyek Telematika Departemen Teknik Komputer FTEIC-ITS yang telah memberikan bimbingan dan arahan.
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
- Cara Kerja Alat
- Spesifikasi
- Fitur
- Arsitektur Sistem
- Flowchart
- Proses Pengerjaan
- Pembagian Tugas
- Waktu Pengerjaan Kegiatan

BAB III - PENGUJIAN
- Perakitan dan Pemasangan Hardware
- Integrasi Aplikasi

BAB IV - PENUTUP

DAFTAR PUSTAKA

---

# BAB I - PENDAHULUAN

## LATAR BELAKANG

Logistik pengiriman barang tahap akhir (last-mile delivery) saat ini menghadapi tantangan besar berupa inefisiensi waktu dan biaya operasional yang tinggi akibat kemacetan serta ketergantungan pada kurir konvensional. Berdasarkan riset, penggunaan drone untuk pengiriman otomatis mulai menjadi tren global karena mampu memangkas waktu distribusi secara signifikan. Namun, implementasi drone shipping masih terkendala biaya perangkat yang mahal dan sistem monitoring yang belum terintegrasi.

Proyek ini hadir untuk mengintegrasikan teknologi drone otonom dengan sistem telematika berbasis IoT. Dengan memanfaatkan protokol MQTT untuk transmisi data koordinat dan status perangkat secara real-time, proyek ini bertujuan menciptakan solusi pengiriman barang yang cepat, murah (low-cost), dan dapat diimplementasikan dalam ekosistem pasar modern.

Sebagai solusi atas permasalahan tersebut, dikembangkanlah **Shopping Drone (DroneMart)** — sebuah platform belanja dan pengiriman berbasis drone yang mengintegrasikan tiga komponen utama: (1) aplikasi mobile untuk pelanggan berbasis Flutter, (2) dashboard manajemen untuk merchant berbasis Flutter, serta (3) perangkat keras drone rakitan sendiri menggunakan frame F450 yang dikendalikan melalui komunikasi MQTT dan protokol MAVLink. Drone dibangun dari komponen-komponen standar industri meliputi motor brushless A2212 1000KV, ESC 30A, propeller 1045, Pixhawk 2.4.8 sebagai flight controller, GPS Module M8N untuk navigasi, serta LilyGO T-Call A7670E (ESP32 + modem 4G LTE) sebagai onboard computer yang menjembatani komunikasi antara cloud dan flight controller.

Keunggulan utama Shopping Drone terletak pada arsitektur komunikasi real-time yang memungkinkan pemantauan posisi drone secara langsung (live tracking) melalui peta interaktif, pengiriman perintah penerbangan jarak jauh, serta notifikasi status pengiriman yang diperbarui secara kontinu. Dengan integrasi Firebase untuk autentikasi pengguna dan sinkronisasi data, serta broker MQTT berbasis cloud (HiveMQ) untuk komunikasi dengan drone, Shopping Drone menghadirkan solusi end-to-end untuk ekosistem belanja dan pengiriman udara modern.

## RUMUSAN MASALAH

Berdasarkan latar belakang di atas, permasalahan utama yang diselesaikan dalam proyek ini meliputi:

### 1. Hambatan Logistik pada Jalur Darat Perkotaan
Tingginya kepadatan lalu lintas di area pasar dan permukiman menyebabkan kurir konvensional kehilangan efisiensi waktu secara signifikan, terutama untuk barang belanjaan yang bersifat perishable (cepat rusak). **Solusi:** Mengimplementasikan drone yang bergerak pada jalur udara bebas hambatan (Point-to-Point) dengan navigasi berbasis GPS Waypoints, memangkas waktu pengiriman hingga 70% dibandingkan kurir konvensional.

### 2. Risiko Human Error dan Keamanan Paket di Jalan
Pengiriman manual oleh kurir memiliki risiko kesalahan navigasi manusia, kecelakaan lalu lintas, hingga potensi paket dicuri oleh oknum kurir yang tidak bertanggung jawab. **Solusi:** Menghilangkan faktor human error dengan sistem terbang otonom yang dikendalikan oleh Flight Controller. Sistem dilengkapi dengan cargo box yang hanya dapat terbuka secara otomatis melalui perintah dari server ketika drone sudah mencapai koordinat tujuan, mencegah pencurian.

### 3. Tingginya Biaya Operasional Per Satuan Barang
Untuk pengiriman barang ringan namun mendesak (seperti dokumen atau obat-obatan), penggunaan kendaraan bermotor tidak efisien secara biaya karena konsumsi bahan bakar dan biaya perawatan kendaraan tetap dihitung per rute, bukan per berat beban. **Solusi:** Mengganti penggunaan bahan bakar fosil dengan energi listrik baterai yang jauh lebih murah per kilometer untuk beban ringan.

### 4. Bagaimana merancang dan membangun aplikasi mobile multiplatform menggunakan Flutter yang menyediakan layanan belanja produk kebutuhan sehari-hari dengan fitur pelacakan pengiriman drone secara real-time?

### 5. Bagaimana mengintegrasikan flight controller Pixhawk 2.4.8 dengan mikrokontroler LilyGO T-Call A7670E (ESP32) agar drone dapat menerima perintah penerbangan (arm, takeoff, goto, land, RTL) melalui jaringan seluler 4G LTE dan mengirimkan data telemetri (GPS, baterai, attitude) secara berkala ke cloud MQTT?

## TUJUAN

Adapun tujuan dari proyek ini adalah sebagai berikut:

1. Merancang dan membangun aplikasi mobile multiplatform berbasis Flutter yang menyediakan fitur katalog produk, keranjang belanja, checkout, dan pelacakan pengiriman drone secara real-time dengan visualisasi peta interaktif menggunakan Flutter Map dan OpenStreetMap.

2. Merakit dan mengkonfigurasi drone pengiriman menggunakan frame F450, motor brushless A2212 1000KV, ESC 30A, Pixhawk 2.4.8, GPS Module M8N, dan LilyGO T-Call A7670E sebagai sistem kendali otonom berbasis IoT.

3. Mengimplementasikan sistem komunikasi MQTT dua arah antara aplikasi Flutter dan perangkat drone melalui broker cloud HiveMQ, yang menangani topik perintah (command), permintaan data (request), status, lokasi GPS, dan telemetri drone secara efisien.

4. Mengintegrasikan flight controller Pixhawk 2.4.8 dengan mikrokontroler LilyGO T-Call A7670E menggunakan protokol MAVLink, sehingga drone dapat dikendalikan dari jarak jauh melalui jaringan seluler 4G LTE (SIM by.U) untuk misi pengiriman otonom.

5. Membangun dashboard merchant berbasis Flutter yang mencakup halaman dashboard statistik, pengelolaan produk, manajemen pesanan, pengiriman drone, dan laporan penjualan dalam satu aplikasi terpadu.

6. Mengintegrasikan layanan Firebase Authentication untuk autentikasi pengguna (pelanggan dan merchant) serta Firebase Firestore untuk penyimpanan data produk, pesanan, dan profil pengguna secara real-time.

## MANFAAT

Adapun manfaat dari proyek ini adalah sebagai berikut:

### Bagi Pelanggan

- **Pengiriman Cepat dan Transparan:** Fitur live tracking memungkinkan pelanggan memantau posisi drone secara real-time di peta, lengkap dengan estimasi waktu tiba, status pengiriman, dan indikator baterai drone. Pengiriman via jalur udara memangkas waktu signifikan.
- **Keamanan Paket:** Cargo box hanya dapat dibuka oleh penerima yang sah di titik koordinat tujuan, mencegah pencurian oleh pihak yang tidak berwenang.
- **Kemudahan Belanja:** Pelanggan dapat menjelajahi katalog produk kebutuhan sehari-hari (makanan ringan, minuman, perawatan diri, kebutuhan rumah) melalui antarmuka yang intuitif.

### Bagi Merchant (Penjual)

- **Optimalisasi Biaya Operasional:** Penggunaan tenaga listrik baterai jauh lebih murah per kilometer dibandingkan kendaraan bermotor untuk beban ringan.
- **Otomatisasi Pengiriman:** Fitur "Kirim Drone" memungkinkan penjual mengirimkan drone ke lokasi pelanggan hanya dengan satu klik, dengan konfirmasi status pengiriman yang real-time.
- **Manajemen Toko Terpadu:** Dashboard terpadu untuk mengelola produk (tambah/edit/hapus), memantau pesanan masuk, mengirim drone, dan melihat laporan penjualan dalam satu aplikasi.

### Bagi Bidang Keilmuan dan Pengembangan Teknologi

- **Implementasi Arsitektur IoT Terintegrasi:** Proyek ini memberikan kontribusi praktis mengenai integrasi mobile development (Flutter), Internet of Things (ESP32 + MQTT), sistem kendali drone (Pixhawk + MAVLink), dan layanan cloud (Firebase + HiveMQ) ke dalam satu solusi arsitektur end-to-end.
- **Referensi Pengembangan Drone Delivery:** Dokumentasi teknis dan kode sumber proyek dapat menjadi referensi bagi pengembang lain yang ingin membangun sistem pengiriman berbasis drone menggunakan teknologi open-source dan komponen terjangkau.

---

# BAB II - PEMBAHASAN

## DESKRIPSI PRODUK

Shopping Drone (DroneMart) adalah platform belanja dan pengiriman berbasis drone yang terdiri dari tiga komponen utama:

1. **Aplikasi Pelanggan (Customer App)** — Aplikasi mobile berbasis Flutter untuk menjelajahi dan membeli produk kebutuhan sehari-hari. Menyediakan fitur katalog produk, keranjang belanja, checkout, dan live drone tracking dengan peta interaktif.

2. **Dashboard Merchant (Seller Dashboard)** — Aplikasi berbasis Flutter untuk merchant mengelola toko, produk, pesanan masuk, pengiriman drone, dan memantau laporan penjualan.

3. **Perangkat Keras Drone** — Drone rakitan sendiri menggunakan frame F450 dengan komponen: 4x Motor Brushless A2212 1000KV, 4x ESC 30A, 2 pasang Propeller 1045, Pixhawk 2.4.8, GPS Module M8N, Power Module, Safety Switch & Buzzer, Anti-Vibration Damper, Baterai LiPo 3S/4S, Radio Telemetry 433MHz, dan LilyGO T-Call A7670E (ESP32 + modem 4G LTE) sebagai onboard computer. Drone menjalankan misi pengiriman otonom ke lokasi pelanggan.

Seluruh komponen terhubung melalui infrastruktur komunikasi MQTT (HiveMQ Cloud) dan Firebase untuk sinkronisasi data real-time. Sistem mengadopsi arsitektur client-server dengan pola komunikasi publish-subscribe melalui broker MQTT. Drone secara berkala mempublikasikan data telemetri (GPS, baterai, attitude) ke topik MQTT yang dilanggan oleh aplikasi Flutter. Perintah penerbangan (arm, takeoff, goto, land, RTL) dikirim dari dashboard merchant ke drone melalui topik command MQTT. Protokol MAVLink menjembatani komunikasi antara LilyGO (ESP32) dan Pixhawk.

## CARA KERJA ALAT

Sistem Shopping Drone bekerja dalam tiga tahap utama:

### 1. Tahap Inisialisasi & Pemesanan (Input)

- **Order Entry:** Pengguna memesan barang melalui aplikasi mobile. Merchant menyiapkan paket dan memasukkannya ke dalam cargo box drone.
- **Mission Planning:** Merchant memasukkan koordinat tujuan pada dashboard. Sistem secara otomatis menentukan titik-titik navigasi (waypoints) dan ketinggian aman untuk menghindari rintangan darat.
- **Pre-flight Check:** Mikrokontroler ESP32 (LilyGO) mengecek status kesehatan baterai dan sinyal GPS melalui komunikasi dengan Pixhawk. Jika semua parameter normal, sistem memberikan status "Ready to Fly".

### 2. Tahap Navigasi & Transmisi Telemetri (Process)

- **Autonomous Flight:** Drone lepas landas secara otomatis dan terbang menuju koordinat tujuan menggunakan data dari Flight Controller (Pixhawk/ArduPilot).
- **Data Streaming:** Selama penerbangan, ESP32 mengambil data dari Flight Controller melalui protokol MAVLink (koordinat GPS, ketinggian, sisa baterai, attitude) dan mengirimkannya ke server Cloud melalui protokol MQTT menggunakan jaringan seluler 4G LTE (modem A7670E + SIM by.U).
- **Real-time Monitoring:** Pengguna dan Merchant dapat memantau pergerakan drone secara real-time di peta pada dashboard monitoring aplikasi.

### 3. Tahap Pendaratan & Penyerahan Paket (Output)

- **Precision Arrival:** Setelah mencapai koordinat tujuan, drone akan turun secara perlahan (Auto-land) dengan dikendalikan oleh Pixhawk.
- **Secure Release:** Setelah sensor mendeteksi drone telah mendarat dengan aman, Flight Controller mengirimkan sinyal untuk membuka kunci cargo box.
- **Mission Accomplished:** Paket diterima pengguna, drone mengunci kembali cargo box, dan terbang kembali ke titik awal (Return to Launch) secara otomatis.

## SPESIFIKASI

### Spesifikasi Perangkat Lunak (Software)

- **Framework Frontend:** Flutter 3.x (Dart SDK >= 2.17.0 < 4.0.0) untuk aplikasi pelanggan dan dashboard merchant (Android & iOS).
- **State Management:** Provider (ChangeNotifier) — UserProvider, CategoryProvider, RestaurantProvider, CartProvider, MqttProvider, ProductProvider.
- **Peta Interaktif:** Flutter Map v8.3.0 + LatLong2 v0.9.1 + OpenStreetMap tile layer untuk visualisasi rute dan posisi drone.
- **Komunikasi MQTT:** Library mqtt_client v10.1.0 untuk koneksi aplikasi ke broker MQTT cloud (HiveMQ: SSL/TLS port 8883, CrystalMQ: port 1883).
- **Backend & Autentikasi:** Firebase Authentication (email/password) + Firebase Firestore untuk penyimpanan data terpusat.
- **HTTP Client:** Library http v1.6.0 untuk komunikasi REST API.
- **UI/UX:** Google Fonts (Poppins, Ubuntu, Dancing Script, Circular), simple_animations v5.2.0, flutter_spinkit, showcaseview, carousel_slider, transparent_image.
- **Firmware Drone:** Arduino IDE + board ESP32, library TinyGSM (modem A7670E), MAVLink v2, ArduinoJson.
- **Broker MQTT:** HiveMQ Cloud (SSL/TLS) dan CrystalMQ sebagai message broker.
- **Ground Control:** Mission Planner / QGroundControl untuk kalibrasi dan konfigurasi Pixhawk.

### Spesifikasi Perangkat Keras (Hardware)

**Drone:**
- 1x Frame F450 (quadcopter)
- 4x Motor Brushless A2212 1000KV
- 4x ESC 30A
- 2 Pasang Propeller 1045
- 1x Pixhawk 2.4.8 (Flight Controller, firmware ArduPilot)
- 1x GPS Module M8N (navigasi + compass)
- 1x Power Module Pixhawk (catu daya + monitoring baterai)
- 1x Safety Switch & Buzzer
- 1x Kartu MicroSD (data logging)
- 1x Anti-Vibration Damper (peredam getaran)
- 1x Baterai LiPo 3S/4S 4500-5000mAh
- 1x Charger LiPo
- 1x Radio Telemetry 433MHz (ground control)
- 1x Cargo Box + Servo (mekanisme buka/tutup otomatis)

**Onboard Computer:**
- 1x LilyGO T-Call A7670E (ESP32 + Modem 4G LTE A7670E)
- 1x SIM Card by.U (APN: byu)
- 1x GPS Sekunder (opsional, redundant)

**Perangkat Pengguna:**
- Smartphone Android/iOS untuk aplikasi pelanggan dan dashboard merchant

## FITUR

### Fitur Aplikasi Pelanggan (Customer App)

1. **Autentikasi Pengguna:** Login dan registrasi akun dengan email/password via Firebase Auth. Dual-role: buyer dan seller.
2. **Katalog Produk Interaktif:** Grid produk 4 kolom dengan gambar, nama, harga, rating. Fitur pencarian teks dan filter kategori (Makanan Ringan, Minuman, Perawatan Diri, Kebutuhan Rumah).
3. **Keranjang Belanja:** Tambah/kurang/hapus item, ringkasan total harga, notifikasi "ditambahkan ke keranjang".
4. **Live Drone Tracking:** Peta OpenStreetMap interaktif menampilkan posisi drone real-time, rute penerbangan (garis hijau = jalur ditempuh, garis biru putus-putus = jalur tersisa), status pengiriman (preparing → flying → arriving → delivered), estimasi jarak & waktu tiba, indikator baterai dengan progress bar.
5. **Profil Pengguna:** Informasi akun dan role.

### Fitur Dashboard Merchant (Seller Dashboard)

1. **Dashboard Statistik:** Kartu ringkasan jumlah produk, pesanan aktif, rating toko.
2. **Manajemen Produk:** Tambah/edit/hapus produk dengan detail nama, kategori, harga, rating, gambar.
3. **Manajemen Pesanan:** Daftar pesanan masuk dengan info pelanggan, alamat, status.
4. **Pengiriman Drone:** Pilih pesanan → klik "Kirim Drone" → drone takeoff otomatis menuju koordinat pelanggan. Konfirmasi status real-time via MQTT.
5. **Laporan Penjualan:** Ringkasan pendapatan dan performa toko.
6. **Informasi Toko:** Pengelolaan profil toko (nama, alamat, kontak).

## ARSITEKTUR SISTEM

```
┌──────────────────────────────────────────────────────────────────────┐
│                   Shopping Drone Architecture                        │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌──────────────────┐   ┌──────────────────┐   ┌─────────────────┐  │
│  │  Customer App    │   │  Merchant App    │   │  Firebase Cloud │  │
│  │  (Flutter)       │   │  (Flutter)       │   │  (Auth + DB)    │  │
│  └────────┬─────────┘   └────────┬─────────┘   └────────┬────────┘  │
│           │                      │                       │          │
│           └──────────┬───────────┘                       │          │
│                      │                                   │          │
│                      ▼                                   │          │
│           ┌───────────────────┐                          │          │
│           │   MQTT Broker     │                          │          │
│           │   HiveMQ Cloud    │                          │          │
│           └────────┬──────────┘                          │          │
│                    │                                     │          │
│                    ▼                                     │          │
│  ┌──────────────────────────────────────────────────────┴───────┐  │
│  │              LilyGO T-Call A7670E (ESP32)                    │  │
│  │  ┌─────────────────┐  ┌────────────────────────────────┐    │  │
│  │  │ Modem 4G LTE    │  │ MQTT Client (TinyGSM)          │    │  │
│  │  │ (SIM by.U)      │  │ Topic: protel/drone/*          │    │  │
│  │  └─────────────────┘  └────────────────────────────────┘    │  │
│  │                                                              │  │
│  │  Serial2 (TX=17, RX=16) ───────► TELEM2 Pixhawk 2.4.8      │  │
│  │  Protokol: MAVLink v2, Baud: 57600                          │  │
│  └─────────────────────────────────────────────────────────────┘  │
│                              │                                     │
│                              ▼                                     │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │              Pixhawk 2.4.8 (Flight Controller)               │ │
│  │  ┌──────────┐  ┌──────────┐  ┌───────────┐  ┌────────────┐ │ │
│  │  │ GPS M8N  │  │ Power    │  │ ESC 30A   │  │ Telemetry  │ │ │
│  │  │ Module   │  │ Module   │  │ (x4)      │  │ 433MHz     │ │ │
│  │  └──────────┘  └──────────┘  └─────┬─────┘  └────────────┘ │ │
│  │                                    │                         │ │
│  │                    ┌───────────────┼───────────────┐         │ │
│  │                    ▼               ▼               ▼         │ │
│  │              Motor A2212     Motor A2212     Motor A2212     │ │
│  │              1000KV (x4)     + Prop 1045                     │ │
│  └──────────────────────────────────────────────────────────────┘ │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

Diagram di atas menggambarkan arsitektur sistem Shopping Drone secara keseluruhan. Aplikasi pelanggan dan dashboard merchant (Flutter) berkomunikasi dengan broker MQTT HiveMQ Cloud untuk mengirim perintah dan menerima data telemetri drone. LilyGO T-Call A7670E bertindak sebagai onboard computer yang menjembatani komunikasi antara cloud (MQTT) dan flight controller (Pixhawk via MAVLink). Firebase digunakan untuk autentikasi pengguna dan penyimpanan data aplikasi. Pixhawk 2.4.8 mengendalikan seluruh hardware penerbangan (GPS, ESC, motor, telemetry radio).

## FLOWCHART

### Flowchart Drone (Hardware)

```
┌──────────────┐
│    START     │
└──────┬───────┘
       ▼
┌──────────────┐     ┌──────────────┐
│ Init ESP32   │────▶│ Init Modem   │
│ (Serial, I/O)│     │ A7670E (LTE) │
└──────────────┘     └──────┬───────┘
                            ▼
                     ┌──────────────┐     ┌──────────────┐
                     │ Connect      │────▶│ Subscribe    │
                     │ MQTT (TLS)   │     │ MQTT Topics  │
                     └──────┬───────┘     └──────┬───────┘
                            │                    │
                            ▼                    │
                     ┌──────────────┐            │
                     │ Init MAVLink │            │
                     │ Serial2      │            │
                     └──────┬───────┘            │
                            │                    │
              ┌─────────────┴────────────┐       │
              ▼                          ▼       │
       ┌────────────┐            ┌────────────┐  │
       │ HEARTBEAT  │            │ MQTT LOOP  │◀─┘
       │ to Pixhawk │            │ Check CMD  │
       └─────┬──────┘            └─────┬──────┘
             │                         │
             ▼                         ▼
       ┌────────────┐           ┌────────────┐
       │ READ       │           │ EXECUTE    │
       │ TELEMETRY  │           │ COMMAND    │
       │ (MAVLink)  │           │ (ARM,TO,   │
       └─────┬──────┘           │ LAND, etc) │
             │                  └─────┬──────┘
             ▼                         │
       ┌────────────┐                  │
       │ PUBLISH    │                  │
       │ MQTT       │                  │
       │ GPS/Status │                  │
       │ /Battery   │                  │
       └─────┬──────┘                  │
             │                         │
             └────────────┬────────────┘
                          ▼
                   ┌────────────┐
                   │   LOOP     │
                   │ (kembali)  │
                   └────────────┘
```

### Flowchart Aplikasi Mobile (Software)

```
┌──────────────────┐
│   USER BUKA APP  │
└────────┬─────────┘
         ▼
┌──────────────────┐     ┌──────────────────┐
│ LOGIN/REGISTER   │────▶│ AUTHENTICATED?   │
│ (Firebase Auth)  │     └────────┬─────────┘
└──────────────────┘              │
                       ┌──────────┴──────────┐
                       ▼                     ▼
                ┌────────────┐        ┌────────────┐
                │ BUYER?     │        │ SELLER?    │
                │ (Customer) │        │ (Merchant) │
                └─────┬──────┘        └─────┬──────┘
                      │                     │
                      ▼                     ▼
┌──────────────────────────────────┐  ┌──────────────────┐
│         MAIN SCREEN             │  │  SELLER DASHBOARD │
│  ┌───────────┬──────────────┐   │  │  - Dashboard      │
│  │ HOME PAGE │ ORDER PAGE   │   │  │  - Kelola Produk  │
│  │ - Katalog │ - Cart       │   │  │  - Pesanan Masuk  │
│  │ - Search  │ - Tracking   │   │  │  - Kirim Drone    │
│  │ - Filter  │   Drone      │   │  │  - Laporan        │
│  └───────────┴──────────────┘   │  │  - Profil Toko    │
│  + PROFILE PAGE                 │  └──────────────────┘
└──────────────────────────────────┘
         │                              │
         └──────────────┬───────────────┘
                        ▼
              ┌──────────────────┐
              │ MQTT CONNECTION  │
              │ (HiveMQ Cloud)   │
              │ Subscribe:       │
              │ protel/drone/*   │
              │ Publish:         │
              │ protel/drone/cmd │
              └──────────────────┘
```

## PROSES PENGERJAAN

Proses pengerjaan proyek Shopping Drone dibagi dalam beberapa tahap:

1. **Analisis & Perancangan Sistem:** Menganalisis alur pengguna, menentukan spesifikasi drone dan aplikasi, merancang arsitektur MQTT, mendesain skema Firebase, dan membuat proposal proyek.

2. **Perakitan Drone (Hardware):** Merakit frame F450, memasang motor brushless A2212 + ESC 30A + propeller 1045, menginstal Pixhawk 2.4.8 + GPS M8N + Power Module, memasang anti-vibration damper, mengkonfigurasi radio telemetry 433MHz, dan mengintegrasikan LilyGO T-Call A7670E.

3. **Pengembangan Firmware Drone:** Memprogram ESP32 (Arduino IDE) untuk koneksi LTE (TinyGSM), MQTT client (publish/subscribe topik protel/drone/*), dan komunikasi MAVLink dengan Pixhawk.

4. **Pengembangan Aplikasi Flutter (Customer App):** UI/UX pelanggan: home page (katalog produk grid 4 kolom), detail produk, keranjang belanja, checkout, drone tracking page (Flutter Map + MQTT telemetry), profil pengguna.

5. **Pengembangan Aplikasi Flutter (Seller Dashboard):** Dashboard statistik, manajemen produk (CRUD), manajemen pesanan, pengiriman drone (publish MQTT command), laporan penjualan, informasi toko.

6. **Integrasi & Pengujian:** Menghubungkan Flutter ↔ MQTT Broker ↔ Drone, integrasi Firebase Auth + Firestore, pengujian akurasi tracking, responsivitas command, sinkronisasi data, dan stabilitas koneksi.

7. **Dokumentasi & Laporan:** Menyusun dokumentasi teknis, panduan penggunaan (MQTT Setup Guide, Arduino IDE Guide), dan laporan akhir.

## PEMBAGIAN TUGAS

Deskripsi tugas masing-masing anggota:

- **Salman Al Ghifary — Desain UI/UX dan Pengembangan Aplikasi Mobile (Flutter):** Bertanggung jawab merancang UI aplikasi pelanggan dan dashboard merchant, membangun halaman katalog produk, keranjang belanja, checkout, drone tracking dengan Flutter Map, serta mengintegrasikan Firebase Authentication.

- **Andika Fathurrahman Achiral — Mekanisme Drone dan Cargo (Hardware):** Merakit drone (frame F450, motor, ESC, propeller, Pixhawk, GPS), mengkonfigurasi flight controller, mengembangkan firmware ESP32 (LilyGO + TinyGSM + MAVLink), serta merancang mekanisme cargo box dengan servo.

## WAKTU PENGERJAAN KEGIATAN

| No | Kegiatan | Minggu 1-2 | Minggu 3-4 | Minggu 5-6 | Minggu 7-8 | Minggu 9-10 | Minggu 11-12 |
|----|----------|:----------:|:----------:|:----------:|:----------:|:-----------:|:------------:|
| 1 | Analisis & Perancangan | ✓ | | | | | |
| 2 | Perakitan Drone | ✓ | ✓ | | | | |
| 3 | Dev Firmware (ESP32) | | ✓ | ✓ | ✓ | | |
| 4 | Dev Customer App | | ✓ | ✓ | ✓ | | |
| 5 | Dev Seller Dashboard | | | ✓ | ✓ | ✓ | |
| 6 | Integrasi MQTT & Firebase | | | | ✓ | ✓ | |
| 7 | Pengujian & Debugging | | | | | ✓ | ✓ |
| 8 | Dokumentasi & Laporan | | | | | | ✓ |

---

# BAB III - PENGUJIAN

## 3.1 PERAKITAN DAN PEMASANGAN HARDWARE

### Perakitan Drone

Tahap perakitan drone meliputi:

**Assembly Frame F450:**
- Memasang 4 lengan frame ke body utama
- Memasang landing gear
- Memasang anti-vibration damper pada mounting plate Pixhawk

**Instalasi Powertrain:**
- Memasang 4x Motor Brushless A2212 1000KV pada ujung lengan frame
- Menghubungkan motor ke 4x ESC 30A
- Memasang 2 pasang Propeller 1045 (CW dan CCW)
- Menghubungkan ESC ke Power Module Pixhawk
- Memasang Baterai LiPo 3S/4S 4500-5000mAh

**Instalasi Flight Controller:**
- Memasang Pixhawk 2.4.8 di atas anti-vibration damper
- Menghubungkan GPS Module M8N ke port GPS/I2C Pixhawk
- Menghubungkan Power Module ke port POWER Pixhawk
- Menghubungkan Safety Switch & Buzzer
- Memasang Kartu MicroSD untuk data logging
- Menghubungkan Radio Telemetry 433MHz ke port TELEM1

**Wiring LilyGO T-Call A7670E ke Pixhawk:**
- GPIO16 (RX2) LilyGO → Pin TX TELEM2 Pixhawk
- GPIO17 (TX2) LilyGO → Pin RX TELEM2 Pixhawk
- GND LilyGO → GND TELEM2 Pixhawk
- Catu daya terpisah untuk LilyGO (USB power bank / baterai)

**Konfigurasi Modem 4G LTE:**
- SIM Card by.U dipasang pada slot SIM LilyGO
- APN: `byu` (tanpa username/password)
- Modem diinisialisasi melalui Serial1 (baud 115200, pin RX=25, TX=26)

**Pengecekan Awal:**
- Verifikasi AT command modem (`AT`, `AT+CPIN?`, `AT+CREG?`)
- Verifikasi registrasi jaringan 4G LTE (`AT+COPS?`)
- Verifikasi koneksi GPRS (`AT+CGATT?`)

### Kalibrasi dan Konfigurasi Pixhawk

- Kalibrasi akselerometer, giroskop, dan kompas melalui Mission Planner
- Kalibrasi ESC dan motor
- Konfigurasi parameter MAVLink (baud TELEM2 = 57600)
- Pengujian GPS fix (> 8 satelit, HDOP < 1.5)
- Pengujian motor spin (tanpa propeller)
- Pengujian failsafe (radio loss, battery low)

## 3.2 INTEGRASI APLIKASI

### Pengujian Autentikasi Firebase

Menguji proses registrasi akun baru (email & password) dan login pengguna. Verifikasi bahwa pengguna role "seller" diarahkan ke Seller Dashboard, role "buyer" ke Customer App. Pengujian mencakup validasi form, error handling, dan persistensi sesi.

### Pengujian Koneksi MQTT

**Aplikasi ke Broker:**
- Koneksi Flutter ke HiveMQ Cloud (SSL/TLS port 8883, kredensial)
- Subscribe topik: `protel/drone/status`, `protel/drone/location`, `protel/drone/telemetry`
- Verifikasi penerimaan data telemetri JSON real-time
- Publish command ke `protel/drone/command` (PING, STATUS, ARM)

**Drone ke Broker:**
- Koneksi ESP32 (TinyGSM) ke HiveMQ via SSL/TLS
- Subscribe topik: `protel/drone/command`, `protel/drone/request`
- Publish GPS (setiap 1 detik), status (setiap 2 detik), telemetri (setiap 5 detik)
- Verifikasi via Serial Monitor Arduino IDE

### Pengujian Live Tracking

Simulasi pengiriman dari hangar (koordinat ITS: lat -7.2823, lng 112.7931) ke lokasi pelanggan:
- Verifikasi rute divisualisasikan di Flutter Map
- Marker drone bergerak real-time mengikuti GPS dari MQTT
- Status berubah: preparing → flying → arriving → delivered
- Indikator baterai, jarak tersisa, estimasi waktu berfungsi

### Pengujian Dashboard Merchant

- Manajemen Produk: CRUD produk tersimpan di Firebase Firestore
- Pengiriman Drone: Command terkirim ke topik MQTT, status drone berubah
- Laporan Penjualan: Data sesuai pesanan yang diproses

---

# BAB IV - PENUTUP

Proyek Shopping Drone (Drone Shopping Delivery System) yang telah kami kembangkan memberikan wawasan mendalam dan pengalaman praktis dalam integrasi teknologi drone otonom, Internet of Things (IoT), dan mobile development untuk solusi logistik udara modern.

Kami berhasil merakit sebuah drone quadcopter menggunakan frame F450 dengan komponen standar industri (motor A2212 1000KV, ESC 30A, Pixhawk 2.4.8, GPS M8N) yang terintegrasi dengan mikrokontroler LilyGO T-Call A7670E sebagai onboard computer. Drone mampu berkomunikasi secara dua arah dengan aplikasi mobile melalui protokol MQTT menggunakan jaringan seluler 4G LTE, memungkinkan pengiriman perintah penerbangan jarak jauh dan transmisi data telemetri secara real-time.

Dari sisi perangkat lunak, kami membangun aplikasi mobile multiplatform menggunakan Flutter yang mencakup Customer App (katalog produk, keranjang belanja, live drone tracking dengan Flutter Map) dan Seller Dashboard (manajemen produk, pesanan, pengiriman drone, laporan). Integrasi Firebase Authentication dan Firestore memungkinkan manajemen pengguna dan data yang terpusat, sementara broker MQTT HiveMQ Cloud menjembatani komunikasi antara aplikasi dan drone.

Kami menyadari bahwa proyek ini masih memiliki ruang pengembangan, seperti implementasi computer vision untuk obstacle avoidance, optimasi rute dengan algoritma pathfinding, dan peningkatan keamanan komunikasi end-to-end. Namun, purwarupa yang dihasilkan telah membuktikan konsep integrasi drone delivery system secara end-to-end.

Kami mengucapkan terima kasih kepada dosen pembimbing, rekan satu tim, dan semua pihak yang telah mendukung proyek ini. Pengalaman ini menjadi aset berharga dalam karir profesional kami, khususnya di bidang IoT, drone engineering, mobile development, dan cloud integration.

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
