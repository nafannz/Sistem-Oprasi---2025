Laporan Praktikum Sistem Oprasi

Image

Dosen Pengampu : Dr Ferry Astika Saputra ST, M.Sc

Oleh : Naf’an Nashohu Zayyan 3124521008 D3 IT A

Politeknik Elektronika Negeri Surabaya (PENS) LA 2025

Soal nomor 5.17
Process	Burst Time	Priority
P₁      5	          4
P₂	    3	          1
P₃	    1	          2
P₄	    7	          2
P₅	    4	          3

Semua proses tiba pada waktu 0.

a. Gantt Charts untuk keempat algoritma:

1. FCFS
Urutan berdasarkan kedatangan: P₁, P₂, P₃, P₄, P₅
Gantt Chart:
| P1 | P2 | P3 | P4 | P5 |
0    5    8    9   16   20

2. SJF (Shortest Job First)
Urutan berdasarkan burst time: P₃ (1), P₂ (3), P₅ (4), P₁ (5), P₄ (7)
Gantt Chart:
| P3 | P2 | P5 | P1 | P4 |
0    1    4    8   13   20

3. Non-Preemptive Priority
Urutan berdasarkan prioritas (descending): P₁ (4), P₅ (3), P₃ (2), P₄ (2), P₂ (1)
Jika prioritas sama, ambil yang datang lebih dulu.
Gantt Chart:
| P1 | P5 | P3 | P4 | P2 |
0    5    9   10   17   20

4. RR (Quantum = 2)
Initial Order: P₁, P₂, P₃, P₄, P₅
Kita eksekusi secara bergantian sebanyak 2 ms.
Gantt Chart:
|P1|P2|P3|P4|P5|P1|P2|P4|P5|P1|P4|P4|
0  2  4  5  7  9 11 13 15 17 19 20

b. Turnaround Time (TAT) = Completion Time - Arrival Time
Arrival Time = 0 untuk semua

FCFS:
P1: 5, P2: 8, P3: 9, P4: 16, P5: 20
SJF:
P3: 1, P2: 4, P5: 8, P1: 13, P4: 20
Priority:
P1: 5, P5: 9, P3: 10, P4: 17, P2: 20
RR:
P1: 19, P2: 11, P3: 5, P4: 20, P5: 17

c. Waiting Time (WT) = TAT - Burst Time
FCFS:
P1: 5 - 5 = 0
P2: 8 - 3 = 5
P3: 9 - 1 = 8
P4: 16 - 7 = 9
P5: 20 - 4 = 16

SJF:
P3: 1 - 1 = 0
P2: 4 - 3 = 1
P5: 8 - 4 = 4
P1: 13 - 5 = 8
P4: 20 - 7 = 13

Priority:
P1: 5 - 5 = 0
P5: 9 - 4 = 5
P3: 10 - 1 = 9
P4: 17 - 7 = 10
P2: 20 - 3 = 17

RR:
P1: 19 - 5 = 14
P2: 11 - 3 = 8
P3: 5 - 1 = 4
P4: 20 - 7 = 13
P5: 17 - 4 = 13

d. Minimum Average Waiting Time
Hitung rata-rata waiting time:
FCFS: (0+5+8+9+16)/5 = 7.6
SJF: (0+1+4+8+13)/5 = 5.2
Priority: (0+5+9+10+17)/5 = 8.2
RR: (14+8+4+13+13)/5 = 10.4
Jawaban: SJF memberikan rata-rata waiting time minimum.


Soal nomor 5.18
Process	Priority	Burst	Arrival
P₁	    8	        15	  0
P₂	    3	        20	  0
P₃	    4 	      20	  20
P₄	    4	        20	  25
P₅	    5	        5	    45
P₆	    5	        15	  55

a. Gantt Chart Construction :

t = 0: P₁(8) dan P₂(3) tersedia → jalankan P₁ (priority 8 lebih tinggi)
P₁ burst = 15 → dijalankan hingga selesai (karena tidak ada proses prioritas lebih tinggi masuk)
css
[0 - 15]  P₁ (selesai)

t = 15: P₂ masih ada → jalankan P₂ (priority 3)
less
[15 - 20]  P₂ (sisa: 15)

t = 20: P₃ datang (priority 4) → lebih tinggi dari P₂ → preempt P₂
less
[20 - 30]  P₃ (quantum 10, sisa: 10)

t = 25: P₄ datang (priority 4) → sama dengan P₃ → masuk antrean RR

t = 30 - 40: P₄ giliran (priority 4, quantum 10, sisa: 10)
css
[30 - 40]  P₄

t = 40 - 45: P₃ giliran lagi (sisa: 10)
css
[40 - 45]  P₃ (selesai)

t = 45: P₅ datang (priority 5) → lebih tinggi dari P₄ → preempt P₄
css
[45 - 50]  P₅ (selesai)

t = 50 - 55: P₄ kembali (sisa: 10)
css
[50 - 55]  P₄ (selesai)

t = 55: P₆ datang (priority 5)
Sisa hanya P₂ dan P₆, tapi P₆ (priority 5) > P₂ (priority 3)
less
[55 - 65]  P₆ (quantum 10, sisa: 5)

t = 65 - 70: P₆ selesai (sisa 5)
css
[65 - 70]  P₆ (selesai)

t = 70 - 80: P₂ kembali (sisa: 15 → 10)
css
[70 - 80]  P₂

t = 80 - 85: P₂ selesai (sisa: 5)
css
[80 - 85]  P₂ (selesai)

Final Gantt Chart
less
| P₁ | P₂ | P₃ | P₄ | P₃ | P₅ | P₄ | P₆ | P₆ | P₂ | P₂ |
0   15   20   30   40   45   50   55   65   70   80   85

b. Turnaround Time (TAT) = Completion - Arrival
Process	Arrival	Completion	Turnaround
P₁	    0	      15	        15
P₂	    0	      85	        85
P₃	    20	    45	        25
P₄	    25	    55	        30
P₅	    45	    50	        5  
P₆	    55	    70	        15

c. Waiting Time (WT) = Turnaround - Burst
Process	Turnaround	Burst	Waiting
P₁	    15	        15	  0
P₂	    85	        20	  65
P₃	    25	        20	  5
P₄	    30	        20	  10
P₅	    5	          5	    0
P₆	    15	        15	  0

Jawaban Akhir:
a. Gantt Chart:
css
[0-15] P₁ → [15-20] P₂ → [20-30] P₃ → [30-40] P₄ → [40-45] P₃ → [45-50] P₅ → [50-55] P₄ → [55-65] P₆ → [65-70] P₆ → [70-80] P₂ → [80-85] P₂

b. Turnaround Time:
P₁: 15
P₂: 85
P₃: 25
P₄: 30
P₅: 5
P₆: 15

c. Waiting Time:
P₁: 0
P₂: 65
P₃: 5
P₄: 10
P₅: 0
P₆: 0



