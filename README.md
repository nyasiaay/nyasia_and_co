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

Perbedaan utama antara form POST dan form GET di Django adalah bagaimana keduanya menangani data dan kasus penggunaannya yang dimaksudkan. GET untuk mengambil data dengan data yang terlihat di URL, sedangkan POST untuk mengirim data ke server secara aman dengan data di badan permintaan. Pilihan di antara keduanya bergantung pada fungsionalitas spesifik dan persyaratan keamanan aplikasi web.


**2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?**

XML (eXtensible Markup Language), JSON (JavaScript Object Notation), dan HTML (Hypertext Markup Language) adalah tiga format data berbeda yang sering digunakan untuk tujuan berbeda dalam konteks pengiriman data di web.

JSON (JavaScript Object Notation) adalah format pengiriman data yang diturunkan dari Object dalam Javascript. Data JSON disimpan dalam bentuk array dengan _key_ dan _value_. _Key_ akan dipanggil dan nilainya akan dikembalikan. _Value_ dapat berupa tipe data sederhana (_string, number,_ dan _boolean_) atau objek. Karena penyimpanan elemen JSON yang efisien, JSON sering digunakan untuk pemrograman dalam berbagai bahasa seperti C++ dan Python. Kekurangannya adalah tampilan JSON yang kurang rapih sehingga menyulitkan pembaca dalam membacanya.

Sedangkan, XML (Extensible Markup Language) merupakan bahasa markup. Berbeda dengan JSON, XML mengutamakan menampilkan data yang disimpan secara terstruktur dan rapi. Namun, bisa dikatakan hal ini kurang efisien. Manusia dapat memahami bahasa markup XML lebih baik daripada JSON, yang pada dasarnya adalah sebuah array.

HTML (HyperText Markup Language) adalah bahasa markup seperti XML. Hanya saja, HTML berkonsentrasi pada proses menampilkan data daripada transfer data. HTML adalah bahasa markup yang digunakan untuk menerapkan prinsip tata letak dan format pada dokumen teks.


**3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?**

JSON (JavaScript Object Notation) sering digunakan dalam aplikasi web modern karena sifatnya yang dapat dibaca manusia, ringan, dan tidak bergantung pada bahasa, sehingga memudahkan pertukaran data antara berbagai komponen dan layanan. Kesederhanaannya, dukungan asli dalam bahasa pemrograman, kompatibilitas dengan JavaScript, dan manfaat keamanan menjadikannya pilihan utama untuk pertukaran data, baik dalam aplikasi web maupun antar layanan web, mendorong interoperabilitas dan komunikasi yang efisien.


**4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).**

1) Membuat input form untuk menambahkan objek model pada app sebelumnya.

   Pertama-tama saya membuka `urls.py` yang ada di _folder_ `nyasia_co` dan mengubah _path_ yang ada pada `urlpatterns` menjadi seperti berikut supaya saat membuka web nya tidak perlu menambah `/main`
   
         urlpatterns = [
          path('', include('main.urls'))
            path('admin/', admin.site.urls),
         ]

   Selanjutnya saya membuat _folder_ baru bernama `templates` pada _folder_ utama dan membuat _file_ HTML bernama `base.html`. Ini berfungsi sebagai kerangka umum untuk halaman webnya. Lalu saya mengisi _file_ tersebut dengan kode sebagai berikut:

         {% load static %}
         <!DOCTYPE html>
         <html lang="en">
             <head>
                 <meta charset="UTF-8" />
                 <meta
                     name="viewport"
                     content="width=device-width, initial-scale=1.0"
                 />
                 {% block meta %}
                 {% endblock meta %}
             </head>
         
             <body>
                 {% block content %}
                 {% endblock content %}
             </body>
         </html>

   Setelah itu saya membuka berkas `settings.py` yang ada di _folder_ `nyasia_co` dan mengubah kodenya agar _file_ `base.html` terdeteksi sebagai berkas template

         TEMPLATES = [
             {
                 'BACKEND': 'django.template.backends.django.DjangoTemplates',
                 'DIRS': [BASE_DIR / 'templates'], # Tambahkan kode ini
                 'APP_DIRS': True,
                 ...
             }
         ]

   Kemudian saya mengubah kode pada berkas `main.html` yang ada di _folder_ `templates` menjadi berikut ini agar ia menggunakan template utama `base.html`

         {% extends 'base.html' %}
         
         {% block content %}
             <h1>nyasia & co.</h1>
         
             <h5>Name:</h5>
             <p>{{name}}</p>
         
             <h5>Class:</h5>
             <p>{{class}}</p>
         {% endblock content %}

   Setelah itu, saya membuat _file_ baru bernama `forms.py` di direktori utama dan menambahkan kode sebagai berikut:

         from django.forms import ModelForm
         from main.models import Item
         
         class ProductForm(ModelForm):
             class Meta:
                 model = Item
                 fields = ["name", "amount", "description"]
   
   Kemudian saya mengubah berkas `views.py` yang ada di _folder_ `main` dan menambahkan beberapa _import_ sebagai berikut:

         from django.http import HttpResponseRedirect
         from main.forms import ProductForm
         from django.urls import reverse
         from main.models import Item

   Lalu, saya menambahkan fungsi baru dengan nama `create_product` di berkas `views.py` agar menerima parameter `request` untuk menghasilkan formulir yang dapat menambahkan data produk secara otomatis ketika data di-_submit_ dari _form_.

         def create_product(request):
             form = ProductForm(request.POST or None)
         
             if form.is_valid() and request.method == "POST":
                 form.save()
                 return HttpResponseRedirect(reverse('main:show_main'))
         
             context = {'form': form}
             return render(request, "create_product.html", context)

