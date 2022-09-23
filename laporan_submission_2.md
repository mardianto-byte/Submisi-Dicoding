# Laporan Proyek Machine Learning - Mardianto

## Project Overview

`Education is the most powerful weapon which you can use to change the world - Nelson Mandela`  
  
  Quote tersebut menyatakan bahwa pendidikan merupakan hal yang penting untuk setiap individu. Dengan pendidikan, setiap individu akan membuka jendela pengetahuan baru yang dimiliki. Dalam pendidikan, tidak setiap orang memiliki kesempatan untuk dapat merasakan pendidikan secara formal untuk mengasah keahlian yang dimiliki. Namun, keterbatasan akses tidak akan menjadi penghalang bagi setiap individu dalam memiliki kebebasan pendidikan. Dalam dunia digital saat ini, pendidikan bisa didapatkan dari berbagai sumber, salah satunya kursus online. Pada penelitian, menyatakan bahwa tidak terdapat perbedaa signifikan dalam rasio lulus-gagal yang mengindikasikan bahwa kursus online juga memberikan penilaian secara selektif dan efektif terhadap kelulusan. Temuan menarik lainnya adalah kursus online dapat mengurangi gap prestasi siswa. Spekulasi menyatakan bahwa dengan anonimitas, siswa yang kurang terlayani lebih dapat mencapai potensinya tanpa adanya stereotip [2]. Pada penemuan di penelitian lain, didapatkan bahwa Siswa menyukai video pembelajaran berdurasi pendek untuk menjaga konsentrasi siswa dan dengan memanfaatkan kursus online berbasis video pembelajaran, siswa dapat mengatur kecepatan video sesuai dengan kebutuhan [1]. Dengan kemudahan dan berbagai keuntungan tersebut, pembelajaran online dapat menjadi salah satu alternatif setiap orang untuk mengeksplor pembelajaran yang diinginkan. Namun, prefernsi materi yang ingin dipelajari menjadi hal menarik untuk dibahas agar pengguna dapat memanfaatkan pembelajaran yang diterima secara efektif serta mengkombinasikannya dengan pegetahuan yang dimiliki.    

## Business Understanding

### Problem Statements

Pernyataan masalah:
- Kesulitan dalam memilih materi yang akan dipelajari pada kursus online.
- Kurangnya pengetahuan mengenai kesesuaian materi yang akan diambil dengan preferensi yang dimiliki.
- Kurangnya referensi dalam mengambil kursus yang sesuai.

### Goals

Tujuan yang ingin dicapai:
- Membantu dalam memilih kursus online yang sesuai. 
- Mengetahui kesesuaian materi yang akan diambil dengan preferensi yang dimiliki.
- Memberi referensi dalam mengambil kursus yang sesuai

## Soution statement

Solusi yang dapat dilakukan: Dikarenakan informasi pada dataset yang terbatas, maka solusi yang dapat dilakukan adalah membuat sebuah sistem rekomendasi yang dapat memberikan rekomendasi terhadap title course yang diberikan oleh pengguna. Sistem akan memanfaatkan Content based filtering dimana rekomendasi yang diberikan didasarkan pada relevansi dari setiap judul kursus.


## Data Understanding

### Source

Dataset yang digunakan dalam project ini merupakan dataset yang didapatkan melalui platform kaggle dengan jumlah data sebanyak 891 data dengan memperhatikan 7 features.

Sumber data didapatkan dari [Kaggle](https://www.kaggle.com/datasets/siddharthm1698/coursera-course-dataset)

### Data Loading

Proses data loading dilakukan untuk membaca isi data pada datase. Proses dilakukan dengan melakukan proses import library yang dibutuhkan untuk melakukan proses loading data seperti pandas. Kemudian, lakukan proses loading dan cek isi dari data

![image](https://user-images.githubusercontent.com/72394753/191901354-5e5d8f48-6b9c-4917-ac68-d3d8ad13b8ce.png)

### Deskripsi Varibel

Variabel-variabel pada Airline Passanger Satisfaction dataset adalah sebagai berikut:

course_code: nomor kode kursus

course_title: judul kursus

course_organization: organisasi penyedia kursus

course_Certificate_type: jenis sertifikat kursus

course_rating: rating kursus

course_difficulty: tingkat kesulitan kursus

course_students_enrolled: jumlah siswa yang enroll pada kursus

![image](https://user-images.githubusercontent.com/72394753/191901487-be906044-9bf1-4509-a19d-ccfb16eb2a2e.png)

### Univariate Analysis
![image](https://user-images.githubusercontent.com/72394753/191901557-3a786e8b-fbb0-440b-9434-46a8249b9bad.png)
![image](https://user-images.githubusercontent.com/72394753/191901593-f8a32ca2-5a10-4450-894c-3aa7cf3d06c1.png)


## Data Preparation

### Handling missing value

Tidak terdapat missing value pada data
![image](https://user-images.githubusercontent.com/72394753/191901782-7202b3af-846f-4881-8a50-21426898e6b0.png)

### Reduksi Feature

Proses reduksi feature dilakukan untuk mengurangi jumlah fitur yang digunakan dalam parameter namun tetap mendapatkan sebagian informasi yang dibutuhkan. Dengan demikian, proses training dapat dilakukan lebih cepat dan efisien karena feature yang diproses telah mencakup sebagian besar informasi. Selain itu, hal ini dapat dilakukan untuk menghindari terjadinya kasus overfitting. 

Feature yang akan direduksi meliputi feature yang dianggap kurang memberikan informasi terhadap pilihan pengguna seperti course_code dan course_organization

![image](https://user-images.githubusercontent.com/72394753/191901912-f96d1bd0-eb2a-4110-b55e-2e015c4af499.png)

### Handling Duplicate

Tidak terdapat duplikasi data pada dataset
![image](https://user-images.githubusercontent.com/72394753/191902040-c58fe8e6-6c47-4051-a86d-cf7ed1446a34.png)


## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

### Content Based Filtering

Kelebihan

- Model tidak memerlukan data dari user lain karena rekomendasi spesifik. Dengan ini, maka kan lebih mudah untuk mendapat lebih banyak user

- Model dapat menangkap minat user secara sesifik dan merekomendasikan berbagai pilihan yang berbeda dari berbagai user


Kekurangan

- Model hanya bisa membuat rekomendasi berdasarkan ketertarikan user dan terbatas dalam melihat ketertarikan user lainnya.



## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

## Referensi

[1] N. Mamgain, A. Sharma and P. Goyal, "Learner's perspective on video-viewing features offered by MOOC providers: Coursera and edX," 2014 IEEE International Conference on MOOC, Innovation and Technology in Education (MITE), 2014, pp. 331-336, doi: 10.1109/MITE.2014.7020298.

[2] F. Zabihian, "Achievement gap in online and hybrid courses versus face-to-face courses among engineering and computer science students," 2018 IEEE Frontiers in Education Conference (FIE), 2018, pp. 1-5, doi: 10.1109/FIE.2018.8658579.
