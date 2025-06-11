# 🔍 Depth-First Search (DFS) - Rangkuman Materi

---

## 📖 Definisi DFS

**Depth-First Search (DFS)** adalah salah satu metode penelusuran dalam struktur data seperti graf atau pohon. Cara kerja DFS dapat diibaratkan seperti menyusuri jalan bercabang, di mana kita akan terus berjalan ke arah satu cabang hingga mencapai ujung, sebelum kembali dan mencoba cabang lainnya.

### 🎯 Karakteristik Utama:
- **Mengunjungi simpul (node) sedalam mungkin** terlebih dahulu
- **Backtrack** jika sudah tidak ada jalur lain yang bisa dilalui
- Dapat **dijalankan menggunakan rekursi** atau dengan bantuan **struktur data stack**
- Memerlukan **mekanisme penandaan** untuk menghindari kunjungan berulang

---

## 🔧 Jenis-Jenis DFS

| No | Jenis DFS | Deskripsi |
|:--:|-----------|-----------|
| 1️⃣ | **DFS Rekursif** | Implementasi menggunakan pemanggilan fungsi rekursif |
| 2️⃣ | **DFS Iteratif** | Menggunakan struktur data stack untuk simulasi rekursi |
| 3️⃣ | **DFS untuk Deteksi Siklus** | Mendeteksi adanya siklus dalam graf |
| 4️⃣ | **DFS untuk Topological Sort** | Mengurutkan simpul berdasarkan dependensi |
| 5️⃣ | **DFS untuk Komponen Terhubung/SCC** | Menemukan komponen yang saling terhubung |
| 6️⃣ | **DFS Terbatas Kedalaman & IDDFS** | Membatasi kedalaman pencarian |

---

## ⚠️ Tantangan dan Batasan

### 🚨 Tantangan Utama:

#### 1. **Deteksi Siklus**
- DFS dapat terjebak dalam infinite loop jika graf memiliki siklus
- **Solusi:** Menggunakan mekanisme penandaan node yang sudah dikunjungi

#### 2. **Penggunaan Memori Tinggi**
- Rekursi DFS membutuhkan stack yang dalam
- **Risiko:** Stack overflow pada graf besar atau jalur panjang

#### 3. **Tidak Menjamin Jalur Terpendek**
- DFS menemukan jalur pertama yang ditemukan, bukan yang optimal
- **Konsekuensi:** Kurang cocok untuk pencarian jalur terpendek

### 🔒 Batasan Algoritma:

| Batasan | Penjelasan |
|---------|------------|
| ❌ **Efisiensi** | Tidak efisien untuk graf besar dan kompleks |
| 🔗 **Cakupan** | Hanya menjelajah satu komponen terhubung |
| 🎯 **Optimalisasi** | Tidak cocok untuk mencari jalur terpendek |
| 💾 **Memori** | Berisiko stack overflow pada graf dengan kedalaman besar |
| 🔄 **Siklus** | Tidak otomatis menangani graf dengan siklus |

---

## 🌍 Penerapan dalam Dunia Nyata

### 🏢 **Sistem Komputer**
- **📁 File Explorer:** Menjelajah folder & subfolder di komputer
- **🔍 Dependency Analysis:** Deteksi siklus pada graf dependensi

### 🎮 **Gaming & Puzzle**
- **🧩 Puzzle Solving:** Menyelesaikan Sudoku & N-Queens
- **🗺️ Pathfinding:** Eksplorasi jalur di maze atau peta game

### 📱 **Sosial Media**
- **👥 Network Analysis:** Analisis hubungan di jejaring sosial
- **🔗 Connection Mapping:** Pemetaan koneksi antar pengguna

---

## 💡 Contoh Implementasi

### 📊 **Contoh 1: Traversal Lengkap**
```
Graf: A → B → D → F
      ↓   ↓
      C → E

Urutan kunjungan: A → B → D → F → C → E
```

### 🎯 **Contoh 2: Pencarian Target**
```
Graf: A → B → D → F (Target)
      ↓   ↓
      C → E

Urutan kunjungan: A → B → D → F ✅
```

### 🧮 **Latihan Soal Kompleks**
```
Graf dengan 12 simpul: A, B, C, D, E, F, G, H, I, J, K, L
Pencarian dari A ke J

Hasil: A → B → E → H → I → L → J
```

---

## 💻 Struktur Kode

### 🔄 **Pseudocode DFS Rekursif:**
```python
function DFS(node, visited):
    mark node as visited
    process node
    
    for each neighbor of node:
        if neighbor not visited:
            DFS(neighbor, visited)
```

### 📚 **Pseudocode DFS Iteratif:**
```python
function DFS_Iterative(start):
    create empty stack
    push start to stack
    
    while stack not empty:
        node = pop from stack
        if node not visited:
            mark node as visited
            process node
            push all unvisited neighbors to stack
```

---

## 📝 Kesimpulan

### ✅ **Kelebihan DFS:**
- **🚀 Sederhana** dan mudah diimplementasikan
- **💾 Hemat memori** untuk graf sparse
- **🔍 Efektif** untuk menemukan jalur atau komponen terhubung
- **🛠️ Serbaguna** untuk berbagai aplikasi graf

### ❌ **Kekurangan DFS:**
- **🚫 Tidak menjamin** jalur terpendek
- **⚠️ Risiko stack overflow** pada graf dalam
- **🔄 Masalah dengan siklus** tanpa penanganan khusus
- **📊 Kurang efisien** untuk graf besar dan kompleks

### 🎯 **Aplikasi Terbaik:**
DFS sangat cocok untuk deteksi siklus, topological sorting, pemecahan maze, dan analisis komponen terhubung dalam graf.

---

