### Nama    : Nyasia Aludra Yasmina

### NPM     : 2206828185

### Kelas   : PBP E

### Link    : `https://nyasia-and-co.adaptable.app/main/`

# Tugas 2

## 1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial). ##

**1) Membuat sebuah proyek Django baru.**

   Untuk membuat proyek Django baru, pertama-tama kita perlu membuat repositori baru di github lalu membuat direktori baru bernama `nyasia_and_co`. Setelah itu kita tambahkan berkas `requirements.txt` di direktori tersebut. Di dalam file txt itu kita tambahkan beberapa _dependencies_ yaitu:
   
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/64cffdfe-bd61-42a2-8bde-40b0e9f331ed)


   Lalu, kita perlu jalankan _virtual environment_ dan kemudian menginstall  _dependencies_ di requirements.txt dengan menjalankan perintah berikut:
        `pip install -r requirements.txt`

   Selanjutnya, kita membuat proyek Django baru sesuai nama aplikasi yang sudah dibuat dengan melakukan perintah sebagai berikut:
        `django-admin startproject nyasia_and_co .`
        Kemudian kita perlu tambahkan `*` pada `ALLOWED_HOST` di `settings.py` agar semua host diizinkan mengakses untuk proses deployment nanti.

   Lalu, kita jalankan server Django dengan perintah `python manage.py runserver` di terminal.

   Setelah itu, kita perlu mengupload proyek ke repositori dengan melakukan `add`, `commit`, dan `push`.


**2) Membuat aplikasi dengan nama main pada proyek tersebut.**

   Untuk membuat aplikasi main pada proyek tersebut dapat dilakukan dengan menjalankan perintah: `python manage.py startapp main`

    
**3) Melakukan routing pada proyek agar dapat menjalankan aplikasi main.**
   Setelah membuat aplikasi main, kita melakukan routing pada proyek dengan cara menambahkan `main` ke berkas `settings.py` pada variabel `INSTALLED_APPS` di dalam direktori proyek `nyasia_and_co` seperti berikut

   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/937bcc0c-65f5-4b46-a392-74a99ab621cd)



**4) Membuat model pada aplikasi main dengan nama Item dan memiliki atribut wajib sebagai berikut.**
 
  - `name` sebagai nama item dengan tipe `CharField`.
        
  - `amount` sebagai jumlah item dengan tipe `IntegerField.` 
        
  - `description` sebagai deskripsi item dengan tipe `TextField`.
        
  Kita dapat membuat model tersebut dengan mengisi berkas `models.py` seperti berikut ini:

![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/3db87086-d979-4e38-95e0-50c7563769ac)


        
  Setelah itu, kita perlu melakukan migrasi untuk menyimpan model dan atributnya pada database dengan menjalankan perintah sebagai berikut di terminal.
   
  ```python
  python manage.py makemigrations
  python manage.py migrate
  ```


**5) Membuat sebuah fungsi pada views.py untuk dikembalikan ke dalam sebuah template HTML yang menampilkan nama aplikasi serta nama dan kelas kamu.**

  Pertama-tama kita perlu membuat berkas `main.html` di dalam berkas `templates` yang berisi sebagai berikut:
        
  ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/b6f1382d-1c06-4ffd-8c34-a5228907f2a0)

   
  Selanjutnya kita perlu membuka berkas `views.py` yang ada di dalam berkas aplikasi `main` kemudian kita menambahkan baris impor sebagai berikut di bagian berkas paling atas dan kita juga tambahkan fungsi `show_main` di bawah _import_ seperti berikut ini:

  ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/9f47d6f1-bb6f-42f5-aa16-e7c7b2d57737)

    
**6) Membuat sebuah routing pada urls.py aplikasi main untuk memetakan fungsi yang telah dibuat pada views.py.**

  Untuk mengerjakan langkah ini kita perlu membuat berkas `urls.py` di direktori aplikasi `main`untuk memetakan fungsi yang sudah dibuat di `views.py` dan mengisi berkas `urls.py` sebagai berikut:

  ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/bd74df1c-2b91-47d1-a4ce-c7c0cfc0cc91)

    
**7) Melakukan deployment ke Adaptable terhadap aplikasi yang sudah dibuat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet.**
  - Pertama-tama kita perlu membuat akun di Adaptable.io dengan akun github yang berisi repositori yang sudah dibuat sebelumnya.
        
  - Lalu kita dapat membuat aplikasi dengan menekan `New App` kemudian sambungkan dengan repositori `nyasia_and_co` dengan menekan `Connect an Existing Repository`.
        
  - Selanjutnya kita pilih proyek `nyasia_and_co`kemudian pilih `Python App Template`, `PostgreSQL`, dan versi python yang tepat.
        
  - Setelah itu kita tambahkan perintah `python manage.py migrate && gunicorn nyasia-and-co.wsgi`
        
  - Lalu, proses deploy aplikasi dapat dilihat di website Adaptible.io



## 2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html. ##

   ![CLIENT](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/0ad43871-8976-4471-b30d-8b90a217d05b)

   Saat _client_ memasukkan URL ke browsernya, mereka menginisiasi permintaan. Setelah itu, dilakukan pemetaan alamat dari URL ke _views_ yang sesuai. _Views_ akan mengirimkan permintaan data ke _Models_, yang akan mengembalikan data dari _database_.  _Views_ akan berhubungan dengan berkas HTML di template setelah menerima data dari _Models_. _Views_ pada fungsi akan mengarah ke berkas HTML. Data yang dikumpulkan dari akses database _Models_ kemudian dikembalikan sesuai dengan panggilan dalam berkas HTML. _Webpage_ kemudian akan ditampilkan kepada _client_ berdasarkan parameter pada file HTML yang telah disiapkan.

