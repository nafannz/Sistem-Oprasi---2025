Laporan Praktikum Sistem Oprasi

![Image](https://github.com/user-attachments/assets/838b068c-4d85-452a-aca6-352d279fbd3f)

Dosen Pengampu : Dr Ferry Astika Saputra ST, M.Sc

Oleh : Naf’an Nashohu Zayyan 3124521008 D3 IT A

Politeknik Elektronika Negeri Surabaya (PENS) LA 2025


Analisa code program algrotima schedulling

code 1 SJF without arrival time (non-preemptive) :
#include<stdio.h>
struct proc
{
    int no,bt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    struct proc p[10],tmp;
    float avgtat=0,avgwt=0;
    int n,ct=0;
    printf("<--SJF Scheduling Algorithm Without Arrival Time (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].bt>p[j+1].bt)
            {
				tmp=p[j];
				p[j]=p[j+1];
				p[j+1]=tmp;
            }
    printf("\nProcessNo\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        ct+=p[i].bt;
		p[i].ct=p[i].tat=ct;
		avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}

Analaisa :
Alur Program
Input jumlah proses (n)
Input burst time untuk tiap proses
Urutkan proses berdasarkan burst time menggunakan bubble sort
Hitung untuk setiap proses:
CT (Completion Time)
TAT (Turn Around Time) = CT
WT (Waiting Time) = TAT - Burst Time
Cetak hasil dan hitung rata-rata TAT dan WT

input :
P1 = 6
P2 = 8
P3 = 7
P4 = 3

output :
P4 = 3
P1 = 6
P3 = 7
P2 = 8

Perhitungan SJF
Process	BT	CT	TAT	WT
P4	    3	  3	  3	  0
P1	    6	  9	  9	  3
P3	    7  	16	16	9
P2	    8  	24	24	16

Chart (SJF Scheduling Chart)
|  P4  |   P1   |   P3   |   P2   |
0      3        9        16       24

Kesimpulan
- SJF sangat optimal jika semua proses sudah diketahui burst time-nya dan datang bersamaan.
- Memberikan rata-rata waktu tunggu (waiting time) yang lebih kecil dibanding algoritma lainnya seperti FCFS.
- Namun, tidak adil jika arrival time diperhitungkan (bisa menyebabkan starvation terhadap proses dengan burst time besar).


Code 2 SJF with arrival time (non-prremptive) :

#include<stdio.h>
struct proc
{
    int no,at,bt,it,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    int  n,j,min=0;
    float avgtat=0,avgwt=0;
    struct proc p[10],temp;
    printf("<--SJF Scheduling Algorithm (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    for(j=1;j<n&&p[j].at==p[0].at;j++)
        if(p[j].bt<p[min].bt)
            min=j;
    temp=p[0];
    p[0]=p[min];
    p[min]=temp;
    p[0].it=p[0].at;
    p[0].ct=p[0].it+p[0].bt;
    for(int i=1;i<n;i++)
    {
        for(j=i+1,min=i;j<n&&p[j].at<=p[i-1].ct;j++)
            if(p[j].bt<p[min].bt)
                min=j;
        temp=p[i];
        p[i]=p[min];
        p[min]=temp;
        if(p[i].at<=p[i-1].ct)
            p[i].it=p[i-1].ct;
        else
            p[i].it=p[i].at;
        p[i].ct=p[i].it+p[i].bt;
    }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        p[i].tat=p[i].ct-p[i].at;
        avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].at,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}

Analisa :
- Mempertimbangkan waktu kedatangan (arrival time)
- Proses dengan burst time terkecil di antara proses yang sudah datang akan dipilih
- Proses tidak diganggu (non-preemptive) setelah dimulai

Input :
Proses	Arrival Time (AT)	Burst Time (BT)
P1	    0	                7
P2	    2	                4
P3	    4	                1
P4	    5	                4

Langkah Penjadwalan (SJF Non-Preemptive)
Waktu 0 → P1 saja yang datang → pilih P1
Waktu 7 → P2, P3, P4 sudah datang → pilih P3 (BT terkecil)
Waktu 8 → sisa P2 dan P4 → pilih P2
Waktu 12 → tinggal P4 → pilih P4

Perhitungan
Process	AT	BT	CT	TAT = CT - AT	WT = TAT - BT
P1	    0	  7	  7	  7	            0
P3	    4	  1	  8	  4	            3
P2	    2	  4	  12	10	          6
P4	    5	  4	  16	11	          7

Rata-Rata
Average TAT = (7 + 4 + 10 + 11) / 4 = 8.0
Average WT = (0 + 3 + 6 + 7) / 4 = 4.0

Chart :
|   P1   | P3 |   P2   |   P4   |
0       7    8        12       16

Kesimpulan
- Algoritma SJF dengan Arrival Time lebih adil karena mempertimbangkan waktu kedatangan.
- Lebih kompleks dari SJF tanpa arrival karena proses harus dipilih dari yang sudah datang saja.
- Dapat mengurangi waktu tunggu rata-rata, tetapi tetap bisa menyebabkan starvation pada proses dengan BT besar dan AT besar.

Code 3 SRTF (preemptive) :

#include<stdio.h>
#define MAX 9999
struct proc
{
    int no,at,bt,rt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    p.rt=p.bt;
    return p;
}
int main()
{
    struct proc p[10],temp;
    float avgtat=0,avgwt=0;
    int n,s,remain=0,time;
    printf("<--SRTF Scheduling Algorithm (Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\n");
    p[9].rt=MAX;
    for(time=0;remain!=n;time++)
    {
        s=9;
        for(int i=0;i<n;i++)
            if(p[i].at<=time&&p[i].rt<p[s].rt&&p[i].rt>0)
                s=i;
        p[s].rt--;
        if(p[s].rt==0)
        {
            remain++;
            p[s].ct=time+1;
            p[s].tat=p[s].ct-p[s].at;
            avgtat+=p[s].tat;
            p[s].wt=p[s].tat-p[s].bt;
            avgwt+=p[s].wt;
            printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[s].no,p[s].at,p[s].bt,p[s].ct,p[s].tat,p[s].wt);
        }
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}

Analisis Program: SRTF (Preemptive)
- Proses dengan remaining burst time terkecil akan dieksekusi terlebih dahulu.
- Jika ada proses baru yang datang dengan burst time lebih kecil dari proses yang sedang berjalan, maka preemption terjadi (proses diganti).
- Digunakan untuk sistem real-time, lebih adil terhadap proses kecil yang datang belakangan.

Input :
Process	Arrival Time (AT)	Burst Time (BT)
P1	    0	                7
P2	    2	                4
P3	    4	                1
P4	    5	                4

Simulasi Waktu Eksekusi (Timeline)
Gantt Chart (setiap satuan waktu):

Time: 0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15
       P1  P1  P2  P2  P3  P2  P2  P4  P4  P4  P4  P1  P1  P1  P1  P1

Hasil Akhir Per Proses :
Process	AT	BT	CT	TAT = CT - AT	WT = TAT - BT
P1	    0	  7	  16	16	          9
P2	    2	  4	  7	  5	            1
P3	    4	  1	  5	  1	            0
P4	    5	  4	  11	6	            2

Rata-Rata :
Average TAT = (16 + 5 + 1 + 6) / 4 = 7.0
Average WT = (9 + 1 + 0 + 2) / 4 = 3.0

Chart :
| P1 | P2 | P3 | P2 | P4 | P1 |
0    2    4    5    7    11   16

Kesimpulan
- SRTF mengurangi waktu tunggu rata-rata dibanding SJF Non-Preemptive.
- Cocok untuk sistem yang butuh respons cepat terhadap proses kecil.
- Kekurangan: proses besar bisa mengalami starvation jika terus-menerus disalip oleh proses kecil baru.
