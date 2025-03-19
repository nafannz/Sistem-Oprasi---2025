Resume Appendix-A
1. Pendahuluan
Sistem operasi (OS) adalah perangkat lunak yang bertindak sebagai perantara antara pengguna dan perangkat keras komputer. Fungsi utama OS meliputi:
•	Manajemen sumber daya komputer (CPU, memori, penyimpanan, perangkat I/O)
•	Menyediakan layanan untuk program aplikasi
•	Mengontrol dan mengelola eksekusi proses
OS berkembang dari sistem batch hingga sistem modern yang mendukung multi-programming, time-sharing, dan komputasi terdistribusi. Sistem operasi memungkinkan efisiensi dalam penggunaan perangkat keras dan meningkatkan pengalaman pengguna.
2. Struktur Sistem Operasi
OS terdiri dari beberapa komponen utama:
•	Kernel: Bagian inti dari OS yang menangani manajemen memori, manajemen proses, sistem file, dan komunikasi perangkat.
•	Sistem Panggilan (System Calls): Antarmuka antara aplikasi dan OS yang memungkinkan program meminta layanan dari OS.
•	User Interface: Bisa berupa Command-Line Interface (CLI) atau Graphical User Interface (GUI).
•	Modular OS: Beberapa OS menggunakan arsitektur modular untuk meningkatkan fleksibilitas dan keamanan.
•	Mikrokernel: OS modern mengadopsi pendekatan mikrokernel untuk meningkatkan stabilitas dan mengurangi risiko crash.
3. Manajemen Proses
•	Proses: Program dalam eksekusi yang memiliki status (new, ready, running, waiting, terminated).
•	Scheduling: OS menggunakan algoritma penjadwalan seperti FCFS, SJF, Round Robin, dan Multilevel Queue untuk mengelola eksekusi proses.
•	Komunikasi Antar-Proses (IPC): Digunakan untuk berbagi data antar-proses melalui mekanisme seperti message passing dan shared memory.
•	Threads: OS modern mendukung multi-threading untuk meningkatkan efisiensi penggunaan CPU.
•	Deadlock: Kondisi di mana dua atau lebih proses saling menunggu sumber daya yang terkunci. OS menerapkan teknik seperti pencegahan dan deteksi deadlock.
4. Manajemen Memori
•	Alokasi Memori: Bisa bersifat kontigu atau non-kontigu (paging dan segmentation).
•	Virtual Memory: Memungkinkan eksekusi program yang lebih besar dari memori fisik dengan menggunakan teknik seperti demand paging dan swapping.
•	Fragmentasi: Masalah dalam alokasi memori yang dapat dikurangi dengan teknik seperti compaction dan paging.
•	Memori Cache: Digunakan untuk meningkatkan kecepatan akses data.
5. Sistem Penyimpanan
•	Sistem File: Struktur yang digunakan untuk mengelola data dalam penyimpanan sekunder. OS menyediakan metode akses seperti sequential dan direct access.
•	Manajemen Disk: OS menangani alokasi blok, penjadwalan disk, dan optimasi performa penyimpanan.
•	Journaling File System: Digunakan untuk mencegah kehilangan data akibat kegagalan sistem.
•	RAID (Redundant Array of Independent Disks): Teknologi untuk meningkatkan keandalan penyimpanan data.
6. Manajemen I/O
•	Driver Perangkat: Perangkat lunak yang menghubungkan OS dengan perangkat keras.
•	Buffering dan Caching: Teknik untuk meningkatkan efisiensi akses data dari perangkat I/O.
•	DMA (Direct Memory Access): Teknologi untuk meningkatkan efisiensi transfer data antar-perangkat I/O dan memori utama.
7. Keamanan dan Proteksi
•	Keamanan: Melindungi sistem dari ancaman eksternal seperti malware dan serangan cyber.
•	Proteksi: Mekanisme kontrol akses yang memastikan hanya pengguna yang berwenang dapat mengakses sumber daya tertentu.
•	Enkripsi Data: Digunakan untuk melindungi informasi sensitif dalam sistem penyimpanan dan komunikasi.
•	Autentikasi Pengguna: Mencakup teknik seperti password, biometrik, dan two-factor authentication.
8. Sistem Terdistribusi
•	Konsep: Sistem yang terdiri dari beberapa komputer yang berkomunikasi melalui jaringan.
•	Sinkronisasi: Memastikan operasi pada sistem terdistribusi berjalan secara koheren.
•	Sistem Berbasis Cloud: Model penyimpanan dan komputasi berbasis internet.
•	Load Balancing: Digunakan untuk mendistribusikan beban kerja antar-server dalam sistem terdistribusi.
9. Sistem Operasi Khusus
•	Sistem Waktu Nyata (Real-Time OS): Digunakan pada aplikasi dengan batas waktu ketat seperti kendaraan otomatis dan sistem kendali industri.
•	Sistem Mobile: OS yang dirancang untuk perangkat mobile seperti Android dan iOS.
•	Sistem Embedded: OS yang digunakan pada perangkat tertanam seperti mesin industri dan peralatan medis.
10. Tren Masa Depan Sistem Operasi
•	Virtualisasi: Penggunaan hypervisor untuk menjalankan beberapa OS dalam satu mesin fisik.
•	Containerization: Teknologi seperti Docker untuk menjalankan aplikasi dalam lingkungan yang terisolasi.
•	Keamanan Berbasis AI: Implementasi kecerdasan buatan untuk deteksi ancaman dan mitigasi serangan keamanan.
•	Quantum Computing: Tantangan dan peluang dalam pengembangan OS untuk komputer kuantum.