## 3. Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment? ##

Virtual environment digunakan untuk untuk mengisolasi dan mengelola dependensi dan lingkungan pengembangan. Dengan virtual environment, kita dapat membuat lingkungan terisolasi yang tidak berinteraksi dengan lingkungan Python global di sistem. Meskipun memungkinkan untuk membuat aplikasi web berbasis Django tanpa virtual environment dalam lingkungan server lokal dengan menggunakan environment Python bawaan, hal ini menjadi lebih rumit saat proyek perlu di-host secara online. Ketika di-host, server akan mencari daftar dependensi dalam berkas "requirements.txt" untuk memenuhi paket yang diperlukan oleh proyek. Jika virtual environment tidak diinisialisasi dan "requirements.txt" tidak ada, mesin host tidak akan tahu dependensi apa yang diperlukan untuk menjalankan server, sehingga proyek tidak dapat berfungsi.

## 4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya. ##
   
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
## ##

# Tugas 3


## 1. Apa perbedaan antara form POST dan form GET dalam Django? ##

Perbedaan utama antara form POST dan form GET di Django adalah bagaimana keduanya menangani data dan kasus penggunaannya yang dimaksudkan. GET untuk mengambil data dengan data yang terlihat di URL, sedangkan POST untuk mengirim data ke server secara aman dengan data di badan permintaan. Pilihan di antara keduanya bergantung pada fungsionalitas spesifik dan persyaratan keamanan aplikasi web.


## 2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data? ##

XML (eXtensible Markup Language), JSON (JavaScript Object Notation), dan HTML (Hypertext Markup Language) adalah tiga format data berbeda yang sering digunakan untuk tujuan berbeda dalam konteks pengiriman data di web.

JSON (JavaScript Object Notation) adalah format pengiriman data yang diturunkan dari Object dalam Javascript. Data JSON disimpan dalam bentuk array dengan _key_ dan _value_. _Key_ akan dipanggil dan nilainya akan dikembalikan. _Value_ dapat berupa tipe data sederhana (_string, number,_ dan _boolean_) atau objek. Karena penyimpanan elemen JSON yang efisien, JSON sering digunakan untuk pemrograman dalam berbagai bahasa seperti C++ dan Python. Kekurangannya adalah tampilan JSON yang kurang rapi sehingga menyulitkan pembaca dalam membacanya.

Sedangkan, XML (Extensible Markup Language) merupakan bahasa markup. Berbeda dengan JSON, XML mengutamakan menampilkan data yang disimpan secara terstruktur dan rapi. Namun, bisa dikatakan hal ini kurang efisien. Manusia dapat memahami bahasa markup XML lebih baik daripada JSON, yang pada dasarnya adalah sebuah array.

HTML (HyperText Markup Language) adalah bahasa markup seperti XML. Hanya saja, HTML berkonsentrasi pada proses menampilkan data daripada transfer data. HTML adalah bahasa markup yang digunakan untuk menerapkan prinsip tata letak dan format pada dokumen teks.


## 3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern? ##

JSON (JavaScript Object Notation) sering digunakan dalam aplikasi web modern karena sifatnya yang dapat dibaca manusia, ringan, dan tidak bergantung pada bahasa, sehingga memudahkan pertukaran data antara berbagai komponen dan layanan. Kesederhanaannya, dukungan asli dalam bahasa pemrograman, kompatibilitas dengan JavaScript, dan manfaat keamanan menjadikannya pilihan utama untuk pertukaran data, baik dalam aplikasi web maupun antar layanan web, mendorong interoperabilitas dan komunikasi yang efisien.


## 4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial). ##

**1) Membuat input form untuk menambahkan objek model pada app sebelumnya.**

   Pertama-tama saya membuka `urls.py` yang ada di _folder_ `nyasia_co` dan mengubah _path_ yang ada pada `urlpatterns` menjadi seperti berikut supaya saat membuka web nya tidak perlu menambah `/main`

```python
   urlpatterns = [
   path('', include('main.urls'))
   path('admin/', admin.site.urls),
    ]
```

   Selanjutnya saya membuat _folder_ baru bernama `templates` pada _folder_ utama dan membuat _file_ HTML bernama `base.html`. Ini berfungsi sebagai kerangka umum untuk halaman webnya. Lalu saya mengisi _file_ tersebut dengan kode sebagai berikut:

```python
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
```

   Setelah itu saya membuka berkas `settings.py` yang ada di _folder_ `nyasia_co` dan mengubah kodenya agar _file_ `base.html` terdeteksi sebagai berkas template

```python
         TEMPLATES = [
             {
                 'BACKEND': 'django.template.backends.django.DjangoTemplates',
                 'DIRS': [BASE_DIR / 'templates'], # Tambahkan kode ini
                 'APP_DIRS': True,
                 ...
             }
         ]
```

   Kemudian saya mengubah kode pada berkas `main.html` yang ada di _folder_ `templates` menjadi berikut ini agar ia menggunakan template utama `base.html`

