# N-Queens Problem - Rangkuman Materi

---

## Definisi N-Queens Problem

**N-Queens Problem** adalah sebuah masalah klasik dalam bidang algoritma dan teori komputasi, yang berfokus pada **penempatan sejumlah ratu (queen) di papan catur berdimensi N × N** sedemikian rupa sehingga tidak ada dua ratu yang saling menyerang.

### Konsep Dasar:
- **N ratu** harus ditempatkan pada **papan N × N**
- **Tidak ada konflik** antara ratu yang ditempatkan
- **Setiap ratu** harus aman dari serangan ratu lainnya

## Tujuan Utama N-Queens Problem

### 1. **Penempatan Ratu yang Aman**
- Setiap ratu harus ditempatkan di posisi yang **tidak satu baris**, **tidak satu kolom**, dan **tidak satu diagonal** dengan ratu lainnya
- Memastikan tidak ada ratu yang dapat menyerang ratu lain

### 2. **Menghindari Konflik**
- Tujuan ini mengharuskan algoritma untuk **mengecek konflik horizontal, vertikal, dan diagonal** secara cermat setiap kali menempatkan sebuah ratu
- Validasi posisi secara real-time

### 3. **Menemukan Semua Solusi**
- **Dalam beberapa kasus**: dicari semua solusi valid yang mungkin
- **Dalam kasus lain**: cukup satu solusi yang valid (untuk mempercepat proses)

### 4. **Melatih Pemahaman Algoritma**
Tujuan praktis dari mempelajari masalah ini:
- **Memahami algoritma backtracking**
- **Belajar tentang constraint satisfaction problems (CSP)**
- **Meningkatkan kemampuan** dalam pemrograman logika dan rekursif

## Batasan Masalah (Constraints)

### 1. **Jumlah Ratu = Ukuran Papan (N)**
- Harus menempatkan **tepat N ratu** pada papan N × N
- **Tidak boleh lebih atau kurang** dari N ratu

### 2. **Satu Ratu per Baris dan Kolom**
- Hanya diperbolehkan **satu ratu di setiap baris dan kolom**
- Tidak boleh ada dua ratu yang:
  - Berada di **baris yang sama**
  - Berada di **kolom yang sama**

### 3. **Tidak Ada Dua Ratu dalam Diagonal yang Sama**
- Setiap ratu tidak boleh berada dalam **satu garis diagonal** dengan ratu lain
- Berlaku untuk:
  - **Diagonal utama** (↘)
  - **Diagonal balik** (↙)

### 4. **Papan Catur Berbentuk Persegi**
- Ukuran papan harus berbentuk **persegi (N × N)**
- Tidak diperbolehkan papan non-persegi seperti 8×7 atau 5×6

### 5. **Posisi Aman Harus Dicek Sebelum Penempatan**
- Algoritma wajib **mengecek apakah posisi aman** sebelum menempatkan ratu
- Jika tidak aman, posisi tersebut harus dihindari
- Dalam backtracking: dilakukan **pemangkasan/cut**

### 6. **Nilai N ≥ 4 untuk Solusi Non-Trivial**
- **Tidak ada solusi** untuk:
  - N = 2 (papan 2×2)
  - N = 3 (papan 3×3)
- **Solusi pertama** yang mungkin muncul dimulai dari **N = 4**

### 7. **Tidak Ada Rintangan atau Hambatan di Papan**
- Diasumsikan bahwa **papan kosong sepenuhnya** tanpa penghalang
- **Semua sel tersedia** untuk ditempati ratu selama tidak melanggar aturan konflik

## Dasar Teori dan Konsep Backtracking

### Apa itu Backtracking?
**Backtracking** adalah metode algoritma pencarian berbasis rekursi yang digunakan untuk menyelesaikan masalah dengan:
- **Mencoba semua kemungkinan solusi** secara sistematis
- **Mundur (backtrack)** jika suatu kemungkinan tidak menghasilkan solusi yang valid
- **Eksplorasi mendalam** dengan pemangkasan dini