Saya juga mengubah fungsi `show_main` pada berkas `views.py` sebagai berikut untuk mengambil seluruh _object_ Item yang tersimpan pada _database_.

         def show_main(request):
             products = Item.objects.all()
         
             context = {
                 'name': 'Nyasia Aludra Yasmina', 
                 'class': 'PBP E', 
                 'products': products
             }
         
             return render(request, "main.html", context)

   Setelah itu, saya membuka `urls.py` pada _folder_ `main` dan _import_ fungsi `create_product`

         from main.views import show_main, create_product

   Lalu, saya menambahkan _path url_ ke dalam `urlpatterns` pada `urls.py` di _folder_ `main` untuk mengakses fungsi yang sudah di-_import_

         path('create-product', create_product, name='create_product'),

   Kemudian, saya membuat _file_ HTML baru bernama `create_product.html` di _folder_ `template` dalam `main` dan menambahkan kode sebagai berikut:

         {% extends 'base.html' %} 
         
         {% block content %}
         <h1>Add New Product</h1>
         
         <form method="POST">
             {% csrf_token %}
             <table>
                 {{ form.as_table }}
                 <tr>
                     <td></td>
                     <td>
                         <input type="submit" value="Add Product"/>
                     </td>
                 </tr>
             </table>
         </form>
         
         {% endblock %}

   Dan pada berkas `main.html` saya menambahkan kode sebagai berikut:

             <table>
                 <tr>
                     <th>Name</th>
                     <th>Amount</th>
                     <th>Description</th>
         
                 </tr>
         
         
                 {% for product in products %}
                     <tr>
                         <td>{{product.name}}</td>
                         <td>{{product.amount}}</td>
                         <td>{{product.description}}</td>
         
                     </tr>
                 {% endfor %}
             </table>
         
         <br />
         
         <a href="{% url 'main:create_product' %}">
             <button>
                 Add New Product
             </button>
         </a>
         
         
         {% endblock content %}


2) Menambahkan 5 fungsi views untuk melihat objek yang sudah ditambahkan dalam format HTML, XML, JSON, XML by ID, dan JSON by ID.

   Untuk menambahkan 5 fungsi views tersebut, pertama-tama saya menambahkan _import_ di berkas `views.py` pada direktori `main` sebagai berikut:

         from django.http import HttpResponse
         from django.core import serializers

   Selanjutnya saya menambahkan fungsi-fungsi berikut di berkas `views.py` pada direktori `main`

         def show_xml(request):
             data = Item.objects.all()
             return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
         
         def show_json(request):
             data = Item.objects.all()
             return HttpResponse(serializers.serialize("json", data), content_type="application/json")
         
         def show_xml_by_id(request, id):
             data = Item.objects.filter(pk=id)
             return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
         
         def show_json_by_id(request, id):
             data = Item.objects.filter(pk=id)
             return HttpResponse(serializers.serialize("json", data), content_type="application/json")

   
3) Membuat routing URL untuk masing-masing views yang telah ditambahkan pada poin 2.

   Untuk membuat routing URL, saya _import_ fungsi-fungsi sebagai berikut pada berkas `urls.py`:

         from main.views import show_main, create_product, show_xml, show_json, show_xml_by_id, show_json_by_id

   Kemudian saya menambahkan _path_ url berikut ini di `urlpatterns` untuk mengakses fungsi yang sudah diimpor.

         urlpatterns = [
             path('', show_main, name='show_main'),
             path('create-product', create_product, name='create_product'),
             path('xml/', show_xml, name='show_xml'), 
             path('json/', show_json, name='show_json'), 
             path('xml/<int:id>/', show_xml_by_id, name='show_xml_by_id'),
             path('json/<int:id>/', show_json_by_id, name='show_json_by_id'), 
         
         ]

   Lalu, kita dapat mengecek dengan mengakses _link-link_ berikut ini:
   
   http://localhost:8000

   http://localhost:8000/xml

   http://localhost:8000/json

   http://localhost:8000/xml/[id]

   http://localhost:8000/json/[id]

   
**Screenshot hasil akses URL pada Postman**
1) HTML
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/1a549322-4657-4d36-8981-4192dabb2a8c)
   
2) XML
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/038b77c9-5edf-4f10-91cc-8a3699ba302c)

3) JSON
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/035a6571-ae7d-4ac6-9554-de02ad7fc610)

4) XML _by ID_
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/ec18c23d-456c-4846-a747-a951ec7ad104)

5) JSON _by ID_
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/1f945a32-ddc3-48ee-911a-1210f04d7f33)




