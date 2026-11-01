# Pertemuan 12 - File I/O dan Error Handling

Nama: Aulia Citra
NIM: 2225250012
Kelas: 3F
Mata Kuliah: Algoritma dan Pemrograman
Program Studi: S1 Pendidikan Matematika FKIP Untirta

## Tujuan
Membaca, memvalidasi, mengolah, dan menulis data file menggunakan Python serta menangani FileNotFoundError dan ValueError.

## Isi Folder
- latihan/: enam program latihan file I/O dan error handling.
- tugas/rekap_nilai_file.py: program Tugas 5.
- data/catatan.txt: hasil latihan menulis dan menambahkan teks.
- data/nilai.txt: data input rekap nilai.
- data/hasil_rekap.txt: hasil rekap nilai.

## Format File Input
Setiap baris menggunakan format NIM,nilai dengan pemisah koma. Nilai desimal menggunakan titik.

Contoh data Tugas 5:
```text
A001,85
A002,78
A003,92
A004,abc
A005,74
A006,88
```

Baris kosong dilewati. Baris dengan format atau nilai yang tidak valid dilaporkan dan dilewati.

## Cara Menjalankan
Buka terminal dari folder utama proyek, lalu jalankan:
```powershell
py tugas/rekap_nilai_file.py
```

Pada laptop saya digunakan perintah py karena perintah python belum mengarah ke instalasi Python.

Untuk menjalankan latihan:
```powershell
py latihan/01_tulis_file.py
py latihan/02_baca_file.py
py latihan/03_append_file.py
py latihan/04_proses_baris.py
py latihan/05_file_not_found.py
py latihan/06_value_error.py
```

Latihan 4 menggunakan data yang seluruh nilainya valid, seperti contoh:
```text
A001,85
A002,78
A003,92
A004,74
```

Jika ingin menguji ulang Latihan 4, simpan sementara isi data Tugas 5, gunakan data latihan di atas, lalu kembalikan data Tugas 5 setelah selesai.

Latihan 1 menimpa isi catatan.txt. Latihan 3 menambahkan satu baris setiap kali dijalankan. Latihan 6 meminta input melalui terminal.

## Alur Program Tugas 5
1. Fungsi baca_data() membaca file dengan mode r dan encoding UTF-8.
2. Setiap baris dibersihkan menggunakan strip().
3. Baris kosong dilewati.
4. Baris dipisahkan menjadi NIM dan nilai menggunakan split(",").
5. Nilai dikonversi menjadi float dan record valid disimpan dalam list berisi tuple.
6. Fungsi tulis_rekap() menghitung statistik dan menulis hasil dengan mode w.
7. Nilai minimal 60 dihitung sebagai lulus.

## Error yang Ditangani
- FileNotFoundError: menampilkan pesan ketika file input tidak ditemukan.
- ValueError: melaporkan dan melewati baris yang formatnya tidak sesuai atau nilainya tidak dapat dikonversi menjadi float.

## Hasil Rekap Data Contoh
```text
Jumlah data valid: 5
Rata-rata: 83.40
Minimum: 74.00
Maksimum: 92.00
Jumlah lulus: 5
```

## Test Case Tugas 5

| Kasus | Kondisi | Hasil yang Diharapkan | Hasil Aktual | Status |
|---|---|---|---|---|
| Normal | A004,abc diganti A004,80; seluruh enam baris valid | 6 data, rata-rata 82.83, minimum 74.00, maksimum 92.00, lulus 6 | Sesuai hasil yang diharapkan | Berhasil |
| File hilang | nilai.txt sementara diubah menjadi nilai_cadangan.txt | Pesan file tidak ditemukan dan tidak ada traceback | Pesan File tidak ditemukan: data/nilai.txt; program selesai tanpa traceback | Berhasil |
| Nilai invalid | Menggunakan data contoh dengan A004,abc | Baris keempat dilewati; 5 data valid, rata-rata 83.40, minimum 74.00, maksimum 92.00, lulus 5 | Sesuai hasil yang diharapkan | Berhasil |
| Baris kosong | Menambahkan baris kosong pada data normal | Baris kosong dilewati; hasil rekap tetap sama dengan kasus normal | Sesuai hasil yang diharapkan | Berhasil |
| Batas lulus | A004,80 pada data normal diganti A004,60 | 6 data, rata-rata 79.50, minimum 60.00, maksimum 92.00, lulus 6 | Sesuai hasil yang diharapkan | Berhasil |

Setelah pengujian, nama file dan data input dikembalikan ke contoh Tugas 5, lalu program dijalankan kembali untuk memperbarui hasil_rekap.txt.

## Refleksi
Saya menemukan bahwa nilai berupa teks seperti abc tidak dapat dikonversi menjadi float. Program menangani kondisi tersebut menggunakan except ValueError pada setiap baris, sehingga baris yang salah dilewati dan data lain tetap diproses. Saya juga memahami bahwa mode w menimpa isi file, sedangkan mode a menambahkan data di akhir file.

## Sumber dan Bantuan
- Bahan Ajar Pertemuan 12: File Input-Output dan Penanganan Error Dasar, Dr. Aan Hendrayana, S.Si., M.Pd., Tahun Ajaran 2026/2027 Ganjil.
- Contoh kode latihan dan solusi ringkas Tugas 5 mengacu pada bahan ajar.
- Bantuan ChatGPT digunakan untuk panduan langkah praktik, pengecekan hasil, dan penyusunan dokumentasi.

Data yang digunakan merupakan data contoh dari bahan ajar.