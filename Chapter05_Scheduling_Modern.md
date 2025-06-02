
# 💻 Tugas Chapter 05 - Algoritma Scheduling (S10)

## 📌 1. SJF (Shortest Job First) - Tanpa Arrival Time

### 🧠 Deskripsi
Algoritma *Shortest Job First* (SJF) tanpa arrival time adalah metode non-preemptive di mana semua proses dianggap tiba bersamaan (AT = 0). Proses dengan burst time terpendek dieksekusi lebih dulu.

### 📊 Contoh Data
| Process | Burst Time |
|--------:|-----------:|
| P1      | 6          |
| P2      | 8          |
| P3      | 7          |
| P4      | 3          |
| P5      | 4          |

### ✅ Langkah Eksekusi
Urutan berdasarkan burst time: P4 → P5 → P1 → P3 → P2  
Hitung CT, TAT, dan WT seperti biasa.

### 🧾 Hasil
| Process | BT | CT | TAT | WT |
|--------:|---:|---:|----:|---:|
| P1      | 6  | 13 | 13  | 7  |
| P2      | 8  | 28 | 28  | 20 |
| P3      | 7  | 20 | 20  | 13 |
| P4      | 3  | 3  | 3   | 0  |
| P5      | 4  | 7  | 7   | 3  |

### 📈 Gantt Chart
```
| P4 | P5 |  P1  |  P3  |   P2   |
0    3    7     13     20      28
```

### 📉 Rata-rata
- ⏱ Average TAT: 14.2  
- ⌛ Average WT: 8.6

---

## 📌 2. SJF (Shortest Job First) - Dengan Arrival Time

### 🧠 Deskripsi
SJF dengan arrival time memperhitungkan waktu kedatangan setiap proses. Proses dengan burst time terpendek dari proses yang sudah tiba akan dipilih.

### 📊 Contoh Data
| Process | Arrival Time | Burst Time |
|--------:|-------------:|-----------:|
| P1      | 0            | 7          |
| P2      | 2            | 4          |
| P3      | 4            | 1          |
| P4      | 5            | 4          |
| P5      | 6            | 3          |

### ✅ Langkah Eksekusi
- t=0: P1 →  
- t=7: P3 →  
- t=8: P5 →  
- t=11: P2 →  
- t=15: P4

### 🧾 Hasil
| Process | AT | BT | CT | TAT | WT |
|--------:|---:|---:|---:|----:|---:|
| P1      | 0  | 7  | 7  | 7   | 0  |
| P2      | 2  | 4  | 15 | 13  | 9  |
| P3      | 4  | 1  | 8  | 4   | 3  |
| P4      | 5  | 4  | 19 | 14  | 10 |
| P5      | 6  | 3  | 11 | 5   | 2  |

### 📈 Gantt Chart
```
|   P1   | P3 | P5 |  P2  |  P4  |
0       7   8   11    15    19
```

### 📉 Rata-rata
- ⏱ Average TAT: 8.6  
- ⌛ Average WT: 4.8

---

## 📌 3. SRTF (Shortest Remaining Time First) - Preemptive

### 🧠 Deskripsi
SRTF adalah versi preemptive dari SJF, di mana proses yang sedang berjalan dapat dipotong jika ada proses baru dengan burst time lebih pendek.

### 📊 Contoh Data
| Process | Arrival Time | Burst Time |
|--------:|-------------:|-----------:|
| P1      | 0            | 8          |
| P2      | 1            | 4          |
| P3      | 2            | 9          |
| P4      | 3            | 5          |
| P5      | 4            | 2          |

### ✅ Langkah Eksekusi
- t=0: P1  
- t=1: P2 → preempt P1  
- t=5: P2 selesai → jalankan P5  
- t=7: P5 selesai → P4  
- t=12: P4 selesai → P1  
- t=19: P1 selesai → P3  
- t=28: Selesai

### 🧾 Hasil
| Process | AT | BT | CT | TAT | WT |
|--------:|---:|---:|---:|----:|---:|
| P1      | 0  | 8  | 19 | 19  | 11 |
| P2      | 1  | 4  | 5  | 4   | 0  |
| P3      | 2  | 9  | 28 | 26  | 17 |
| P4      | 3  | 5  | 12 | 9   | 4  |
| P5      | 4  | 2  | 7  | 3   | 1  |

### 📈 Gantt Chart
```
|P1|  P2  |P5|  P4  |   P1   |     P3     |
0  1     5  7     12      19           28
```

### 📉 Rata-rata
- ⏱ Average TAT: 12.2  
- ⌛ Average WT: 6.6

---

## 📚 Perbandingan Algoritma

| Algorithm         | Avg TAT | Avg WT |
|------------------|--------:|-------:|
| SJF (Tanpa AT)   | 14.2    | 8.6    |
| SJF (Dengan AT)  | 8.6     | 4.8    |
| SRTF (Preemptive)| 12.2    | 6.6    |

### 💬 Kesimpulan:
- **SJF tanpa AT** cocok untuk proses yang datang bersamaan.
- **SJF dengan AT** lebih realistis namun bisa tidak optimal.
- **SRTF** ideal untuk respon cepat, namun berisiko starving.
