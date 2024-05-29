
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
insert into dosen values
    ("DS001", "Nofal Arianto"),
    ("DS002", "Ario Talib"),
    ("DS003", "Ayu Rahmadina"),
    ("DS004", "Ratna Kumala"),
    ("DS005", "Vika Prasetyo");

SELECT*FROM Dosen;

`````
Output :
![alt text](Screenshot/H2.png)

`````
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
![alt text](Screenshot/H3.png)

`````
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
![alt text](Screenshot/H4.png)

`````
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
![alt text](Screenshot/H5.png)

# Latihan
- JOIN table Mahasiswa dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama, Mahasiswa.jk, Dosen.nama AS "Dosen PA"
FROM Mahasiswa INNER JOIN Dosen ON Dosen.kd_ds = Mahasiswa.kd_ds;
`````
Output :
![alt text](Screenshot/J1.png)

- LEFT JOIN table Mahasiswa dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama, Mahasiswa.jk, Dosen.nama AS "Dosen PA"
FROM Mahasiswa LEFT JOIN Dosen ON Dosen.kd_ds = Mahasiswa.kd_ds;
`````
Output:
![alt text](Screenshot/J2.png)

- JOIN table JadwalMengajar, Dosen, dan Matakuliah
`````
SELECT Matakuliah.kd_mk, Matakuliah.nama, Matakuliah.sks, Dosen.nama AS "Dosen Pengampu"
FROM JadwalMengajar
LEFT JOIN Matakuliah ON JadwalMengajar.kd_mk = Matakuliah.kd_mk
LEFT JOIN Dosen ON JadwalMengajar.kd_ds = Dosen.kd_ds;
`````
Output:
![alt text](Screenshot/J3.png)

- JOIN table JadwalMengajar, Dosen, dan Matakuliah
`````
SELECT Matakuliah.kd_mk, Matakuliah.nama, Matakuliah.sks, Dosen.nama AS "Dosen Pengampu", JadwalMengajar.hari, JadwalMengajar.jam, JadwalMengajar.ruang
FROM JadwalMengajar
LEFT JOIN Matakuliah ON JadwalMengajar.kd_mk = Matakuliah.kd_mk
LEFT JOIN Dosen ON JadwalMengajar.kd_ds = Dosen.kd_ds;
`````
Output :
![alt text](Screenshot/J4.png)

- JOIN tabel KRSMahasiswa, Mahasiswa, Matakuliah, dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama AS "nama", Dosen.nama AS "Dosen PA", Matakuliah.nama AS "Matakuliah", Matakuliah.sks, Dosen.nama AS "Dosen Pengampu"
FROM KRSMahasiswa
JOIN Mahasiswa ON KRSMahasiswa.nim = Mahasiswa.nim
JOIN Matakuliah ON KRSMahasiswa.kd_mk = Matakuliah.kd_mk
JOIN Dosen ON KRSMahasiswa.kd_ds = Dosen.kd_ds;
`````
Output :
![alt text](Screenshot/J5.png)

## SELESAI <img align="center" alt="Ikhsan-Python" height="40" width="45" src="https://em-content.zobj.net/source/microsoft-teams/337/student_1f9d1-200d-1f393.png"> <img align="center" alt="Ikhsan-Python" height="40" width="45" src="https://em-content.zobj.net/thumbs/160/twitter/348/flag-indonesia_1f1ee-1f1e9.png">
