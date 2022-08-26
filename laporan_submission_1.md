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

Dataset yang digunakan dalam project ini merupakan dataset yang didapatkan melalui platform kaggle dengan jumlah data sebanyak 103904 data dengan memperhatikan 25 features.

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

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

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
