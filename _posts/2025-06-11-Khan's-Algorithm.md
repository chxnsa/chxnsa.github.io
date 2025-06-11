# 🔗 Kahn's Algorithm - Rangkuman Materi

## 🎯 Definisi dan Pengenalan

**Kahn's Algorithm** adalah algoritma yang digunakan untuk melakukan **topological sort** pada graf berarah tanpa siklus (DAG - Directed Acyclic Graph). Algoritma ini diperkenalkan oleh **Arthur B. Kahn pada tahun 1962**.

### 📋 Tujuan Utama:
Menyusun simpul-simpul dalam urutan sedemikian rupa sehingga **jika ada edge dari simpul U ke simpul V, maka U muncul sebelum V** dalam urutan hasil.

### 🌍 Aplikasi Praktis:
- 📅 **Penjadwalan tugas** (task scheduling)
- 💻 **Kompilasi kode** dan sistem build
- 🔗 **Dependency management** antar modul
- 📦 **Package management** systems

---

## 🧩 Konsep Utama

### 1️⃣ **Graf Berarah (Directed Graph)**
- Graf yang memiliki **arah pada setiap edge**
- Menunjukkan hubungan **ketergantungan** atau **urutan**
- Setiap edge memiliki **titik awal** dan **titik tujuan**

### 2️⃣ **DAG (Directed Acyclic Graph)**
DAG adalah graf berarah tanpa siklus yang digunakan untuk:
- 🎯 **Memodelkan hubungan dependensi** atau urutan tugas
- ⚡ **Menghasilkan urutan topologis** secara efisien
- 🔄 **Memastikan tidak ada ketergantungan** yang bertentangan
- 📊 **Merepresentasikan struktur kompleks** tanpa perulangan

### 3️⃣ **Acyclic (Tanpa Siklus)**
- Graf **tidak boleh memiliki rangkaian edge** yang membentuk loop
- **Kritis untuk Kahn's Algorithm** karena topological sort hanya mungkin pada DAG
- Jika ada siklus: node akan **saling bergantung secara circular** → tidak bisa diurutkan linier

### 4️⃣ **In-degree**
**In-degree** adalah jumlah edge yang **masuk ke suatu node**.

🔍 **Fungsi In-degree dalam Kahn's Algorithm:**
- 📊 **Mengukur dependensi** node
- 🎯 **Menentukan urutan eksekusi**
- 🔍 **Mendeteksi siklus** dengan memantau node yang tidak pernah mencapai in-degree = 0

### 5️⃣ **Topological Sort**
Metode pengurutan node dalam DAG berdasarkan ketergantungan hierarkis.

#### ✨ **Karakteristik Utama:**
| Karakteristik | Penjelasan |
|---------------|------------|
| 🎯 **Berlaku untuk DAG** | Hanya dapat diterapkan pada graf tanpa siklus |
| 🔄 **Multiple Valid Orders** | Dapat menghasilkan beberapa urutan valid yang berbeda |
| ⚡ **Kompleksitas Linear** | Waktu eksekusi O(V + E) yang sangat efisien |

---

## 🚀 Langkah-langkah Algorithm

### **Step 1: 📊 Hitung In-degree**
```
Untuk setiap node dalam graf:
    Hitung jumlah edge yang masuk ke node tersebut
```

### **Step 2: 🎯 Inisialisasi Queue**
```
Masukkan semua node dengan in-degree = 0 ke dalam queue
```

### **Step 3: 🔄 Proses Queue**
```
Selama queue tidak kosong:
    1. Keluarkan node dari queue (u)
    2. Masukkan u ke dalam hasil topological sort
    3. Untuk setiap tetangga v dari u:
       - Kurangi in-degree[v] sebanyak 1
       - Jika in-degree[v] = 0, masukkan v ke queue
```

### **Step 4: ✅ Validasi Hasil**
```
Jika jumlah node dalam hasil ≠ jumlah node di graf:
    Graf memiliki siklus (tidak valid untuk topological sort)
```

---

## 💡 Contoh Implementasi

### 🧮 **Contoh Soal:**
```
Graf DAG:
1 → 2 → 3
1 → 4
2 → 4
```

### 📋 **Langkah Penyelesaian:**

#### **Step 1: Hitung In-degree**
| Node | In-degree |
|:----:|:---------:|
| 1    | 0         |
| 2    | 1         |
| 3    | 1         |
| 4    | 2         |

#### **Step 2: Queue Awal**
```
Node dengan in-degree = 0: [1]
```

#### **Step 3: Proses Queue**

**Iterasi 1:**
```
- Ambil: 1, Hasil: [1]
- Kurangi in-degree tetangga (2, 4):
  • in-degree[2] = 0 → queue = [2]
  • in-degree[4] = 1
```

**Iterasi 2:**
```
- Ambil: 2, Hasil: [1, 2]
- Kurangi in-degree tetangga (3, 4):
  • in-degree[3] = 0 → queue = [3]
  • in-degree[4] = 0 → queue = [3, 4]
```

