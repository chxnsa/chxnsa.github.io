# 📊 Subset Sum Problem - Rangkuman Materi

---

## 🎯 Definisi Subset Sum Problem

**Subset Sum Problem** adalah masalah fundamental dalam computer science yang bertujuan untuk:

> 📋 **Definisi**: Diberikan himpunan bilangan bulat tidak kosong dan sebuah angka target `m`, carilah subset (bagian) dari himpunan tersebut yang jumlahnya sama dengan `m`.

### 🔍 Contoh Sederhana:
```
Input: arr[] = [3, 34, 4, 12, 5, 2], sum = 9
Output: Benar ✅
Penjelasan: Ada subset (4, 5) dengan jumlah 9

Input: arr[] = [3, 34, 4, 12, 5, 2], sum = 30  
Output: Salah ❌
Penjelasan: Tidak ada subset yang jumlahnya 30
```

---

## 🏷️ Klasifikasi Masalah: NP-Complete

### 🧩 Karakteristik NP-Complete:
- **📈 Sulit Diselesaikan**: Tidak ada algoritma efisien (polinomial) yang diketahui
- **⚡ Mudah Diverifikasi**: Jika sudah ada solusi, dapat diverifikasi dengan cepat
- **🔗 Universal**: Semua masalah NP lainnya dapat direduksi ke Subset Sum
- **🌟 Fundamental**: Bagian dari masalah "P vs NP" dalam ilmu komputer

### 💡 Implikasi:
Jika ada cara cepat untuk menyelesaikan Subset Sum, maka semua masalah NP bisa diselesaikan dengan cepat!

---

## 🛠️ Pendekatan Penyelesaian

### 1. 💪 Brute Force (Rekursif)

#### 🔄 Cara Kerja:
- Setiap elemen memiliki 2 pilihan: **diambil** atau **tidak diambil**
- Mencoba semua kombinasi subset yang mungkin
- Menggunakan rekursi untuk eksplorasi semua kemungkinan

#### 📊 Kompleksitas:
- **Waktu**: `O(2^n)` 
- **Ruang**: `O(n)` (untuk stack rekursi)

#### 📈 Contoh Jumlah Kombinasi:
```
3 angka  → 2³ = 8 kombinasi
10 angka → 2¹⁰ = 1.024 kombinasi  
30 angka → 2³⁰ = 1.073.741.824 kombinasi
```

#### ✅ Kelebihan:
- Sederhana untuk dipahami
- Pasti menemukan solusi jika ada

#### ❌ Kekurangan:
- Tidak efisien untuk `n` besar
- Waktu eksekusi eksponensial

### 2. 🧠 Dynamic Programming

#### 💾 Cara Kerja:
- Menggunakan tabel untuk menyimpan hasil subproblem
- Menghindari perhitungan berulang
- Membangun solusi dari subproblem yang lebih kecil

#### 📊 Kompleksitas:
- **Waktu**: `O(n × T)` (n = jumlah elemen, T = target sum)
- **Ruang**: `O(n × T)` (dapat dioptimalkan menjadi `O(T)`)

#### ✅ Kelebihan:
- Efisien untuk target sum yang tidak terlalu besar
- Menghindari perhitungan berulang

#### ❌ Kekurangan:
- Memakan banyak memori untuk target sum yang besar
- Tidak cocok untuk bilangan negatif

---

## 🔄 Variasi Masalah Subset Sum

### A. 🔺 Subset Sum dengan Elemen Negatif

#### 📋 Deskripsi:
Masalah klasik biasanya menggunakan bilangan positif, tetapi variasi ini memungkinkan elemen negatif.

#### 🎯 Contoh:
```
S = {-7, -3, -2, 5, 8}, target = 0
Solusi: {-3, -2, 5} → (-3) + (-2) + 5 = 0 ✅
```

#### ⚠️ Konsekuensi:
- Dynamic Programming standar tidak cukup
- Indeks array tidak bisa negatif
- Perlu modifikasi pendekatan

### B. 🔢 Counting Subsets

#### 📋 Deskripsi:
Menghitung **berapa banyak** subset yang memenuhi jumlah target, bukan hanya apakah ada.