```python
         {% extends 'base.html' %}
         
         {% block content %}
             <h1>nyasia & co.</h1>
         
             <h5>Name:</h5>
             <p>{{name}}</p>
         
             <h5>Class:</h5>
             <p>{{class}}</p>
         {% endblock content %}
```

   Setelah itu, saya membuat _file_ baru bernama `forms.py` di direktori utama dan menambahkan kode sebagai berikut:

```python
         from django.forms import ModelForm
         from main.models import Item
         
         class ProductForm(ModelForm):
             class Meta:
                 model = Item
                 fields = ["name", "amount", "description"]
```
   
   Kemudian saya mengubah berkas `views.py` yang ada di _folder_ `main` dan menambahkan beberapa _import_ sebagai berikut:

```python
         from django.http import HttpResponseRedirect
         from main.forms import ProductForm
         from django.urls import reverse
         from main.models import Item
```

   Lalu, saya menambahkan fungsi baru dengan nama `create_product` di berkas `views.py` agar menerima parameter `request` untuk menghasilkan formulir yang dapat menambahkan data produk secara otomatis ketika data di-_submit_ dari _form_.

```python
         def create_product(request):
             form = ProductForm(request.POST or None)
         
             if form.is_valid() and request.method == "POST":
                 form.save()
                 return HttpResponseRedirect(reverse('main:show_main'))
         
             context = {'form': form}
             return render(request, "create_product.html", context)
```

   Saya juga mengubah fungsi `show_main` pada berkas `views.py` sebagai berikut untuk mengambil seluruh _object_ Item yang tersimpan pada _database_.

```python
         def show_main(request):
             products = Item.objects.all()
         
             context = {
                 'name': 'Nyasia Aludra Yasmina', 
                 'class': 'PBP E', 
                 'products': products
             }
         
             return render(request, "main.html", context)
```

   Setelah itu, saya membuka `urls.py` pada _folder_ `main` dan _import_ fungsi `create_product`

```python
         from main.views import show_main, create_product
```

   Lalu, saya menambahkan _path url_ ke dalam `urlpatterns` pada `urls.py` di _folder_ `main` untuk mengakses fungsi yang sudah di-_import_
```python
         path('create-product', create_product, name='create_product'),
```

   Kemudian, saya membuat _file_ HTML baru bernama `create_product.html` di _folder_ `template` dalam `main` dan menambahkan kode sebagai berikut:

```python
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
```

   Dan pada berkas `main.html` saya menambahkan kode sebagai berikut:

```python
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
```

**2) Menambahkan 5 fungsi views untuk melihat objek yang sudah ditambahkan dalam format HTML, XML, JSON, XML by ID, dan JSON by ID.**

   Untuk menambahkan 5 fungsi views tersebut, pertama-tama saya menambahkan _import_ di berkas `views.py` pada direktori `main` sebagai berikut:

```python
         from django.http import HttpResponse
         from django.core import serializers
```

   Selanjutnya saya menambahkan fungsi-fungsi berikut di berkas `views.py` pada direktori `main`

```python
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
```
   
**3) Membuat routing URL untuk masing-masing views yang telah ditambahkan pada poin 2.**

   Untuk membuat routing URL, saya _import_ fungsi-fungsi sebagai berikut pada berkas `urls.py`:

```python
         from main.views import show_main, create_product, show_xml, show_json, show_xml_by_id, show_json_by_id
```

   Kemudian saya menambahkan _path_ url berikut ini di `urlpatterns` untuk mengakses fungsi yang sudah diimpor.

```python
         urlpatterns = [
             path('', show_main, name='show_main'),
             path('create-product', create_product, name='create_product'),
             path('xml/', show_xml, name='show_xml'), 
             path('json/', show_json, name='show_json'), 
             path('xml/<int:id>/', show_xml_by_id, name='show_xml_by_id'),
             path('json/<int:id>/', show_json_by_id, name='show_json_by_id'), 
         
         ]
```

   Lalu, kita dapat mengecek dengan mengakses _link-link_ berikut ini:
   
   http://localhost:8000

   http://localhost:8000/xml

   http://localhost:8000/json

   http://localhost:8000/xml/[id]

   http://localhost:8000/json/[id]

   
## 5. Screenshot hasil akses URL pada Postman ##
**1) HTML**
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/1a549322-4657-4d36-8981-4192dabb2a8c)
   
**2) XML**
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/038b77c9-5edf-4f10-91cc-8a3699ba302c)

**3) JSON**
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/035a6571-ae7d-4ac6-9554-de02ad7fc610)

**4) XML _by ID_**
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/ec18c23d-456c-4846-a747-a951ec7ad104)

**5) JSON _by ID_**
   ![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/1f945a32-ddc3-48ee-911a-1210f04d7f33)
## ##

# Tugas 4

## 1. Apa itu Django UserCreationForm, dan jelaskan apa kelebihan dan kekurangannya? ##

Django `UserCreationForm` adalah _built-in form class_ dalam sistem autentikasi Django, dirancang khusus untuk menyederhanakan pembuatan formulir pendaftaran pengguna dalam aplikasi web Django. Kegunaan utama formulir ini adalah untuk memungkinkan pengguna mendaftar akun di aplikasi web kita. Formnya mencakup tiga bidang _default_: 'username,' 'password1,' and 'password2' (biasa digunakan untuk konfirmasi kata sandi). `UserCreationForm` memudahkan pembuatan akun pengguna baru yang dapat mengakses dan menggunakan aplikasi web kita.

Untuk menggunakan `UserCreationForm` kita perlu _import_ dari django.contrib.auth.forms. seperti berikut ini:

    from django.contrib.auth.forms import UserCreationForm  

