
# Tugas Praktikum { Pertemuan ke 12 } <img src=https://logos-download.com/wp-content/uploads/2016/05/MySQL_logo_logotype.png width="130px" >


|**Nama**|**NIM**|**Kelas**|**Matkul**|
|----|---|-----|------|
|Oktavia Rizkha Kurniawati|312310509|TI.23.A5|Basis Data|

# Soal Latihan Praktikum 

![alt text](Screenshot/T1.png)

![alt text](Screenshot/T2.png)

![alt text](Screenshot/T3.png)

![alt text](Screenshot/T4.png)

![alt text](Screenshot/T5.png)

## Latihan

- Lakukan JOIN table Mahasiswa dan Dosen.
- Lakukan JOIN tabel Matakuliah dan Dosen.
- Lakukan JOIN table JadwalMengajar, Dosen, dan Matakuliah.
- Lakukan JOIN tabel KrsMahasiswa, Mahasiswa, Matakuliah, dan Dosen.

## Buat Script SQL JOIN Table berdasarkan skema data diatas.

```
CREATE DATABASE Praktikum5;

USE Praktikum5;

CREATE TABLE Dosen(
kd_ds VARCHAR(10) NOT NULL PRIMARY KEY,
nama VARCHAR(25) NOT NULL
);

INSERT INTO Dosen (`kd_ds`, `nama`) VALUES
('DS001', 'Nofal Arianto');
('DS002', 'Ario Talib');
('DS003', 'Ayu Rahmadina');
('DS004', 'Ratna Kumala');
('DS005', 'Vika Prasetyo');

SELECT*FROM Dosen;
`````
***Output :***

![Screenshot 2024-05-29 192718](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/a40c7220-8eee-470d-a931-4e018750385f)


`````
CREATE TABLE Mahasiswa(
nim VARCHAR(10) NOT NULL,
nama VARCHAR(25) NOT NULL,
jk enum ('L','P'),
tgl_lahir VARCHAR(15),
jalan VARCHAR(30) ,
Kota VARCHAR(15),
kodepos VARCHAR(15),
no_hp VARCHAR(15),
kd_ds VARCHAR(10)
);

INSERT INTO Mahasiwa (`nim`, `nama`, `jk`, `tgl_lahir`, 'jalan',`Kota`,'kodepos','nohp',`kd_ds`) VALUES
('1812345', 'Ari Santoso', 'L', '1999-10-11', 'Bekasi', 'DS002'),
('1823456', 'Dina Marlina', 'P', '1998-11-20', 'Jakarta'),
('1834567', 'Rahmat Hidayat', 'L', '1999-05-10', 'Bekasi'),
('1845678', 'Jaka Sampurna', 'L', '2000-10-19', 'Cikarang'),
('1856789', 'Tia Lestari', 'P', '1999-02-15', 'Karawang'),
('1867890', 'Anton Sinaga', 'L', '1998-06-22', '', 'Bekasi'),
('1912345', 'Listia Nastiti', 'P', '2001-10-23', 'Jakarta'),
('1923456', 'Amira Jarisa', 'P', '2001-01-24', 'Karawang', 'DS004'),
('1934567', 'Laksana Mardito', 'L', '1999-04-14', 'Cikarang'),
('1945678', 'Jura Marsina', 'p', '2000-05-10', 'Cikarang'),
('1956789', 'Dadi Martani', 'L', '2001-08-29', 'Bekasi', 'DS005'),
('1967890', 'Bayu Laksono', 'L', '1999-07-22', 'Cikarang', 'DS004'),

SELECT * FROM Mahasiswa;

`````
Output :

![Screenshot 2024-05-29 192902](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/3accd70c-99f8-4605-8124-e4711b920f7d)


`````
CREATE TABLE Matakuliah(
kd_mk VARCHAR(10) NOT NULL PRIMARY KEY,
nama VARCHAR(25) NOT NULL,
sks VARCHAR(30)
);

INSERT INTO Matakuliah VALUES
('MK001', 'Algoritma Dan Pemrogaman', 3),
('MK002', 'Praktikum Algoritma Dan Pemrograman', 1),
('MK003', 'Teknologi Basis Data', 3),
('MK004', 'Praktikum Teknologi Basis Data', 1),
('MK005', 'Pemrograman Dasar', 3),
('MK006', 'Pemrograman Berorientasi Objek', 3),
('MK007', 'Struktur Data', 3),
('MK008', 'Arsitektur Komputer', 2);

SELECT * FROM Matakuliah;
`````
Output :

![Screenshot 2024-05-29 192918](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/a58ce528-cc29-41d6-8000-b4d84735de91)


