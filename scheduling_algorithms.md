
# Tugas Chapter 05 - Algoritma Scheduling (S10)

##  1. SJF (Shortest Job First) - Tanpa Arrival Time

###  Deskripsi
Algoritma *Shortest Job First* (SJF) tanpa arrival time adalah metode non-preemptive di mana semua proses dianggap tiba bersamaan (AT = 0). Proses dengan burst time terpendek dieksekusi lebih dulu.

###  Contoh Data
| Process | Burst Time |
|--------:|-----------:|
| P1      | 9          |
| P2      | 2          |
| P3      | 5          |
| P4      | 1          |
| P5      | 6          |

###  Langkah Eksekusi
Urutan berdasarkan burst time: P4 → P2 → P3 → P5 → P1  
Hitung CT, TAT, dan WT seperti biasa.

###  Hasil
| Process | BT | CT | TAT | WT |
|--------:|---:|---:|----:|---:|
| P1      | 9  | 23 | 23  | 14 |
| P2      | 2  | 3  | 3   | 1  |
| P3      | 5  | 8  | 8   | 3  |
| P4      | 1  | 1  | 1   | 0  |
| P5      | 6  | 14 | 14  | 8  |

###  Gantt Chart
```
| P4 | P2 |  P3  |  P5  |    P1    |
0    1    3     8     14       23
```

###  Rata-rata
-  Average TAT: 9.8  
-  Average WT: 5.2

---

##  2. SJF (Shortest Job First) - Dengan Arrival Time

###  Deskripsi
SJF dengan arrival time memperhitungkan waktu kedatangan setiap proses. Proses dengan burst time terpendek dari proses yang sudah tiba akan dipilih.

###  Contoh Data
| Process | Arrival Time | Burst Time |
|--------:|-------------:|-----------:|
| P1      | 0            | 6          |
| P2      | 1            | 3          |
| P3      | 2            | 7          |
| P4      | 3            | 1          |
| P5      | 5            | 4          |

###  Langkah Eksekusi
- t=0: P1  
- t=6: P4 (paling kecil)  
- t=7: P2  
- t=10: P5  
- t=14: P3

###  Hasil
| Process | AT | BT | CT | TAT | WT |
|--------:|---:|---:|---:|----:|---:|
| P1      | 0  | 6  | 6  | 6   | 0  |
| P2      | 1  | 3  | 10 | 9   | 6  |
| P3      | 2  | 7  | 21 | 19  | 12 |
| P4      | 3  | 1  | 7  | 4   | 3  |
| P5      | 5  | 4  | 14 | 9   | 5  |

###  Gantt Chart
```
|   P1   | P4 |  P2  |  P5  |    P3    |
0       6    7    10     14       21
```

###  Rata-rata
-  Average TAT: 9.4  
-  Average WT: 5.2

---

##  3. SRTF (Shortest Remaining Time First) - Preemptive

###  Deskripsi
SRTF adalah versi preemptive dari SJF, di mana proses yang sedang berjalan dapat dipotong jika ada proses baru dengan burst time lebih pendek.

###  Contoh Data
| Process | Arrival Time | Burst Time |
|--------:|-------------:|-----------:|
| P1      | 0            | 5          |
| P2      | 2            | 3          |
| P3      | 4            | 6          |
| P4      | 5            | 2          |
| P5      | 6            | 4          |

###  Langkah Eksekusi
- t=0: P1  
- t=2: P2 → preempt P1  
- t=5: P2 selesai → P4  
- t=7: P4 selesai → P1  
- t=10: P1 selesai → P5  
- t=14: P5 selesai → P3  
- t=20: P3 selesai

###  Hasil
| Process | AT | BT | CT | TAT | WT |
|--------:|---:|---:|---:|----:|---:|
| P1      | 0  | 5  | 10 | 10  | 5  |
| P2      | 2  | 3  | 5  | 3   | 0  |
| P3      | 4  | 6  | 20 | 16  | 10 |
| P4      | 5  | 2  | 7  | 2   | 0  |
| P5      | 6  | 4  | 14 | 8   | 4  |

###  Gantt Chart
```
|P1| P2 |P4|  P1  |  P5  |     P3     |
0  2    5   7     10    14         20
```

###  Rata-rata
-  Average TAT: 7.8  
-  Average WT: 3.8

---

##  Perbandingan Algoritma

| Algorithm         | Avg TAT | Avg WT |
|------------------|--------:|-------:|
| SJF (Tanpa AT)   | 9.8     | 5.2    |
| SJF (Dengan AT)  | 9.4     | 5.2    |
| SRTF (Preemptive)| 7.8     | 3.8    |

###  Kesimpulan:
- **SJF tanpa AT** tetap efisien untuk beban seragam.
- **SJF dengan AT** cocok untuk sistem nyata dengan waktu kedatangan berbeda.
- **SRTF** memberi efisiensi waktu tunggu, tetapi perlu pengelolaan proses preemptive.