### Mengapa N-Queens Bisa Diselesaikan dengan Backtracking?

1. **Masalahnya Bersifat Rekursif dan Bertingkat**
   - Setiap langkah membangun solusi parsial
   - Struktur masalah dapat dipecah menjadi subproblem

2. **Ada Banyak Solusi Parsial yang Bisa Disaring Dini**
   - Constraint checking memungkinkan early pruning
   - Menghindari eksplorasi cabang yang tidak mungkin

3. **Ada Pembatas (Constraint) yang Jelas**
   - Aturan konflik yang tegas dan mudah diperiksa
   - Validasi dapat dilakukan pada setiap langkah

4. **Tidak Perlu Mencoba Semua Kombinasi secara Brute Force**
   - Pemangkasan mengurangi space pencarian secara signifikan
   - Efisiensi lebih baik dibanding exhaustive search

## Langkah-langkah Penyelesaian dengan Backtracking

### 1. **Mulai dari Baris Pertama**
- Inisialisasi papan kosong
- Mulai penempatan dari baris ke-0

### 2. **Periksa Keamanan Posisi**
- Untuk setiap kolom di baris current:
  - Cek konflik horizontal (baris)
  - Cek konflik vertikal (kolom)  
  - Cek konflik diagonal

### 3. **Tempatkan Ratu Jika Aman**
- Jika posisi aman, tempatkan ratu
- Lanjut ke baris berikutnya (rekursi)

### 4. **Backtrack Jika Tidak Ada Posisi Aman**
- Jika tidak ada posisi yang valid di baris current
- Mundur ke baris sebelumnya
- Coba posisi lain di baris sebelumnya

### 5. **Simpan Solusi Jika Semua Ratu Berhasil Ditempatkan**
- Jika berhasil menempatkan N ratu
- Simpan konfigurasi sebagai solusi valid

### 6. **Lanjutkan untuk Mencari Semua Solusi (Opsional)**
- Untuk mencari multiple solutions
- Lanjutkan backtracking setelah menemukan satu solusi

## Contoh Penyelesaian: Papan 4×4

### Soal:
Tempatkan 4 ratu di papan 4×4 sehingga tidak ada dua ratu yang menyerang satu sama lain.

### Proses Penyelesaian:

#### **Langkah 1: Baris ke-0**
- Coba kolom 0 → **aman** → tempatkan ratu di **(0,0)**

#### **Langkah 2: Baris ke-1**
- Kolom 0 → **konflik** (satu kolom dengan ratu di (0,0))
- Kolom 1 → **konflik** (diagonal dengan ratu di (0,0))
- Kolom 2 → **aman** → tempatkan ratu di **(1,2)**

#### **Langkah 3: Baris ke-2**
- Kolom 0 → **konflik** (satu kolom)
- Kolom 1 → **konflik** (diagonal)
- Kolom 2 → **konflik** (satu kolom)
- Kolom 3 → **aman** → tempatkan ratu di **(2,3)**

#### **Langkah 4: Baris ke-3**
- Kolom 1 → **aman** → tempatkan ratu di **(3,1)**

### Hasil Solusi:
```
Q . . .
. . Q .
. . . Q
. Q . .
```

**Semua ratu berhasil ditempatkan ✓**

## Implementasi Algoritma

### Pseudocode Backtracking untuk N-Queens:
```
Algorithm SolveNQueens(board, row, N):
    1. If row == N:
        return True  // Semua ratu berhasil ditempatkan
    
    2. For col = 0 to N-1:
        a. If IsSafe(board, row, col, N):
            - Place queen at board[row][col]
            - If SolveNQueens(board, row+1, N):
                return True
            - Remove queen from board[row][col] (backtrack)
    
    3. return False  // Tidak ada solusi di branch ini

Algorithm IsSafe(board, row, col, N):
    1. Check column conflict:
       For i = 0 to row-1:
           If board[i][col] == 1: return False
    
    2. Check diagonal conflict (upper left):
       For i = row-1, j = col-1; i >= 0 AND j >= 0; i--, j--:
           If board[i][j] == 1: return False
    
    3. Check diagonal conflict (upper right):
       For i = row-1, j = col+1; i >= 0 AND j < N; i--, j++:
           If board[i][j] == 1: return False
    
    4. return True
```