#### 🎯 Contoh:
```
S = {2, 3, 5, 6, 8, 10}, sum = 10
```

#### 🧮 Rumus DP:
```
dp[i][j] = dp[i-1][j] + dp[i-1][j - arr[i-1]]
(jika j >= arr[i-1])
```

### C. 🎯 Closest Subset Sum

#### 📋 Deskripsi:
Jika tidak ada subset dengan jumlah tepat, cari subset dengan jumlah **terdekat** dengan target.

#### 🎯 Contoh:
```
S = {1, 3, 4, 8}, target = 10
Kemungkinan: {1,3,4}=8, {3,8}=11, {1,8}=9
Terdekat: 9 dan 11
```

### D. 🎒 Hubungan dengan 0/1 Knapsack Problem

#### 🔗 Persamaan:
- Sama-sama memilih subset dari elemen
- Sama-sama bisa diselesaikan dengan Dynamic Programming
- Sama-sama memiliki batasan total

#### 🔄 Perbedaan:
| Aspek | Subset Sum | 0/1 Knapsack |
|-------|------------|---------------|
| **Tujuan** | Total sum = target | Maksimalkan nilai |
| **Nilai vs Berat** | nilai = berat | berat ≠ nilai |
| **Kondisi** | Exact match | Optimization |

---

## ⚠️ Kompleksitas & Keterbatasan

### 🚫 Keterbatasan Utama:

#### 1. **Kompleksitas Tinggi**
- Brute Force: `O(2^n)` - eksponensial
- DP: `O(n × sum)` - pseudo-polynomial

#### 2. **Masalah dengan Input Besar**
- Tidak efisien untuk `n` yang besar
- Tidak efisien untuk nilai `sum` yang besar
- Kesulitan dengan elemen negatif

#### 3. **Sifat NP-Complete**
- Belum ada algoritma polinomial yang diketahui
- Solusi optimal memerlukan waktu eksponensial dalam kasus terburuk

---

## 💻 Contoh Implementasi

### 🎯 Kasus: S = {2, 4, 5, 9}, Target = 18

#### Analisis:
- Perlu mencari subset yang jumlahnya = 18
- Kemungkinan: {2, 4, 5, 9} → 2 + 4 + 5 + 9 = 20 ❌
- Kemungkinan: {4, 5, 9} → 4 + 5 + 9 = 18 ✅

### 🔄 Implementasi Brute Force:
```cpp
// Fungsi rekursif mencoba setiap kombinasi
// Menyimpan hasil dalam vector result
// Kompleksitas: O(2^n)
```

### 🧠 Implementasi Dynamic Programming:
```cpp
// Tabel dp[i][j] = true jika ada subset dari {S[0],...,S[i-1]} 
//                  yang jumlahnya j
// Fungsi findSubset merekonstruksi solusi
// Kompleksitas: O(n × T)
```

---

## 📝 Kesimpulan

### 🎯 Poin Utama:

1. **📚 Definisi**: Subset Sum Problem mencari bagian dari himpunan yang jumlahnya sama dengan target tertentu

2. **🏷️ Klasifikasi**: Termasuk masalah NP-Complete yang fundamental dalam computer science

3. **🛠️ Pendekatan**:
   - **Brute Force**: Sederhana tapi tidak efisien (`O(2^n)`)
   - **Dynamic Programming**: Lebih efisien untuk kasus tertentu (`O(n×T)`)

4. **🔄 Variasi**: Berbagai variasi masalah dengan karakteristik dan solusi berbeda

5. **⚠️ Keterbatasan**: Tidak ada solusi polinomial yang diketahui untuk semua kasus

6. **🌟 Pentingnya**: Masalah fundamental yang terkait dengan pertanyaan besar "P vs NP" dalam ilmu komputer

### 💡 Takeaway:
Subset Sum Problem adalah contoh sempurna dari masalah yang **mudah dipahami** tetapi **sulit diselesaikan secara efisien**, menjadikannya salah satu masalah paling penting dalam teori kompleksitas komputasi.

---
