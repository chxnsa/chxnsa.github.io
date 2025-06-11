# Fractional Knapsack Problem - Rangkuman Materi

## Definisi Fractional Knapsack

**Fractional Knapsack** adalah varian dari masalah knapsack (ransel) dalam algoritma, di mana kita boleh mengambil sebagian dari suatu item (misalnya setengah, seperempat, dsb.) untuk memaksimalkan nilai total barang dalam kapasitas ransel tertentu.

### Asal Kata:
- **Fractional**: Berarti pecahan atau bagian. Dalam konteks ini, kita boleh mengambil sebagian dari suatu item (tidak harus utuh)
- **Knapsack**: Artinya ransel atau tas. Ini adalah metafora untuk kapasitas penyimpanan terbatas

## Permasalahan Knapsack Problem

Pada dasarnya, **Knapsack Problem** adalah sebuah masalah yang muncul ketika kita memiliki:
- Sebuah tas dengan **kapasitas terbatas**
- Kumpulan **barang-barang** dengan berat dan nilai tertentu
- **Tujuan**: Memilih barang-barang yang dapat dimasukkan ke dalam tas untuk **memaksimalkan nilai total** barang yang dibawa

## Jenis-Jenis Knapsack Problem

### 1. 0/1 Knapsack Problem
- Kita **hanya bisa memilih barang utuh**
- **Tidak bisa mengambil sebagian** (fractional) dari barang
- Keputusan biner: ambil atau tidak ambil

### 2. Fractional Knapsack Problem
- Kita **bisa mengambil sebagian** dari barang
- **Tidak hanya barang utuh** yang dapat diambil
- Lebih fleksibel dalam optimasi

## Penjelasan Konsep Fractional Knapsack

Bayangkan Anda memiliki:
- **Tas dengan kapasitas terbatas**
- **Beberapa barang** dengan berat dan nilai tertentu
- **Tujuan**: Memaksimalkan nilai barang yang dibawa tanpa melebihi kapasitas

### Keunggulan Fractional Knapsack:
- **Boleh "memotong" barang!** 
- Contoh: Jika hanya bisa membawa 3 kg dari emas seberat 5 kg, tidak masalah
- **Nilai tetap proporsional** dengan bagian yang diambil

## Strategi Penyelesaian dengan Algoritma Greedy

### Langkah-langkah Penyelesaian:
1. **Hitung rasio nilai per berat** (value/weight) untuk setiap barang
2. **Urutkan barang** berdasarkan rasio tertinggi ke terendah
3. **Masukkan barang ke tas** berdasarkan urutan rasio
4. **Ambil sebagian** jika barang tidak muat seluruhnya

## Contoh Soal dan Penyelesaian

### Data Soal:
Sebuah tas memiliki kapasitas maksimum **50 kg**. Tersedia 3 barang:

| Barang | Berat (kg) | Nilai (Rp) |
|--------|------------|------------|
| A      | 10         | 60         |
| B      | 20         | 100        |
| C      | 30         | 120        |

**Pertanyaan**: Tentukan nilai maksimum yang dapat dibawa dengan strategi Fractional Knapsack!

### Penyelesaian:

#### Langkah 1: Hitung Nilai per Berat (Rasio)
- **Barang A**: 60 ÷ 10 = **6.0**
- **Barang B**: 100 ÷ 20 = **5.0**
- **Barang C**: 120 ÷ 30 = **4.0**

#### Langkah 2: Urutkan Berdasarkan Rasio Tertinggi
1. **Barang A** → rasio 6.0 (tertinggi)
2. **Barang B** → rasio 5.0
3. **Barang C** → rasio 4.0 (terendah)

#### Langkah 3: Masukkan Barang ke Tas

**Kapasitas awal tas = 50 kg**

1. **Ambil Barang A** (10 kg, nilai 60)
   - Masih muat → ambil seluruhnya
   - Sisa kapasitas = 50 - 10 = **40 kg**
   - Total nilai = **60**

2. **Ambil Barang B** (20 kg, nilai 100)
   - Masih muat → ambil seluruhnya
   - Sisa kapasitas = 40 - 20 = **20 kg**
   - Total nilai = 60 + 100 = **160**

