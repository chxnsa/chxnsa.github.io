# Huffman Coding - Rangkuman Materi

## Pendahuluan

**Huffman Coding** adalah algoritma kompresi data lossless yang dikembangkan oleh David A. Huffman pada tahun 1952. Algoritma ini menggunakan pendekatan greedy untuk membangun kode optimal yang meminimalkan rata-rata panjang kode untuk setiap karakter berdasarkan frekuensi kemunculannya.

## Definisi dan Konsep Dasar

### Apa itu Huffman Coding?
Huffman Coding adalah teknik encoding yang memberikan kode dengan panjang variabel untuk setiap karakter, di mana:
- **Karakter yang sering muncul** mendapat kode yang **lebih pendek**
- **Karakter yang jarang muncul** mendapat kode yang **lebih panjang**
- Hasil encoding dapat di-decode kembali tanpa kehilangan informasi (lossless)

### Prinsip Dasar
1. **Variable-Length Encoding**: Panjang kode berbeda untuk setiap karakter
2. **Prefix-Free Property**: Tidak ada kode yang menjadi prefix dari kode lain
3. **Optimal Encoding**: Meminimalkan total panjang encoded message

## Mengapa Huffman Coding Penting?

### Keunggulan:
- **Kompresi Optimal**: Memberikan hasil kompresi terbaik untuk encoding prefix-free
- **Lossless**: Data dapat dipulihkan 100% tanpa kehilangan
- **Efisien**: Algoritma relatif sederhana dengan kompleksitas yang baik
- **Widely Used**: Digunakan dalam berbagai aplikasi kompresi

### Aplikasi dalam Dunia Nyata:
- **JPEG compression** (dalam tahap tertentu)
- **ZIP files** dan algoritma kompresi lainnya
- **Network protocols** untuk menghemat bandwidth
- **Database compression** untuk menghemat storage
- **Multimedia compression** (audio, video)

## Algoritma Huffman Coding

### Langkah-langkah Pembentukan Huffman Tree:

1. **Hitung Frekuensi**: Tentukan frekuensi kemunculan setiap karakter
2. **Buat Node Leaf**: Setiap karakter menjadi node dengan frekuensinya
3. **Buat Priority Queue**: Urutkan node berdasarkan frekuensi (ascending)
4. **Bangun Tree**: 
   - Ambil dua node dengan frekuensi terkecil
   - Gabungkan menjadi node baru dengan frekuensi = jumlah keduanya
   - Node baru menjadi parent, dua node tadi menjadi children
   - Masukkan node baru ke priority queue
   - Ulangi sampai tersisa satu node (root)
5. **Generate Codes**: Traverse tree untuk mendapatkan kode setiap karakter

### Aturan Traversal untuk Kode:
- **Ke kiri**: tambahkan bit '0'
- **Ke kanan**: tambahkan bit '1'
- **Leaf node**: dapatkan kode lengkap untuk karakter

## Contoh Implementasi

### Contoh 1: Sederhana
**Input String**: "ABCABC"

#### Langkah 1: Hitung Frekuensi
| Karakter | Frekuensi |
|----------|-----------|
| A        | 2         |
| B        | 2         |
| C        | 2         |

#### Langkah 2: Bangun Huffman Tree
```
Initial Queue: A(2), B(2), C(2)

Step 1: Gabung A(2) + B(2) = Node1(4)
Queue: C(2), Node1(4)

Step 2: Gabung C(2) + Node1(4) = Root(6)
Tree Structure:
       Root(6)
      /        \
    C(2)     Node1(4)
             /        \
           A(2)      B(2)
```

#### Langkah 3: Generate Codes
- **C**: 0
- **A**: 10
- **B**: 11

#### Langkah 4: Encoding
"ABCABC" → "10 11 0 10 11 0" → "101101011110"

### Contoh 2: Lebih Kompleks
**Input String**: "AAABBC"

#### Langkah 1: Hitung Frekuensi
| Karakter | Frekuensi |
|----------|-----------|
| A        | 3         |
| B        | 2         |
| C        | 1         |

#### Langkah 2: Bangun Huffman Tree
```
Initial Queue: C(1), B(2), A(3)

Step 1: Gabung C(1) + B(2) = Node1(3)
Queue: A(3), Node1(3)

Step 2: Gabung A(3) + Node1(3) = Root(6)
Tree Structure:
       Root(6)
      /        \
    A(3)     Node1(3)
             /        \
           C(1)      B(2)
```

#### Langkah 3: Generate Codes
- **A**: 0
- **C**: 10
- **B**: 11

#### Langkah 4: Encoding
"AAABBC" → "0 0 0 11 11 10" → "000111110"

**Perbandingan Efisiensi**:
- Fixed-length (2 bits): 6 × 2 = 12 bits
- Huffman coding: 9 bits
- **Penghematan**: 25%

## Implementasi dalam Pseudocode

