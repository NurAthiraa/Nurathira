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
sql

Microsoft Windows [Version 10.0.19045.6456]
(c) Microsoft Corporation. All rights reserved.

C:\xampp\mysql\bin>mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 10.4.32-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> CREATE DATABASE perpustakaan;
Query OK, 1 row affected (0.003 sec)

MariaDB [(none)]> USE perpustakaan;
Database changed
MariaDB [perpustakaan]> CREATE TABLE anggota (
    ->     id_anggota INT AUTO_INCREMENT PRIMARY KEY,
    ->     nama VARCHAR(100),
    ->     alamat VARCHAR(150),
    ->     no_hp VARCHAR(20)
    -> );
Query OK, 0 rows affected (0.024 sec)

MariaDB [perpustakaan]> CREATE TABLE buku (
    ->     id_buku INT AUTO_INCREMENT PRIMARY KEY,
    ->     judul VARCHAR(150),
    ->     penulis VARCHAR(100),
    ->     tahun_terbit INT
    -> );
Query OK, 0 rows affected (0.019 sec)

MariaDB [perpustakaan]> CREATE TABLE peminjaman (
    ->     id_peminjaman INT AUTO_INCREMENT PRIMARY KEY,
    ->     id_anggota INT,
    ->     id_buku INT,
    ->     tanggal_pinjam DATE,
    ->     tanggal_kembali DATE,
    ->     FOREIGN KEY (id_anggota) REFERENCES anggota(id_anggota),
    ->     FOREIGN KEY (id_buku) REFERENCES buku(id_buku)
    -> );
Query OK, 0 rows affected (0.047 sec)

MariaDB [perpustakaan]> INSERT INTO anggota (nama, alamat, no_hp) VALUES
    -> ('Andi', 'Jl. Kenanga No.1', '0812100001'),
    -> ('Budi', 'Jl. Mawar No.2', '0812100002'),
    -> ('Cici', 'Jl. Melati No.3', '0812100003'),
    -> ('Doni', 'Jl. Dahlia No.4', '0812100004'),
    -> ('Eka', 'Jl. Anggrek No.5', '0812100005'),
    -> ('Fina', 'Jl. Flamboyan No.6', '0812100006'),
    -> ('Gilang', 'Jl. Kamboja No.7', '0812100007'),
    -> ('Hana', 'Jl. Teratai No.8', '0812100008'),
    -> ('Indra', 'Jl. Cempaka No.9', '0812100009'),
    -> ('Joko', 'Jl. Rambutan No.10', '0812100010'),
    -> ('Kiki', 'Jl. Durian No.11', '0812100011'),
    -> ('Lina', 'Jl. Mangga No.12', '0812100012'),
    -> ('Mika', 'Jl. Nangka No.13', '0812100013'),
    -> ('Nina', 'Jl. Matoa No.14', '0812100014'),
    -> ('Omar', 'Jl. Jeruk No.15', '0812100015');
Query OK, 15 rows affected (0.015 sec)
Records: 15  Duplicates: 0  Warnings: 0

MariaDB [perpustakaan]> INSERT INTO buku (judul, penulis, tahun_terbit) VALUES
    -> ('Belajar Java Dasar', 'R. Saputra', 2020),
    -> ('Algoritma & Struktur Data', 'D. Widodo', 2019),
    -> ('Basis Data Lanjut', 'A. Wirawan', 2021),
    -> ('Matematika Diskrit', 'R. Hartono', 2018),
    -> ('Pemrograman Web', 'S. Ramadhan', 2022),
    -> ('Sistem Operasi', 'I. Kurnia', 2017),
    -> ('Jaringan Komputer', 'F. Nugroho', 2020),
    -> ('Kecerdasan Buatan', 'U. Pratama', 2023),
    -> ('Machine Learning', 'T. Ananda', 2021),
    -> ('Statistik Dasar', 'B. Hidayat', 2016),
    -> ('Pemrograman Python', 'V. Putri', 2022),
    -> ('Pemrograman C++', 'H. Abdul', 2018),
    -> ('Rekayasa Perangkat Lunak', 'M. Suryono', 2020),
    -> ('Analisis Data', 'W. Kurniawan', 2023),
    -> ('Manajemen Proyek IT', 'S. Kurnia', 2021);
