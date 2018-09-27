# materi toeri pada minggu ke 4

## Rekaptulasi
    dalam panduan pemula untuk teknik data bagian saya menjalankan bahwa kemempuan analisi organisasi di bangun berlapis-lapis
    dari mengumpulkan data mentah dan membangun gudang data untuk menerapkan pembelajaran mesin. mengapa teknik data memainkan peran 
    penting dalam semua bidang ini.
    bagi mereka yang baru dalam proses ETL, sy memperkenalkan beberapa kerangka kerja open source yang populer yang dibuat oleh perusahaan
    seperti linkedin, pinterst, spotfy.
    
## Part II Overview
    pertama saya akan memperkenalkan pemodelan data, proses desain dimana prang dengan hati-hati mendefinisikan skema tabel dan relasi data 
    untuk menangkap metrik dan dimensi bisnis. 
    
## Data Modeling
    ketika seorang pengguna berinteraksi dengan produk seperti Medium, informasinya. seperti postingan yang di simpan dan jumlah 
    tampilan semuanya di tangkap oleh sistem. untuk melayani mereka secara akurat dan tepat waktu kepada pengguna. sangan penting
    untuk mengoptimalkan bisnis data produksi untuk pemrosesan transaksi online. 
    
## Data Modeling Normalization and star schema
    untuk memberikan contoh keputusan desain yang terlibat, kita sering perlu memutuskan sejauhmana tabel harus di normalkan
    namun proliferasi tabel yang lebih kecil juga berarti bahwa pelacakan hubungan data membuthkan ketekunan yang lebih.
    
## Pengukuran Data Historis   
    keuntungan lain yang penting dari menggunakan data temp sebagai kunci partisi adalah kemudahan pengukuran data, ketika pipa 
    ETL dibangun itu menghitung matrik dan dimensi di depan, bukan kebelakang. seringkali kita mungkin ingin meninjau kembali
    Tren dan gerakan Historis.
    
## Menentukan Grafik Acyclic Sutradara (DAG)
    Seperti yang kami sebutkan di posting sebelumnya, setiap pekerjaan ETL, pada intinya, dibangun di atas
    tiga blok bangunan: Extract,Transform, dan Load. Sesederhana mungkin terdengar konseptual, pekerjaan ETL
    dalam kehidupan nyata seringkali kompleks, yang terdiri dari banyak kombinasi tugas E, T, dan L. Akibatnya,
    seringkali berguna untuk memvisualisasikan aliran data kompleks menggunakan grafik. Secara visual, simpul 
    dalam grafik mewakili tugas, dan panah menunjukkan ketergantungan satu tugas pada tugas lainnya.Mengingat
    bahwa data hanya perlu dihitung satu kali pada tugas yang diberikan dan perhitungannya kemudian diteruskan, 
    grafik diarahkan dan asiklik. Inilah sebabnya mengapa pekerjaan Airflow sering disebut 
    sebagai "DAGs" (Directed Acyclic Graphs).
    
## ETL Best Practices To Follow   
   Seperti halnya kerajinan apapun, menulis pekerjaan Aliran Udara yang ringkas, mudah dibaca, dan terukur membutuhkan latihan. Pada pekerjaan pertama saya, ETL kepada saya hanyalah serangkaian tugas mekanis biasa yang harus saya selesaikan. Saya tidak melihatnya sebagai kerajinan atau saya tidak tahu praktik terbaik. Di Airbnb, saya belajar banyak tentang praktik terbaik dan saya mulai menghargai ETL yang baik dan betapa indahnya mereka. Di bawah ini, saya daftar daftar prinsip yang tidak lengkap yang harus dipatuhi oleh saluran pipa ETL yang baik:
