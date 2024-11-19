# Penjadwalan Preemptive Prioritas - Sistem Tertanam Multitasking

## Gambaran Umum

Repository ini berisi implementasi dan analisis penjadwalan preemptive prioritas dalam sistem tertanam multitasking. Proyek ini mensimulasikan dua tugas dengan waktu eksekusi dan interval periodik yang berbeda, mengendalikan LED untuk memvisualisasikan status tugas (aktif, siap, atau di-preempt).  

Latihan ini bertujuan untuk memberikan pemahaman kualitatif tentang bagaimana penjadwalan preemptive prioritas memengaruhi kinerja sistem waktu nyata.

---

## Deskripsi Masalah

### Tujuan Utama:
1. Memahami perilaku runtime tugas dengan penjadwalan preemptive prioritas.
2. Mengamati dan menganalisis interferensi tugas selama preemption.
3. Mengidentifikasi bagaimana prioritas tugas memengaruhi waktu eksekusi dan penggunaan prosesor.

### Spesifikasi Tugas:
| **Nama Tugas**         | **Waktu Periodik** | **Waktu Eksekusi** | **Deskripsi**                                                                                                                                  |
|-------------------------|--------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| `FlashGreenLedTask`     | 10 detik          | 4 detik             | Menyimulasikan eksekusi dengan menyalakan LED Hijau (berkedip) sementara LED Biru tetap menyala selama status aktif/siap.                     |
| `FlashRedLedTask`       | 2 detik           | 0,5 detik           | Menyimulasikan eksekusi dengan menyalakan LED Merah (berkedip) sementara LED Oranye tetap menyala selama status aktif/siap.                   |

### Visualisasi Perilaku:
- LED Hijau/Merah berkedip saat tugas sedang dieksekusi.
- LED Biru/Oranye menunjukkan bahwa tugas berada dalam status aktif/siap.
- Jika terjadi preemption, kedipan berhenti (LED Hijau/Merah menjadi menyala/mati stabil) selama periode preemption.

---

## Detail Implementasi

### Struktur Tugas
#### `FlashGreenLedTask`
```c
Mulai loop tak hingga
1. Nyalakan LED Biru.
2. Berkedipkan LED Hijau selama 4 detik (dengan frekuensi 20 Hz).
3. Matikan LED Hijau.
4. Matikan LED Biru.
5. Tunda tugas selama 6 detik (menggunakan `osDelay`).
Akhiri loop tak hingga.
```

#### `FlashRedLedTask`
```c
Mulai loop tak hingga
1. Nyalakan LED Oranye.
2. Berkedipkan LED Merah selama 0,5 detik (dengan frekuensi 20 Hz).
3. Matikan LED Merah.
4. Matikan LED Oranye.
5. Tunda tugas selama 1,5 detik (menggunakan `osDelay`).
Akhiri loop tak hingga.
```