Query OK, 15 rows affected (0.018 sec)
Records: 15  Duplicates: 0  Warnings: 0

MariaDB [perpustakaan]> INSERT INTO peminjaman (id_anggota, id_buku, tanggal_pinjam, tanggal_kembali) VALUES
    -> (1, 1, '2025-01-01', '2025-01-08'),
    -> (2, 2, '2025-01-02', '2025-01-09'),
    -> (3, 3, '2025-01-03', '2025-01-10'),
    -> (4, 4, '2025-01-04', '2025-01-11'),
    -> (5, 5, '2025-01-05', '2025-01-12'),
    -> (6, 6, '2025-01-06', '2025-01-13'),
    -> (7, 7, '2025-01-07', '2025-01-14'),
    -> (8, 8, '2025-01-08', '2025-01-15'),
    -> (9, 9, '2025-01-09', '2025-01-16'),
    -> (10, 10, '2025-01-10', '2025-01-17'),
    -> (11, 11, '2025-01-11', '2025-01-18'),
    -> (12, 12, '2025-01-12', '2025-01-19'),
    -> (13, 13, '2025-01-13', '2025-01-20'),
    -> (14, 14, '2025-01-14', '2025-01-21'),
    -> (15, 15, '2025-01-15', '2025-01-22');
Query OK, 15 rows affected (0.015 sec)
Records: 15  Duplicates: 0  Warnings: 0

MariaDB [perpustakaan]> DESC anggota;
+------------+--------------+------+-----+---------+----------------+
| Field      | Type         | Null | Key | Default | Extra          |
+------------+--------------+------+-----+---------+----------------+
| id_anggota | int(11)      | NO   | PRI | NULL    | auto_increment |
| nama       | varchar(100) | YES  |     | NULL    |                |
| alamat     | varchar(150) | YES  |     | NULL    |                |
| no_hp      | varchar(20)  | YES  |     | NULL    |                |
+------------+--------------+------+-----+---------+----------------+
4 rows in set (0.033 sec)

MariaDB [perpustakaan]> SELECT * FROM anggota;
+------------+--------+--------------------+------------+
| id_anggota | nama   | alamat             | no_hp      |
+------------+--------+--------------------+------------+
|          1 | Andi   | Jl. Kenanga No.1   | 0812100001 |
|          2 | Budi   | Jl. Mawar No.2     | 0812100002 |
|          3 | Cici   | Jl. Melati No.3    | 0812100003 |
|          4 | Doni   | Jl. Dahlia No.4    | 0812100004 |
|          5 | Eka    | Jl. Anggrek No.5   | 0812100005 |
|          6 | Fina   | Jl. Flamboyan No.6 | 0812100006 |
|          7 | Gilang | Jl. Kamboja No.7   | 0812100007 |
|          8 | Hana   | Jl. Teratai No.8   | 0812100008 |
|          9 | Indra  | Jl. Cempaka No.9   | 0812100009 |
|         10 | Joko   | Jl. Rambutan No.10 | 0812100010 |
|         11 | Kiki   | Jl. Durian No.11   | 0812100011 |
|         12 | Lina   | Jl. Mangga No.12   | 0812100012 |
|         13 | Mika   | Jl. Nangka No.13   | 0812100013 |
|         14 | Nina   | Jl. Matoa No.14    | 0812100014 |
|         15 | Omar   | Jl. Jeruk No.15    | 0812100015 |
+------------+--------+--------------------+------------+
15 rows in set (0.009 sec)

