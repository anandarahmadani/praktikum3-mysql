# Soal Latihan Praktikum
| Variabel | isi |
| -------- | --- |
|***Nama***| Ananda Rahmadani |
|***NIM***| 312310461 |
|***Kelas***| TI.23.A.5 |
|***Matakuliah***| Baisis Data |

1. Lakukan penambahan data pada tabel mahasiswa dengan mengisi kd_ds yang belum ada pada data dosen.
dengan menggunakan kode berikut :
```
INSERT INTO dosen (kd_ds, nama) VALUES
    ('DS001', 'TYA'),
    ('DS002', 'ZIVA'),
    ('DS003', 'ARSY'),
    ('DS004', 'LULU'),
    ('DS005', 'NANDA'),
    ('DS006', 'VIA');
```
![Screenshot 1](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/1c7e720e-6bca-42a1-b411-13eec4fbd62e)

***Output :***
![Screenshot 1 1](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/6a5ad7aa-a85b-4abd-8bb4-47e0ad6f2f94)


2. Hapus satu record data pada tabel dosen yang telah dirujuk pada tabel mahasiswa. 
```
DELETE FROM dosen WHERE kd_ds = 'DS005';
```
***Output :***
![Screenshot 2](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/3f95fe93-684a-4641-974d-de1f75f99bfe)

3. Ubah mode menjadi **ON UPDATE CASCADE ON DELETE RESTRICT** 

Untuk mengubah CONSTRAINT FOREIGN KEY menjadi **ON UPDATE CASCADE** dan **ON DELETE RESTRICT**, Anda perlu menambahkan CONSTRAINT dengan opsi yang diinginkan. Berikut adalah langkah-langkahnya:

Tambahkan CONSTRAINT FOREIGN KEY dengan opsi ON UPDATE CASCADE dan ON DELETE RESTRICT:
```
ALTER TABLE mahasiswa
ADD CONSTRAINT fk_dosen
FOREIGN KEY (kd_ds)
REFERENCES dosen (kd_ds)
ON UPDATE CASCADE
ON DELETE RESTRICT;
```
***Output :***
![Screenshot 3](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/5d59ca3e-e35c-4943-9b9f-4604a483f52b)

4. Lakukan perubahan data pada tabel dosen (kd_ds)

Berikut adalah contoh perintah untuk melakukan perubahan data pada tabel "dosen" dengan kolom "kd_ds":
```
UPDATE dosen SET kd_ds = 'DS005' WHERE nama = 'NANDA';
```
Perintah di atas akan mengubah nilai kolom `"kd_ds" "NANDA" menjadi "DS005" pada tabel "dosen"`. Anda dapat menyesuaikan nilai yang ingin Anda ubah dan kondisi WHERE sesuai dengan kebutuhan Anda.

Pastikan untuk menjalankan perintah dengan hati-hati dan memastikan bahwa perubahan data yang Anda lakukan sesuai dengan kebutuhan dan kebijakan yang berlaku dalam basis data Anda.

***Output :***
![Screenshot 4](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/3d44b060-41ab-48b4-a046-19403d11f9ea)

5. Lakukan penghapusan data pada tabel dosen

Untuk menghapus data dari tabel "dosen" dengan kondisi "kd_ds = 'DS006'", Anda dapat menggunakan perintah DELETE dengan sintaks yang benar. Berikut adalah contoh perintah yang dapat Anda gunakan:
```
DELETE FROM Dosen WHERE kd_ds = 'DS006';
```

***Output :***
![Screenshot 5](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/a2aa5599-6315-40e2-8c9f-d7f81924b2c6)

6. Ubah mode menjadi **ON UPDATE CASCADE ON DELETE SET NULL**
```
ALTER TABLE mahasiswa
DROP FOREIGN KEY fk_dosen;
```
```
ALTER TABLE mahasiswa
ADD CONSTRAINT fk_dosen
FOREIGN KEY (kd_ds)
REFERENCES dosen (kd_ds)
ON DELETE SET NULL;
```
***Output :***
![Screenshot 6](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/8380a5bb-3111-4b4e-afb1-c51a9af82df5)

Dengan perubahan di atas, ketika Anda menghapus record dari tabel "dosen" yang memiliki referensi di tabel "mahasiswa", nilai kolom "kd_ds" dalam tabel "mahasiswa" yang mengacu pada record yang dihapus akan diatur menjadi NULL.

