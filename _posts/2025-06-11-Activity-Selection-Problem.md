# Activity Selection Problem (ASP) - Rangkuman Materi

---

## Definisi Activity Selection Problem (ASP)

**Activity Selection Problem (ASP)** adalah masalah klasik dalam ilmu komputer yang bertujuan untuk memilih serangkaian aktivitas yang dapat dilakukan dalam satu periode waktu, dengan batasan bahwa aktivitas-aktivitas tersebut tidak boleh tumpang tindih.

## Pentingnya ASP dalam Dunia Nyata

ASP sangat penting karena banyak ditemukan dalam berbagai situasi praktis, seperti:
- **Jadwal ruangan** - Mengatur penggunaan ruangan agar tidak bentrok
- **Wawancara kerja** - Menjadwalkan wawancara tanpa konflik waktu
- **Pengelolaan sumber daya** - Mengoptimalkan penggunaan sumber daya terbatas

## Batasan Masalah (Constraints)

1. **Tidak boleh ada tumpang tindih aktivitas**: Aktivitas yang dipilih harus memiliki waktu mulai yang lebih besar atau sama dengan waktu selesai aktivitas yang sebelumnya dipilih

2. **Hanya satu aktivitas dalam satu waktu**: Tidak dapat melakukan lebih dari satu aktivitas yang berlangsung pada waktu yang sama, sehingga harus memanfaatkan waktu dengan sebaik-baiknya

## Greedy Algorithm

### Definisi
**Greedy Algorithm** adalah pendekatan pemecahan masalah yang membuat keputusan terbaik atau optimal pada setiap langkah, dengan harapan bahwa keputusan-keputusan lokal yang optimal ini akan menghasilkan solusi yang global optimal.

### Mengapa ASP Cocok dengan Greedy Algorithm?

1. **Memiliki struktur optimalitas lokal**: Memilih aktivitas yang selesai lebih cepat memberikan ruang untuk aktivitas lain
2. **Solusi optimal terbentuk dari keputusan lokal**: Setiap pilihan aktivitas yang optimal secara lokal berkontribusi pada solusi optimal secara keseluruhan

## Strategi Penyelesaian dengan Algoritma Greedy

### Langkah-langkah Penyelesaian ASP:

1. **Urutkan aktivitas berdasarkan waktu selesai**
2. **Pilih aktivitas pertama** (yang selesai paling cepat)
3. **Pilih aktivitas berikutnya** jika waktu mulai ≥ waktu selesai aktivitas terakhir yang dipilih
4. **Ulangi langkah ketiga** sampai semua aktivitas diperiksa

## Contoh Penyelesaian

### Contoh 1:
**Data aktivitas:**
- Aktivitas A: [waktu mulai, waktu selesai]
- Aktivitas B: [waktu mulai, waktu selesai]
- Aktivitas C: [waktu mulai, waktu selesai]

**Proses:**
1. **Langkah 1**: Urutkan berdasarkan waktu selesai
2. **Langkah 2**: Pilih aktivitas pertama dalam daftar terurut
3. **Langkah 3**: Pilih aktivitas yang tidak tumpang tindih
4. **Langkah 4**: Ulangi proses

**Hasil**: Aktivitas yang terpilih adalah B, C dengan jumlah maksimal 2 aktivitas.

### Contoh 2 (Latihan):
**Hasil**: Aktivitas yang terpilih adalah E, D, F dengan jumlah maksimal 3 aktivitas.

## Implementasi dalam C++

### Komponen Utama Implementasi:

1. **Struktur Activity**: 
   - Mendefinisikan dua atribut: waktu mulai (`start`) dan waktu selesai (`finish`)

2. **Fungsi Compare**: 
   - Mengurutkan aktivitas berdasarkan waktu selesai menggunakan `sort()`

3. **Fungsi activitySelection**:
   - Pilih aktivitas pertama yang selesai lebih cepat
   - Gunakan loop untuk memilih aktivitas yang tidak tumpang tindih
   - Cetak aktivitas yang dipilih beserta waktu mulai dan selesai

4. **Bagian Main**: 
   - Mendefinisikan aktivitas dan memanggil fungsi `activitySelection`

### Contoh Output:
Aktivitas yang dipilih adalah A, C, dan D. Program berhasil memilih aktivitas sebanyak mungkin yang tidak saling bertumpang tindih, sesuai dengan prinsip greedy.

## Kesimpulan

Activity Selection Problem (ASP) adalah masalah optimasi yang sangat umum dalam dunia nyata. Dengan pendekatan greedy, masalah ini dapat diselesaikan secara efisien dengan cara:

- Memilih aktivitas yang selesai paling awal
- Memastikan tidak ada aktivitas yang bertabrakan
- Mengoptimalkan jumlah aktivitas yang dapat dilakukan

### Keunggulan Solusi Greedy untuk ASP:
1. **Kesederhanaan logika** - Algoritma mudah dipahami dan diimplementasikan
2. **Efisiensi waktu komputasi** - Kompleksitas waktu yang relatif rendah
3. **Aplikabilitas luas** - Dapat diterapkan dalam berbagai skenario penjadwalan

### Aplikasi Praktis:
- Pengelolaan kelas
- Penggunaan ruang
- Pengaturan wawancara
- Manajemen sumber daya terbatas

Pendekatan greedy untuk ASP memberikan solusi optimal dengan implementasi yang sederhana dan efisien, menjadikannya pilihan yang sangat baik untuk masalah penjadwalan dalam berbagai konteks.

---