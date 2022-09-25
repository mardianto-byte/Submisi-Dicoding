# Laporan Proyek Machine Learning - Mardianto

## Project Overview

`Education is the most powerful weapon which you can use to change the world - Nelson Mandela`  
  
  Kutipan tersebut menyatakan bahwa pendidikan merupakan hal yang penting untuk setiap individu. Dengan pendidikan, setiap individu akan membuka jendela pengetahuan baru yang dimiliki. Dalam pendidikan, tidak setiap orang memiliki kesempatan untuk dapat merasakan pendidikan secara formal untuk mengasah keahlian yang dimiliki. Namun, keterbatasan akses tidak akan menjadi penghalang bagi setiap individu dalam memiliki kebebasan pendidikan. Dalam dunia digital saat ini, pendidikan bisa didapatkan dari berbagai sumber, salah satunya kursus online. Pada penelitian, menyatakan bahwa tidak terdapat perbedaa signifikan dalam rasio lulus-gagal yang mengindikasikan bahwa kursus online juga memberikan penilaian secara selektif dan efektif terhadap kelulusan. Temuan menarik lainnya adalah kursus online dapat mengurangi gap prestasi siswa. Spekulasi menyatakan bahwa dengan anonimitas, siswa yang kurang terlayani lebih dapat mencapai potensinya tanpa adanya stereotip [2]. Pada penemuan di penelitian lain, didapatkan bahwa Siswa menyukai video pembelajaran berdurasi pendek untuk menjaga konsentrasi siswa dan dengan memanfaatkan kursus online berbasis video pembelajaran, siswa dapat mengatur kecepatan video sesuai dengan kebutuhan [1]. Dengan kemudahan dan berbagai keuntungan tersebut, pembelajaran online dapat menjadi salah satu alternatif setiap orang untuk mengeksplor pembelajaran yang diinginkan. Namun, prefernsi materi yang ingin dipelajari menjadi hal menarik untuk dibahas agar pengguna dapat memanfaatkan pembelajaran yang diterima secara efektif serta mengkombinasikannya dengan pegetahuan yang dimiliki.    

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

Proses data loading dilakukan untuk membaca isi data pada datase. Proses dilakukan dengan melakukan proses import library yang dibutuhkan untuk melakukan proses loading data seperti pandas. Kemudian, lakukan proses loading dan cek isi dari data.

### Deskripsi Varibel

Variabel-variabel pada Airline Passanger Satisfaction dataset adalah sebagai berikut:

course_code: nomor kode kursus

course_title: judul kursus

course_organization: organisasi penyedia kursus

course_Certificate_type: jenis sertifikat kursus

course_rating: rating kursus

course_difficulty: tingkat kesulitan kursus

course_students_enrolled: jumlah siswa yang enroll pada kursus

### Univariate Analysis
Pada Univariate Analysis akan dilakukan proses observasi terhadap banyaknya organisasi penyedia kursus, jenis sertifikat kursus, serta tingkat kesulitan kursus. 
Didapatkan bahwa terdapat 3 jenis sertifikat kursus yaitu _'specialization'_, _'course'_, dan _'professional certificate'_. Sedangkan untuk tingkat kesulitan terdapat 4 tingkat kesulitan yaitu _'Beginner'_, _'Intermediate'_, _'Mixed'_, _'Advanced'_

## Data Preparation

### Handling missing value

Tidak terdapat missing value pada dataset. Pada implementasi kode, dilakukan dengan menghitung jumlah dari data yang memiliki nilai kosong /_null_. 

### Reduksi Feature

Proses reduksi feature dilakukan untuk mengurangi jumlah fitur yang digunakan dalam parameter namun tetap mendapatkan sebagian informasi yang dibutuhkan. Dengan demikian, proses training dapat dilakukan lebih cepat dan efisien karena feature yang diproses telah mencakup sebagian besar informasi. Selain itu, hal ini dapat dilakukan untuk menghindari terjadinya kasus overfitting. 

Feature yang akan direduksi meliputi feature yang dianggap kurang memberikan informasi terhadap pilihan pengguna seperti course_code dan course_organization

### Handling Duplicate