Kelebihan Django `UserCreationForm` :
  1) Mudah digunakan
     Karena `UserCreationForm` sudah _built-in_ dalam django, untuk menggunakannya kita hanya perlu men-_import_
  2) Dapat di-_custom_
     Kita dapat mengkostumisasi sesuai dengan kebutuhan kita. Kita dapat melakukan kustomisasi dengan menambahkan bidang tambahan atau mengubah yang sudah ada untuk menyesuaikan kebutuhan aplikasi web kita.
  3) Integrasi dengan sistem autentikasi django
     Karena `UserCreationForm` sudah terintegrasi dengan baik dengan sistem autentikasi Django, yang membuatnya lebih mudah untuk mengelola autentikasi pengguna.

Kekurangan Django `UserCreationForm` :
  1) Keterbatasan dalam Bidang
     `UserCreationForm` hanya menyertakan beberapa bidang dasar seperti username, password, dan email. Jika kita memerlukan bidang tambahan untuk profil pengguna, kita perlu membuat form kustom atau menggunakan aplikasi pihak ketiga.
  2) _Styling_ UI yang terbatas
     HTML dan _style_ default form mungkin tidak cocok dengan desain dan estetika aplikasi web kita. Kita perlu meluangkan waktu dalam menata gaya dan mengintegrasikannya ke frontend kita, yang mungkin memerlukan keahlian CSS dan JavaScript.
  3) Ketergantungan pada Django
     Jika kita memutuskan untuk menggunakan _framework_ lain di masa depan, kita mungkin perlu menulis ulang bagian autentikasi kita, termasuk penggunaan UserCreationForm.

## 2. Apa perbedaan antara autentikasi dan otorisasi dalam konteks Django, dan mengapa keduanya penting? ##

Autentikasi dan otorisasi adalah dua konsep penting dalam pengembangan web, termasuk Django. Berikut perbedaan keduanya:

- **Autentikasi**
  
  Autentikasi adalah proses memverifikasi identitas pengguna. Ini melibatkan pemeriksaan apakah pengguna tersebut sesuai dengan klaimnya. Sistem autentikasi Django sangat _general_ dan tidak menyediakan beberapa fitur yang biasa ditemukan dalam sistem autentikasi web.

- **Otorisasi**

  Otorisasi menentukan apa yang boleh dilakukan oleh pengguna yang diautentikasi. Ini adalah proses pemberian atau penolakan akses ke data tertentu. Dalam proses otorisasi, otoritas seseorang atau pengguna diperiksa untuk mengakses data. Di Django, otorisasi menentukan apa yang boleh dilakukan oleh pengguna yang diautentikasi.

Baik autentikasi dan otorisasi penting dalam Django dan pengembangan web secara umum. Mereka membantu memastikan bahwa hanya pengguna yang berwenang yang dapat mengakses data tertentu dan melakukan tindakan tertentu. Hal ini membantu melindungi informasi sensitif dan mencegah akses tidak sah ke sistem dan data penting. 

## 3. Apa itu cookies dalam konteks aplikasi web, dan bagaimana Django menggunakan cookies untuk mengelola data sesi pengguna? ##

_Cookies_ adalah potongan kecil data yang disimpan di sisi klien dan dikirim ke server dengan setiap _request_. Dalam konteks aplikasi web, _cookies_ digunakan untuk menyimpan data pengguna, seperti informasi login, preferensi, dan data sesi. Django, menggunakan _cookies_ untuk mengelola data sesi pengguna. Berikut ini bagaimana Django menggunakan _cookies_ untuk mengelola data sesi pengguna:

- Django mengabstraksi proses pengiriman dan penerimaan _cookies_ dengan menempatkan _cookies_ ID sesi di sisi klien dan menyimpan semua data terkait di sisi server.

- _Framework_ sesi membiarkan kita menyimpan data arbitrer berdasarkan per pengunjung situs. Ini menyimpan data di sisi server dan mengabstraksi pengiriman dan penerimaan _cookies_.

- _Cookies_ berisi ID sesi, bukan data itu sendiri, kecuali kita menggunakan _backend_ berbasis _cookies_. Data itu sendiri tidak disimpan di sisi klien, dan ini bagus dari sudut pandang keamanan.

- Secara _default_, Django membuat serial data sesi menggunakan JSON. Kita dapat menggunakan pengaturan untuk menyesuaikan format serialisasi sesi.

- Django menyediakan dukungan penuh untuk sesi anonim. Data sesi disimpan di sisi server, sedangkan _cookies_ disimpan di sisi klien.

- Ada beberapa cara berbeda untuk mengkonfigurasi mesin sesi yang mengontrol cara menyimpan sesi, yaitu dalam database atau cache.

- Secara _default_, Django hanya menyimpan ke database sesi dan mengirimkan _cookies_ sesi ke klien ketika sesi telah dimodifikasi atau dihapus.

## 4. Apakah penggunaan cookies aman secara default dalam pengembangan web, atau apakah ada resiko potensial yang harus diwaspadai? ##

Meskipun _cookies_ adalah fitur umum dalam pengembangan web, ada potensi risiko terkait penggunaannya yang harus diwaspadai oleh _developers_.

- _Cyberattacks_: _Cookies_ dapat digunakan untuk mempertahankan serangan berbahaya seperti _cross-site scripting_ (XSS) atau _cross-site request forgery_ (CSRF).