Setelah menjalankan perintah di atas, Anda dapat kembali mencoba menghapus record dengan menggunakan perintah berikut:

7. Lakukan penghapusan data pada tabel dosen
```
DELETE FROM dosen WHERE kd_ds = 'DS003';
```
***0utput :***
![Screenshot 7](https://github.com/anandarahmadani/praktikum3-mysql/assets/147919907/c8d0cbf9-dce7-46bb-aa19-9d2ee809e464)

Perintah ini akan menghapus record dengan nilai "DS003" dari tabel "dosen", dan karena menggunakan opsi ON DELETE SET NULL, nilai kolom "kd_ds" dalam tabel "mahasiswa" yang mengacu pada record yang dihapus akan diatur menjadi NULL.

# Evaluasi dan Pertanyaan

### Tulis semua perintah-perintah SQL percobaan di atas beserta outputnya!

- Membuat foreign key

Dalam ALTER TABLE:
```
ALTER TABLE mahasiswa
ADD CONSTRAINT fk_dosen
FOREIGN KEY (kd_ds) REFERENCES dosen(kd_ds)
```

Dalam CREATE TABLE:
```
CREATE TABLE mahasiswa(
nim VARCHAR(10) NOT NULL,
nama VARCHAR(100) NOT NULL,
kd_ds VARCHAR(10),
PRIMARY KEY(nim),
CONSTRAINT fk_Dosen FOREIGN KEY (kd_ds)
REFERENCES dosen(kd_ds)
);
```

- Mengubah data
```
UPDATE mahasiswa
SET kd_ds = 'DS001' WHERE nim = 112233445;
```

- Menampilkan CREATE TABLE
```
SHOW CREATE TABLE  mahasiswa;
Mode ON UPDATE CASCADE ON DELETE CASCADE
```
```
ALTER TABLE mahasiswa
DROP FOREIGN KEY fk_mahasiswa_dosen,
ADD CONSTRAINT fk_dosen FOREIGN KEY (kd_ds) REFERENCES dosen(kd_ds) ON UPDATE CASCADE ON DELETE CASCADE;
```

- Menghapus data
```
DELETE FROM dosen WHERE kd_ds = 'DS001';
Mode ON UPDATE CASCADE ON DELETE NOT NULL
```
```
ALTER TABLE <table>
DROP FOREIGN KEY <nama_constraint_lama>,
ADD CONSTRAINT <nama_constraint_baru> FOREIGN KEY (field) REFERENCES <table_references(filed_references)> ON UPDATE CASCADE ON DELETE NOT NULL;
```

- Mengubah data
```
UPDATE dosen
SET kd_ds = 'DS006' WHERE nama = 'Haha Hihi';
```

- Menghapus data
```
DELETE FROM dosen WHERE nim = 'DS003';
```

### Apa bedanya penggunaan RESTRICT dan penggunaan CASCADE

- **RESTRICT:** Ketika Anda mode ON DELETE RESTRICT digunakan,maka penghapusan data tabel dosen yang di rujuk oleh data pada tabel mahasiswa tidak akan diizinkan.

- **CASCADE:** Sebaliknya, ketika mode ON DELETE RESTRICT digunakan,maka penghapusan data pada tabel dosen yang di rujuk oleh data pada tabel mahasiswa akan secara otomatis menghapus data pada tabel mahasiswa tsb.

### Berikan Kesimpulan anda !

- SQL Constraint digunakan untuk menentukan aturan untuk data dalam tabel Penggunaan CONSTRAINT FOREIGN KEY sangatlah penting untuk menjaga integritas data dalam basis data relasional. Dengan menggunakan CONSTRAINT FOREIGN KEY kita dapat memastikan bahwa data pada tabel yang berelasi selalu konsisten dan tidak mengalami anomali data.

### Buat laporan praktikum yang berisi, langkah-langkah praktikum beserta screenshot yang sudah dilakukan dalam bentuk dokumen.

<img src=https://pngimg.com/uploads/google_drive/google_drive_PNG9.png width="110px" >

- [Link Laporan Praktim] 
https://drive.google.com/file/d/1kP9NwseJ5DD5GblYPYK2jAbirhNMIwl5/view?usp=drive_link

#TERIMAKASIH
