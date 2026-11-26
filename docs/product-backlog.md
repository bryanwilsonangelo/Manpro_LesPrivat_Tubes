## Product Backlog

Daftar kebutuhan fitur (Product Backlog) untuk aplikasi **EduCapy** disusun berdasarkan prioritas bisnis untuk mendukung layanan les privat *one-on-one* bagi tiga peran utama (**Murid**, **Pengajar**, dan **Admin**).

| ID | Epik / Modul | Item Product Backlog (User Story) | Peran | Prioritas | Target Sprint |
| :---  | :--- | :--- | :--- | :---: | :---: |
| **PB-01** | **Autentikasi & Hak Akses** | Sebagai pengguna, saya dapat melakukan registrasi dan masuk (*login*) ke sistem sesuai dengan peran (Murid, Pengajar, atau Admin) agar hak akses data terjaga. | Semua Peran | Tinggi | Sprint 3 |
| **PB-02** | **Manajemen Profil Pengguna** | Sebagai pengguna, saya dapat melihat dan memperbarui data diri serta informasi akun pribadi secara terpusat. | Murid, Pengajar | Tinggi | Sprint 3 |
| **PB-03** | **Manajemen Data Master & Pengguna** | Sebagai Admin, saya dapat mengelola (melihat, memverifikasi, mengubah, dan menghapus) data akun murid, pengajar, serta mata pelajaran yang tersedia. | Admin | Tinggi | Sprint 3 |
| **PB-04** | **Ketersediaan Jadwal Pengajar** | Sebagai Pengajar, saya dapat mengatur dan memperbarui slot waktu ketersediaan mengajar sesuai jadwal luang saya. | Pengajar | Tinggi | Sprint 3 |
| **PB-05** | **Pencarian Profil Pengajar** | Sebagai Murid, saya dapat mencari dan melihat profil pengajar berdasarkan mata pelajaran, keahlian, dan jadwal yang tersedia. | Murid | Tinggi | Sprint 3 |
| *PB-06* | *Pemesanan & Penjadwalan Les* | Sebagai Murid, saya dapat mengajukan pemesanan jadwal les privat one-on-one dengan memilih pengajar, tanggal, sesi waktu, serta lokasi/metode belajar. | Murid | Tinggi | Sprint 4 |
| *PB-07* | *Konfirmasi Jadwal Les* | Sebagai Pengajar, saya dapat menerima atau menolak permintaan jadwal les yang diajukan oleh murid. | Pengajar | Tinggi | Sprint 4 |
| *PB-08* | *Monitoring & Riwayat Sesi Les* | Sebagai Murid, Pengajar, dan Admin, saya dapat memantau status jadwal les yang akan datang maupun riwayat pertemuan yang telah selesai. | Semua Peran | Sedang | Sprint 4 |
| *PB-09* | *Validasi Bentrok Jadwal* | Sebagai sistem, aplikasi dapat mencegah pemesanan pada slot waktu yang sudah terisi agar tidak terjadi jadwal ganda (double booking). | Sistem / Semua | Sedang | Sprint 4 |
| *PB-10* | *Dashboard Ringkasan Operasional* | Sebagai Admin, saya dapat melihat ringkasan statistik operasional (jumlah murid, pengajar aktif, dan total sesi les) pada halaman utama dashboard. | Admin | Rendah | Sprint 4 |
---

## Rincian Product Backlog & Acceptance Criteria

#### **PB-01: Autentikasi & Hak Akses Multi-Peran**
* **Deskripsi:** Sistem menyediakan mekanisme pendaftaran akun baru dan proses masuk (*login*) yang memisahkan tampilan dan hak akses antara **Murid**, **Pengajar**, dan **Admin**.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan antarmuka halaman *Login* dan *Register* beserta validasi input.
  * Pembuatan endpoint API autentikasi pengguna dan pengecekan peran (*role*).
  * Pembatasan rute/halaman (*Route Guard*) agar pengguna hanya dapat mengakses menu sesuai perannya.
* **Acceptance Criteria:**
  * Pengguna baru dapat mendaftar dengan memilih peran (*Murid* atau *Pengajar*) menggunakan email yang belum terdaftar.
  * Pengguna yang berhasil *login* langsung diarahkan ke halaman dashboard masing-masing peran.
  * Sistem menolak akses jika kredensial salah atau jika pengguna mencoba membuka halaman milik peran lain.

#### **PB-02: Manajemen Profil Pengguna**
* **Deskripsi:** Halaman khusus bagi Murid dan Pengajar untuk melihat dan memperbarui informasi identitas diri, kontak, serta preferensi akademik.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan tampilan formulir profil pengguna (nama lengkap, nomor telepon, alamat/domisili, jenjang pendidikan untuk Murid, dan keahlian/bio untuk Pengajar).
  * Pembuatan endpoint `GET` dan `PUT/UPDATE` profil ke database MySQL.
* **Acceptance Criteria:**
  * Data profil pengguna yang sedang *login* tampil secara otomatis pada halaman profil.
  * Perubahan data yang disimpan langsung terbarui di database dan muncul saat halaman dimuat ulang.

#### **PB-03: Manajemen Data Master & Pengguna**
* **Deskripsi:** Panel kontrol bagi Admin untuk mengelola seluruh data pengguna terdaftar serta daftar mata pelajaran yang ditawarkan di aplikasi EduCapy.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan tabel manajemen pengguna (Murid & Pengajar) dilengkapi fitur ubah status dan hapus akun.
  * Pembuatan fitur CRUD (Tambah, Lihat, Ubah, Hapus) data master mata pelajaran.
* **Acceptance Criteria:**
  * Admin dapat melihat daftar lengkap akun Murid dan Pengajar beserta detail informasinya.
  * Admin dapat menambah, mengedit, atau menghapus mata pelajaran sehingga langsung muncul pada opsi pilihan Pengajar dan Murid.

