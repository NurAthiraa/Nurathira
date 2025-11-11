# Tugas Basis Data – Database Perpustakaan

Repository ini berisi tugas Basis Data yang mencakup:
- Membuat 1 database  
- Membuat minimal 3 tabel  
- Insert 15 data di setiap tabel  
- Menggunakan query **WHERE** dan **BETWEEN**

---

 1. Nama Database
`perpustakaan`

---

 2. Struktur Tabel

 Tabel: anggota
- id_anggota (INT, PRIMARY KEY)  
- nama (VARCHAR)  
- alamat (VARCHAR)  
- no_hp (VARCHAR)  

 Tabel: buku
- id_buku (INT, PRIMARY KEY)  
- judul (VARCHAR)  
- penulis (VARCHAR)  
- tahun (INT)

 Tabel: pinjam
- id_pinjam (INT, PRIMARY KEY)  
- id_anggota (INT, FOREIGN KEY)  
- id_buku (INT, FOREIGN KEY)  
- tanggal_pinjam (DATE)

---

 3. Perintah SQL Dasar

 Membuat database
```sql
CREATE DATABASE perpustakaan;
USE perpustakaan;
```

---

 Membuat Tabel
```sql
CREATE TABLE anggota (
  id_anggota INT PRIMARY KEY,
  nama VARCHAR(100),
  alamat VARCHAR(100),
  no_hp VARCHAR(20)
);

CREATE TABLE buku (
  id_buku INT PRIMARY KEY,
  judul VARCHAR(100),
  penulis VARCHAR(100),
  tahun INT
);

CREATE TABLE pinjam (
  id_pinjam INT PRIMARY KEY,
  id_anggota INT,
  id_buku INT,
  tanggal_pinjam DATE,
  FOREIGN KEY (id_anggota) REFERENCES anggota(id_anggota),
  FOREIGN KEY (id_buku) REFERENCES buku(id_buku)
);
```

---

 4. Insert 15 Data ke Setiap Tabel

 Tabel **anggota**
```sql
INSERT INTO anggota VALUES
(1, 'Alya', 'Bandung', '081111111'),
(2, 'Budi', 'Jakarta', '082222222'),
(3, 'Citra', 'Surabaya', '083333333'),
(4, 'Dina', 'Bandung', '084444444'),
(5, 'Eko', 'Medan', '085555555'),
(6, 'Fani', 'Padang', '086666666'),
(7, 'Gilang', 'Bogor', '087777777'),
(8, 'Hana', 'Malang', '088888888'),
(9, 'Indra', 'Bali', '089999999'),
(10,'Joko', 'Solo', '080000001'),
(11,'Kiki', 'Depok', '080000002'),
(12,'Lala', 'Makassar', '080000003'),
(13,'Miko', 'Pontianak', '080000004'),
(14,'Nina', 'Palembang', '080000005'),
(15,'Omar', 'Lombok', '080000006');
```

---

 Tabel **buku**
```sql
INSERT INTO buku VALUES
(1, 'Pemrograman Java', 'Andi', 2018),
(2, 'Basis Data', 'Bambang', 2020),
(3, 'Algoritma', 'Cindy', 2016),
(4, 'Jaringan Komputer', 'Dodi', 2019),
(5, 'Sistem Operasi', 'Eka', 2017),
(6, 'AI Dasar', 'Fery', 2021),
(7, 'Machine Learning', 'Gina', 2022),
(8, 'Struktur Data', 'Hadi', 2015),
(9, 'Pemrograman Web', 'Indah', 2018),
(10,'Android Dasar', 'Jamal', 2019),
(11,'Data Mining', 'Koko', 2014),
(12,'Etika Teknologi', 'Lina', 2020),
(13,'IoT Pemula', 'Maya', 2021),
(14,'Keamanan Siber', 'Nando', 2017),
(15,'Cloud Computing', 'Oscar', 2022);
```

---

 Tabel **pinjam**
```sql
INSERT INTO pinjam VALUES
(1, 1, 1, '2024-01-01'),
(2, 2, 3, '2024-01-02'),
(3, 3, 2, '2024-01-03'),
(4, 4, 5, '2024-01-04'),
(5, 5, 4, '2024-01-05'),
(6, 6, 6, '2024-01-06'),
(7, 7, 7, '2024-01-07'),
(8, 8, 8, '2024-01-08'),
(9, 9, 9, '2024-01-09'),
(10,10,10,'2024-01-10'),
(11,11,11,'2024-01-11'),
(12,12,12,'2024-01-12'),
(13,13,13,'2024-01-13'),
(14,14,14,'2024-01-14'),
(15,15,15,'2024-01-15');
```

---

 5. Contoh Query WHERE dan BETWEEN

 WHERE
```sql
SELECT * FROM anggota
WHERE nama LIKE 'A%';

SELECT * FROM buku
WHERE tahun > 2018;

SELECT * FROM peminjaman
WHERE id_anggota = 5;

```

 BETWEEN
```sql
SELECT * FROM buku
WHERE tahun_terbit BETWEEN 2019 AND 2022;

SELECT * FROM anggota
WHERE id_anggota BETWEEN 5 AND 10;

SELECT * FROM peminjaman
WHERE tanggal_pinjam BETWEEN '2025-01-05' AND '2025-01-10';



```

---