**Iterasi 3:**
```
- Ambil: 3, Hasil: [1, 2, 3]
- Tidak ada tetangga
```

**Iterasi 4:**
```
- Ambil: 4, Hasil: [1, 2, 3, 4]
- Tidak ada tetangga
```

#### **🎉 Hasil Akhir:**
```
Topological Sort: [1, 2, 3, 4]
```

---

## 💻 Struktur Implementasi

### 🐍 **Pseudocode:**
```python
function kahnsAlgorithm(graph):
    # Step 1: Hitung in-degree
    in_degree = calculateInDegree(graph)
    queue = []
    result = []
    
    # Step 2: Masukkan node dengan in-degree 0
    for node in graph:
        if in_degree[node] == 0:
            queue.append(node)
    
    # Step 3: Proses queue
    while queue is not empty:
        current = queue.pop()
        result.append(current)
        
        for neighbor in graph[current]:
            in_degree[neighbor] -= 1
            if in_degree[neighbor] == 0:
                queue.append(neighbor)
    
    # Step 4: Validasi
    if len(result) != len(graph):
        return "Graf memiliki siklus!"
    
    return result
```

### ⚡ **Kompleksitas:**
- **⏰ Time Complexity:** O(V + E)
  - V = jumlah vertex (node)
  - E = jumlah edge
- **💾 Space Complexity:** O(V)

---

## 📊 Simulasi Proses Visual

### 🎯 **Contoh Graf Kompleks:**
```
Graf: 0 ← 2 ← 3
      ↑   ↑   ↑
      4 → 5 → 1
```

### 🔄 **Proses Step-by-Step:**

| Step | Queue | Processed | Result | In-degree Status |
|:----:|:-----:|:---------:|:------:|:---------------:|
| 0    | [4,5] | -         | []     | [1,1,1,1,0,0]   |
| 1    | [5]   | 4         | [4]    | [0,1,1,1,0,0]   |
| 2    | [0]   | 5         | [4,5]  | [0,0,1,1,0,0]   |
| 3    | [2]   | 0         | [4,5,0]| [0,0,0,1,0,0]   |
| 4    | [3]   | 2         | [4,5,0,2]| [0,0,0,0,0,0] |
| 5    | [1]   | 3         | [4,5,0,2,3]| [0,0,0,0,0,0] |
| 6    | []    | 1         | [4,5,0,2,3,1]| Final |

**🎉 Hasil Final:** `[4, 5, 0, 2, 3, 1]`

---

## ✅ Keunggulan dan Keterbatasan

### 🌟 **Keunggulan:**
- ⚡ **Efisien** dengan kompleksitas O(V + E)
- 🎯 **Mudah dipahami** dan diimplementasikan
- 🔄 **Dapat mendeteksi siklus** secara otomatis
- 🛠️ **Aplikasi luas** dalam berbagai domain
- 📊 **Stabil** dan dapat diandalkan

### ⚠️ **Keterbatasan:**
- 🚫 **Tidak dapat digunakan** jika graf mengandung siklus
- 📋 **Hanya berlaku untuk DAG** (Directed Acyclic Graph)
- 🔄 **Hasil tidak unik** - bisa ada beberapa urutan valid
- 💾 **Membutuhkan memory tambahan** untuk queue dan in-degree array

---

## 🌍 Aplikasi dalam Dunia Nyata

### 💻 **Software Development:**
- 🔧 **Build Systems:** Maven, Gradle untuk dependency resolution
- 📦 **Package Managers:** npm, pip untuk mengatur urutan instalasi
- 🏗️ **Compilation:** Menentukan urutan kompilasi file sumber

### 📋 **Project Management:**
- 📅 **Task Scheduling:** Critical Path Method (CPM)
- 🎯 **Resource Planning:** Menentukan urutan tugas berdasarkan dependensi
- ⏰ **Timeline Management:** Project milestone sequencing

### 🎓 **Academic Systems:**
- 📚 **Course Prerequisites:** Menentukan urutan mata kuliah
- 🎖️ **Degree Requirements:** Menyusun curriculum pathway
- 📖 **Learning Dependencies:** Skill development sequences

---

## 📝 Kesimpulan

### 🎯 **Ringkasan Kahn's Algorithm:**

| Aspek | Detail |
|-------|--------|
| 🎪 **Konsep** | Topological sorting untuk DAG menggunakan in-degree |
| ⚡ **Efisiensi** | O(V + E) - sangat efisien untuk graf besar |
| 🛠️ **Implementasi** | Mudah dipahami dengan queue dan array in-degree |
| 🌍 **Aplikasi** | Penjadwalan, dependency resolution, kompilasi |
| ⚠️ **Batasan** | Hanya untuk DAG - tidak bisa menangani siklus |

### 🔑 **Key Takeaways:**
- **📊 In-degree dan queue** adalah kunci utama algoritma
- **🔄 Deteksi siklus** terintegrasi dalam proses
- **🎯 Cocok untuk dependency management** dalam skala besar
- **💻 Implementasi straightforward** di berbagai bahasa pemrograman

---