#### **PB-04: Ketersediaan Jadwal Pengajar (*Teacher Availability*)**
* **Deskripsi:** Fitur bagi Pengajar untuk menentukan hari dan jam luang (*time slots*) di mana mereka bersedia menerima permintaan les privat.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan antarmuka pengaturan jadwal mengajar (hari/tanggal, jam mulai, dan jam selesai).
  * Pembuatan logika penyimpanan dan penghapusan slot ketersediaan di database.
* **Acceptance Criteria:**
  * Pengajar dapat menambahkan satu atau lebih slot waktu luang.
  * Slot waktu yang dibuat oleh Pengajar otomatis terbaca oleh sistem saat Murid mencari jadwal les.

#### **PB-05: Pencarian & Detail Profil Pengajar**
* **Deskripsi:** Katalog pengajar yang memungkinkan Murid menelusuri daftar pengajar, memfilter berdasarkan mata pelajaran, dan melihat informasi detail serta jadwal luang pengajar.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan tampilan daftar kartu profil pengajar (*Tutor Cards*) dan kolom pencarian/filter mata pelajaran.
  * Pembuatan halaman/modal detail profil pengajar yang menampilkan biodata, mata pelajaran yang diampu, dan slot waktu tersedia.
* **Acceptance Criteria:**
  * Murid dapat memfilter daftar pengajar berdasarkan nama atau mata pelajaran tertentu.
  * Halaman detail menampilkan informasi pengajar secara akurat beserta daftar slot jadwal luang yang masih aktif.

#### *PB-06: Pemesanan & Penjadwalan Les Privat*
* **Deskripsi:** Fitur utama bagi Murid untuk mengajukan sesi belajar *one-on-one* dengan memilih pengajar, mata pelajaran, tanggal, slot jam yang tersedia, serta metode/lokasi belajar (Online atau Tatap Muka).
* **Pemecahan Tugas (Tasks):**
  * Pembuatan formulir pemesanan sesi les (*Booking Form*) pada profil pengajar.
  * Pembuatan endpoint `POST` untuk menyimpan transaksi pemesanan baru dengan status awal *Menunggu Konfirmasi (Pending)*.
* **Acceptance Criteria:**
  * Murid hanya dapat memilih slot waktu yang disediakan oleh pengajar terkait.
  * Pengajuan pemesanan tersimpan di database dan langsung muncul di daftar permintaan masuk pada dashboard Pengajar.

#### *PB-07: Konfirmasi Jadwal Les oleh Pengajar*
* **Deskripsi:** Mekanisme bagi Pengajar untuk meninjau permintaan les yang masuk dari Murid dan memberikan keputusan (Menerima atau Menolak).
* **Pemecahan Tugas (Tasks):**
  * Pembuatan daftar permintaan pemesanan masuk (*Incoming Requests*) pada dashboard Pengajar.
  * Pembuatan tombol aksi **Terima** dan **Tolak** yang memperbarui status jadwal di database.
* **Acceptance Criteria:**
  * Pengajar dapat melihat detail permintaan (nama murid, mata pelajaran, tanggal, jam, dan catatan/lokasi).
  * Jika diterima, status berubah menjadi *Terkonfirmasi (Confirmed)*; jika ditolak, status berubah menjadi *Ditolak (Rejected)* dan slot waktu kembali terbuka.

#### *PB-08: Monitoring & Riwayat Sesi Les*
* **Deskripsi:** Tampilan terpusat untuk memantau seluruh jadwal les yang akan datang maupun riwayat pertemuan yang telah selesai atau dibatalkan bagi Murid, Pengajar, dan Admin.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan tab/filter status jadwal (*Menunggu*, *Terkonfirmasi*, *Selesai*, *Dibatalkan*).
  * Pembuatan fitur penandaan sesi *Selesai* setelah waktu les berakhir.
* **Acceptance Criteria:**
  * Murid dan Pengajar dapat melihat daftar jadwal pribadi mereka secara *real-time* sesuai perubahan status.
  * Admin dapat memantau keseluruhan transaksi penjadwalan les di seluruh sistem.

#### *PB-09: Validasi Bentrok Jadwal (Anti Double-Booking)*
* **Deskripsi:** Logika validasi di sisi *back-end* dan antarmuka untuk mencegah terjadinya pemesanan ganda pada pengajar, tanggal, dan jam yang sama.
* **Pemecahan Tugas (Tasks):**
  * Penambahan pengecekan ketersediaan slot sebelum menyimpan pesanan baru di server.
  * Penonaktifan/penyembunyian slot waktu pada UI jika slot tersebut sudah dipesan dan terkonfirmasi.
* **Acceptance Criteria:**
  * Sistem menolak pengajuan jadwal apabila pengajar sudah memiliki jadwal terkonfirmasi pada waktu yang sama dan menampilkan pesan peringatan yang jelas.
  * Slot yang sudah terisi tidak dapat dipilih kembali oleh murid lain.

#### *PB-10: Dashboard Ringkasan Operasional Admin*
* **Deskripsi:** Halaman ringkasan (*overview*) khusus Admin yang menyajikan metrik utama aktivitas operasional bimbingan belajar EduCapy.
* **Pemecahan Tugas (Tasks):**
  * Pembuatan query agregasi data dari database (total murid, total pengajar, total mata pelajaran, dan jumlah sesi les berdasarkan status).
  * Pembuatan komponen kartu statistik (*Summary Cards*) pada halaman utama dashboard Admin.
* **Acceptance Criteria:**
  * Angka statistik pada dashboard Admin ditampilkan secara dinamis sesuai data aktual yang tersimpan di database MySQL[cite: 5, 24, 26].