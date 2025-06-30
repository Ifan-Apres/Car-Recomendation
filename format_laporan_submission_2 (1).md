# Laporan Proyek Machine Learning Car Recomendation - Khusnil Arifandi Purnama

## Project Overview

Menghadapi fenomena choice overload di pasar otomotif ([Iyengar & Lepper, 2000](https://faculty.washington.edu/jdb/345/345%20Articles/Iyengar%20%26%20Lepper%20(2000).pdf)), di mana konsumen kesulitan membuat keputusan optimal, proyek ini diangkat untuk mengembangkan sebuah sistem rekomendasi cerdas. Masalah ini perlu diselesaikan untuk menyederhanakan proses pengambilan keputusan yang kompleks dengan mengimplementasikan metode content-based filtering. Dengan memanfaatkan data spesifikasi teknis, sistem ini menggunakan metrik Cosine Similarity untuk secara efektif menghitung kemiripan antar mobil—sebuah pendekatan yang umum dalam sistem rekomendasi ([Ricci et al., 2011]  (https://www.cs.ubbcluj.ro/~gabis/DocDiplome/SistemeDeRecomandare/Recommender_systems_handbook.pdf)). Selain itu, proyek ini juga mengimplementasikan algoritma K-Nearest Neighbors (KNN), sebuah metode yang sangat efisien untuk menemukan sejumlah 'k' tetangga terdekat dalam ruang fitur, yang berfungsi sebagai pendekatan alternatif yang lebih terukur untuk memberikan rekomendasi. Dengan demikian, sistem ini menyediakan alat bantu praktis yang mampu menyajikan daftar kendaraan paling relevan berdasarkan referensi dari pengguna, sehingga mengatasi inefisiensi dalam proses pemilihan

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana kita dapat membangun sebuah sistem yang mampu menerjemahkan preferensi subjektif pengguna ("Saya suka mobil X") menjadi skor kemiripan objektif, untuk mengungkap alternatif kendaraan dengan nilai terbaik dan mencegah konsumen kehilangan potensi penghematan jutaan rupiah?
- Bagaimana kita dapat mengkalkulasi 'jarak kemiripan' antar kendaraan secara matematis berdasarkan vektor fitur gabungannya, sehingga memungkinkan konsumen membuat keputusan pembelian senilai ratusan juta rupiah yang sepenuhnya didukung oleh data objektif, bukan sekadar perbandingan manual yang bias?
- Bagaimana kita bisa menciptakan sebuah jembatan teknologi yang mampu mengubah niat sederhana pengguna (misalnya, "cari mobil seperti Toyota Camry") menjadi penemuan instan melalui real-time vector similarity search, sehingga secara drastis mengurangi waktu dan kebingungan dalam proses pemilihan mobil?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Tujuan utama proyek ini adalah untuk mengkuantifikasi kemiripan antar mobil dengan mengembangkan sebuah skor objektif. Proyek ini akan membangun model yang mengubah puluhan atribut teknis setiap mobil (seperti harga, tenaga kuda, dan efisiensi BBM) menjadi sebuah vektor fitur numerik yang seragam. Dengan menggunakan metrik Cosine Similarity serta algoritma K-Nearest Neighbors (KNN), sistem kemudian akan menghitung dan menemukan mobil-mobil dengan kemiripan tertinggi. Hasilnya adalah sebuah daftar peringkat yang secara objektif mengungkap mobil-mobil "kembaran" yang mungkin menawarkan nilai lebih baik, sehingga memberdayakan konsumen untuk membuat keputusan finansial yang lebih cerdas dan terinformasi.
- Proyek ini bertujuan untuk menciptakan sebuah 'ruang fitur' di mana setiap mobil direpresentasikan sebagai sebuah titik data unik. Untuk mencapai ini, proyek akan melakukan feature engineering dengan mengonversi data kategorikal (seperti kelas kendaraan) dan menormalisasi data numerikal untuk menciptakan sebuah vektor fitur yang komprehensif. Dengan mengimplementasikan kalkulasi Cosine Similarity untuk mengukur sudut antar vektor dan algoritma K-Nearest Neighbors (KNN) untuk secara efisien menemukan titik-titik data terdekat, proyek ini secara efektif akan menghitung "jarak" dan kemiripan antar mobil. Tujuan akhirnya adalah menyediakan sebuah mekanisme yang memungkinkan keputusan pembelian yang sepenuhnya data-driven, menggantikan proses perbandingan manual yang tidak akurat dengan analisis matematis yang solid dan tidak bias.
- Tujuan dari proyek ini adalah membangun sebuah fungsi rekomendasi yang beroperasi sebagai jembatan penemuan instan. Secara spesifik, proyek ini akan merancang sebuah alur proses komputasi yang efisien dengan mengimplementasikan model K-Nearest Neighbors (KNN): menerima input nama mobil dari pengguna, secara cepat menemukan vektor fitur mobil tersebut, dan dalam hitungan detik melakukan pencarian kemiripan (similarity search) yang telah dioptimalkan terhadap ribuan vektor lainnya. Dengan mengembalikan daftar 5 atau 10 mobil teratas yang paling mirip, proyek ini bertujuan untuk memberikan pengalaman pengguna yang mulus dan responsif, secara signifikan memotong waktu riset dan mengatasi kebingungan akibat terlalu banyak pilihan (choice overload).


    ### Solution statements
    - **Content-Based Filtering Menggunakan Cosine Similarity:** Pendekatan solusi pertama adalah dengan mengimplementasikan sistem rekomendasi berbasis konten (content-based filtering) yang memanfaatkan metrik Cosine Similarity. Proses ini dimulai dengan feature engineering, di mana seluruh atribut relevan dari setiap mobil, baik kategorikal maupun numerik, diubah menjadi sebuah vektor fitur numerik yang seragam dan telah dinormalisasi. Setiap mobil kemudian direpresentasikan sebagai sebuah vektor unik dalam ruang fitur multi-dimensi. Ketika pengguna memilih sebuah mobil referensi, sistem akan menghitung kosinus sudut antara vektor mobil tersebut dengan semua vektor mobil lainnya untuk mendapatkan skor kemiripan objektif. Pendekatan ini sangat transparan karena rekomendasi yang dihasilkan didasarkan langsung pada kemiripan atribut yang jelas dan tidak memerlukan data historis dari pengguna lain, sehingga efektif untuk menangani produk baru
    - **Content-Based Filtering dengan K-Nearest Neighbors (KNN):** Sebagai alternatif, pendekatan kedua menggunakan algoritma K-Nearest Neighbors (KNN) untuk menemukan kemiripan berbasis konten. Sama seperti pendekatan pertama, setiap mobil akan ditransformasikan menjadi sebuah vektor fitur dalam ruang multi-dimensi. Namun, alih-alih menghitung Cosine Similarity ke seluruh dataset, algoritma KNN akan di-training untuk memetakan posisi setiap mobil. Saat pengguna memberikan input, sistem akan mencari 'K' mobil lain (tetangga terdekat) yang memiliki jarak paling minim ke mobil referensi, biasanya menggunakan metrik seperti Euclidean Distance. Keunggulan pendekatan ini terletak pada fleksibilitasnya dalam menggunakan berbagai metrik jarak dan potensinya yang lebih mudah untuk dikembangkan menjadi model hibrida di masa depan jika data interaksi pengguna telah tersedia.
  
## Data Understanding
Dataset yang digunakan dalam analisis ini adalah "Large Dataset of Cars" yang berisi kumpulan data komprehensif mengenai berbagai kendaraan beserta spesifikasi teknis utamanya. Data ini mencakup total 432 entri mobil dengan 15 fitur yang berbeda. Kondisi data relatif bersih, meskipun terdapat beberapa nilai yang hilang pada kolom Cylinders yang memerlukan penanganan sebelum analisis lebih lanjut. Sumber data dapat diakses dan diunduh melalui tautan berikut: [Large Dataset of Cars](https://www.kaggle.com/datasets/makslypko/large-cars-dataset)

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- Brand         : Merupakan merek dari mobil (contoh: Acura, Audi, BMW).
- Model         : Merupakan nama model spesifik dari mobil tersebut.
- VehicleClass  : Merupakan klasifikasi atau jenis bodi mobil (contoh: SUV, Sedan, Sports Car).
- Region        : Merupakan wilayah geografis di mana mobil tersebut diproduksi (contoh: Asia, Europe).
- DriveTrain    : Merupakan jenis sistem penggerak roda pada mobil (contoh: All-Wheel Drive, Front-Wheel Drive).
- MSRP          : Merupakan harga eceran yang disarankan oleh produsen (Manufacturer's Suggested Retail Price).
- DealerCost    : Merupakan harga beli mobil bagi dealer dari produsen.
- EngineSize    : Merupakan ukuran atau volume mesin dalam satuan liter.
- Cylinders     : Merupakan jumlah silinder yang dimiliki oleh mesin mobil.
- HorsePower    : Merupakan tenaga maksimum yang dapat dihasilkan oleh mesin dalam satuan tenaga kuda.
- MPG_City      : Merupakan efisiensi bahan bakar mobil dalam satuan mil per galon (Miles Per Gallon) untuk kondisi berkendara di dalam kota.
- MPG_Highway   : Merupakan efisiensi bahan bakar mobil dalam satuan mil per galon (Miles Per Gallon) untuk kondisi berkendara di jalan tol.
- Weight        : Merupakan berat total kendaraan dalam satuan pon (lbs).
- Wheelbase     : Merupakan jarak antara sumbu roda depan dan sumbu roda belakang.
- Length        : Merupakan panjang total kendaraan dari ujung bumper depan hingga belakang.

Dataset ini memiliki beberapa karakteristik:

- Memiliki 7 fitur kategorikal dan 8 fitur numerik.
- Memiliki 0 data duplikat.
- Memiliki 2 missing value di fitur Cylinders.

![image](https://github.com/user-attachments/assets/7bec5053-5c33-4c35-b686-10f3b14255c6)


![image](https://github.com/user-attachments/assets/db41b0e9-9ca5-46c1-afaf-91604879b3a2)


Serta memiliki jumlah nilai unik tiap fitur sebagai berikut:

![image](https://github.com/user-attachments/assets/51dc6d68-cbcd-4b95-9ea9-b27c24356b5d)

Berikut merupakan cuplikan isi dataset.

![image](https://github.com/user-attachments/assets/37cbc8bd-0a5b-4d9e-ad5e-fc6fb5c1a8fe)

Berikut merupakan analisis deskriptif dari dataset.

![image](https://github.com/user-attachments/assets/8062813d-ace9-45cb-ab56-ca3ddee7f7b4)


Selanjutnya, akan dilakukan Exploratory Data Analysis Basic dengan melihat distribusi data dari dataset sebagai berikut.

![image](https://github.com/user-attachments/assets/f3c6e439-8638-4d2d-8225-aca9eb3fcd5c)
Dari histogram tersebut, diketahui bahwa jumlah mobil terbanyak berdasarkan merek didominasi oleh merek Toyota, diikuti oleh Chevrolet dan Mercedes-Benz. Diketahui juga bahwa Merek Hummer menempati posisi terendah dalam jumlah mobil berdasarkan merek.

![image](https://github.com/user-attachments/assets/257e1494-725a-4955-9e91-34dd06b7c9f7)
Selanjutnya, didapat histogram jumlah mobil berdasarkan kelas mobil. Diketahui bahwa kelas sedan mendominasi dalam hal jumlah mobil yaitu lebih dari 250 jenis mobil diikuti SUV dan Sports. Mobil Hybrid menempati posisi terakhir dari jumlah mobil berdasarkan kelas

![image](https://github.com/user-attachments/assets/02a5e406-846c-4e8d-9138-50328f96f6f5)

Dari Bar chat distribusi nilai MSRP terhadap jumlah mobil tersebut, didapat pola distribusi cenderung ke skew ke kanan (right-skewed) atau disebut positive skew. Sebagian besar data terdistribusi disekitar nilai MSRP $ 25,000 mengindikasikan rata rata harga MSRP mobil di sekitar $25,000. Disisi lain, terdapat juga mobil dengan harga yang sangat tinggi yaitu di nilai $200,000. 

![image](https://github.com/user-attachments/assets/310ef0ff-221a-408b-b7ee-3e94ea26e973)
Didapat juga distribusi jumlah silinder terhadap jumlah mobil. Dari distribusi tersebut diketahui bahwa jumlah silinder terbanyak dari semua mobil adalah berjumlah 6 silinder, diikuti dengan jumlah silinder 4, dan terdapat juga mobil dengan silinder berjumlah 12.

![image](https://github.com/user-attachments/assets/2557ab80-79cd-4add-a25d-ed8bd43270f3)
Dari Bar Chart distribusi kapasitas mesin, didapat distribusi kapasitas mesin yang tidak merata. Namun, kapasitas mesin yang memiliki jumlah mobil terbanyak terdapat pada kapasitas mesin 2.5 liter.

![image](https://github.com/user-attachments/assets/80d68d51-6dbc-41cb-b570-236bea60972d)
Dari distribusi konsumsi BBM dalam kota (MPG_City), sebagian besar mobil memiliki konsumsi BBM (MPG_City) sekitar 16-21 miles/galon.

![image](https://github.com/user-attachments/assets/215dcef3-a55b-414c-8b92-25d7d92d4802)
Dari distribusi konsumsi BBM dalam Tol (MPG_Highway), sebagian besar mobil memiliki konsumsi BBM (MPG_Highway) sekitar 25-29 miles/galon.


## Data Preparation
Dalam dataset ini, fitur MSRP dan DealerCost merupakan type object/kategorikal. Karena MSRP merupakan harga suatu mobil, maka kedua fitur tersebut akan diubah menjadi fitur numerik

```
car_df['MSRP'] = car_df['MSRP'].str.replace('$', '').str.replace(',', '').astype(float)

car_df['DealerCost'] = car_df['DealerCost'].str.replace('$', '').str.replace(',', '').astype(float)
```
Dari data understanding, diketahui bahwa terdapat 2 missing value di fitur Cylinders.
![image](https://github.com/user-attachments/assets/4e681d6a-b6e8-4837-b76a-9bd2d26a3358)
Dari [mazdausanews](https://news.mazdausa.com/download/RX-8-Spec-Sheet-Final.pdf) diketahui bahwa Mazda dengan model RX-8 tidak mempunyai mesin bertenaga piston, melainkan memakai mesin rotary. Oleh karena itu nilai NaN pada fitur Cylinders akan diganti dengan nilai nol dan akan dibuat fitur baru yaitu Engine_Type. 
```
car_df['Cylinders'] = car_df['Cylinders'].fillna(0)
car_df['Engine_Type'] = 'Piston' # Isi semua dengan 'Piston' sebagai default
car_df.loc[car_df['Model'] == 'RX-8 4dr automatic', 'Engine_Type'] = 'Rotary'
car_df.loc[car_df['Model'] == 'RX-8 4dr manual', 'Engine_Type'] = 'Rotary'
```
Selanjutnya, akan dibuat fitur baru bernama 'Document' didalam DataFrame pandas car_df. Proses ini dilakukan dengan menerapkan fungsi create_document pada setiap baris data. Untuk setiap baris, fungsi ini akan mengambil nilai dari kolom 'VehicleClass', 'Region', 'DriveTrain', dan 'Engine_Type', lalu menggabungkannya menjadi satu kalimat tunggal yang dipisahkan oleh spasi. Pada dasarnya, kode ini menciptakan sebuah kolom teks ringkasan untuk setiap mobil berdasarkan gabungan empat atribut utamanya.

```
def create_document(row):

  vehicle_class = row.get('VehicleClass', '')
  region = row.get('Region', '')
  drive_train = row.get('DriveTrain', '')
  engine_type = row.get('Engine_Type', '')

  return f" {vehicle_class} {region} {drive_train} {engine_type}"
car_df['Document'] = car_df.apply(create_document, axis=1)
```
TF-IDF digunakan untuk vektorisasi teks dan StandardScaler digunakan untuk feature scaling dari kolom numerik. Dalam pemrosesan data ini juga akan menggunakan bobot pada setiap jenis feature, pemberian bobot bertujuan untuk menyeimbangkan pengaruh setiap fitur. Untuk fitur 'Document' akan dikenakan bobot 1.0 dan fitur numerik diberi bobot 3.0. Setelah itu, matriks hasil vektorisasi dengan TF-IDF akan digabung dengan matriks dense numerik. Didapat hybrid_matrix yang merupakan matriks hibrida gabungan atau matrix penggabungan antara vektorisasi 'Document' dengan TF-IDF dan matrix dense numerik.

```
numerical_features = ['MSRP', 'EngineSize', 'Cylinders', 'HorsePower', 'MPG_City', 'MPG_Highway', 'Weight', 'Wheelbase', 'Length']
numerical_features = [col for col in numerical_features if col in car_df.columns]
# Vektorisasi Teks dengan TF-IDF
tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(car_df['Document'])
scaler = StandardScaler()
numerical_matrix_scaled = scaler.fit_transform(car_df[numerical_features])
# Memberi bobot pada setiap jenis fitur untuk menyeimbangkan pengaruhnya
text_weight = 1.0
numeric_weight =  3.0 
# Menggabungkan matriks sparse TF-IDF dengan matriks dense numerik
hybrid_matrix = hstack([
    tfidf_matrix * text_weight,
    np.array(numerical_matrix_scaled) * numeric_weight
]).tocsr() # tocsr() untuk efisiensi

print(f"\nDimensi Matriks Hibrida Gabungan: {hybrid_matrix.shape}")
```


## Modeling
Pada tahap pengembangan model, digunakan pendekatan Content-Based Filtering untuk membangun sistem rekomendasi mobil. Pendekatan ini dipilih karena mampu memberikan rekomendasi yang relevan berdasarkan kemiripan atribut atau fitur intrinsik dari setiap mobil, tanpa memerlukan data histori interaksi pengguna. Untuk menyelesaikan permasalahan ini, diusulkan dua implementasi algoritma yang berbeda guna membandingkan performa dan efisiensinya.

### 1. Cosine Similarity
Solusi pertama memanfaatkan perhitungan Cosine Similarity pada matriks fitur gabungan (hybrid_matrix). Matriks ini merupakan representasi numerik dari seluruh fitur mobil, baik yang bersifat kategorikal (seperti kelas kendaraan dan jenis penggerak) maupun numerik (seperti tenaga kuda dan efisiensi bahan bakar).
```
cosine_sim_hybrid = cosine_similarity(hybrid_matrix, hybrid_matrix)
def get_hybrid_recommendations(model_title, similarity_matrix=cosine_sim_hybrid, num_recommendations=5):
    if model_title not in indices:
        # Jika tidak ada yang sama persis, cari yang mengandung judul itu
        matches = [m for m in indices.index if model_title in m]
        if not matches:
            return f"Model '{model_title}' tidak ditemukan dalam dataset."
        model_title = matches[0] # Ambil yang pertama kali cocok
        print(f"Menampilkan hasil untuk model yang ditemukan: '{model_title}'")

    idx = indices[model_title]

    # Mendapatkan skor kemiripan dari semua mobil dengan mobil tersebut
    sim_scores = list(enumerate(similarity_matrix[idx]))

    # Mengurutkan mobil berdasarkan skor kemiripan
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)

    # Mendapatkan skor dari N mobil paling mirip (dimulai dari 1 untuk skip mobil itu sendiri)
    sim_scores = sim_scores[1:num_recommendations+1]

    # Mendapatkan index mobil
    car_indices = [i[0] for i in sim_scores]

    # Mengembalikan N mobil paling mirip
    return car_df[['Brand', 'Model', 'VehicleClass', 'MSRP', 'HorsePower', 'Engine_Type']].iloc[car_indices]

model_input = input("Masukkan nama model mobil: ")
recommendations = get_hybrid_recommendations(model_input)
recommendations
```
Model ini terlebih dahulu menghitung matriks kemiripan kosinus berukuran (N x N), di mana N adalah jumlah total mobil. Matriks ini menyimpan skor kemiripan (antara 0 dan 1) untuk setiap pasang mobil. Saat pengguna meminta rekomendasi untuk mobil tertentu, sistem akan mencari baris yang sesuai dengan mobil tersebut di matriks kemiripan, lalu mengurutkan skornya untuk menemukan mobil-mobil lain dengan skor tertinggi.

Untuk contoh, penulis menggunakan mobil dengan model Viper SRT-10 convertible 2dr dari Merek Dodge. Lalu, model akan memberi rekomendasi 5 mobil paling mirip. Didapat rekomendasi Top-5 sebagai berikut
![image](https://github.com/user-attachments/assets/7cd195d9-c1fa-4382-8c1e-9d00451220b4)

### K-Nearest Neighbors (KNN)
Solusi kedua menggunakan algoritma K-Nearest Neighbors (KNN), khususnya implementasi NearestNeighbors dari scikit-learn. Pendekatan ini bertujuan untuk menemukan 'K' tetangga terdekat (mobil paling mirip) untuk sebuah titik data (mobil) dalam ruang fitur.

```
knn_model = NearestNeighbors(n_neighbors=11, metric='cosine', algorithm = 'brute')
knn_model.fit(hybrid_matrix)

def get_knn_recommendations(model_name, knn_model, car_df, data_matrix): 
    try:
        model_idx = car_df[car_df['Model'] == model_name].index[0]
    except IndexError:
        print(f"Model '{model_name}' tidak ditemukan dalam dataset.")
        return

    # Dapatkan fitur dari mobil yang dipilih dari matriks data
    model_features = data_matrix[model_idx] 

    # Cari tetangga terdekat
    distances, indices = knn_model.kneighbors(model_features)
    
    similar_car_indices = indices[0][1:]

    print(f"Rekomendasi untuk mobil: {model_name}")
    print("--------------------------------------------------")
    print(car_df.iloc[model_idx])
    print("\nBerikut adalah 10 mobil yang paling mirip:")
    print("--------------------------------------------------")

    return car_df.iloc[similar_car_indices]
knn_recommendations = get_knn_recommendations('Viper SRT-10 convertible 2dr', knn_model, car_df, hybrid_matrix) # <-- Menggunakan hybrid_matrix
knn_recommendations
```
Alih-alih membuat matriks kemiripan penuh, KNN membangun sebuah struktur data yang dioptimalkan untuk kueri pencarian tetangga terdekat. Dengan metric='cosine', algoritma ini secara efisien mencari k mobil dengan jarak kosinus terkecil (yang berarti kemiripan kosinus tertinggi) dari mobil yang diberikan

Untuk contoh,
Untuk contoh, penulis menggunakan mobil dengan model Viper SRT-10 convertible 2dr dari Merek Dodge. Lalu, model akan memberi rekomendasi 5 mobil paling mirip. Didapat rekomendasi Top-5 sebagai berikut.

![image](https://github.com/user-attachments/assets/574d9dc3-b440-47e7-a92f-56b8ddec9d43)

![image](https://github.com/user-attachments/assets/c9183bb3-7bdb-4a7d-93af-1e04a6434652)


## Evaluation
Untuk mengukur performa sistem rekomendasi mobil yang telah dibuat, digunakan pendekatan evaluasi yang menggabungkan analisis kualitatif dan kuantitatif. Karena ini adalah masalah unsupervised learning (content-based filtering) di mana tidak ada label "benar" atau "salah" yang absolut, metrik evaluasi yang dipilih harus dapat mengukur relevansi dan akurasi dari rekomendasi yang dihasilkan.

Metrik evaluasi utama yang digunakan adalah Analisis Kualitatif (Case Study) dan Precision@k.

### 1. Case Study
Analisis kualitatif dilakukan dengan menguji beberapa input mobil yang representatif dan secara manual memeriksa kualitas dari Top-N rekomendasi yang dihasilkan. Tujuannya adalah untuk mendapatkan pemahaman intuitif apakah model bekerja dengan logis.

Saat model (Cosine Similarity & K-Nearest Neighbors) diuji dengan input mobil "Viper SRT-10 convertible 2dr", sistem berhasil merekomendasikan mobil-mobil yang sangat relevan. Dari model Cosine Similarity 5 rekomendasi teratas, mayoritas adalah mobil dari kelas Sport juga, seperti Chevrolet Corvette convertible 2d, CLK500 coupe 2dr (convertible), dan XLR convertible 2dr.

![image](https://github.com/user-attachments/assets/574d9dc3-b440-47e7-a92f-56b8ddec9d43)

![image](https://github.com/user-attachments/assets/7cd195d9-c1fa-4382-8c1e-9d00451220b4)

Lalu, untuk 10 rekomendasi dari model K-Nearest Neighbors, mayoritas adalah mobil dari kelas Sport seperti Chevrolet Corvette convertible 2d, CLK500 coupe 2dr (convertible), dan XLR convertible 2dr.

![image](https://github.com/user-attachments/assets/c9183bb3-7bdb-4a7d-93af-1e04a6434652)

Hal ini menunjukkan bahwa model berhasil menangkap fitur-fitur penting seperti kelas kendaraan, Wheel Driver, dan spesifikasi mesin yang serupa untuk mengidentifikasi mobil lain yang mirip. Hasil ini mengonfirmasi secara kualitatif bahwa solusi yang diimplementasikan berjalan sesuai dengan yang diharapkan.


### Precision@k
Untuk evaluasi kuantitatif, metrik Precision@k digunakan. Metrik ini sangat cocok untuk sistem rekomendasi karena mengukur seberapa akurat daftar rekomendasi yang diberikan kepada pengguna. Precision@k mengukur proporsi item yang relevan dalam k item teratas yang direkomendasikan. Dalam konteks proyek ini, kita dapat mendefinisikan sebuah item sebagai "relevan" jika mobil yang direkomendasikan memiliki VehicleClass yang sama dengan mobil input. Precission@k memiliki persamaan:

![image](https://github.com/user-attachments/assets/c22d59e1-d5fb-4a23-a9be-179e1242dba0)

Setelah menghitung Precissio@k terhadap model, kedua model tersebut mendapat skor rata rata Precission@10 sebesar 71%. 

![image](https://github.com/user-attachments/assets/4416edd7-b672-4931-8bb1-a75af39de00b)

![image](https://github.com/user-attachments/assets/d34e499a-9bc1-40e7-9a4d-75e68cc68da2)