- Pembajakan: Tergantung pada bagaimana _cookies_ digunakan dan diekspos, _cookies_ dapat menimbulkan resiko keamanan yang serius. Misalnya, _cookies_ dapat dibajak, dan token sesi/autentikasi sensitif yang disimpan dalam _cookies_ dapat diambil oleh pelaku kejahatan, sehingga menyebabkan pencurian kredensial dan informasi identitas pribadi, serta penipuan kartu kredit.

- Kebocoran data: Jika informasi dari _cookies_ jatuh ke tangan yang salah, data pengguna berisiko diretas, menjadi sasaran _ransomware_, dan aktivitas berbahaya lainnya.

Untuk mengurangi risiko ini, _developers_ dapat mengambil beberapa tindakan, seperti menyetel tanda aman pada _cookies_, menggunakan HTTPS saat mengunjungi situs, dan menyimpan _cookies_ dengan informasi sensitif dalam format terenkripsi. Dengan mengambil tindakan pencegahan ini, pengembang dapat membantu memastikan bahwa penggunaan _cookies_ mereka aman dan terjamin.

## 5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial). ##

**1. Mengimplementasikan fungsi registrasi, login, dan logout untuk memungkinkan pengguna untuk mengakses aplikasi sebelumnya dengan lancar.**

  Untuk mengimplementasikan fungsi registrasi, login, dan logout, pertama-tama kita perlu meng-_import_ `redirect`. `UserCreationForm`, dan `messages` pada berkas `views.py` yang ada di _folder_ `main`.

```python
      from django.shortcuts import redirect
      from django.contrib.auth.forms import UserCreationForm
      from django.contrib import messages  
```
    
  Dengan meng-_import_ `UserCreationForm`, pengguna baru dapat mendaftar dengan mudah di aplikasi web kita tanpa harus menulis kode dari awal.

  **- Registrasi:**
    
  Untuk mengimplementasikan fungsi registrasi, kita perlu membuat fungsi dengan nama `register` yang menerima parameter `request`pada berkas `views.py` yang ada di _folder_ `main` dengan kode seperti berikut:

```python
        def register(request):
        form = UserCreationForm()

        if request.method == "POST":
          form = UserCreationForm(request.POST)
          if form.is_valid():
              form.save()
              messages.success(request, 'Your account has been successfully created!')
              return redirect('main:login')
        context = {'form':form}
        return render(request, 'register.html', context)
```

  Selanjutnya kita perlu membuat berkas HTML baru dengan nama `register.html` pada direktori `main/templates` dengan isi kode sebagai berikut:
```python
        {% extends 'base.html' %}

        {% block meta %}
            <title>Register</title>
        {% endblock meta %}

        {% block content %}  

        <div class = "login">
    
            <h1>Register</h1>  

               <form method="POST" >  
                  {% csrf_token %}  
                  <table>  
                    {{ form.as_table }}  
                    <tr>  
                        <td></td>
                        <td><input type="submit" name="submit" value="Daftar"/></td>  
                    </tr>  
                  </table>  
                </form>

            {% if messages %}  
              <ul>   
                {% for message in messages %}  
                   <li>{{ message }}</li>  
                   {% endfor %}  
              </ul>   
            {% endif %}

        </div>  

        {% endblock content %}
```

  Lalu, kita buka `urls.py` di subdirektori `main` dan _import_ fungsi tadi

```python
    from main.views import register
```

  Yang terakhir, kita tambahkan _path url_ ke dalam `urlpatterns`untuk mengakses fungsi yang sudah di _import_

```python
    path('register/', register, name='register'),
```

  **- Login:**
  
  Untuk mengimplementasikan fungsi login, kita perlu meng- _import_ `authenticate` dan `login` di berkas `views.py` pada _folder_ `main`

```python
    from django.contrib.auth import authenticate, login
```

  Selanjutnya, kita perlu membuat fungsi dengan nama `login` yang menerima parameter `request`pada berkas `views.py` yang ada di _folder_ `main` dengan kode seperti berikut:

```python
    def login_user(request):
        if request.method == 'POST':
            username = request.POST.get('username')
            password = request.POST.get('password')
            user = authenticate(request, username=username, password=password)
            if user is not None:
                login(request, user)
                return redirect('main:show_main')
            else:
                messages.info(request, 'Sorry, incorrect username or password. Please try again.')
        context = {}
        return render(request, 'login.html', context)
```

  Setelah itu, kita perlu membuat berkas HTML baru dengan nama `login.html` pada direktori `main/templates` dengan isi kode sebagai berikut:

```python
    {% extends 'base.html' %}

    {% block meta %}
        <title>Login</title>
    {% endblock meta %}

    {% block content %}

    <div class = "login">

        <h1>Login</h1>

        <form method="POST" action="">
            {% csrf_token %}
            <table>
                <tr>
                    <td>Username: </td>
                    <td><input type="text" name="username" placeholder="Username" class="form-control"></td>
                </tr>
                        
                <tr>
                    <td>Password: </td>
                    <td><input type="password" name="password" placeholder="Password" class="form-control"></td>
                </tr>

                <tr>
                    <td></td>
                    <td><input class="btn login_btn" type="submit" value="Login"></td>
                </tr>
            </table>
        </form>

        {% if messages %}
            <ul>
                {% for message in messages %}
                    <li>{{ message }}</li>
                {% endfor %}
            </ul>
        {% endif %}     
            
        Don't have an account yet? <a href="{% url 'main:register' %}">Register Now</a>

    </div>

    {% endblock content %}
```

  Lalu, kita buka `urls.py` di subdirektori `main` dan _import_ fungsi tadi

