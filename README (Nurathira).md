# Tugas Basis Data – Database Perpustakaan

Repository ini berisi tugas Basis Data yang mencakup:
- Membuat 1 database  
- Membuat minimal 3 tabel  
- Insert 15 data di setiap tabel  
- Menggunakan query WHERE dan BETWEEN

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
 Insert 15 Data per Tabel
Semua data lengkap berada di folder /sql
- create_table.sql  
- insert_data.sql  

---

 4. Contoh Query WHERE dan BETWEEN

 WHERE
```sql
SELECT * FROM anggota
WHERE nama LIKE 'A%';

SELECT * FROM buku
WHERE tahun > 2018;
```

 BETWEEN
```sql
SELECT * FROM buku
WHERE tahun BETWEEN 2016 AND 2020;

SELECT * FROM pinjam
WHERE tanggal_pinjam BETWEEN '2024-01-05' AND '2024-01-12';
```

