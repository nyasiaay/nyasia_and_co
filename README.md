### Nama    : Nyasia Aludra Yasmina

### NPM     : 2206828185

### Kelas   : PBP E

### Link    : `https://nyasia-and-co.adaptable.app/main/`

### Tugas 2

**1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).**

1) Membuat sebuah proyek Django baru.

   Untuk membuat proyek Django baru, pertama-tama kita perlu membuat repositori baru di github lalu membuat direktori baru bernama `nyasia_and_co`. Setelah itu kita tambahkan berkas `requirements.txt` di direktori tersebut. Di dalam file txt itu kita tambahkan beberapa _dependencies_ yaitu:
   
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/64cffdfe-bd61-42a2-8bde-40b0e9f331ed)


   Lalu, kita perlu jalankan _virtual environment_ dan kemudian menginstall  _dependencies_ di requirements.txt dengan menjalankan perintah berikut:
        `pip install -r requirements.txt`

   Selajutnya, kita membuat proyek Django baru sesuai nama aplikasi yang sudah dibuat dengan melakukan perintah sebagai berikut:
        `django-admin startporject nyasia_and_co .`
        Kemudian kita perlu tambahkan `*` pada `ALLOWED_HOST` di `settings.py` agar semua host diizinkan mengaksesu untuk proses deployment nanti.

   Lalu, kita jalankan server Django dengan perintah `python manage.py runserver` di terminal.

   Setelah itu, kita perlu mengupload proyek ke repositori dengan melakukan `add`, `commit`, dan `push`.


2) Membuat aplikasi dengan nama main pada proyek tersebut.

   Untuk membuat aplikasi main pada proyek tersebut dapat dilakukan dengan menjalankan perintah: `python manage.py startapp main`

    
3) Melakukan routing pada proyek agar dapat menjalankan aplikasi main.

   Setelah membuat aplikasi main, kita melakukan routing pada proyek dengan cara menambahkan `main` ke berkas `settings.py` pada variabel `INSTALLED_APPS` di dalam direktori proyek `nyasia_and_co` seperti berikut

   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/937bcc0c-65f5-4b46-a392-74a99ab621cd)



 4) Membuat model pada aplikasi main dengan nama Item dan memiliki atribut wajib sebagai berikut.
 
      - `name` sebagai nama item dengan tipe `CharField`.
        
      - `amount` sebagai jumlah item dengan tipe `IntegerField.` 
        
      - `description` sebagai deskripsi item dengan tipe `TextField`.
        
      Kita dapat membuat model tersebut dengan mengisi berkas `models.py` seperti berikut ini:

       ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/ef49294e-6265-4acd-baa6-248775b15b31)

        
      Setelah itu, kita perlu melakukan migrasi untuk menyimpan model dan atributnya pada database dengan menjalankan perintah sebagai berikut di terminal.
   
           python manage.py makemigrations
           python manage.py migrate


5) Membuat sebuah fungsi pada views.py untuk dikembalikan ke dalam sebuah template HTML yang menampilkan nama aplikasi serta nama dan kelas kamu.

      Pertama-tama kita perlu membuat berkas `main.html` di dalam berkas `templates` yang berisi sebagai berikut:
        
      ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/b6f1382d-1c06-4ffd-8c34-a5228907f2a0)

   
      Selanjutnya kita perlu membuka berkas `views.py` yang ada di dalam berkas aplikasi `main` kemudian kita menambahkan baris impor sebagai berikut di bagian berkas paling atas dan kita juga tambahkan fungsi `show_main` di bawah importi seperti berikut ini:

      ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/9f47d6f1-bb6f-42f5-aa16-e7c7b2d57737)

    
6) Membuat sebuah routing pada urls.py aplikasi main untuk memetakan fungsi yang telah dibuat pada views.py.

      Untuk mengerjakan langkah ini kita perlu membuat berkas `urls.py` di direktori aplikasi `main`untuk memetakan fungsi yang sudah dibuat di `views.py` dan mengisi berkas `urls.py` sebagai berikut:

      ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/bd74df1c-2b91-47d1-a4ce-c7c0cfc0cc91)

    
7) Melakukan deployment ke Adaptable terhadap aplikasi yang sudah dibuat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet.
      - Pertama-tama kita perlu membuat akun di Adaptable.io dengan akun github yang berisi repositori yang sudah dibuat sebelumnya.
        
      - Lalu kita dapat membuat aplikasi dengan menekan `New App` kemudian sambungkan dengan repositori `nyasia_and_co` dengan menekan `Connect an Existing Repository`.
        
      - Selanjutnya kita pilih proyek `nyasia_and_co`kemudian pilih `Python App Template`, `PostgreSQL`, dan versi python yang tepat.
        
      - Setelah itu kita tambahkan perintah `python manage.py migrate && gunicorn nyasia-and-co.wsgi`
        
      - Lalu, proses deploy aplikasi dapat dilihat di website Adaptible.io



**2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html.**

   ![CLIENT](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/0ad43871-8976-4471-b30d-8b90a217d05b)

   Saat _client_ memasukkan URL ke browsernya, mereka menginisiasi permintaan. Setelah itu, dilakukan pemetaan alamat dari URL ke _views_ yang sesuai. _Views_ akan mengirimkan permintaan data ke _Models_, yang akan mengembalikan data dari _database_.  _Views_ akan berhubungan dengan berkas HTML di template setelah menerima data dari _Models_. _Views_ pada fungsi akan mengarah ke berkas HTML. Data yang dikumpulkan dari akses database _Models_ kemudian dikembalikan sesuai dengan panggilan dalam berkas HTML. _Webpage_ kemudian akan ditampilkan kepada _client_ berdasarkan parameter pada file HTML yang telah disiapkan.