```
Algorithm BuildHuffmanTree(characters, frequencies):
    1. Create leaf nodes for each character with its frequency
    2. Create a priority queue (min-heap) with all leaf nodes
    3. While queue has more than one node:
        a. Extract two nodes with minimum frequency
        b. Create new internal node with these two as children
        c. Set frequency = sum of children frequencies
        d. Insert new node back to queue
    4. Return the remaining node as root

Algorithm GenerateCodes(root, code, codes):
    1. If root is leaf:
        codes[root.character] = code
        return
    2. If root has left child:
        GenerateCodes(root.left, code + "0", codes)
    3. If root has right child:
        GenerateCodes(root.right, code + "1", codes)

Algorithm HuffmanEncode(text):
    1. Count frequency of each character
    2. Build Huffman tree
    3. Generate codes for each character
    4. Replace each character with its code
    5. Return encoded string
```

## Analisis Kompleksitas

### Kompleksitas Waktu:
- **Menghitung frekuensi**: O(n), dimana n = panjang teks
- **Membangun tree**: O(k log k), dimana k = jumlah karakter unik
- **Generate codes**: O(k)
- **Encoding**: O(n)
- **Total**: **O(n + k log k)**

### Kompleksitas Ruang:
- **Tree storage**: O(k)
- **Code table**: O(k)
- **Priority queue**: O(k)
- **Total**: **O(k)**

## Decoding Huffman Code

### Proses Decoding:
1. **Mulai dari root** Huffman tree
2. **Baca bit encoding** satu per satu
3. **Traverse tree**:
   - Bit '0' → ke kiri
   - Bit '1' → ke kanan
4. **Saat mencapai leaf**: 
   - Output karakternya
   - Kembali ke root
5. **Ulangi** sampai semua bit selesai

### Contoh Decoding:
**Encoded**: "101101011110"
**Tree**: Sama seperti contoh 1

```
Bit: 1 0 1 1 0 1 0 1 1 1 1 0
     A   B C A B   C
```
**Result**: "ABCABC"

## Optimasi dan Varian

### Canonical Huffman Coding:
- **Standardisasi** representasi tree
- **Efisiensi storage** untuk menyimpan tree structure
- **Faster decoding** dengan lookup table

### Adaptive Huffman Coding:
- **Dynamic tree building** saat encoding/decoding
- **Tidak perlu** transmisi tree structure
- **Cocok** untuk streaming data

## Perbandingan dengan Algoritma Lain

| Algoritma | Type | Rasio Kompresi | Kompleksitas | Use Case |
|-----------|------|----------------|--------------|----------|
| **Huffman** | Lossless | Sedang | O(n log k) | Text, general |
| **LZ77** | Lossless | Tinggi | O(n) | ZIP, PNG |
| **RLE** | Lossless | Rendah | O(n) | Simple repetition |
| **Arithmetic** | Lossless | Tinggi | O(n) | High precision |

## Kelebihan dan Kekurangan

### Kelebihan:
1. **Optimal** untuk prefix-free encoding
2. **Lossless** compression
3. **Sederhana** untuk diimplementasikan
4. **Efisien** untuk data dengan distribusi frekuensi tidak uniform
5. **Mathematical foundation** yang kuat

### Kekurangan:
1. **Memerlukan dua pass**: hitung frekuensi, lalu encode
2. **Overhead** untuk transmisi tree structure
3. **Tidak cocok** untuk data dengan distribusi uniform
4. **Fixed tree** untuk seluruh data
5. **Tidak optimal** untuk very small files

## Implementasi Praktis

### Struktur Data yang Dibutuhkan:
```
Class Node:
    character: char or null
    frequency: integer
    left: Node
    right: Node
    isLeaf: boolean

Class PriorityQueue:
    - Min-heap based on frequency
    - Support insert, extractMin operations

Class HuffmanCoder:
    - buildTree(frequencies)
    - generateCodes(root)
    - encode(text)
    - decode(encodedText, tree)
```

### Optimasi Implementasi:
1. **Bit manipulation** untuk efisiensi storage
2. **Lookup tables** untuk faster encoding/decoding
3. **Memory management** untuk large files
4. **Streaming support** untuk real-time applications

## Kesimpulan

**Huffman Coding** adalah algoritma fundamental dalam kompresi data yang:

1. **Menggunakan prinsip greedy** untuk membangun encoding optimal
2. **Memberikan kompresi lossless** dengan efisiensi yang baik
3. **Sangat efektif** untuk data dengan distribusi frekuensi tidak merata
4. **Menjadi dasar** untuk banyak algoritma kompresi modern
5. **Memiliki aplikasi luas** dalam teknologi digital

### Poin Penting:
- **Greedy choice**: Selalu gabungkan dua node dengan frekuensi terkecil
- **Optimal substructure**: Solusi optimal terdiri dari solusi optimal subproblem
- **Prefix-free property**: Memastikan decoding yang tidak ambigu
- **Trade-off**: Kompleksitas tambahan vs efisiensi kompresi

Huffman Coding tetap relevan dan penting dalam era digital modern, terutama dalam aplikasi yang memerlukan kompresi data yang efisien dan dapat diandalkan.