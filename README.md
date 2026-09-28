# **Sistem Manajemen Barbershop**
# **UTS Pemrograman Berorientasi Objek (PBO)**

Nama: Aura Putri Anandita Syarif NIM: 2509116094 Program Studi: Sistem Informasi (C)

============================================================================

## **Deskripsi Singkat Program**

Program ini membantu mengelola kegiatan sehari-hari di sebuah barbershop: mencatat data pelanggan dan barber, menampilkan daftar layanan, mengatur antrean pelayanan, sampai pembayaran.

Ada dua jenis pelanggan (reguler dan member yang dapat diskon) serta dua jenis barber (biasa dan senior yang kapasitasnya lebih besar dengan biaya tambahan). Kedua jenis ini mewarisi data dan perilaku dasar yang sama dari satu class induk, lalu masing-masing menambahkan aturannya sendiri.

Program dibagi menjadi tiga bagian:

1. Model (Orang, Pelanggan, PelangganMember, Barber, BarberSenior, Layanan, Pelayanan) - menyimpan data dan aturan setiap objek.
2. Controller (BarbershopController) - menyimpan seluruh data program (ArrayList) dan semua logika bisnis (tambah, ubah, hapus, hitung diskon, hitung biaya, ubah status).
3. View (Main) - menu dan tampilan di layar, memanggil Controller untuk memproses data.

Data awal (dummy) sudah diisi otomatis saat program dijalankan, jadi menu "tampilkan" bisa langsung dicoba tanpa perlu input data dulu.

### ***Elemen Wajib yang Diterapkan***

Inheritance (2 jalur pewarisan):

- Orang (superclass) → Pelanggan → PelangganMember
- Orang (superclass) → Barber → BarberSenior

Orang menyimpan data yang sama untuk semua orang (ID dan nama). Pelanggan dan Barber menambahkan data masing-masing, lalu PelangganMember dan BarberSenior menyesuaikan sebagian perilakunya.

- Polymorphism - Overriding: Method getPeran(), getKapasitas(), getBiayaTambahan(), dan getPersenDiskon() ditulis ulang di sub-class supaya hasilnya berbeda. Contoh: Barber.getKapasitas() mengembalikan 5, sedangkan BarberSenior.getKapasitas() (override) mengembalikan 7.

- Polymorphism - Overloading: BarbershopController punya dua method dengan nama sama tapi parameter berbeda, Versi pertama otomatis menambahkan pelanggan reguler, versi kedua bisa memilih jenisnya lewat parameter tambahan. Pola yang sama juga ada di tambahBarber(...).

- Condition (if-else): Dipakai di hampir semua validasi dan pengecekan status, misalnya menentukan status barber (Tersedia, Melayani, Penuh, Tidak Tersedia) berdasarkan jumlah pelanggan aktif, atau mengecek apakah ID sudah dipakai sebelum data baru ditambahkan.

- Looping: for dipakai untuk menelusuri ArrayList (mencari data, menampilkan daftar, menghitung ringkasan), dan while dipakai untuk menu yang terus muncul sampai pengguna memilih kembali atau keluar, serta untuk mengulang pembacaan input sampai valid.

============================================================================

## **Alur Program**

Saat dijalankan, program menampilkan:

### ***menu utama***

<img width="320" height="220" alt="image" src="https://github.com/user-attachments/assets/e2cbc760-fb66-4d47-8214-7c6d05412706" />

Cara menggunakannya:

- Ketik angka menu, lalu tekan Enter.
- Kelola Pelanggan / Kelola Barber membuka sub-menu untuk menambah, menampilkan, mengubah, atau menghapus data. Saat menambah, program akan menanyakan jenisnya (reguler/member atau biasa/senior).
- Pelayanan Pelanggan adalah alur utama: pilih pelanggan, pilih barber yang tersedia, pilih layanan, lalu sistem otomatis membuat ID pelayanan dan nomor antrean serta menghitung totalnya (harga layanan + biaya tambahan barber senior jika ada, dikurangi diskon jika pelanggan member).
- Status pelayanan berubah dari Menunggu → Diproses → Selesai, lalu bisa dibayar dengan Tunai atau QRIS, mengubah status pembayaran dari Belum Bayar menjadi Lunas.
- Sepanjang program, kalau pengguna mengetik data yang salah (misalnya ID kosong atau nomor HP tidak valid), program akan menampilkan pesan kesalahan dan meminta input ulang, bukan langsung berhenti.
- Ketik 0 di menu utama untuk keluar.

### ***Kelola Pelanggan***

<img width="626" height="576" alt="image" src="https://github.com/user-attachments/assets/4e3ae5bb-ff19-4b91-a220-65bcd266cbd3" />


Tampilan pertama saat program dijalankan. Pengguna memilih menu kelola pelanggan lalu ke menu tambah ppelanggan, untuk menambahkan daftar pelanggan di Barbershop.

