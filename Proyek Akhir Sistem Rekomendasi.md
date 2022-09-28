# Laporan Proyek Akhir Sistem Rekomendasi - Albert Ewaldo Arthur Daeli

## Project Review

Film merupakan salah satu hiburan yang sangat digemari oleh masyarakat. Kegiatan menonton film ini memiliki manfaat yang positif bagi penontonnya. 
menonton film dapat menghilangkan rasa jenuh, stress dan emosi yang tidak beraturan. selain itu dengan menonton film, kita juga dapat mempelajari 
bahasa asing.

## Business Understanding

oleh karena itu saya membuat sistem rekomendasi film untuk menghasilkan kumpulan film yang mungkin akan disukai oleh pengguna dengan menggunakan 
metode Content-based filtering : Memberikan rekomendasi berdasarkan kemiripan atribut dari item atau barang yang disukai. 
Pada sistem rekomendasi film kemiripan berdasarkan atribut yang dimiliki oleh film seperti genre atau jenis film.

## Problem Statements

1. Bagaimana cara membuat sistem rekomendasi film yang sesuai dengan keinginan pengguna?
2. Apa saja yang harus diketahui agar mendapatkan rekomendasi film yang sesuai dengan keinginan pengguna?

## Goals

1. Menggunakan metode Content Based Filtering agar bisa merekomendasikan film berdasarkan kemiripan jenis film.
2. Merekomendasikan Judul film berdasarkan Genre Film yang sesuai dengan keinginan pengguna.

## Data Understanding

Data yang saya pakai pada proyek ini adalah data yang bisa digunakan untuk merekomendasikan film yaitu Movie Recommendation yang saya unduh dari 
website "kaggle.com". Dataset ini memiliki 4803 data sampel dan 24 kolom. 
Berikut ini adalah link dataset yang saya pakai : https://www.kaggle.com/datasets/lucifierx/movie-recommendation

## Variabel-variabel pada Movie Recommendation Dataset : 

1. index : Merupakan nomor urut pada film.
2. budget : Merupakan Biaya Produksi pada film.
3. genres : Merupakan jenis atau kategori pada film.	
4. homepage : Merupakan link website pada film.	
5. id : Merupakan nomor objek pada film.	
6. keywords : Merupakan jenis kata kunci untuk mencari film.	
7. original language : Merupakan jenis bahasa resmi pada film.	
8. original title : Merupakan jenis judul resmi pada film.	
9. overview : Merupakan gambaran atau keterangan pada jenis film.	
10. popularity : Digunakan untuk menentukan seberapa banyak orang yang menyukai film.
11. Production Companies : Merupakan Sebuah perusahaan yang menciptakan sebuah produksi film.
12. production Countries : Merupakan letak negara pada suatu perusahaan.
13. Release Date : Merupakan tanggal rilis pada suatu film
14. Revenue : Merupakan pendapatan atau jumlah uang yang di dapat pada suatu produksi film	
15. runtime : Merupakan jenis yang menghitung waktu atau durasi pada film.	
16. spoken languages : Merupakan jenis bahasa yang digunakan dalam film.	
17. status : Digunakan untuk menampilkan apakah film sudah di rilis atau tidak.	
18. tagline : Merupakan deskripsi singat pada film.	
19. title : Merupakan judul pada film.	
20. vote average : Merupakan nilai rata-rata pada voting atau pilihan. 	
21. vote count : Merupakan jumlah voting atau pilihan pada film.	
22. cast : Merupakan pemain yang memerankan sebuah karakter pada film.	
23. crew : Merupakan orang yang membuat sebuah film.	
24. director : Merupakan orang yang menjalankan sebuah film sesuai dengan skenario.

## Data Preparation

Tahapan yang saya pakai untuk membuat sistem rekomendasi adalah sebagai berikut :

1. Load Library Python : Digunakan untuk mengimport atau memuat beberapa library dalam membuat sistem rekomendasi.
2. Load Dataset : Digunakan untuk memuat dataset yang dipakai untuk membuat sistem rekomendasi.
3. Handling Missing Values : Pada tahap ini digunakan untuk memeriksa atau checking data apakah terdapat missing values atau data yang kosong atau tidak. 
   Data yang saya pakai beberapa ada yang missing values dan ada yang tidak.
4. Exploratory Data Analysis (EDA) : Digunakan untuk melihat data dalam bentuk diagram. data yang dilihat berupa Data Popularity, Data vote average atau nilai rata-rata yang memilih film, dan Data Count atau jumlah yang memilih film 
![image](https://user-images.githubusercontent.com/111255438/192695256-738f20f4-6751-42df-a6b3-8cff23ad2ec8.png) 
- Pada tabel diatas menunjukan bahwa data popularity paling ada di angka lebih dari 800, dan data kedua ada di bawah angka 800
![image](https://user-images.githubusercontent.com/111255438/192695588-4e33693f-4405-444f-aed2-8cd26fec8520.png) 
-  Pada tabel diatas menunjukan bahwa data average atau nilai rata-rata pilihan paling tinggi berada di angka 8, dan vote count atau jumlah pilihan berada di angka 14000

5. Modeling :Digunakan untuk membuat fitur pada sistem rekomendasi.
6. Recommendation : Digunakan untuk membuat rekomendasi film berdasarkan judul dan genre.

## Modeling

1. Pada tahapan modeling ini, pertama saya menggunakan fungsi "idx = indices[title]" yang digunakan untuk memanggil index film berdasarkan title atau judul.
2. Tahap kedua adalah "sim_scores" yang digunakan untuk mendapatkan daftar skor kesamaan kosinus, untuk film tertentu dengan film lainnya.
3. Tahap Ketiga adalah fungsi "sim_scores = sim_scores[1:11]" yang digunakan untuk mendapatkan 10 elemen teratas pada suatu film.
4. Kemudian saya memanggil get_recommendation untuk mendapatkan rekomendasi film berdasarkan kemiripan genre. disini saya memasukan judul film action 
   yang berjudul "Rush Hour 2", kemudian saya mendapatkan 9 rekomendasi film yang mirip berdasarkan genre atau jenis film yaitu action

## Evaluasi
Pada tahap evaluasi ini, Metrik yang saya pakai adalah Accuracy Score, Confusion Matrix, dan Classification Report :

1. Accuracy Score = Merupakan rasio prediksi benar baik itu positif maupun negatif terhadap keseluruhan data. Hasil akurasi yang saya dapat adalah 1.0
2. Confusion Matrix = Merupakan pengukuran performa untuk masalah klasifikasi machine learning, Dimana keluaran dapat berupa kelas atau lebih. Hasil confusion matrix yang saya dapat adalah 3.0.0.
3. Classification Report = Merupakan proses memprediksi nilai pada yang terdiri dari 3 metrik yaitu Precision, Recall, dan F1-Score.
   1. Precision = Merupakan kecocokan antara bagian antara bagian data yang diambil dengan informasi yang dibutuhkan. Nilai presisi yang saya dapatkan adalah 1.00
   2. Recall = Merupakan tingkat keberhasilan sistem dalam menemukan kembali sebuah informasi. Nilai Recall yang saya dapatkan adalah 1.00
   3. F1-Score = Merupakan data yang menggambarkan perbandingan rata-rata precision dan recall yang dibobotkan. Nilai yang saya dapatkan dari F1-Score adalah 1.00

## Kesimpulan

Dengan adanya sistem rekomendasi film yang saya buat agar pengguna bisa mengetahui ada film apa saja yang sesuai dengan genre yang mereka akan tonton