Tidak terdapat duplikasi data pada dataset
![image](https://user-images.githubusercontent.com/72394753/191902040-c58fe8e6-6c47-4051-a86d-cf7ed1446a34.png)


## Modeling

### Content Based Filtering

Kelebihan

- Model tidak memerlukan data dari user lain karena rekomendasi spesifik. Dengan ini, maka kan lebih mudah untuk mendapat lebih banyak user

- Model dapat menangkap minat user secara sesifik dan merekomendasikan berbagai pilihan yang berbeda dari berbagai user


Kekurangan

- Model hanya bisa membuat rekomendasi berdasarkan ketertarikan user dan terbatas dalam melihat ketertarikan user lainnya.

Model yang dibuat akan menampilkan top 5 rekomendasi course yang dapat diambil oleh pengguna berdasarkan keyword yang diberikan. Pada contoh diatas, model akan menerima input berupa Cloud Computing dan sistem akan memberikan rekomendasi course yang berelasi terhadap keyword.  

Pada implementasi kode, akan memanfaatkan TF-IDF Vectorizer yang akan menemukan representasi fitur penting dari data judul kursus.  Kemudian dilakukan proses _fit transformation _ yang menghasilkan matriks (891, 1433) dimana terdapat 891 data kursus yang dikategorikan kedalam 1433 kategori. Lakukan proses perhitungan derajat kesamaan dengan memanfaatkan teknik _cosine similarity_ . Dengan menggunakan teknik tersebut, kita dapat mendekteksi kesamaan antara satu kursus dengan yang lain didasarkan pada judul kursus. Untuk mendapatkan sejumlah rekomendasi, dalam hal ini dipilih 5, jalankan fungsi _course recomendations_. Pada fungsi _course_recomendations_, akan dilakukan 10 data kursus tertinggi berdasarkan tingkat _similarity_ yang akan dijadikan sebagai rekomendasi.

Pada query Cloud Computing, berikut merupakan hasil rekomendasi yang diberikan

| No | course_title                                   | course_difficulty |
|----|------------------------------------------------|-------------------|
| 1  | Introduction to Cloud Computing                | Beginner          |
| 2  | Cloud Computing Basics (Cloud 101)             | Beginner          |
| 3  |                      Fundamentals of Computing | Beginner          |
| 4  | Cloud Engineering with Google Cloud            | Intermediate      |
| 5  | Preparing for the Google Cloud Associate Cloud | Beginner          |
| 6  | Networking in Google Cloud                     | Intermediate      |
| 7  |             Data Engineering with Google Cloud | Intermediate      |
| 8  |              Security in Google Cloud Platform | Intermediate      |
| 9  | Developing APIs with Google Cloud's Apigee API | Intermediate      |
| 10 |        Industrial IoT on Google Cloud Platform | Beginner          |

## Evaluation

Dikarenakan berdasarkan dataset, tidak ditemukan preferensi dari pengguna sehingga kita tidak dapat mengevaluasi secara pasti preferensi dari pengguna itu sendiri. 
Namun jika dilihat dari hasil yang didapatkan, diketahui bahwa hasil yang ditampilkan berkorelasi cukup baik terhadap keyword yang diberikan sehingga percobaan evaluasi yang dapat dilakukan adalah melakukan filter terhadap dataset untuk menemukan kursus yang memiliki materi tertentu serta melakukan presiksi, apakah hasil prediksi terdapat pada list filter dengan memanfaatkan _Precision_. 


Pada contoh evaluasi, kita memisalkan pengguna yang akan mencari rekomendasi kelas _Cloud Computing_, pada hasil yang diberikan terdapat 26 daftar kelas yang relevan. 

| No | course_title                                                         | course_Certificate_type | course_rating | course_difficulty | course_students_enrolled
|----|----------------------------------------------------------------------|------------------------:|--------------:|------------------:| ------------------------
| 1  | AWS Fundamentals: Going Cloud-Native	                                |  COURSE                 |       4.7     | Beginner          | 110k
| 2  | AWS Fundamentals: Migrating to the Cloud	                            |  COURSE                 |       4.5     | Intermediate      | 13k
| 3  | Advanced Machine Learning with TensorFlow on Google Cloud            |  SPECIALIZATION	        |       4.5     | Advanced          | 35k 
| 4  | Architecting with Google Cloud Platform 日本語版	                     |  SPECIALIZATION	       |       4.5     | Intermediate      | 4.2k
| 5  | Building Scalable Java Microservices with SpringBoot and SpringCloud |  COURSE                 |       4.3     | Intermediate      | 24k
| 6  | Business Transformation with Google Cloud	                          |  COURSE                 |       4.7     | Beginner          | 10k
| 7  | Cloud Computing                                                      |  SPECIALIZATION	        |       4.4     | Intermediate      | 110k
| 8  | Cloud Computing Basics (Cloud 101)	                                  |  COURSE                 |       4.5     | Beginner          | 37k
| 9  | Cloud Engineering with Google Cloud	                                | PROFESSIONAL CERTIFICATE|       4.7     | Intermediate      | 310k
| 10 | Data Engineering on Google Cloud Platform 日本語版	                   |  SPECIALIZATION         |       4.4     | Intermediate      | 3k
| 11 | Data Engineering with Google Cloud	                                  | PROFESSIONAL CERTIFICATE|       4.6     | Intermediate      | 120k
| 22 | Developing APIs with Google Cloud's Apigee API platform              |  SPECIALIZATION         |       4.6     | Intermediate      | 16k
| 13 | Developing Applications with Google Cloud Platform                   |  SPECIALIZATION         |       4.7     | Intermediate      | 300k
| 14 | Developing Applications with Google Cloud Platform                   |  SPECIALIZATION         |       4.8     | Intermediate      | 4k
| 15 | Elastic Google Cloud Infrastructure: Scaling and Automation          |  COURSE	                |       4.7     | Intermediate      | 57k 
| 16 | Essential Google Cloud Infrastructure: Core Services                 |  COURSE	                |       4.7     | Intermediate      | 68k
| 17 | Essential Google Cloud Infrastructure: Foundation                    |  COURSE	                |       4.7     | Intermediate      | 83k
| 18 | From Data to Insights with Google Cloud Platform	                    |  SPECIALIZATION	        |       4.6     | Beginner          | 26k
| 19 | Google Cloud Platform Big Data and Machine Learning Fundamentals     |  COURSE                 |       4.6     | Intermediate      | 120k
| 20 | Google Cloud Platform Fundamentals for AWS Professionals             |  COURSE                 |       4.7     | Intermediate      | 36k
| 21 | Industrial IoT on Google Cloud Platform                              |  COURSE                 |       4.5     | Beginner          | 34k
| 22 | Introduction to Cloud Computing	                                    |  COURSE                 |       4.6     | Beginner          | 2.6k
| 23 | Machine Learning with TensorFlow on Google Cloud Platform            |  SPECIALIZATION	        |       4.5     | Intermediate      | 72k
| 24 | Networking in Google Cloud		                                        |  SPECIALIZATION	        |       4.7     | Intermediate      | 290k
| 25 | Preparing for the Google Cloud Associate Cloud Engineer Exam         |  COURSE                 |       4.7     | Beginner          | 22k
| 26 | Security in Google Cloud Platform	                                  |  SPECIALIZATION	        |       4.7     | Intermediate      | 300k

Saat dilakukan proses rekomendasi, 9 hasil yang diberikan sesuai karena memberikan gambaran materi yang dipelajari adalah _cloud computing_ namun juga terdapat 1 rekomendasi kelas _Fundamentals of computing_ yang dirasa bisa kurang relevan  

| No | course_title                                   | course_difficulty |
|----|------------------------------------------------|-------------------|
| 1  | Introduction to Cloud Computing                | Beginner          |
| 2  | Cloud Computing Basics (Cloud 101)             | Beginner          |
| 3  |                      Fundamentals of Computing | Beginner          |
| 4  | Cloud Engineering with Google Cloud            | Intermediate      |
| 5  | Preparing for the Google Cloud Associate Cloud | Beginner          |
| 6  | Networking in Google Cloud                     | Intermediate      |
| 7  |             Data Engineering with Google Cloud | Intermediate      |
| 8  |              Security in Google Cloud Platform | Intermediate      |
| 9  | Developing APIs with Google Cloud's Apigee API | Intermediate      |
| 10 |        Industrial IoT on Google Cloud Platform | Beginner          |

Meskipun demikian, dapat dikatakan bahwa metric precision yang diberikan tinggi. Pada hasil rekomendasi, terdapat 9 dari 10 rekomendasi yang sesuai dengan hasil yang diinginkan (rekomendasi Fundamentals of Computing kurang sesuai dengan topik diinginkan). dengan demikian 9/10 x 100% = 90% merupakan nilai presisi dari model dan itu merupakan hasil yang cukup baik. 

## Referensi

[1] N. Mamgain, A. Sharma and P. Goyal, "Learner's perspective on video-viewing features offered by MOOC providers: Coursera and edX," 2014 IEEE International Conference on MOOC, Innovation and Technology in Education (MITE), 2014, pp. 331-336, doi: 10.1109/MITE.2014.7020298.

[2] F. Zabihian, "Achievement gap in online and hybrid courses versus face-to-face courses among engineering and computer science students," 2018 IEEE Frontiers in Education Conference (FIE), 2018, pp. 1-5, doi: 10.1109/FIE.2018.8658579.

[3] https://sdsawtelle.github.io/blog/output/mean-average-precision-MAP-for-recommender-systems.html