```python
    from main.views import login_user
```

  Yang terakhir, kita tambahkan _path url_ ke dalam `urlpatterns`untuk mengakses fungsi yang sudah di _import_

```python
    path('login/', login_user, name='login'),
```

  **- Logout:**

  Untuk mengimplementasikan fungsi logout, kita perlu meng- _import_ `logout` di berkas `views.py` pada _folder_ `main`

```python
    from django.contrib.auth import logout
```

  Setelah itu, kita perlu menambahkan kode di bawah ini ke fungsi `logout`

```python
    def logout_user(request):
        logout(request)
        return redirect('main:login')
```

  Selanjutnya, kita tambahkan potongan kode di bawah ini setelah _hyperlink tag_ untuk _Add New Product_ pada berkas `main.html`.

```python
    <a href="{% url 'main:logout' %}">
        <button>
            Logout
        </button>
    </a>
```

  Lalu, kita buka `urls.py` di subdirektori `main` dan _import_ fungsi tadi

```python
    from main.views import logout_user
```

  Yang terakhir, kita tambahkan _path url_ ke dalam `urlpatters`untuk mengakses fungsi yang sudah di _import_

```python
    path('logout/', logout_user, name='logout'),
```

**2. Membuat dua akun pengguna dengan masing-masing tiga dummy data menggunakan model yang telah dibuat pada aplikasi sebelumnya untuk setiap akun di lokal.**

Saya sudah membuat dua akun bernama nyasiaay dan aludra dan sudah menambahkan masing-masing tiga produk ke tiap akun.

**3. Menghubungkan model Item dengan User.**

Pertama-tama kita perlu _import_ user ke berkas `models.py` pada _folder_ `main`.

Lalu, kita tambahkan potongan kode di bawah ini pada model `Item`:

```python
    class Item(models.Model):
        user = models.ForeignKey(User, on_delete=models.CASCADE)
```

Selanjutnya, kita buka `view.py` di _folder_ `main` dan ubah potongan kode pada fungsi create_product menjadi sebagai berikut:

```python
    def create_product(request):
    form = ProductForm(request.POST or None)

    if form.is_valid() and request.method == "POST":
        product = form.save(commit=False)
        product.user = request.user
        product.save()
        return HttpResponseRedirect(reverse('main:show_main'))
```

**4. Menampilkan detail informasi pengguna yang sedang logged in seperti username dan menerapkan cookies seperti last login pada halaman utama aplikasi.**

Pertama-tama, kita ubah fungsi `show_main` menjadi seperti di bawah dengan fungsi untuk menampilkan objek `Item` yang diasosiasikan dengan pengguna yang sedang login.

```python
        def show_main(request):
            products = Product.objects.filter(user=request.user)

            context = {
                'name': request.user.username,
```

Untuk menampilkan data _last login_, kita perlu meng-_import_ `datetime` di berkas `views.py` pada _folder_ main, lalu mengubah kode `login_user` menjadi seperti berikut:

```python
    if user is not None:
        login(request, user)
        response = HttpResponseRedirect(reverse("main:show_main")) 
        response.set_cookie('last_login', str(datetime.datetime.now()))
        return response
```

Selanjutnya, kita tambahkan `context` pada fungsi `show_main` dengan kode berikut:

```python
    'last_login': request.COOKIES['last_login'],
```

Setelah itu untuk menghapus data cookie pengguna yang baru saja logout, kita tambahkan kode di fungsi `logout_user` dengan kode berikut:

```python
response = HttpResponseRedirect(reverse('main:login'))
response.delete_cookie('last_login')
```

Untuk menampilkan informasi user yang sedang login, kita tambahkan context di berkas `main.html` seperti berikut:

```python
    <h5>Sesi terakhir login: {{ last_login }}</h5>
```

**4. Membuat tombol menambah dan mengurangi jumlah _Item_ dan tombol _delete Item_**

Pertama-tama kita _import_ fungsi `get_object_or_404`, setelah itu kita buat fungsi masing-masing untuk menambah, mengurangi, dan menghapus _item_ seperti berikut ini pada berkas `views.py`:

```python
@login_required(login_url='/login')
def add_amount(request, item_id):
    item = get_object_or_404(Item, pk=item_id, user=request.user)
    item.amount += 1
    item.save()
    return HttpResponseRedirect(reverse('main:show_main'))

@login_required(login_url='/login')
def minus_amount(request, item_id):
    item = get_object_or_404(Item, pk=item_id, user=request.user)
    item.amount -= 1
    item.save()
    return HttpResponseRedirect(reverse('main:show_main'))

@login_required(login_url='/login')
def delete_item(request, item_id):
    item = get_object_or_404(Item, pk=item_id, user=request.user)
    item.delete()
    return HttpResponseRedirect(reverse('main:show_main'))
```

Setelah itu kita mengubah kode di berkas `main.html` menjadi seperti berikut agar fungsi-fungsinya terhubung dan menambah tombol yang diperlukan:

```python
        {% for product in products %}
            <tr>
                <td>{{ product.name }}</td>
                <td>{{ product.amount }}</td>
                <td>{{ product.description }}</td>
                <td>
                    <a href="{% url 'main:add_amount' product.id %}">
                        <button>
                            +
                        </button>
                    </a>
                    <a href="{% url 'main:minus_amount' product.id %}">
                        <button>
                            -
                        </button>
                    </a>
                    <a href="{% url 'main:delete_item' product.id %}">
                        <button>
                            Delete
                        </button>
                    </a>
                </td>
            </tr>
        {% endfor %}
```

