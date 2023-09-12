### Nama    : Nyasia Aludra Yasmina

### NPM     : 2206828185

### Kelas   : PBP E

### Link    : https://nyasia-and-co.adaptable.app/main/


**1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).**


**2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html.**


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
