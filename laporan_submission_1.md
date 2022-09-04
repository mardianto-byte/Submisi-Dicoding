# Laporan Proyek Machine Learning - Mardianto

## Domain Proyek

Bisnis jasa transportasi merupakan salah satu bidang yang sangat berkembang di Indonesia. Proses Digitalisasi yang dilakukan oleh pihak maskapai maupun berbagai aplikasi pemesanan tiket transportasi turut menyumbang tingginya intensitas penggunaan jasa transportasi serta kompetisi antar maskapai. Karena merupakan salah satu usaha sektor jasa, interaksi terhadap penumpang merupakan hal yang penting untuk dijaga dalam rangka menjaga loyalitas penumpang terhadap produk jasa yang ditawarkan. Dengan demikian, tingkat kepuasan penumpang terhadap layanan yang diberikan perlu dipertimbangkan. Di Indonesia sendiri, dengan jumlah penduduk yang tinggi, dan beribu pulau yang tersebar, penggunaan pesawat sebagai sarana transportasi antar pulau sering dipilih menjadi salah satu alternatif. Dengan mengetahui tingkat kepuasaan penumpang, maskapai dapat meningkatkan pelayanan yang diberikan secara tepat sasaran sesuai dengan bagian dimana penumpang merasa kurang puas. Dengan meningkatkan pelayanan pada bidang yang tepat, diharapkan akan dapat meningkatkan loyalitas penumpang, mendapatkan target penumpang baru, dapat bersaing terhadap kompetitor, serta memperkuat citra brand. Berdasarkan riset pada [Investigating airline passenger satisfaction: Data mining method](https://www.sciencedirect.com/science/article/abs/pii/S2210539521001097?via%3Dihub), Kualitas layanan sangat berpengaruh terhadap pilihan penumpang dalam persaingan maskapai penerbangan. Maskapai penerbangan harus meningkatkan layanan menggunakan pendekatan evaluasi layanan berbasis pelanggan dengan mengetahui layanan mana yang paling efektif strategi untuk memenuhi kepuasan penumpang. 

## Business Understanding

### Problem Statements

Pernyataan masalah : 

- Kompetisi antar maskapai penerbangan di Indonesia
- Ketidaktepatan dalam peningkatan layanan maskapai
- Kesulitan dalam mendapatkan loyalitas penumpang

### Goals

Tujuan yang ingin dicapai : 

-  Meningkatkan loyalitas penumpang
-  Mendapatkan target penumpang baru
-  Memperkuat citra brand

### Solution statement

Solusi yang dapat dilakukan :

- Memanfaatkan model K-Nearest Neighbors dalam melakukan proses klasifikasi kepuasan penumpang dengan memperhatikan n neighbors = 10 dan p = 2 sebagai parameter untuk memanfaatkan pengukuran jarak menggunakan minowski. Metrik evaluasi yang digunakan yaitu metrik accuracy.
- Memanfaatkan model SVM sebagai perbandingan terhadap model uji lain dengan Metrik evaluasi yang digunakan yaitu metrik accuracy.
- Memanfaatkan model Decision Tree sebagai perbandingan terhadap model uji lain dengan Metrik evaluasi yang digunakan yaitu metrik accuracy.

## Data Understanding

Dataset yang digunakan dalam project ini merupakan dataset yang didapatkan melalui platform kaggle dengan jumlah data sebanyak 103904 data dengan memperhatikan 25 features. Tidak terdapat data null pada dataset.

Sumber data didapatkan dari [Kaggle](https://www.kaggle.com/datasets/deltasierra452/airline-pax-satisfaction-survey)

### Variabel-variabel pada Airline Passanger Satisfaction dataset adalah sebagai berikut:

Id: nomor Id penumpang

Gender: Jenis kelamin penumpang (Female, Male)

Customer Type: Tipe penumpang (Loyal customer, disloyal customer)

Age: Usia penumpang

Type of Travel: Tujuan penerbangan penumpang (Personal Travel, Business Travel)

Class: Kelas kursi penumpang (Business, Eco, Eco Plus)

Flight Distance: Jarak penerbangan

Inflight wifi service: Level kepuasan terhadap inflight wifi service (0,1,2,3,4,
5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Departure/Arrival time convenient: Level kepuasan terhadap waktu keberangkatan dan ketibaan (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Ease of Online booking: Level kepuasan terhadap online booking (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Gate location: Level kepuasan terhadap lokasi Gate/ Pintu (0,1,2,3,4,5/ 0=Not 
Applicable; 1=Least Satisfied to 5=Most Satisfied)

Food and drink: Level kepuasan terhadap pelayanan makanan dan minuman (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Online boarding: Level kepuasan terhadap online boarding (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Seat comfort: Level kepuasan terhadap kenyamanan kursi (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Inflight entertainment: Level kepuasan terhadap hiburan selama penerbangan (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

On-board service: Level kepuasan terhadap On-board service (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Leg room service: Level kepuasan terhadap ruang kaki penumpang (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Baggage handling: Level kepuasan terhadap penanganan bagasi (1,2,3,4,5/ 1=Least Satisfied to 5=Most Satisfied)

Checkin service: Level kepuasan terhadap Check-in service (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Inflight service: Level kepuasan terhadap layanan dalam penerbangan (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Cleanliness: Level kepuasan terhadap kebersihan (0,1,2,3,4,5/ 0=Not Applicable; 1=Least Satisfied to 5=Most Satisfied)

Departure Delay in Minutes: Waktu terlambat keberangkatan (menit) 

Arrival Delay in Minutes: Waktu terlambat ketibaan (menit) 

Satisfaction: Level kepuasan terhadap maskapai ('satisfied', 'neutral or dissatisfied')

### Pada tahap data understanding akan dilakukan beberapa tahapan:

#### Data loading
Proses data loading dilakukan untuk membaca isi data pada datase. Proses dilakukan dengan melakukan proses import library yang dibutuhkan untuk melakukan proses loading data seperti pandas. Kemudian, lakukan proses loading dan cek isi dari data

![image](https://user-images.githubusercontent.com/72394753/188206167-1ff3cd03-78a8-456a-830c-a033f76dc98a.png)

Output kode di atas memberikan informasi sebagai berikut:

Ada 103.904 baris (records atau jumlah pengamatan) dalam dataset.

Terdapat 25 kolom yaitu: SR, id, Gender,	Customer_Type,	Age,	Type_of_Travel,	Class,	Flight_Distance,	Inflight_wifi_service,	Departure/Arrival_time_convenient,
Ease_of_Online_booking, Gate_location, Food_and_drink, Online_boarding, Seat_comfort, Inflight_entertainment, On-board_service, Leg_room_service, Baggage_handling, Checkin_service, Inflight_service, Cleanliness, Departure_Delay_in_Minutes, Arrival_Delay_in_Minutes, satisfaction                       

#### Exploratory Data Analysis - Deskripsi Variabel

![image](https://user-images.githubusercontent.com/72394753/188209292-a67341ea-1a2c-485a-ae62-52b65b2be494.png)

Dari output terlihat bahwa:

Terdapat 5 kolom dengan tipe object, yaitu: Gender,	Customer_Type,	Type_of_Travel,	Class, satisfaction (target fitur)

Terdapat 19 kolom numerik dengan tipe data int64 yaitu: SR, id,	Age,	Flight_Distance,	Inflight_wifi_service,	Departure/Arrival_time_convenient,
Ease_of_Online_booking, Gate_location, Food_and_drink, Online_boarding, Seat_comfort, Inflight_entertainment, On-board_service, Leg_room_service, Baggage_handling, Checkin_service, Inflight_service, Cleanliness, Departure_Delay_in_Minutes

Terdapat 1 kolom numerik dengan tipe data float64, yaitu: Arrival_Delay_in_Minutes

Gunakan fungsi `describe()` untuk mendapatkan informasi statistik pada masing-masing kolom

#### Exploratory Data Analysis - Menangani Missing Value dan Outliers

##### Missing Value
Tidak terdapat missing value pada dataset, namun dijelaskan bahwa pada survey, nilai 0 merupakan nilai yang tidak applicable sehingga data survey dengan nilai 0 perlu dihilangkan 
![image](https://user-images.githubusercontent.com/72394753/188282876-97994e4b-7144-4e03-a32a-89eff66221a8.png)


##### Outliers

![image](https://user-images.githubusercontent.com/72394753/188210330-c39a9ef3-3f26-43a4-ad16-c1eab70ea0fa.png)
![image](https://user-images.githubusercontent.com/72394753/188210458-4ac22747-d5a0-493a-8a7a-3345c8100a0f.png)

Pada boxplot, terlihat terdapat outlier pada feature Flight_distance, Departure_Delay_in_Minutes, dan Arrival_Delay_in_Minutes.

Outlier tersebut perlu diperhatikan, karena sangat memungkinkan untuk memberikan informasi baru terkait data. Selain itu, delay pada pesawat merupakan hal yang memungkinkan terjadinya keterlambatan dalam penerbangan pesawat dan ketibaan pesawat dalam waktu yang lama. 

#### Exploratory Data Analysis - Univariate Analysis
Lakukan proses analisa feature kategorik dengan melakukan proses visualisasi dengan diagram batang.

Terdapat beberapa point yang dapat diambil : 

1. Distribusi gender laki - laki dan perempuan yang mengisi survey cukup merata
2. Sebagian besar pengisi survey adalah loyal customer
3. Sebagian besar tujuan travel penumpang adalah untuk urusan bisnis
4. Kelas bisnis merupakan kelas yang paling banyak dipilih diikuti kelas eco dan eco plus
5. Kebersihan, Layanan maskapai, layanan Check in, Penanganan bagasi, Ruang kaki pada pesawat, 
pelayanan selama penerbangan, hiburan, kenyamanan kursi, ketepatan waktu sampai dan berangkat
 maskapai memiliki rating cukup baik.
6. Online boarding,makanan dan minuman, lokasi gate, kemudahan online booking, layanan wifi selama penerbangan
memiliki rating yang kurang baik.
7. Secara umum, penumpang tidak merasa puas/ netral terhadap layanan maskapai

#### Exploratory Data Analysis - Multivariate Analysis
Untuk mencari korelasi antar feature, manfaatkan visualisasi heatmap. Dalam proses visualisasi heatmap, nilai target satisfaction memiliki korelasi positif yang cukup erat terhadap Online_boarding dan inflight_entertaiment. Selain itu, dipilih juga feature lainnya yang memiliki korelasi cukup erat terhadap 2 feature tersebut yaitu inflight_wifi_service dan cleanliness untuk menghidari teradinya overfitting terhadap 2 feature dikarena reduksi yang cukup signifikan.

## Data Preparation

### Reduksi Feature
Proses reduksi feature dilakukan untuk mengurangi jumlah fitur yang digunakan dalam parameter namun tetap mendapatkan sebagian informasi yang dibutuhkan. Dengan demikian, proses training dapat dilakukan lebih cepat dan efisien karena feature yang diproses telah mencakup sebagian besar informasi. Selain itu, hal ini dapat dilakukan untuk menghindari terjadinya kasus overfitting. 

Feature yang akan direduksi meliputi ffeature lainnya selain feature yang telah dipertimbangkan pada multivariate analysis. Proses update dapat dilakukan dengan membuang kolom yang tidak digunakan dan tetap menyimpan feature yang dibutuhkan pada dataset.

![image](https://user-images.githubusercontent.com/72394753/188301162-389d9cde-ceff-4f75-a805-b5a58e4d2626.png)

### Category feature encoding
Melakukan proses one-hot encoding terhadap categorical feature. Hal ini dilakukan agar model dapat mengetahui nilai dari feature tersebut sehingga bisa mendapatkan informasi yang dibutuhkan atau berguna.

![image](https://user-images.githubusercontent.com/72394753/188301186-94b3871f-a71e-4c8f-b341-2fb6ae5d123d.png)

### Train-Test-Split
Proses membagi data menjadi data latih dan data uji sangat berguna untuk mengevaluasi seberapa baik model kita dalam melakukan proses prediksi jika diberikan sebuah data baru diluar data latih. Dengan demikian, jika terjadi oerfit dapat diketahui dengan cepat dan proses optimalisasi dapat dilakukan sedini mungkin.

![image](https://user-images.githubusercontent.com/72394753/188301202-8a12d0ce-5b32-4cc3-be87-20fe9c4ada0a.png)

pada data test cukup menggunakan 10% data dari keseluruhan dataset saja dikarenakan jumlah data yng cukup besar pada dataset dan 10% dari dataset memiliki jumlah yang cukup sebagai data uji.

## Modeling

Pada model development, akan dilakukan percobaan pada 3 model yaitu : 
- KNN
- SVM
- Decision Tree

### KNN
![image](https://user-images.githubusercontent.com/72394753/188301902-42161d83-2687-43de-b24f-4b4f83a75a0e.png)

Akan dilakukan proses import library yang dibutuhkan. Kemudian, inisiasi KNeighborsClassifier dengan parameter n_neighbors=10 dan p=2, 
dimana n_neighbors merupakan parameter yang digunakan untuk menentukan jumlah point tetangga yang dibutuhkan dalam proses klasifikasi. Dalam menentukan jarak, metric yang digunakan adalah metric minowski (p=2). Lakukan proses latih pada data train dan proses uji pada data test. 

Kelebihan model KNN:
- Model KNN akan memiliki performa yang baik karena periode training. 
- Selain itu, KNN juga mudah untuk diimplementasi

Kelemahan model KNN:
- Mode KNN krang efektif jika dijalankan pada big dataset karena perlu menghitung jarak tiap point
- Kurang efektif pada data dengan dimensi tinggi

### SVM
![image](https://user-images.githubusercontent.com/72394753/188301346-97fc5ad5-24da-4f92-8b72-cc248edc6aff.png)

Akan dilakukan proses import library yang dibutuhkan. Kemudian, inisiasi SVC dengan parameter kernel='linear' dan random_state=0, 
dimana kernel merupakan parameter yang digunakan untuk mendapat data dan melakukan transformasi kedalam bentuk tertentu untuk dilakukan processing data. Linear merupakan parameter jika data dapat dipisahkan dengan memanfaatkan 1 garis. Random_state = 0 dipilih agar saat mengenerate data, maka data akan dilakukan secara acak. Lakukan proses latih pada data train dan proses uji pada data test. 

Kelebihan model SVM:
- Model SVM akan memiliki performa yang baik pada dimensi tinggi. 
- Selain itu, SVM juga cukup efisien dan outlier tidak memberikan dampak signifikan terhadap hasil 

Kelemahan model SVM:
- Mode SVM cukup lambat jika dijalankan pada big dataset

### Decision Tree
![image](https://user-images.githubusercontent.com/72394753/188301366-94e24bc7-c43b-42c6-a9fb-987325d3ec6a.png)

Akan dilakukan proses import library yang dibutuhkan. Kemudian, inisiasi DecisionTreeClassifier dengan parameter criterion='entropy', random_state=0, 
dimana criterion merupakan parameter yang digunakan untuk mengukur kualitas pemisahan.Teknik yang dipilih adalah entropy. Random_state = 0 dipilih agar saat mengenerate data, maka data akan dilakukan secara acak. Lakukan proses latih pada data train dan proses uji pada data test. 

Kelebihan model Decision Tree:
- Model Decision Tree memiliki automatic feature selection dimana metode decision tree sendiri memiliki tree-like model dalam menentukan keputusan dalam memberikan label berdasarkan pada pernyataan conditional. 

Kelemahan model Decision Tree:
- Mode Decision Tree cukup lambat jika dijalankan pada big dataset serta cenderung untuk terjadi overfit

Model terbaik yang akan digunakan adalah model decision tree. Model decision tree diilih karena model tersebut memiliki tingkat akurasi yang lebih tinggi dibandingkan dengan model lainnya yang diamati.


## Evaluation
Metrik yang digunakan pada kasus ini adalah metrik Akurasi. Metrik akurasi memiliki rumus (TP + TN) / (TP + FP + TN + FP). Metrik akurasi dipilih karena akan dilakukan prediksi terhadap kelas dan kedua kelas (satisfied, neutra/not satisfied) merupakan hal yang penting untuk diperhatikan sehingga akan memperhitungkan setiap true positive dan true negative terhadap keseluruhan prediksi. 

Dalam membandingkan metrik akurasi tiap model, didapatkan bahwa model KNN memiliki akurasi sebesar 0.931, model SVM memilikiakurasi sebesar 0.878, dan model Decision tree memiliki akurasi sebesar 0.94. Jika dilihat, model KNN dan model decision tree memiliki tingkat akurasi yang hampir serupa. Namun, decision tree memiliki tingkat akurasi sedikit lebih baik dibandingkan model lainnya.