Setelah itu, meng-_import_ fungsi yang telah dibuat ke berkas `urls.py`  

```python
from main.views import add_amount, minus_amount, delete_item
```

Dan yang terakhir, kita perlu menambahkan _path url_ ke `urlpatterns` seperti berikut ini:

```python
path('add_amount/<int:item_id>/', add_amount, name='add_amount'),
path('minus_amount/<int:item_id>/', minus_amount, name= 'minus_amount'),
path('delete/<int:item_id>/', delete_item, name='delete_item'),
```

Berikut adalah tampilan kedua akun yang telah saya buat dengan tombol-tombol yang ditambahkan
![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/555831ae-832e-44f0-8ae5-61d0b54b1d77)

![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/e099cc7e-3eec-4b0a-859e-062f3b2b0fac)


![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/555831ae-832e-44f0-8ae5-61d0b54b1d77)

![image](https://github.com/nyasiaay/nyasia_and_co/assets/124874640/e099cc7e-3eec-4b0a-859e-062f3b2b0fac)

# Tugas 5

## 1.Jelaskan manfaat dari setiap element selector dan kapan waktu yang tepat untuk menggunakannya.

CSS selectors digunakan untuk menargetkan elemen HTML yang perlu ditata pada webpage. Ada beragam CSS selectors yang tersedia, memungkinkan akurasi yang sangat baik saat memilih elemen. Berikut manfaat masing-masing pemilih elemen dan kapan waktu yang tepat untuk menggunakannya:

1. **Element Selector**: Selector ini memilih elemen HTML berdasarkan namanya. Cocok digunakan ketika kita ingin menerapkan gaya ke semua elemen atau tag HTML tertentu. Misalnya, jika kita ingin meratakan tengah semua paragraf pada suatu webpage, kita dapat menggunakan kode berikut: `p { text-align: center; } `.

2. **ID Selector**: Selector ini menggunakan atribut ID elemen HTML untuk memilih elemen tertentu. Cocok digunakan ketika kita ingin menerapkan _style_ ke satu elemen berbeda pada webpage. Karena ID harus unik, pilihan ini hanya boleh cocok dengan satu elemen. Misalnya, jika kita ingin menerapkan gaya ke div tertentu dengan ID "myDiv", kita dapat menggunakan kode berikut: `#myDiv { background-color: blue; }`.

3. **Class Selector**: Selector ini memilih elemen dengan atribut _class_ tertentu. Cocok digunakan ketika kita ingin menerapkan _style_ ke banyak elemen dengan  _class_ yang sama.  Karena _class_ dapat digunakan lebih dari satu kali dalam satu halaman, pilihan ini dapat mencocokkan beberapa elemen. Misalnya, jika kita ingin menerapkan style ke semua elemen dengan _class_ "myClass", kita dapat menggunakan kode berikut: `.myClass { font-weight: bold; }`.

4. **Attribute Selector**: Selector ini memilih elemen berdasarkan atribut atau _value_ suatu atribut. Cocok digunakan ketika ingin menerapkan _style_ pada elemen dengan atribut atau _value_ atribut tertentu. Misalnya, jika kita ingin menerapkan _style_ ke semua elemen input dengan tipe "teks", Anda dapat menggunakan kode berikut: `input[type="text"] { border: 1px solid black; }`

5. **Pseudo-class Selector**: Selector ini memilih elemen berdasarkan _state_ tertentu. Cocok digunakan saat kita ingin menerapkan _style_ pada elemen berdasarkan statusnya, misalnya saat elemen tersebut diarahkan atau diklik. Misalnya, jika kita ingin menerapkan _style_ pada tautan saat tautan diarahkan, kita dapat menggunakan kode berikut: `a:hover { color: red; }`

6. **Pseudo-element Selector**: Selector ini memilih dan memberi _style_ pada bagian elemen. Cocok digunakan ketika kita ingin menerapkan _style_ pada bagian tertentu dari suatu elemen, seperti huruf atau baris pertama. Misalnya, jika kita ingin menerapkan gaya pada huruf pertama paragraf, kita dapat menggunakan kode berikut: `p::first-letter { font-size: 200%; }`.

7. **Combinator Selector**: Selector ini memilih elemen berdasarkan pada hubungannya satu sama lain. Cocok digunakan ketika kita ingin menerapkan suatu _style_ pada elemen yang mempunyai hubungan khusus dengan elemen lain, misalnya saat merupakan _child_ dari elemen lain. Misalnya, jika kita ingin menerapkan _style_ ke semua paragraf yang merupakan turunan dari div dengan ID "myDiv", kita dapat menggunakan kode berikut: `#myDiv p { color: green; }`.

Secara keseluruhan, menggunakan selector yang tepat dapat mempermudah menargetkan elemen tertentu dan menerapkan _style_ secara efisien dan rapi.

## 2.Jelaskan HTML5 Tag yang kamu ketahui.

Berikut adalah beberapa tag HTML5 saya ketahui:

1. `<!DOCTYPE>`: Mendefinisikan tipe dokumen dan versi HTML.
2. `<html>`: Mendefinisikan akar dari dokumen HTML.
3. `<head>`: Berisi metadata/informasi untuk dokumen.
4. `<body>`: Mendefinisikan tubuh dokumen.
5. `<h1>` sampai `<h6>`: Mendefinisikan judul HTML.
6. `<p>`: Mendefinisikan paragraf.
7. `<br>`: Mendefinisikan jeda baris tunggal.
8. `<a>`: Mendefinisikan hyperlink.
9. `<img>`: Digunakan untuk menyisipkan gambar.
10. `<table>`, `<tr>`, `<td>`: Digunakan untuk membuat tabel.
11. `<div>`: Mendefinisikan bagian dalam dokumen.
12. `<span>`: Digunakan untuk mengelompokkan elemen inline dalam dokumen.
13. `<form>`: Mendefinisikan formulir HTML untuk input pengguna.
14. `<input>`: Digunakan untuk input pengguna.
15. `<button>`: Membuat tombol yang dapat diklik.

## 3.Jelaskan perbedaan antara margin dan padding.

Dalam _web development_ and _design_, margin dan padding adalah dua konsep penting yang digunakan untuk menciptakan ruang antar elemen. Berikut adalah perbedaan utama antara margin dan padding:

**Margin**
- Menunjukkan ruang luar suatu elemen itu sendiri.
- Mengontrol ruang di luar elemen dan menentukan cara elemen tersebut berinteraksi dengan komponen di sekitarnya atau tepi layar.
- Dapat digunakan untuk memindahkan elemen ke atas atau ke bawah pada _webpage_ serta ke kiri atau ke kanan.
- Sepenuhnya transparan, tanpa warna latar belakang.
- Ukuran margin pada setiap sisi elemen dapat diubah satu per satu.
- Mendorong elemen yang berdekatan untuk menciptakan celah.

**Padding**
- Menunjukkan ruang bagian dalam yang mengelilingi elemen.
- Menentukan bagaimana elemen terlihat dan ditempatkan di dalam _container_.
- Dapat digunakan untuk menciptakan ruang di dalam suatu elemen.
- Nilainya bisa negatif atau bilangan _float_ apapun.
- Dapat mengubah ukuran elemennya sendiri sehingga mempengaruhi seberapa banyak warna isian atau gambar latar belakang yang terlihat di dalam kotak.
- Menggunakan padding untuk membuat celah akan memperbesar ukuran elemen atau memperkecil konten di dalamnya.

Secara singkat, margin adalah ruang di luar suatu elemen, sedangkan padding adalah ruang di dalam suatu elemen. Memahami perbedaan antara margin dan padding sangat penting untuk merancang _layout_ dengan benar.

## 4.Jelaskan perbedaan antara framework CSS Tailwind dan Bootstrap. Kapan sebaiknya kita menggunakan Bootstrap daripada Tailwind, dan sebaliknya?

Bootstrap dan Tailwind adalah dua kerangka CSS populer untuk membuat aplikasi web responsif dan _mobile-first_. Perbedaan utama antara keduanya adalah Bootstrap adalah _framework_ berbasis komponen yang menyediakan komponen yang sudah dibuat sebelumnya dan mencakup utilitas lain untuk _layer display_, spasi, dll. Disisi lain, Tailwind adalah _framework_ yang mengutamakan utilitas yang menawarkan opsi kustomisasi lebih besar dan dilengkapi dengan _widget_ yang telah dirancang sebelumnya yang dapat kita gunakan untuk membangun _webpage_ kita dari awal.

Kapan sebaiknya menggunakan Bootstrap:
- Jika kita memerlukan usaha yang sedikit yang harus diselesaikan dari pihak kita dan menyukai sebagian besar komponen/desain yang disediakan.
- Jika kita menyukai desain Material, ini juga merupakan pilihan yang bagus.
- Jika kita mencari solusi siap pakai dan konsisten yang mencakup sebagian besar skenario desain web.
- Jika kita memprioritaskan _framework_ yang telah dicoba dan diuji dengan pendekatan sederhana.

Kapan sebaiknya menggunakan Tailwind:
- Jika kita ingin merancang antarmuka pengguna kita sendiri.
- Jika kita ingin memiliki lebih banyak opsi kustomisasi.
- Jika kita ingin membuat desain yang lebih fleksibel dan unik.
- Jika kita ingin menghindari kerumitan menulis CSS.

In conclusion, both frameworks are required in different niches. The choice of which framework to use depends on the specific needs of your project. If rapid development, creative control, and customization are paramount, Tailwind CSS shines as a powerful contender. Conversely, if you prioritize a tried-and-tested framework with a straightforward approach, Bootstrap may be the right fit.

Kesimpulannya, kedua _framework_ tersebut diperlukan dalam wadah yang berbeda. Pilihan _framework_ mana yang akan digunakan tergantung pada kebutuhan spesifik proyek yang dibuat. Tailwind CSS unggul sebagai dalam hal _development_ cepat, kebebasan berkreasi, dan kustomisasi Sebaliknya, jika lebih menyukai _framework_ yang telah dicoba dan diuji dengan pendekatan yang jelas, Bootstrap mungkin merupakan pilihan yang tepat.

## 5.Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

**Kustomisasi desain pada _template_ HTML yang telah dibuat pada Tugas 4 dengan menggunakan CSS atau CSS framework (seperti Bootstrap, Tailwind, Bulma) dengan ketentuan sebagai berikut**

**1) Kustomisasi halaman login, register, dan tambah inventori semenarik mungkin.**

**2) Kustomisasi halaman daftar inventori menjadi lebih berwarna maupun menggunakan approach lain seperti menggunakan Card.**