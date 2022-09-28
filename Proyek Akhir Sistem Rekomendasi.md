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

1. pada tahap evaluasi ini, saya memakai tfidf vectorizer yang digunakan untuk menentukan nilai frekuensi sebuah kata dalam suatu data.
2. Kemudian saya memanggil fungsi "tfidf = TfidfVectorizer(stop_words = 'english')" yang digunakan untuk menampilkan bawaan bahasa inggris. 
3. kemudian fungsi "data['genres'] = data['genres'].fillna('')" yang digunakan untuk shorting data pada data genre. 
4. kemudian fungsi "tfidf_matrix = tfidf.fit_transform(data['genres'])" yang digunakan untuk memasukan data genre kedalam vector. 
5. Setelah itu fungsi "tfidf_matrix.shape" yang digunakan untuk menampilkan ukuran data genre yang sudah dimasukan kedalam vector. data pertama yang saya dapat        adalah 4803, dan data kedua yang saya dapat adalah 22
6. Kemudian, saya memanggil fungsi "tfidf_matrix.todense()" yang digunakan menampilkan untuk data vektor tfidf yang diubah dalam bentuk matrix. Hasil yang saya dapat adalah sebagai berikut.
7. ![Image 02](https://user-images.githubusercontent.com/111255438/192812372-ee5e4d66-5040-4fd6-bf9c-d0a20afee8b0.png)
8. Kemudian, setelah saya menghitung data tfidf, saya memanggil fungsi "cosine_sim = linear_kernel(tfidf_matrix, tfidf_matrix)" yang digunakan untuk menghitung matriks kesamaan cosinus.
9. Kemudian, saya memanggil fungsi "indices = pd.Series(data.index, index=data['title']).drop_duplicates()" yang digunakan untuk mengidentifikasi index pada film berdasarkan judul film
10. Setelah itu, saya memanggil fungsi "cosine_sim" yang digunakan untuk menampilkan nilai matriks kesamaan kosinus dalam bentuk array. Hasil yang saya dapat adalah sebagai berikut.
11. ![Image 01](https://user-images.githubusercontent.com/111255438/192813605-7646d3fc-0c35-4bfd-80cf-e53dfb9018a4.png)
12. Setelah itu, saya membuat sistem rekomendasi dengan memanggil fungsi "def get_recommendation(title, cosine_sim=cosine_sim):" yang berisikan fungsi "idx = indices[title]" yang digunakan untuk mendapatkan index film berdasarkan judul film
13. Kemudian, saya memanggil fungsi "sim_scores" yang digunakan untuk mendapatkan daftar skor kesamaan kosinus, untuk film tertentu dengan film lainnya.
14. Berikutnya, saya memanggil fungsi "sim_scores = sim_scores[1:11]" yang digunakan untuk mendapatkan 10 elemen teratas pada suatu film.
15. Kemudian, saya memanggil fungsi " output = pd.DataFrame([data['title'].iloc[movie_indices], data['genres'].iloc[movie_indices]])" yang digunakan untuk menampilkan rekomendasi berdasarkan judul film dan jenis pada film.
16. Setelah itu, saya memanggil fungsi "get_recommendation" yang digunakan untuk menampilkan rekomendasi film berdasarkan judul dan jenis film. outputnya adalah sebagai berikut.
17. ![Image 03](https://user-images.githubusercontent.com/111255438/192828520-e6dd20e7-b4cd-45b9-8b22-19defc24f709.png)
18. Pada gambar diatas, disini saya memasukan judul film yang mempunyai kesamaan genre yaitu action, kemudian saya masukan judul Rush Hour 2 dikarenakan genre film ini adalah action, maka output yang keluar adalah 10 film yang mempunyai kesamaan genre yaitu action.


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
