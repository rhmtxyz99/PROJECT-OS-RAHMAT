# PROJECT-OS-RAHMAT
Project Based Learing 1
## LANGKAH 1 BUAT STRUKTUR DIREKTORI
### Berikut contoh Membuat Direkoti Project_File_Management:
[Deskripsi gambar]
(https://drive.google.com/file/d/1VrifpuUz2Jp4Wfr1SlaVp5pgvdoRKswu/view?usp=sharing)

```
#ubuntu@rahmat-nusi:~ mkdir Project_File_Management


```
### Berikut contoh perintah Berpindah Direktori ke Project_File_Management dan Membuat folder document images archives logs:
[Deskripsi gambar]
(https://drive.google.com/file/d/1DDWgvhBxUNTyGFEezjfUD7vHsP9RmIKo/view?usp=sharing)

```
cd Project_File_Management
```
```
mkdir document images archives logs
```

### Berikut contoh perintah membuat 20 file sample:
[Deskripsi gambar]
(https://drive.google.com/file/d/1Im_pQbvOmzU6o5ygdg1JaB2ZJ_dgs_gs/view?usp=sharing)

```
touch file{1..10}.txt file{11..15}.jpg file{16..18}.pdf file{19..20}.log
```
### Berikut contoh perintah memasukan sebuah teks ke masing masing file yang berbeda:
[Deskripsi gambar]
(https://drive.google.com/file/d/1Vc3sH__-GRKcUa8B3GqEuPG0NFIvnEoQ/view?usp=sharing)

```
 echo "Ini adalah dokumen contoh" > file1.txt
```
```
 echo "Data gambar" > file11.jpg
```
```
echo "Log sistem contoh" > file20.log
```

## LANGKAH 2 SCRIPT ORGANISASI FILE
### Buat Script Organisasi File di dalam direktori projek:
```
nano organisasi_file.sh
```
### ISI SCRIPT
[Deskripsi gambar]

(https://drive.google.com/file/d/1DwRIHzH-5jURXFBeDsO0hdLD_nOSd8ix/view?usp=sharing)

```
#!/bin/bash
# Script untuk mengorganisasi file berdasarkan ekstensi

# Pastikan berada di direktori proyek
cd ~/project_file_management

# Pindahkan file sesuai ekstensi
find . -maxdepth 1 -type f -name "*.txt" -exec mv {} documents/ \;
find . -maxdepth 1 -type f -name "*.jpg" -exec mv {} images/ \;
find . -maxdepth 1 -type f -name "*.pdf" -exec mv {} archives/ \;
find . -maxdepth 1 -type f -name "*.log" -exec mv {} logs/ \;

# Konfirmasi hasil
echo "File berhasil dipindahkan ke folder sesuai ekstensi!"
ls documents images archives logs
```
### Beri Hak Eksekusi:
```
chmod +x organisasi_file.sh
```
### Eksekusi Script Yang Telah Dibuat:
```
./organisasi_file.sh
```

## LANGKAH 3 FUNGSI PENCARIAN 
*Karena saya sudah punya script pencarian file yang bisa mencari berdasarkan nama, ukuran, dan isi konten. Jadi Saya Langsung Buat Fungsi pencariannya.*

### Buat file Search_file.sh
```
nano search_file.sh
```
[Deskripsi gambar]
(https://drive.google.com/file/d/11KP1W8-jfZsyK_wDd6aTQVj5xc_NzJAD/view?usp=sharing)

```
 #!/bin/bash
# Script: search_files.sh
# Fungsi: Mencari file berdasarkan nama, ukuran, atau konten

cd ~/project_file_management

echo "=== PENCARIAN FILE ==="
echo "1. Cari berdasarkan nama"
echo "2. Cari berdasarkan ukuran"
echo "3. Cari berdasarkan isi konten"
read -p "Pilih opsi (1/2/3): " opsi

case $opsi in
  1)
    read -p "Masukkan nama atau pola file (contoh: *.txt): " nama
    echo "Hasil pencarian:"
    find . -type f -name "$nama"
    ;;
  2)
    read -p "Masukkan batas ukuran (contoh: +1M untuk lebih dari 1MB, -500k untuk kurang dari 500KB): " ukuran
    echo "Hasil pencarian:"
    find . -type f -size "$ukuran"
    ;;
  3)
    read -p "Masukkan kata kunci yang ingin dicari dalam file: " keyword
    echo "Hasil pencarian:"
    grep -r "$keyword" .
    ;;
  *)
    echo "Opsi tidak valid."
    ;;
esac
```
### Beri Hak Eksekusi
```
chmod +x search_file.sh
```
### Eksekusi File Yang Telah Dibuat
```
./search_file.sh
```

## Langkah 4 – Generate Laporan File Sistem

*Script ini akan membuat laporan statistik tentang file di direktori proyek, lalu menyimpannya ke report.txt.*
### Buat file report.sh
```
nano report.sh
```
