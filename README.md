# Tugas Praktikum { Pertemuan ke 12 } <img src=https://logos-download.com/wp-content/uploads/2016/05/MySQL_logo_logotype.png width="130px" >


|**Nama**|**NIM**|**Kelas**|**Matkul**|
|----|---|-----|------|
|Nurul Aisyah|312310476|TI.23.A.5|Basis Data|

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
CREATE TABLE Dosen(
    kd_ds VARCHAR(50) NOT NULL PRIMARY KEY,
    nama VARCHAR(100) NOT NULL
);

INSERT INTO Dosen (kd_ds, nama) VALUES
    ('DS001', 'Nofal Arianto'),
    ('DS002', 'Ario Talib'),
    ('DS003', 'Ayu Rahmadina'),
    ('DS004', 'Ratna Kumala'),
    ('DS005', 'Vika Prasetyo');

SELECT * FROM Dosen;
`````
Output :
![alt text](![Screenshot 2024-06-02 223749](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/ba3ef10e-4e4f-4cfd-9e5e-07a99de6afce)
)

`````
INSERT INTO Mahasiswa (nim, nama, jk, tgl_lahir, jalan, Kota, kodepos, no_hp, kd_ds) VALUES
    ('1812345', 'Ari Santoso', 'L', '1999-10-11', 'Jl. Bekasi', 'Bekasi', '17114', '081234567890', 'DS002'),
    ('1823456', 'Dina Marlina', 'P', '1998-11-20', 'Jl. Jakarta', 'Jakarta', '12110', '081234567891', NULL),
    ('1834567', 'Rahmat Hidayat', 'L', '1999-05-10', 'Jl. Bekasi', 'Bekasi', '17114', '081234567892', NULL),
    ('1845678', 'Jaka Sampurna', 'L', '2000-10-19', 'Jl. Cikarang', 'Cikarang', '17530', '081234567893', NULL),
    ('1856789', 'Tia Lestari', 'P', '1999-02-15', 'Jl. Karawang', 'Karawang', '41361', '081234567894', NULL),
    ('1867890', 'Anton Sinaga', 'L', '1998-06-22', 'Jl. Bekasi', 'Bekasi', '17114', '081234567895', NULL),
    ('1912345', 'Listia Nastiti', 'P', '2001-10-23', 'Jl. Jakarta', 'Jakarta', '12110', '081234567896', NULL),
    ('1923456', 'Amira Jarisa', 'P', '2001-01-24', 'Jl. Karawang', 'Karawang', '41361', '081234567897', 'DS004'),
    ('1934567', 'Laksana Mardito', 'L', '1999-04-14', 'Jl. Cikarang', 'Cikarang', '17530', '081234567898', NULL),
    ('1945678', 'Jura Marsina', 'P', '2000-05-10', 'Jl. Cikarang', 'Cikarang', '17530', '081234567899', NULL),
    ('1956789', 'Dadi Martani', 'L', '2001-08-29', 'Jl. Bekasi', 'Bekasi', '17114', '081234567900', 'DS005'),
    ('1967890', 'Bayu Laksono', 'L', '1999-07-22', 'Jl. Cikarang', 'Cikarang', '17530', '081234567901', 'DS004');

SELECT * FROM Mahasiswa;
`````
Output :
![alt text](![Screenshot 2024-06-02 223818](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/dff5bf4c-d726-4169-a731-eb7e4f278d7c)
)

`````
CREATE TABLE Matakuliah(
    kd_mk VARCHAR(50) NOT NULL PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    sks INT
);

INSERT INTO Matakuliah (kd_mk, nama, sks) VALUES
    ('MK001', 'Algoritma Dan Pemrograman', 3),
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
![alt text](![Screenshot 2024-06-02 223844](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/825063df-33be-4834-b150-f9ae306485ba)
)