### Optimasi Fungsi IsSafe:
Untuk efisiensi yang lebih baik, bisa menggunakan array boolean untuk tracking:
- `cols[col]` - tracking kolom yang sudah terisi
- `diag1[row-col+N-1]` - tracking diagonal utama
- `diag2[row+col]` - tracking diagonal balik

## Analisis Kompleksitas

### Kompleksitas Waktu:
- **Worst Case**: O(N!) 
- **Average Case**: Lebih baik karena pruning
- **Best Case**: O(N) jika solusi ditemukan di early stage

### Kompleksitas Ruang:
- **Space Complexity**: O(N²) untuk papan + O(N) untuk recursion stack
- **Total**: O(N²)

### Jumlah Solusi untuk Berbagai N:
| N | Jumlah Solusi |
|---|---------------|
| 4 | 2             |
| 5 | 10            |
| 6 | 4             |
| 7 | 40            |
| 8 | 92            |

## Optimasi dan Variasi

### 1. **Optimasi dengan Constraint Arrays**
```cpp
bool cols[N], diag1[2*N-1], diag2[2*N-1];
// Checking becomes O(1) instead of O(N)
```

### 2. **Iterative Deepening**
- Mulai dengan depth terbatas
- Tingkatkan depth secara bertahap

### 3. **Symmetry Breaking**
- Manfaatkan simetri papan catur
- Kurangi space pencarian hingga 1/8

### 4. **Heuristic Ordering**
- Pilih posisi dengan least constraining value
- Most constrained variable first

## Aplikasi dan Relevansi

### Aplikasi Praktis:
1. **Constraint Satisfaction Problems (CSP)**
2. **Scheduling Problems** - penjadwalan tanpa konflik
3. **Resource Allocation** - alokasi sumber daya terbatas
4. **Graph Coloring** - pewarnaan graph tanpa konflik
5. **Sudoku Solver** - penyelesaian puzzle logika

### Pembelajaran Algoritma:
1. **Backtracking fundamentals**
2. **Recursion dan tree traversal**
3. **Constraint handling**
4. **Optimization techniques**
5. **Space-time tradeoffs**

## Implementasi dalam C++

### Struktur Dasar:
```cpp
class NQueens {
private:
    int N;
    vector<vector<int>> board;
    
public:
    bool isSafe(int row, int col);
    bool solveNQueens(int row);
    void printSolution();
};
```

### Contoh Output:
```
Solution found:
Q . . .
. . Q .
. . . Q
. Q . .
```

## Kesimpulan

**N-Queens Problem** adalah masalah klasik yang sangat efektif untuk pembelajaran algoritma backtracking karena:

### Karakteristik Utama:
1. **Masalah penempatan ratu** di papan catur agar tidak saling menyerang
2. **Dapat diselesaikan dengan algoritma backtracking** secara efisien
3. **Constraint yang jelas** - horizontal, vertikal, dan diagonal
4. **Proses sistematis** - mencoba posisi satu per satu dan mundur jika terjadi konflik

### Proses Penyelesaian:
1. **Penempatan bertahap** di setiap baris dengan memeriksa posisi yang aman
2. **Backtrack** jika tidak ada posisi yang valid
3. **Solusi ditemukan** secara efisien dan sistematis

### Nilai Pembelajaran:
- **Pemahaman backtracking** yang mendalam
- **Constraint satisfaction** dalam problem solving
- **Optimasi algoritma** melalui pruning
- **Rekursi dan tree traversal** yang praktis

N-Queens Problem memberikan fondasi yang kuat untuk memahami algoritma pencarian dengan constraint dan menjadi stepping stone untuk masalah optimasi yang lebih kompleks.