# OOP with Design Patterns

Repository ini berisi implementasi beberapa Design Pattern dalam Object-Oriented Programming (OOP), yaitu Factory Method, Decorator, dan Iterator. Setiap pola desain dijelaskan dengan konsep, diagram kelas, use-case, dan diagram sekuens.

## 1. **Factory Method Design Pattern**
**Factory Method** adalah pola desain kreasional yang digunakan untuk menyediakan antarmuka dalam membuat objek dalam superclass, tetapi memungkinkan subclass untuk mengubah tipe objek yang akan dibuat.

### a. Concept
![Factory Method Concept](https://github.com/user-attachments/assets/1d11d8cf-5810-48d2-946b-521312602d11)
**Factory Method** adalah salah satu pola desain (design pattern) dalam kategori creational pattern yang digunakan untuk membuat objek tanpa menentukan kelas spesifiknya.

Penjelasan Berdasarkan Diagram
  1. Creator (Factory)
     - Kelas abstrak atau antarmuka yang mendeklarasikan metode factoryMethod() yang mengembalikan objek bertipe Product.

  2. ConcreteCreatorA & ConcreteCreatorB
     - Implementasi spesifik dari Creator yang mengoverride factoryMethod(), masing-masing menghasilkan objek ConcreteProductA dan ConcreteProductB.

  3. Product (Abstract Product)
     - Kelas atau antarmuka yang mendefinisikan operasi umum (useProduct()) yang akan digunakan oleh semua produk konkret.

  4. ConcreteProductA & ConcreteProductB
     - Implementasi spesifik dari Product yang merealisasikan metode useProduct() sesuai dengan fungsionalitasnya.

**Factory Method** memungkinkan pembuatan objek dilakukan oleh subclass melalui metode factoryMethod(), sehingga kode utama (Creator) tidak bergantung pada implementasi spesifik produk (ConcreteProductA atau ConcreteProductB). Ini memberikan fleksibilitas dan kemudahan dalam menambahkan produk baru tanpa mengubah kode utama.

### b. Class Diagram
![Factory Method Class Diagram](https://github.com/user-attachments/assets/5a1b6a0d-df23-403a-b304-5c6699bf6b20)

Penjelasan Struktur Class Diagram
  1. Class Vehicle (Superclass/Parent Class)
     - Kelas abstrak yang merepresentasikan kendaraan secara umum dengan atribut seperti brand, manufacture_date, price, mileage, dan features.
     - Memiliki metode display_info() untuk menampilkan informasi kendaraan.

  2. Class Car, Motorcycle, dan Truck (Concrete Products)
     - Mewarisi kelas Vehicle dan memiliki atribut spesifik
     - Masing-masing memiliki metode display_info().

  3. Interface VehicleFactory (Factory Interface)
     - Mendefinisikan metode create_vehicle(), yang akan diimplementasikan oleh subclass untuk membuat objek kendaraan sesuai jenisnya.

  4. Class CarFactory, MotorcycleFactory, dan TruckFactory (Concrete Factories)
     - Masing-masing merupakan implementasi dari VehicleFactory yang merealisasikan metode create_vehicle().
     - CarFactory akan menghasilkan objek Car, MotorcycleFactory menghasilkan objek Motorcycle, dan TruckFactory menghasilkan objek Truck.

  5. Class main (Client Class)
     - Berfungsi sebagai manajer daftar kendaraan (vehicle_list) yang dapat menambah (add_vehicle()), menghapus (remove_vehicle()), dan mendapatkan daftar kendaraan (get_vehicle_list()).
     - Menggunakan VehicleFactory untuk membuat objek kendaraan secara dinamis tanpa mengetahui implementasi spesifiknya.

### c. Use Case
![Factory Method Use Case](https://github.com/user-attachments/assets/8f7f7ce3-ba3d-460f-bea8-641f31f20145)
Aktor (Actor)
  - admin yang dapat melakukan berbagai operasi terhadap kendaraan dalam sistem.

Use Cases (Fitur Aplikasi)
  1. add_vehicle → Pengguna dapat menambahkan kendaraan baru ke dalam daftar, yang dibuat melalui Factory Method (CarFactory, MotorcycleFactory, atau TruckFactory).
  2. remove_vehicle → Pengguna dapat menghapus kendaraan dari daftar yang telah tersedia.
  3. view_vehicle → Pengguna dapat melihat daftar kendaraan yang telah ditambahkan ke dalam sistem.
  4. selesai → Menandakan bahwa pengguna menyelesaikan interaksi dengan sistem.

### d. Sequence Diagram
![image](https://github.com/user-attachments/assets/e00cc6d5-8029-481b-bdc0-b7ff4f14d7f5)
  1. Menambahkan Kendaraan
     - User memilih "Tambah Kendaraan"
     - Main memanggil VehicleFactory untuk menentukan factory yang sesuai berdasarkan jenis kendaraan (Car, Motorcycle, Truck).
     - Factory yang sesuai (CarFactory, MotorcycleFactory, atau TruckFactory) membuat objek kendaraan dan mengembalikannya.
     - Kendaraan yang dibuat ditambahkan ke dalam vehicle_list.
       
  2. Menghapus Kendaraan
     - User memilih "Hapus Kendaraan"
     - Main mencari kendaraan dalam vehicle_list.
     - Jika ditemukan, kendaraan dihapus dari daftar.
     - Sistem mengonfirmasi bahwa kendaraan telah dihapus.
      
  3. Menampilkan Daftar Kendaraan
     - User memilih "Tampilkan Kendaraan"
     - Main mengambil semua kendaraan dari vehicle_list.
     - Memanggil metode display_info() pada setiap kendaraan untuk mendapatkan informasi.
     - Sistem mengembalikan informasi kendaraan kepada pengguna.

---

## 2. **Decorator Design Pattern**
**Decorator** adalah pola desain struktural yang memungkinkan penambahan fitur ke objek secara dinamis tanpa mengubah strukturnya.

### a. Concept
![Decorator Concept](https://github.com/user-attachments/assets/54a91e79-9ab1-4d0b-86fc-2d97b8c9f0f2)
**Decorator Design Pattern** adalah pola desain struktural yang memungkinkan kita untuk menambahkan perilaku baru ke objek secara dinamis tanpa mengubah kode dari kelas aslinya. Pola ini sering digunakan sebagai alternatif yang fleksibel terhadap subclassing.

Penjelasan Berdasarkan Diagram
  1. Component (Interface atau Abstract Class)
     - Merupakan antarmuka dasar yang mendefinisikan operasi yang akan diterapkan pada objek.
     - Dalam diagram, ini direpresentasikan oleh kelas Component dengan metode operation().

  2. ConcreteComponent (Implementasi Komponen Dasar)
     - Kelas ini merupakan implementasi konkret dari Component yang memiliki operasi dasar.
     - ConcreteComponent langsung mengimplementasikan operation().

  3. Decorator (Kelas Abstrak Dekorator)
     - Kelas ini mewarisi dari Component dan memiliki referensi ke objek Component, memungkinkan dekorasi secara rekursif.
     - Metode operation() di sini bertindak sebagai wrapper yang dapat dimodifikasi oleh subclass-nya.

  4. ConcreteDecoratorA & ConcreteDecoratorB (Dekorator Konkret)
     - Kelas-kelas ini memperluas Decorator dan menambahkan perilaku tambahan sebelum atau sesudah memanggil operation() dari objek yang didekorasi.

Dengan pola ini, kita bisa menambahkan fitur ke objek tanpa mengubah kode aslinya, menjadikannya lebih fleksibel dan modular.

### b. Class Diagram
![Decorator Class Diagram](https://github.com/user-attachments/assets/525f4f87-ffc9-4251-b2bd-d6e41a83bc3a)
Class diagram di atas menunjukkan penerapan Decorator Design Pattern dalam konteks aplikasi yang menangani berbagai jenis kendaraan (Vehicle).

Penjelasan Struktur Class Diagram
  1. Vehicle (Interface/Abstract Class)
     - Merupakan antarmuka dasar yang mendefinisikan atribut umum kendaraan seperti brand, manufacture_date, price, mileage, dan features.
     - Memiliki metode display_info() untuk menampilkan informasi kendaraan.

  2. VehicleDecorator (Abstract Decorator Class)
     - Bertindak sebagai kelas dasar untuk semua dekorator.
     - Memiliki referensi _decorated_vehicle ke objek Vehicle yang akan dihias.
     - Menyediakan metode display_info(), yang dapat diperluas oleh dekorator konkret.

  3. Concrete Decorators (CarDecorator, MotorcycleDecorator, TruckDecorator)
     - CarDecorator: Menambahkan atribut num_seats untuk menyimpan jumlah kursi kendaraan.
     - MotorcycleDecorator: Menambahkan atribut engine_capacity untuk kapasitas mesin sepeda motor.
     - TruckDecorator: Menambahkan atribut cargo_capacity untuk kapasitas muatan truk.
     - Masing-masing dekorator memperluas display_info() dengan menambahkan informasi spesifik dari jenis kendaraan yang dihias.

Pola Decorator dalam diagram ini memberikan fleksibilitas dalam menambah atau mengubah perilaku objek Vehicle tanpa perlu membuat subclass baru untuk setiap jenis kendaraan.

### c. Use Case
![Decorator Use Case](https://github.com/user-attachments/assets/8f7f7ce3-ba3d-460f-bea8-641f31f20145)
Aktor (Actor)
  - admin yang dapat melakukan berbagai operasi terhadap kendaraan dalam sistem.

Use Cases (Fitur Aplikasi)
  1. add_vehicle → Pengguna dapat menambahkan kendaraan baru ke dalam daftar, yang dibuat melalui Factory Method (CarFactory, MotorcycleFactory, atau TruckFactory).
  2. remove_vehicle → Pengguna dapat menghapus kendaraan dari daftar yang telah tersedia.
  3. view_vehicle → Pengguna dapat melihat daftar kendaraan yang telah ditambahkan ke dalam sistem.
  4. selesai → Menandakan bahwa pengguna menyelesaikan interaksi dengan sistem.

### d. Sequence Diagram
![Decorator Sequence Diagram](https://github.com/user-attachments/assets/3fc03908-d1ea-45c7-8a87-cd08d19d50ff)
Diagram di atas menunjukkan alur eksekusi aplikasi yang menggunakan Decorator Design Pattern untuk mengelola berbagai jenis kendaraan (Car, Motorcycle, Truck). Berikut adalah proses utama yang digambarkan:

  1. Menambah Kendaraan
     - User memilih jenis kendaraan yang ingin ditambahkan.
     - Main Program membuat objek Vehicle dasar.
     - Berdasarkan jenis kendaraan, program membungkus objek Vehicle dengan decorator yang sesuai:
       - CarDecorator → Menambahkan jumlah kursi
       - MotorcycleDecorator → Menambahkan kapasitas mesin
       - TruckDecorator → Menambahkan kapasitas muatan
     - Setiap decorator memanggil display_info() dari VehicleDecorator, yang pertama-tama menampilkan informasi dasar kendaraan sebelum menambahkan informasi spesifik decorator.
     - Kendaraan yang telah dihias ditambahkan ke dalam Vehicle List, dan aplikasi menampilkan konfirmasi keberhasilan.
       
  2. Melihat Daftar Kendaraan
     - User memilih opsi "Lihat Kendaraan".
     - Main Program mengambil daftar kendaraan yang telah ditambahkan.
     - Informasi kendaraan yang sudah dihias dengan decorator ditampilkan.
       
  3. Menghapus Kendaraan
     - User memilih opsi "Hapus Kendaraan" dan memasukkan merek kendaraan yang ingin dihapus.
     - Main Program mencari kendaraan berdasarkan merek dalam Vehicle List.
     - Jika kendaraan ditemukan, ia dihapus dari daftar.
     - Aplikasi menampilkan pesan bahwa kendaraan berhasil dihapus.


---

## 3. **Iterator Design Pattern**
**Iterator** adalah pola desain perilaku yang digunakan untuk menyediakan cara untuk mengakses elemen-elemen dalam koleksi secara berurutan tanpa mengekspos detail implementasinya.

### a. Concept
![image](https://github.com/user-attachments/assets/721beca4-bbb7-4eb3-8f8c-5302910adb1b)
**Iterator Design Pattern** adalah pola desain perilaku yang digunakan untuk memberikan cara terstruktur dalam mengakses elemen-elemen dalam suatu koleksi (collection) secara berurutan tanpa mengekspos representasi internalnya.

Berdasarkan diagram di atas, berikut adalah konsep dasar dari Iterator Design Pattern:

  1. Interface Iterator
     - Merupakan antarmuka yang mendefinisikan operasi dasar iterasi, yaitu:
       - getNext(): Mengembalikan elemen berikutnya dalam koleksi.
       - hasMore() : bool: Mengembalikan nilai boolean yang menunjukkan apakah masih ada elemen yang tersisa dalam koleksi.
         
  2. ConcreteIterator
     - Implementasi konkret dari Iterator.
     - Memiliki atribut:
       - collection: ConcreteCollection: Menyimpan referensi ke koleksi yang sedang diiterasi.
       - iterationState: Menyimpan posisi iterasi saat ini.
     - Memiliki metode:
       - Konstruktor untuk menginisialisasi iterator dengan koleksi.
       - Implementasi metode getNext() untuk mengambil elemen berikutnya.
       - Implementasi metode hasMore() untuk mengecek apakah masih ada elemen yang dapat diakses.
         
  3. Interface IterableCollection
     - Menyediakan antarmuka bagi koleksi agar bisa menghasilkan iterator.
     - Memiliki metode:
       - createIterator(): Iterator: Metode untuk membuat dan mengembalikan iterator.
       - 
  4. ConcreteCollection
     - Implementasi konkret dari IterableCollection.
     - Memiliki metode createIterator() yang mengembalikan objek ConcreteIterator untuk koleksi ini.

**Iterator Design Pattern** memungkinkan iterasi objek koleksi tanpa harus mengetahui struktur internalnya. Dalam diagram ini, ConcreteCollection berperan sebagai koleksi data yang dapat diiterasi, sementara ConcreteIterator menangani logika iterasi dengan metode hasNext() dan next().

### b. Class Diagram
![classiterator](https://github.com/user-attachments/assets/be4f902e-9853-4011-b630-41a7891f1592)

  1. Iterator Interface
     - Merupakan interface standar yang digunakan dalam desain pola Iterator.
     - Memiliki metode __next__(), yang mengembalikan objek Vehicle.
     - Interface ini digunakan untuk membuat objek yang bisa diiterasi.
  2. Iterable Interface
     - Merupakan interface standar yang harus diimplementasikan oleh kelas yang ingin bisa diiterasi.
     - Memiliki metode __iter__(), yang mengembalikan objek Iterator.
  3. VehicleIterator (ConcreteIterator)
     - Kelas ini mengimplementasikan Iterator dan bertanggung jawab untuk iterasi melalui daftar kendaraan.
  4. VehicleCollection (ConcreteIterable)
     - Kelas ini bertindak sebagai koleksi kendaraan yang dapat diiterasi menggunakan VehicleIterator.

### c. Use Case
![Iterator Use Case](https://github.com/user-attachments/assets/8f7f7ce3-ba3d-460f-bea8-641f31f20145)

Aktor (Actor)
  - admin yang dapat melakukan berbagai operasi terhadap kendaraan dalam sistem.

Use Cases (Fitur Aplikasi)
  1. add_vehicle → Pengguna dapat menambahkan kendaraan baru ke dalam daftar, yang dibuat melalui Factory Method (CarFactory, MotorcycleFactory, atau TruckFactory).
  2. remove_vehicle → Pengguna dapat menghapus kendaraan dari daftar yang telah tersedia.
  3. view_vehicle → Pengguna dapat melihat daftar kendaraan yang telah ditambahkan ke dalam sistem.
  4. selesai → Menandakan bahwa pengguna menyelesaikan interaksi dengan sistem.

### d. Sequence Diagram
![SequenceIterator](https://github.com/user-attachments/assets/a6c71b66-46ce-4f90-b3c1-4b6fd46fb842)

Sequence diagram ini menggambarkan bagaimana pengguna berinteraksi dengan sistem untuk menambah, menghapus, dan menampilkan kendaraan menggunakan Iterator Design Pattern.

  1. Tambah Kendaraan
     Alur proses:
       - Pengguna memanggil add_vehicle(vehicle) pada VehicleCollection.
       - VehicleCollection menginisialisasi objek kendaraan baru.
       - Kendaraan ditambahkan ke dalam daftar kendaraan.
       - Sistem mengonfirmasi bahwa kendaraan berhasil ditambahkan.
         
  2. Hapus Kendaraan
     Alur proses:
       - Pengguna memanggil remove_vehicle(brand).
       - VehicleCollection mencari kendaraan berdasarkan merek dalam daftar.
       - Jika ditemukan, kendaraan dihapus dari daftar.
       - Sistem mengonfirmasi bahwa kendaraan berhasil dihapus.
         
  3. Tampilkan Kendaraan (Menggunakan Iterator)
     Alur proses:
       - Pengguna memanggil get_vehicle_list() untuk mendapatkan daftar kendaraan.
       - VehicleCollection mengembalikan iterator melalui iter().
       - Pengguna memanggil next() untuk mendapatkan kendaraan satu per satu.
       - VehicleIterator mengambil kendaraan berikutnya dalam daftar.
       - Vehicle menampilkan informasi kendaraan (display_info()).
       - Sistem mengembalikan daftar kendaraan kepada pengguna.

Dengan pendekatan ini, pengguna dapat menambahkan, menghapus, dan mengakses kendaraan dengan cara yang lebih terstruktur dan fleksibel.

---

## 4. **CLI APPS OOP PYTHON USING DESIGN PATTERN**

Secara keseluruhan, CLI yang dihasilkan oleh ketiga jenis design pattern tidak ada yang berubah. Hal yang berubah adalah proses yang ada di dalam aplikasi tersebut dan tidak terdeteksi oleh pengguna

![image](https://github.com/user-attachments/assets/486ae520-2ef6-4a8f-b36b-5c2df4c8360f)

![image](https://github.com/user-attachments/assets/2da1c0ec-9277-413f-8fa9-8d0de12ccfd3)


---

Dengan adanya dokumen ini, diharapkan pembaca dapat memahami implementasi dari masing-masing design pattern dalam OOP serta bagaimana pola-pola tersebut dapat digunakan dalam berbagai kasus nyata.