MariaDB [perpustakaan]> SELECT * FROM buku;
+---------+---------------------------+--------------+--------------+
| id_buku | judul                     | penulis      | tahun_terbit |
+---------+---------------------------+--------------+--------------+
|       1 | Belajar Java Dasar        | R. Saputra   |         2020 |
|       2 | Algoritma & Struktur Data | D. Widodo    |         2019 |
|       3 | Basis Data Lanjut         | A. Wirawan   |         2021 |
|       4 | Matematika Diskrit        | R. Hartono   |         2018 |
|       5 | Pemrograman Web           | S. Ramadhan  |         2022 |
|       6 | Sistem Operasi            | I. Kurnia    |         2017 |
|       7 | Jaringan Komputer         | F. Nugroho   |         2020 |
|       8 | Kecerdasan Buatan         | U. Pratama   |         2023 |
|       9 | Machine Learning          | T. Ananda    |         2021 |
|      10 | Statistik Dasar           | B. Hidayat   |         2016 |
|      11 | Pemrograman Python        | V. Putri     |         2022 |
|      12 | Pemrograman C++           | H. Abdul     |         2018 |
|      13 | Rekayasa Perangkat Lunak  | M. Suryono   |         2020 |
|      14 | Analisis Data             | W. Kurniawan |         2023 |
|      15 | Manajemen Proyek IT       | S. Kurnia    |         2021 |
+---------+---------------------------+--------------+--------------+
15 rows in set (0.001 sec)

MariaDB [perpustakaan]> SELECT * FROM peminjaman;
+---------------+------------+---------+----------------+-----------------+
| id_peminjaman | id_anggota | id_buku | tanggal_pinjam | tanggal_kembali |
+---------------+------------+---------+----------------+-----------------+
|             1 |          1 |       1 | 2025-01-01     | 2025-01-08      |
|             2 |          2 |       2 | 2025-01-02     | 2025-01-09      |
|             3 |          3 |       3 | 2025-01-03     | 2025-01-10      |
|             4 |          4 |       4 | 2025-01-04     | 2025-01-11      |
|             5 |          5 |       5 | 2025-01-05     | 2025-01-12      |
|             6 |          6 |       6 | 2025-01-06     | 2025-01-13      |
|             7 |          7 |       7 | 2025-01-07     | 2025-01-14      |
|             8 |          8 |       8 | 2025-01-08     | 2025-01-15      |
|             9 |          9 |       9 | 2025-01-09     | 2025-01-16      |
|            10 |         10 |      10 | 2025-01-10     | 2025-01-17      |
|            11 |         11 |      11 | 2025-01-11     | 2025-01-18      |
|            12 |         12 |      12 | 2025-01-12     | 2025-01-19      |
|            13 |         13 |      13 | 2025-01-13     | 2025-01-20      |
|            14 |         14 |      14 | 2025-01-14     | 2025-01-21      |
|            15 |         15 |      15 | 2025-01-15     | 2025-01-22      |
+---------------+------------+---------+----------------+-----------------+
15 rows in set (0.001 sec)

MariaDB [perpustakaan]> SELECT COUNT(*) FROM anggota;
+----------+
| COUNT(*) |
+----------+
|       15 |
+----------+
1 row in set (0.010 sec)

MariaDB [perpustakaan]> SELECT * FROM anggota LIMIT 5;
+------------+------+------------------+------------+
| id_anggota | nama | alamat           | no_hp      |
+------------+------+------------------+------------+
|          1 | Andi | Jl. Kenanga No.1 | 0812100001 |
|          2 | Budi | Jl. Mawar No.2   | 0812100002 |
|          3 | Cici | Jl. Melati No.3  | 0812100003 |
|          4 | Doni | Jl. Dahlia No.4  | 0812100004 |
|          5 | Eka  | Jl. Anggrek No.5 | 0812100005 |
+------------+------+------------------+------------+
5 rows in set (0.001 sec)

MariaDB [perpustakaan]> SELECT * FROM anggota
    -> WHERE nama LIKE 'A%';
+------------+------+------------------+------------+
| id_anggota | nama | alamat           | no_hp      |
+------------+------+------------------+------------+
|          1 | Andi | Jl. Kenanga No.1 | 0812100001 |
+------------+------+------------------+------------+
1 row in set (0.009 sec)

MariaDB [perpustakaan]> SELECT * FROM buku
    -> WHERE penulis = 'R. Saputra';
+---------+--------------------+------------+--------------+
| id_buku | judul              | penulis    | tahun_terbit |
+---------+--------------------+------------+--------------+
|       1 | Belajar Java Dasar | R. Saputra |         2020 |
+---------+--------------------+------------+--------------+
1 row in set (0.009 sec)

