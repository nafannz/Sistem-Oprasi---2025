1. Layout Memori untuk Sistem Multiprogrammed
- Memori dibagi menjadi beberapa bagian, dengan sistem operasi di bagian atas dan beberapa proses pengguna di bawahnya.
- Pendekatan ini memungkinkan eksekusi beberapa proses secara bersamaan.

2. Mode Dual dan Multimode
- Sistem operasi menggunakan dual-mode untuk melindungi dirinya sendiri dan komponen lainnya.
- Ada mode pengguna dan mode kernel, dengan bit mode yang mengidentifikasi mode eksekusi.
- Instruksi tertentu dianggap privileged dan hanya dapat dijalankan dalam mode kernel.
- Beberapa CPU modern mendukung multi-mode, seperti virtual machine manager (VMM) untuk menangani mesin virtual.

3. Transisi dari Mode Pengguna ke Mode Kernel
- Timer digunakan untuk mencegah proses berjalan tanpa batas atau menghabiskan sumber daya.
- OS mengatur timer yang akan menginterupsi sistem setelah periode waktu tertentu.
- Saat timer mencapai nol, OS mengambil kembali kontrol untuk memastikan sistem tetap berjalan dengan efisien.

4. Manajemen Proses
- Proses adalah program yang sedang dieksekusi, berbeda dari program yang masih pasif.
- Proses membutuhkan sumber daya seperti CPU, memori, I/O, dan data inisialisasi.
- Setelah proses selesai, sumber daya harus dibebaskan kembali ke sistem.
- Proses single-threaded memiliki satu program counter untuk melacak instruksi yang sedang dieksekusi.
- Proses multi-threaded memiliki satu program counter per thread, memungkinkan eksekusi paralel.
- Sistem sering kali memiliki banyak proses yang berjalan bersamaan menggunakan CPU secara multiplexing.

5. Aktivitas Manajemen Proses
- OS bertanggung jawab atas:
  - Membuat dan menghapus proses.
  - Menunda dan melanjutkan proses.
  - Sinkronisasi proses.
  - Komunikasi antar proses.
  - Menangani deadlock.

6. Manajemen Memori
- Semua instruksi dan data program yang sedang berjalan harus berada di memori utama.
- OS mengatur bagian mana dari memori yang digunakan dan oleh siapa.
- Manajemen memori meliputi:
  - Menentukan data mana yang perlu dipindahkan masuk/keluar dari memori.
  - Mengalokasikan dan membebaskan ruang memori.

7. Manajemen File-System
- OS memberikan tampilan logis untuk penyimpanan data melalui file.
- Setiap media penyimpanan dikendalikan oleh perangkat tertentu (HDD, SSD, Tape Drive).
- OS bertanggung jawab atas:
  - Pembuatan dan penghapusan file serta direktori.
  - Akses kontrol terhadap file.
  - Pemetaan file ke penyimpanan sekunder.
  - Pencadangan file ke media penyimpanan yang lebih stabil.

8. Manajemen Penyimpanan Massal
- Penyimpanan massal (disk) digunakan untuk menyimpan data yang tidak cukup di memori utama.
- Manajemen penyimpanan sangat penting untuk kecepatan dan efisiensi sistem.
- OS melakukan berbagai tugas, seperti:
  - Mounting dan unmounting perangkat penyimpanan.
  - Manajemen ruang kosong.
  - Alokasi penyimpanan dan penjadwalan disk.
  - Partisi dan perlindungan data.
- Penyimpanan tambahan seperti **optical storage dan magnetic tape** juga harus dikelola oleh OS atau aplikasi.