**3. Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?**

Virtual environment digunakan untuk untuk mengisolasi dan mengelola dependensi dan lingkungan pengembangan. Dengan virtual environment, kita dapat membuat lingkungan terisolasi yang tidak berinteraksi dengan lingkungan Python global di sistem. Meskipun memungkinkan untuk membuat aplikasi web berbasis Django tanpa virtual environment dalam lingkungan server lokal dengan menggunakan environment Python bawaan, hal ini menjadi lebih rumit saat proyek perlu di-host secara online. Ketika di-host, server akan mencari daftar dependensi dalam berkas "requirements.txt" untuk memenuhi paket yang diperlukan oleh proyek. Jika virtual environment tidak diinisialisasi dan "requirements.txt" tidak ada, mesin host tidak akan tahu dependensi apa yang diperlukan untuk menjalankan server, sehingga proyek tidak dapat berfungsi.

**4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.**
   
 **A. MVC (Model-View-Controller):** pola arsitektur yang pertama kali diperkenalkan dan lebih terfokus pada pemisahan tugas antara Model, View, dan Controller.
   
   - Model: Representasi data dan logika bisnis dari aplikasi. Model mengurus penyimpanan, pengambilan, dan pemrosesan data.
      
   - View: Bertanggung jawab untuk menampilkan informasi kepada pengguna dan menggambarkan tampilan antarmuka pengguna.
      
   - Controller: Berfungsi sebagai perantara antara Model dan View. Menerima input dari pengguna, memprosesnya, dan mengupdate Model serta View sesuai kebutuhan.
              
   **B. MVT (Model-View-Template):**  varian dari MVC yang sering digunakan dalam kerangka kerja web seperti Django (Python). Perbedaan utamanya adalah penggunaan "Template" yang mengatur tampilan HTML, sedangkan dalam MVC, View biasanya memiliki tugas yang lebih besar.
   
   - Model: Komponen yang mengelola data dan logika bisnis dari aplikasi.
      
   - View: Menangani presentasi data dan tampilan antarmuka pengguna.
      
   - Template: Bertanggung jawab untuk mengatur tampilan HTML. Template ini umumnya berisi kode logika sederhana untuk mengisi data dari Model ke View.
         
   **C. MVVM (Model-View-ViewModel):** pola arsitektur yang memisahkan logika presentasi dari View dan memanfaatkan "ViewModel" untuk pengikatan data yang kuat dalam aplikasi berbasis pembaruan tampilan.
   
   - Model: komponen yang mengelola data dan logika bisnis dari aplikasi.
     
   - View: Menampilkan informasi kepada pengguna seperti dalam MVC.
     
   - ViewModel: Memisahkan logika presentasi dari View dan mengatur pengikatan data antara Model dan View. ViewModel ini sering digunakan dalam aplikasi berbasis pembaruan tampilan.



### Tugas 3


**1. Apa perbedaan antara form POST dan form GET dalam Django?**

Perbedaan utama antara form POST dan form GET di Django adalah bagaimana keduanya menangani data dan kasus penggunaannya yang dimaksudkan. GET untuk mengambil data dengan data yang terlihat di URL, sedangkan POST untuk mengirim data ke server secara aman dengan data di badan permintaan. Pilihan Anda di antara keduanya bergantung pada fungsionalitas spesifik dan persyaratan keamanan aplikasi web Anda.


**2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?**

JSON (JavaScript Object Notation) adalah turunan dari Object di Javascript yang digunakan sebagai format untuk data delivery. Data pada JSON disimpan dalam bentuk array yang berisi key dan value. Key akan dipanggil dan value akan dikembalikan. Value dapat berupa tipe data primitif (string, number, boolean) ataupun berupa objek. Dengan demikian, JSON menyimpan elemennya dengan cara yang efisien, sehingga JSON banyak digunakan untuk pemrograman di berbagai bahasa, seperti C++ dan Python. Kekurangannya adalah, Tampilan JSON kurang rapih sehingga kurang mudah dimengerti oleh pembacanya.


Sedangkan, XML (Extensible Markup Language) adalah sebuah bahasa markup. Berbeda dengan JSON, XML lebih berfokus pada penampilan data yang tersimpan secara terstruktur dan rapi. Namun, dapat dikatakan kurang efisien. Bahasa markup yang ada di XML lebih mudah dimengerti manusia dibandingkan JSON yang hanya berupa array.


Sama seperti XML, HTML (HyperText Markup Language) juga merupakan bahasa markup. Hanya saja, HTML lebih berfokus pada proses menyajikan data, bukan mentransfer data. HTML digunakan untuk menerapkan tata letak dan konvensi pemformatan ke dokumen teks.

**3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?**

JSON (JavaScript Object Notation) sering digunakan dalam aplikasi web modern karena sifatnya yang dapat dibaca manusia, ringan, dan tidak bergantung pada bahasa, sehingga memudahkan pertukaran data antara berbagai komponen dan layanan. Kesederhanaannya, dukungan asli dalam bahasa pemrograman, kompatibilitas dengan JavaScript, dan manfaat keamanan menjadikannya pilihan utama untuk pertukaran data, baik dalam aplikasi web maupun antar layanan web, mendorong interoperabilitas dan komunikasi yang efisien.


**4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).**