# MyKebiasaan — prototipe web app

## Isi folder
- `index.html`: aplikasi utama (UI + logika).
- `manifest.json`: metadata instalasi web app.
- `sw.js`: cache untuk mode offline setelah pertama kali dibuka secara online.
- `icon.svg`: ikon aplikasi.

## Fitur yang sudah ada
- Tambah/edit/hapus kebiasaan rutin dan fleksibel.
- Pilih hari aktif dan waktu.
- Checklist dan riwayat per tanggal.
- Statistik harian, mingguan, bulanan, tahunan serta kalender.
- Tema, color wheel, slider kecerahan/kepekatan dan mode gelap.
- Refleksi bebas dengan riwayat.
- Ekspor/impor cadangan JSON.
- Motivasi harian dan permintaan izin notifikasi.

## Penting tentang penyimpanan dan notifikasi
Data disimpan di `localStorage` pada browser/perangkat. Jangan menghapus data situs jika ingin mempertahankan data. Ekspor cadangan secara berkala.
Service worker dan mode offline perlu aplikasi diakses dari HTTPS (atau localhost). Membuka file HTML langsung (`file://`) tidak mengaktifkan semua kemampuan PWA.
Pengingat di prototipe ini diperiksa ketika halaman sedang berjalan. Browser/Android bisa menangguhkan tab di latar belakang, jadi pengingat terjadwal yang andal saat aplikasi tertutup memerlukan pembungkus native Android dengan penjadwal alarm/notifikasi. Notifikasi motivasi terjadwal harian juga belum berjalan otomatis ketika aplikasi benar-benar ditutup.
Untuk versi APK penuh, gunakan proyek WebView/native yang menambahkan penyimpanan dan penjadwal notifikasi Android; jangan anggap versi web ini sudah menyediakan alarm latar belakang yang andal.

## Cara mencoba dari HP Android
1. Ekstrak ZIP.
2. Untuk tes sederhana, buka `index.html` lewat editor HTML/browser yang mendukung file lokal. Sebagian fitur seperti offline/PWA/notifikasi mungkin tidak aktif.
3. Untuk memasang sebagai web app (bukan APK), unggah isi folder ke layanan hosting HTTPS yang kamu kendalikan, lalu buka alamatnya di Chrome Android. Pilih menu ⋮ > Tambahkan ke layar utama / Instal aplikasi. PWA perlu dibuka sekali saat online untuk cache aset.
4. Data browser dan data APK/WebView biasanya terpisah; data tidak otomatis berpindah antar instalasi.

## Mengubah menjadi APK
Dibutuhkan alat pembungkus Android/WebView atau layanan build APK berbasis web. Masukkan URL HTTPS aplikasi sebagai halaman awal, set nama `MyKebiasaan`, ikon `icon.svg`, dan aktifkan penyimpanan lokal/WebView DOM storage bila opsinya ada. Setelah APK dibuat, unduh dan instal dengan mengizinkan instalasi dari sumber tersebut hanya untuk layanan yang kamu percaya.
Perhatian: pembungkus URL saja tetap membutuhkan koneksi untuk pemuatan pertama dan mungkin tidak menyediakan offline penuh atau alarm latar belakang. Untuk APK offline dan notifikasi yang dapat diandalkan, proyek Android native perlu menyertakan aset lokal, izin notifikasi, serta penjadwal alarm. Selalu uji sebelum mengandalkan pengingat penting.

## Keterbatasan prototipe awal
- Ini adalah prototipe pertama, belum diaudit untuk semua ukuran layar/perangkat.
- Pilihan warna disimpan; roda memilih hue dan slider mengubah warna pratinjau.
- Kutipan motivasi sebagian merupakan kalimat buatan aplikasi/parafrasa; atribusi ditandai untuk menghindari klaim kutipan literal yang tidak terverifikasi.
- Statistik dihitung berdasarkan jadwal yang tersimpan dan riwayat checklist.