`````
CREATE TABLE JadwalMengajar(
kd_mk VARCHAR(50) NOT NULL,
kd_ds VARCHAR(50) NOT NULL,
hari ENUM('Senin', 'Selasa', 'Rabu', 'Kamis'),
jam TIME NOT NULL,
ruang VARCHAR(50),
PRIMARY KEY(kd_mk, kd_ds)
);

INSERT INTO JadwalMengajar VALUES
('MK001', 'DS002', 'Senin', '10:00:00', '102'),
('MK002', 'DS002', 'Senin', '13:00:00', 'Lab. 01'),
('MK003', 'DS001', 'Selasa', '08:00:00', '201'),
('MK004', 'DS001', 'Rabu', '10:00:00', 'Lab. 02'),
('MK005', 'DS003', 'Selasa', '10:00:00', 'Lab. 01'),
('MK006', 'DS004', 'Kamis', '09:00:00', 'Lab. 03'),
('MK007', 'DS005', 'Rabu', '08:00:00', '102'),
('MK008', 'DS005', 'Kamis', '13:00:00', '201');

SELECT*FROM JadwalMengajar;

`````
Output :

![Screenshot 2024-05-29 192934](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/8ab2c09d-97d4-4bbb-838b-751ac5b9801b)


`````
CREATE TABLE KRSMahasiswa(
nim VARCHAR(10) NOT NULL,
kd_mk VARCHAR(50) NOT NULL,
kd_ds VARCHAR(50) NOT NULL,
semester VARCHAR(30) NOT NULL,
nilai VARCHAR(50) DEFAULT NULL
);

INSERT INTO KRSMahasiswa VALUES
(1823456, 'MK001', 'DS002', 3, NULL),
(1823456, 'MK002', 'DS002', 1, NULL),
(1823456, 'MK003', 'DS001', 3, NULL),
(1823456, 'MK004', 'DS001', 3, NULL),
(1823456, 'MK007', 'DS005', 3, NULL),
(1823456, 'MK008', 'DS005', 3, NULL);

SELECT * FROM KRSMahasiswa;
`````
Output :

![Screenshot 2024-05-29 192949](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/ffe476df-c73a-4d0b-9006-b558fcf33a3f)


# Latihan
- JOIN table Mahasiswa dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama, Mahasiswa.jk, Dosen.nama AS "Dosen PA"
FROM Mahasiswa INNER JOIN Dosen ON Dosen.kd_ds = Mahasiswa.kd_ds;
`````
Output :

![Screenshot 2024-05-29 193007](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/f3e29444-2de5-4bcd-9c3f-58cfe37cbcc5)


- LEFT JOIN table Mahasiswa dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama, Mahasiswa.jk, Dosen.nama AS "Dosen PA"
FROM Mahasiswa LEFT JOIN Dosen ON Dosen.kd_ds = Mahasiswa.kd_ds;
`````
Output:

![Screenshot 2024-05-29 193021](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/af07ea6a-a2d1-42a2-94d6-6bbcf7b1cb0e)


- JOIN table JadwalMengajar, Dosen, dan Matakuliah
`````
SELECT Matakuliah.kd_mk, Matakuliah.nama, Matakuliah.sks, Dosen.nama AS "Dosen Pengampu"
FROM JadwalMengajar
LEFT JOIN Matakuliah ON JadwalMengajar.kd_mk = Matakuliah.kd_mk
LEFT JOIN Dosen ON JadwalMengajar.kd_ds = Dosen.kd_ds;
`````
Output:

![Screenshot 2024-05-29 193035](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/a70c63a6-c758-4cc4-8ff7-869c2beb2bb1)


- JOIN table JadwalMengajar, Dosen, dan Matakuliah
`````
SELECT Matakuliah.kd_mk, Matakuliah.nama, Matakuliah.sks, Dosen.nama AS "Dosen Pengampu", JadwalMengajar.hari, JadwalMengajar.jam, JadwalMengajar.ruang
FROM JadwalMengajar
LEFT JOIN Matakuliah ON JadwalMengajar.kd_mk = Matakuliah.kd_mk
LEFT JOIN Dosen ON JadwalMengajar.kd_ds = Dosen.kd_ds;
`````
Output :

![Screenshot 2024-05-29 193054](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/3ba5ca30-eb19-4e67-aca6-f7d8e14b458f)


- JOIN tabel KRSMahasiswa, Mahasiswa, Matakuliah, dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama AS "nama", Dosen.nama AS "Dosen PA", Matakuliah.nama AS "Matakuliah", Matakuliah.sks, Dosen.nama AS "Dosen Pengampu"
FROM KRSMahasiswa
JOIN Mahasiswa ON KRSMahasiswa.nim = Mahasiswa.nim
JOIN Matakuliah ON KRSMahasiswa.kd_mk = Matakuliah.kd_mk
JOIN Dosen ON KRSMahasiswa.kd_ds = Dosen.kd_ds;
`````
Output :

![Screenshot 2024-05-29 193109](https://github.com/oktavia18/tugas-praktikum5/assets/147913672/3762b435-a185-414a-98a8-af070e0eddc1)


## SELESAI 
