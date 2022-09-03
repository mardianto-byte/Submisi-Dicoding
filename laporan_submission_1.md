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
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.


### Reduksi Feature
Proses reduksi feature dilakukan untuk mengurangi jumlah fitur yang digunakan dalam parameter namun tetap mendapatkan sebagian informasi yang dibutuhkan. Dengan demikian, proses training dapat dilakukan lebih cepat dan efisien karena feature yang diproses telah mencakup sebagian besar informasi. Selain itu, hal ini dapat dilakukan untuk menghindari terjadinya kasus overfitting. 

Feature yang akan direduksi meliputi ffeature lainnya selain feature yang telah dipertimbangkan pada multivariate analysis. Proses update dapat dilakukan dengan membuang kolom yang tidak digunakan dan tetap menyimpan feature yang dibutuhkan pada dataset.

`
updated_dataset = dataset.drop(['id', 'Food_and_drink', 'Seat_comfort', 'On-board_service', 'Leg_room_service', 'Baggage_handling', 'Checkin_service', 'Inflight_service', 'Age', 'Departure/Arrival_time_convenient', 'Ease_of_Online_booking', 'Flight_Distance', 'Departure_Delay_in_Minutes', 'Arrival_Delay_in_Minutes', 'Gate_location', 'Departure/Arrival_time_convenient'], axis=1)
`

### Category feature encoding
Melakukan proses one-hot encoding terhadap categorical feature. Hal ini dilakukan agar model dapat mengetahui nilai dari feature tersebut sehingga bisa mendapatkan informasi yang dibutuhkan atau berguna.

`
from sklearn.preprocessing import  OneHotEncoder
updated_dataset = pd.concat([updated_dataset, pd.get_dummies(updated_dataset['Gender'], prefix='Gender')],axis=1)
updated_dataset = pd.concat([updated_dataset, pd.get_dummies(updated_dataset['Customer_Type'], prefix='Customer_Type')],axis=1)
updated_dataset = pd.concat([updated_dataset, pd.get_dummies(updated_dataset['Type_of_Travel'], prefix='Type_of_Travel')],axis=1)
updated_dataset = pd.concat([updated_dataset, pd.get_dummies(updated_dataset['Class'], prefix='Class')],axis=1)
updated_dataset.drop(['Gender','Customer_Type','Type_of_Travel', 'Class'], axis=1, inplace=True)
updated_dataset.head()
`

### Train-Test-Split
Proses membagi data menjadi data latih dan data uji sangat berguna untuk mengevaluasi seberapa baik model kita dalam melakukan proses prediksi jika diberikan sebuah data baru diluar data latih. Dengan demikian, jika terjadi oerfit dapat diketahui dengan cepat dan proses optimalisasi dapat dilakukan sedini mungkin.

`
from sklearn.model_selection import train_test_split
X = updated_dataset.drop(["satisfied"],axis =1)
y = updated_dataset["satisfied"]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.1, random_state = 123)
`

Total # of sample in whole dataset: 95711
Total # of sample in train dataset: 86139
Total # of sample in test dataset: 9572

pada data test cukup menggunakan 10% data dari keseluruhan dataset saja dikarenakan jumlah data yng cukup besar pada dataset dan 10% dari dataset memiliki jumlah yang cukup sebagai data uji.

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