`````
CREATE TABLE JadwalMengajar(
    kd_mk VARCHAR(50) NOT NULL,
    kd_ds VARCHAR(50) NOT NULL,
    hari ENUM('Senin', 'Selasa', 'Rabu', 'Kamis'),
    jam TIME NOT NULL,
    ruang VARCHAR(50),
    PRIMARY KEY(kd_mk, kd_ds),
    FOREIGN KEY(kd_mk) REFERENCES Matakuliah(kd_mk),
    FOREIGN KEY(kd_ds) REFERENCES Dosen(kd_ds)
);

INSERT INTO JadwalMengajar (kd_mk, kd_ds, hari, jam, ruang) VALUES
    ('MK001', 'DS002', 'Senin', '10:00:00', '102'),
    ('MK002', 'DS002', 'Senin', '13:00:00', 'Lab. 01'),
    ('MK003', 'DS001', 'Selasa', '08:00:00', '201'),
    ('MK004', 'DS001', 'Rabu', '10:00:00', 'Lab. 02'),
    ('MK005', 'DS003', 'Selasa', '10:00:00', 'Lab. 01'),
    ('MK006', 'DS004', 'Kamis', '09:00:00', 'Lab. 03'),
    ('MK007', 'DS005', 'Rabu', '08:00:00', '102'),
    ('MK008', 'DS005', 'Kamis', '13:00:00', '201');

SELECT * FROM JadwalMengajar;
`````
Output :
![alt text](![Screenshot 2024-06-02 223905](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/1dcc37b7-443a-486d-ba9d-ed5c7a973589)
)

`````
CREATE TABLE KRSMahasiswa(
    nim VARCHAR(50) NOT NULL,
    kd_mk VARCHAR(50) NOT NULL,
    kd_ds VARCHAR(50) NOT NULL,
    semester INT NOT NULL,
    nilai VARCHAR(50) DEFAULT NULL,
    PRIMARY KEY(nim, kd_mk, kd_ds),
    FOREIGN KEY(nim) REFERENCES Mahasiswa(nim),
    FOREIGN KEY(kd_mk) REFERENCES Matakuliah(kd_mk),
    FOREIGN KEY(kd_ds) REFERENCES Dosen(kd_ds)
);

INSERT INTO KRSMahasiswa (nim, kd_mk, kd_ds, semester) VALUES
    ('1823456', 'MK001', 'DS002', 3),
    ('1823456', 'MK002', 'DS002', 1),
    ('1823456', 'MK003', 'DS001', 3),
    ('1823456', 'MK004', 'DS001', 3),
    ('1823456', 'MK007', 'DS005', 3),
    ('1823456', 'MK008', 'DS005', 3);

SELECT * FROM KRSMahasiswa;
`````
Output :
![alt text](![Screenshot 2024-06-02 223930](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/d2e0a57e-0f83-472c-8fea-b864caadb5a1)
)

# Latihan
- JOIN table Mahasiswa dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama, Mahasiswa.jk, Dosen.nama AS "Dosen PA"
FROM Mahasiswa INNER JOIN Dosen ON Dosen.kd_ds = Mahasiswa.kd_ds;
`````
Output :
![alt text](![Screenshot 2024-06-02 223948](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/dfa0ca30-97da-4fe7-b248-d3816b549265)
)

- LEFT JOIN table Mahasiswa dan Dosen
`````
SELECT Mahasiswa.nim, Mahasiswa.nama, Mahasiswa.jk, Dosen.nama AS "Dosen PA"
FROM Mahasiswa LEFT JOIN Dosen ON Dosen.kd_ds = Mahasiswa.kd_ds;
`````
Output:
![alt text](![Screenshot 2024-06-02 224009](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/c8633659-dcef-4110-980b-443f533a3221)
)

- JOIN table JadwalMengajar, Dosen, dan Matakuliah
`````
SELECT Matakuliah.kd_mk, Matakuliah.nama, Matakuliah.sks, Dosen.nama AS "Dosen Pengampu"
FROM JadwalMengajar
LEFT JOIN Matakuliah ON JadwalMengajar.kd_mk = Matakuliah.kd_mk
LEFT JOIN Dosen ON JadwalMengajar.kd_ds = Dosen.kd_ds;
`````
Output:
![alt text](![Screenshot 2024-06-02 224034](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/b7843913-906f-4f62-bf1f-a8291892dac5)
)

- JOIN table JadwalMengajar, Dosen, dan Matakuliah
`````
SELECT Matakuliah.kd_mk, Matakuliah.nama, Matakuliah.sks, Dosen.nama AS "Dosen Pengampu", JadwalMengajar.hari, JadwalMengajar.jam, JadwalMengajar.ruang
FROM JadwalMengajar
LEFT JOIN Matakuliah ON JadwalMengajar.kd_mk = Matakuliah.kd_mk
LEFT JOIN Dosen ON JadwalMengajar.kd_ds = Dosen.kd_ds;
`````
Output :
![alt text](![Screenshot 2024-06-02 224059](https://github.com/nurulaisyah14/TugasPraktikum5/assets/148174512/17246921-0d01-4606-a442-7bc82f97bbf7)
)

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