MariaDB [perpustakaan]> SELECT * FROM peminjaman
    -> WHERE id_anggota = 5;
+---------------+------------+---------+----------------+-----------------+
| id_peminjaman | id_anggota | id_buku | tanggal_pinjam | tanggal_kembali |
+---------------+------------+---------+----------------+-----------------+
|             5 |          5 |       5 | 2025-01-05     | 2025-01-12      |
+---------------+------------+---------+----------------+-----------------+
1 row in set (0.010 sec)

MariaDB [perpustakaan]> SELECT * FROM buku
    -> WHERE tahun_terbit BETWEEN 2019 AND 2022;
+---------+---------------------------+-------------+--------------+
| id_buku | judul                     | penulis     | tahun_terbit |
+---------+---------------------------+-------------+--------------+
|       1 | Belajar Java Dasar        | R. Saputra  |         2020 |
|       2 | Algoritma & Struktur Data | D. Widodo   |         2019 |
|       3 | Basis Data Lanjut         | A. Wirawan  |         2021 |
|       5 | Pemrograman Web           | S. Ramadhan |         2022 |
|       7 | Jaringan Komputer         | F. Nugroho  |         2020 |
|       9 | Machine Learning          | T. Ananda   |         2021 |
|      11 | Pemrograman Python        | V. Putri    |         2022 |
|      13 | Rekayasa Perangkat Lunak  | M. Suryono  |         2020 |
|      15 | Manajemen Proyek IT       | S. Kurnia   |         2021 |
+---------+---------------------------+-------------+--------------+
9 rows in set (0.000 sec)

MariaDB [perpustakaan]> SELECT * FROM anggota
    -> WHERE id_anggota BETWEEN 5 AND 10;
+------------+--------+--------------------+------------+
| id_anggota | nama   | alamat             | no_hp      |
+------------+--------+--------------------+------------+
|          5 | Eka    | Jl. Anggrek No.5   | 0812100005 |
|          6 | Fina   | Jl. Flamboyan No.6 | 0812100006 |
|          7 | Gilang | Jl. Kamboja No.7   | 0812100007 |
|          8 | Hana   | Jl. Teratai No.8   | 0812100008 |
|          9 | Indra  | Jl. Cempaka No.9   | 0812100009 |
|         10 | Joko   | Jl. Rambutan No.10 | 0812100010 |
+------------+--------+--------------------+------------+
6 rows in set (0.001 sec)

MariaDB [perpustakaan]> SELECT * FROM peminjaman
    -> WHERE tanggal_pinjam BETWEEN '2025-01-05' AND '2025-01-10';
+---------------+------------+---------+----------------+-----------------+
| id_peminjaman | id_anggota | id_buku | tanggal_pinjam | tanggal_kembali |
+---------------+------------+---------+----------------+-----------------+
|             5 |          5 |       5 | 2025-01-05     | 2025-01-12      |
|             6 |          6 |       6 | 2025-01-06     | 2025-01-13      |
|             7 |          7 |       7 | 2025-01-07     | 2025-01-14      |
|             8 |          8 |       8 | 2025-01-08     | 2025-01-15      |
|             9 |          9 |       9 | 2025-01-09     | 2025-01-16      |
|            10 |         10 |      10 | 2025-01-10     | 2025-01-17      |
+---------------+------------+---------+----------------+-----------------+
6 rows in set (0.007 sec)

MariaDB [perpustakaan]> SELECT * FROM buku
    -> WHERE tahun_terbit BETWEEN 2019 AND 2022
    ->   AND penulis LIKE '%a%';
+---------+---------------------+-------------+--------------+
| id_buku | judul               | penulis     | tahun_terbit |
+---------+---------------------+-------------+--------------+
|       1 | Belajar Java Dasar  | R. Saputra  |         2020 |
|       3 | Basis Data Lanjut   | A. Wirawan  |         2021 |
|       5 | Pemrograman Web     | S. Ramadhan |         2022 |
|       9 | Machine Learning    | T. Ananda   |         2021 |
|      15 | Manajemen Proyek IT | S. Kurnia   |         2021 |
+---------+---------------------+-------------+--------------+
5 rows in set (0.001 sec)

MariaDB [perpustakaan]>