### ***Kelola Barber***

<img width="710" height="512" alt="image" src="https://github.com/user-attachments/assets/639b1fcb-4c23-4304-9ad2-1f5f456e38d8" />

Di menu kedua ini pengguna memilih menu kelola barber lalu ke menu ubah barber, untuk mengubah nama, no. hp, dan berapa lama pengalamannya.

### ***Lihat Daftar Layanan***

<img width="503" height="335" alt="image" src="https://github.com/user-attachments/assets/2c9ca7cb-7e78-438e-bd43-7421b9fe57bd" />

Di menu ketiga pengguna memilih menu lihat daftar layanan, untuk melihat daftar layanan yang tersedia di Barbershop.

### ***Pelayanan Pelanggan***

<img width="848" height="761" alt="image" src="https://github.com/user-attachments/assets/d9952caf-7c79-4543-8d27-0ebd69c6d3a1" />

Di menu ke empat pengguna memilih menu pelayanan pelanggan lalu ke menu tampilkan semua layanan, untuk melihat pelayanan yang sedang berlangsung dan yang sudah selesai.

### ***Cek Status Pelanggan***

<img width="491" height="337" alt="image" src="https://github.com/user-attachments/assets/e70fd973-4ce0-4e8a-bb32-947fa97297c5" />

Di menu ke lima pengguna memilih menu cek status pelanggan lalu memasukkan id pelanggan untuk melihat pelayanan yang sedang didapatkan pelanggan.

### ***Lihat Status Barber***

<img width="880" height="642" alt="image" src="https://github.com/user-attachments/assets/a6a52004-7804-40e9-bbbf-87a3b8fe9de6" />

DI menu ke enam pengguna memilih menu lihat status barber untuk melihat daftar yang sedang melayani dan yang sedang tersedia.

### ***Ringkasan Barbershop***

<img width="742" height="535" alt="image" src="https://github.com/user-attachments/assets/3a9d3bdc-7881-45e3-8a6b-c9477c968b54" />

Di menu ke enam pengguna memilih menu ringkasan barbershop, untuk melihat total pelanggan, total barber, total layanan, status barber, status pelayanan, dan pendapatan Barbershop.

### ***Keluar***

<img width="626" height="267" alt="image" src="https://github.com/user-attachments/assets/2d98ea1d-bb95-4f9c-bbd9-d00c33bbe0e9" />

Yang terakhir pengguna memilih menu keluar untuk keluar dari menu utama Barbershop.

============================================================================

## **Penjelasan dan Contoh data pelanggan (inheritance & polymorphism)**

### ***Inheritance***

Terdapat satu superclass abstract, Orang, yang diturunkan menjadi dua cabang, dan masing-masing cabang diturunkan sekali lagi:
- Orang menyimpan atribut yang dimiliki semua orang di sistem ini: ID dan nama. Method getPeran() dibuat abstract, sehingga setiap turunannya wajib mendefinisikan perannya sendiri.
- Pelanggan adalah pelanggan biasa, tidak mendapat diskon.
- PelangganMember meng-override method diskon menjadi 10%.
- Barber adalah barber standar dengan kapasitas 5 antrean dan tanpa biaya tambahan.
- BarberSenior meng-override kapasitasnya menjadi 7 antrean, tapi menambahkan biaya jasa Rp10.000.

### ***Polymorphism***

Diterapkan dalam dua bentuk:

- Method overriding 
getPeran(), getPersenDiskon(), getKapasitas(), dan getBiayaTambahan() didefinisikan ulang di tiap subclass dengan hasil yang berbeda-beda (lihat Model/Pelanggan.java, Model/PelangganMember.java, Model/Barber.java, dan Model/BarberSenior.java).
-Method overloading
Di Controller/BarbershopController.java, method tambahPelanggan() dan tambahBarber() masing-masing punya dua versi: versi singkat yang otomatis membuat data reguler/biasa, dan versi lengkap dengan parameter boolean tambahan untuk memilih jenis member/senior.

### ***Salah Satu Contohnya***

<img width="452" height="447" alt="image" src="https://github.com/user-attachments/assets/22256cac-e2e3-4126-9ec1-d9bf0b4c027b" />

Menampilkan data pelanggan reguler dan member. Meskipun ditampilkan lewat method tampilkanData() yang sama, hasilnya berbeda: pelanggan member menunjukkan diskon 10%, pelanggan reguler menunjukkan diskon 0%. Ini contoh polymorphism.

============================================================================

## **Hasil Looping dan Pengelompokkan Data**

<img width="478" height="365" alt="image" src="https://github.com/user-attachments/assets/ba19fdc1-7723-4208-8fa8-b2056f446ad5" />

Menunjukkan hasil looping dan pengelompokan data: jumlah pelanggan per jenis, status barber, status pelayanan, dan total pendapatan.

============================================================================
