3. **Ambil Barang C** (30 kg, nilai 120)
   - **Tidak muat seluruhnya** → ambil sebagian
   - Ambil sebanyak **20 kg dari 30 kg**
   - Proporsi = 20/30 = **2/3**
   - Nilai yang diambil = (2/3) × 120 = **80**
   - Sisa kapasitas = **0 kg**
   - Total nilai = 160 + 80 = **240**

### Hasil Akhir:
- **Nilai maksimum yang dapat dibawa = 240 Rp**
- **Komposisi tas**:
  - Barang A: 10 kg (100% dari barang)
  - Barang B: 20 kg (100% dari barang)
  - Barang C: 20 kg (66.7% dari barang)

## Algoritma Greedy dalam Fractional Knapsack

### Mengapa Greedy Efektif?
- **Pilihan lokal optimal**: Memilih barang dengan rasio nilai/berat tertinggi
- **Tidak perlu backtracking**: Keputusan yang dibuat tidak perlu direvisi
- **Solusi global optimal**: Hasil akhir memberikan nilai maksimum

### Pseudocode:
```
1. Hitung rasio nilai/berat untuk setiap barang
2. Urutkan barang berdasarkan rasio (descending)
3. Inisialisasi total_nilai = 0, sisa_kapasitas = kapasitas_tas
4. Untuk setiap barang dalam urutan:
   a. Jika berat_barang ≤ sisa_kapasitas:
      - Ambil seluruh barang
      - total_nilai += nilai_barang
      - sisa_kapasitas -= berat_barang
   b. Jika tidak:
      - Ambil sebagian barang
      - proporsi = sisa_kapasitas / berat_barang
      - total_nilai += proporsi × nilai_barang
      - sisa_kapasitas = 0
      - BERHENTI
5. Return total_nilai
```

## Analisis Kompleksitas

### Kompleksitas Waktu: **O(n log n)**
- **O(n)** untuk menghitung rasio
- **O(n log n)** untuk mengurutkan barang
- **O(n)** untuk memproses barang

### Kompleksitas Ruang: **O(1)**
- Hanya membutuhkan ruang tambahan yang konstan
- Tidak memerlukan struktur data tambahan yang signifikan

## Perbandingan dengan 0/1 Knapsack

| Aspek | Fractional Knapsack | 0/1 Knapsack |
|-------|---------------------|---------------|
| **Fleksibilitas** | Dapat mengambil sebagian barang | Hanya barang utuh |
| **Algoritma** | Greedy (optimal) | Dynamic Programming |
| **Kompleksitas** | O(n log n) | O(nW) |
| **Solusi** | Selalu optimal | Optimal dengan DP |
| **Aplikasi** | Masalah kontinyu | Masalah diskrit |

## Aplikasi dalam Dunia Nyata

1. **Manajemen Portfolio**: Alokasi investasi dengan batasan modal
2. **Pengiriman Barang**: Optimasi muatan kendaraan pengangkut
3. **Produksi**: Alokasi sumber daya dengan kapasitas terbatas
4. **Penjadwalan**: Optimasi waktu dengan multiple tasks
5. **Resource Allocation**: Distribusi sumber daya terbatas

## Kesimpulan

1. **Fractional Knapsack** memungkinkan pengambilan sebagian barang untuk optimasi
2. **Algoritma Greedy** memberikan solusi optimal dengan memilih berdasarkan rasio nilai/berat tertinggi
3. **Langkah penyelesaian**: 
   - Hitung rasio nilai/berat
   - Urutkan barang berdasarkan rasio
   - Masukkan barang ke tas secara greedy
4. **Kompleksitas waktu O(n log n)** membuatnya efisien untuk dataset besar
5. **Lebih fleksibel** dibanding 0/1 Knapsack karena membolehkan partial selection

### Keunggulan Utama:
- **Solusi optimal** dengan algoritma sederhana
- **Efisiensi waktu** yang baik
- **Aplikabilitas luas** dalam masalah optimasi resource allocation
- **Implementasi mudah** dengan logika greedy yang intuitif