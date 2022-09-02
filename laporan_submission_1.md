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
Tidak terdapat missing value pada dataset

##### Outliers

![image](https://user-images.githubusercontent.com/72394753/188210330-c39a9ef3-3f26-43a4-ad16-c1eab70ea0fa.png)
![image](https://user-images.githubusercontent.com/72394753/188210409-b4a1ad04-35cf-46ac-93c5-0457c210bd8d.png)
![image](https://user-images.githubusercontent.com/72394753/188210458-4ac22747-d5a0-493a-8a7a-3345c8100a0f.png)

Pada boxplot, terlihat terdapat outlier pada feature Flight_distance, Departure_Delay_in_Minutes, dan Arrival_Delay_in_Minutes. Outlier tersebut dapat diabaikan, karena sangat memungkinkan untuk memberikan informasi baru terkait data. 

Selain itu, delay pesawat dalam waktu yang cukup lama dari biasanya merupakan hal yang memungkinkan terjadinya keterlambatan dalam penerbangan pesawat dan ketibaan pesawat.

Outlier pada checkin service sendiri sangat memungkinkan terjadi jika penumpang melakukan proses self check in sebelum hari keberangkatan.

#### Exploratory Data Analysis - Univariate Analysis

#### Exploratory Data Analysis - Multivariate Analysis


## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
