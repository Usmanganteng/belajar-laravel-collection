<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

>
---
<b>requirement/persyaratan</b>
---
> #### Php versi 8
>> - Cara menginstal php dalam bahasa indonesia : https://youtu.be/Uw3ZGIMvIdA?si=mBVZ-lBnoCilASzo
>> - Cara menginstal php dalam bahasa inggris : https://youtu.be/MPRLUd8Pmyo?si=FqN54nVr4duH4Keg
---
> #### Laravel versi 10.0.3
>> - cara menginstal laravel yang versi yang sama 
```
   Composer Create-project laravel\laravel=v10.0.3 nama-folder
```
>> - Cara tahu laravel sekarang versi berapa : https://packagist.org/packages/laravel/laravel
---
<b>materi</b>
---
> #### Collection
> - Laravel Collection, sebuah fitur penting dalam ekosistem Laravel, memberikan kemampuan yang sangat diperlukan untuk memanipulasi data dengan kejelasan dan efisiensi. Sebagai kelas yang memperluas fungsionalitas array PHP standar, Collection menawarkan sejumlah metode bawaan yang memungkinkan pengembang untuk melakukan berbagai operasi, mulai dari filtering hingga sorting, dengan gaya sintaks yang ringkas dan mudah dipahami. Penggunaan Collection tidak hanya meningkatkan kejelasan kode, tetapi juga mempercepat proses pengembangan dengan meminimalkan jumlah kode yang harus ditulis untuk mencapai hasil yang sama.
> 
> - Selain itu, fitur ini memungkinkan pengolahan data dari berbagai sumber dengan cara yang fleksibel dan efektif. Hal ini terutama bermanfaat dalam skenario pengembangan yang kompleks, di mana data dari berbagai sumber seperti database, API, atau input pengguna perlu digabungkan, difilter, atau diurutkan. Dengan Laravel Collection, pengembang dapat mengimplementasikan transformasi data yang diperlukan tanpa harus terjebak dalam penulisan kode yang rumit, menjadikannya alat yang tak ternilai dalam arsenar pengembangan aplikasi Laravel.
---
> #### For Each
> - `forEach` dalam Laravel Collection adalah metode untuk melakukan iterasi pada setiap item dalam koleksi data tanpa mengubah koleksi itu sendiri. Ini memungkinkan Anda untuk menjalankan fungsi pada setiap elemen dalam koleksi dengan gaya sintaks yang bersih dan mudah dibaca.
> - berikut adalah contoh sintaks untuk For Each :
> ```
> $collection = collect([1, 2, 3, 4, 5]);
>
> $collection->forEach(function ($item, $key) {
>    echo "Key: $key, Value: $item\n";
> });
> ```
---
> #### Manipulasi Collection
> - Manipulasi Collection dalam Laravel Collection adalah proses menggunakan metode bawaan seperti `filter`, `map`, `sortBy`, dan lainnya untuk mengubah, menyaring, atau mengurutkan data dalam koleksi dengan cara yang jelas dan efisien. Ini memungkinkan pengembang untuk dengan cepat dan mudah melakukan transformasi data sesuai kebutuhan aplikasi tanpa harus menulis kode yang rumit.
> - berikut adalah contoh sintaks dari fillter, map, dan soryBy yang di gunakan bersama:
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
> 
> // Filter data yang lebih besar dari 2
> $result = $collection->filter(function ($value, $key) {
>     return $value > 2;
> });
> // Hasilnya: [3, 4, 5]
> $result->all();
>
> // Menggandakan setiap nilai dalam koleksi
> $result = $collection->map(function ($item, $key) {
>     return $item * 2;
> });
> // Hasilnya: [2, 4, 6, 8, 10]
> $result->all();
> 
> // Mengurutkan koleksi secara ascending
> $result = $collection->sortBy(function ($value, $key) {
>     return $value;
> });
> // Hasilnya: [1, 2, 3, 4, 5]
> $result->all();
> ```
---
> #### Mapping
> - Mapping dalam Laravel Collection adalah proses mengubah setiap elemen dalam koleksi dengan menggunakan fungsi tertentu dan mengembalikan koleksi baru yang berisi hasil transformasi tersebut. Dengan `map()`, Anda dapat menerapkan fungsi pada setiap item dalam koleksi dan menghasilkan koleksi baru dengan nilai-nilai yang telah dimodifikasi sesuai dengan fungsi tersebut.
> - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
> 
> // Menggandakan setiap nilai dalam koleksi
> $result = $collection->map(function ($item, $key) {
>     return $item * 2;
> });
> 
> // Hasilnya: [2, 4, 6, 8, 10]
> $result->all();
> ```
---
> #### Zipping
> - Zipping dalam Laravel Collection adalah proses menggabungkan dua koleksi secara sejajar, membentuk pasangan nilai dari setiap koleksi untuk membuat koleksi baru. Ini dilakukan dengan metode `zip()`.
> - berikut adalah contoh sintaks dari zipping/zip :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat dua koleksi data
> $collection1 = collect(['a', 'b', 'c']);
> $collection2 = collect([1, 2, 3]);
>
> // Meng-zip kedua koleksi
> $zipped = $collection1->zip($collection2);
> 
> // Hasilnya: [['a', 1], ['b', 2], ['c', 3]]
> $zipped->all();
>```
---
> #### Flattening
> - Flattening dalam Laravel Collection adalah proses mengonversi koleksi yang bersarang menjadi satu level, sehingga semua elemen dari koleksi tersebut digabungkan ke dalam satu array tunggal. Misalnya, jika Anda memiliki koleksi yang berisi beberapa array dalamnya, menggunakan metode `flatten()` akan menghasilkan koleksi baru dengan semua elemen yang tersusun secara linear, tanpa ada array bersarang di dalamnya.
> - berikut adalah contoh sintaks dari flattening :
> ```
> use Illuminate\Support\Collection;
> 
> // Membuat koleksi data yang bersarang
> $nestedCollection = collect([
>    'a',
>    'b',
>    ['c', 'd'],
>    ['e', ['f', 'g']],
>]);
>
>// Meratakan (flattening) koleksi yang bersarang
>$flattened = $nestedCollection->flatten();
>
>// Hasilnya: ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>$flattened->all();
> ```
---
> #### String Representation
> - String Representation dalam Laravel Collection adalah cara di mana koleksi ditampilkan sebagai string. Biasanya, elemen-elemen koleksi dipisahkan oleh koma dan diapit oleh tanda kurung kotak. Misalnya, koleksi `[1, 2, 3]` akan direpresentasikan sebagai `"[1, 2, 3]"`. Ini berguna untuk debugging dan pencetakan.
---
> #### Filtering
> - Filtering dalam Laravel Collection adalah proses memilih elemen-elemen tertentu dari koleksi berdasarkan kriteria yang ditentukan. Misalnya, Anda dapat menyaring elemen-elemen yang memenuhi kondisi tertentu, seperti elemen-elemen dengan nilai lebih besar dari suatu angka.
> - berikut adalah contoh sintaks dari filtering :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
> 
> // Menyaring elemen yang lebih besar dari 2
> $result = $collection->filter(function ($value, $key) {
>    return $value > 2;
> });
>
> // Hasilnya: [3, 4, 5]
> $result->all();
> ```
---
> #### Partitioning
> - Partitioning dalam Laravel Collection adalah proses membagi koleksi menjadi dua kelompok berdasarkan kriteria tertentu. Misalnya, Anda dapat membagi koleksi menjadi kelompok elemen yang memenuhi kondisi tertentu dan kelompok lainnya yang tidak memenuhi kondisi tersebut.
> - berikut adalah contoh sintaks dari :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
> 
> // Membagi koleksi menjadi dua berdasarkan kondisi elemen lebih besar dari 2
> list($greaterThanTwo, $lessThanOrEqualTwo) = $collection->partition(function ($value, $key) {
>    return $value > 2;
> });
> 
> // Hasilnya: [3, 4, 5] dan [1, 2]
> $greaterThanTwo->all();
>$lessThanOrEqualTwo->all();
> ```
---
> #### Testing
> - Testing dalam pengembangan perangkat lunak adalah proses untuk memverifikasi bahwa kode berfungsi seperti yang diharapkan. Dalam Laravel, Anda dapat menggunakan PHPUnit untuk menguji berbagai komponen aplikasi, termasuk koleksi Laravel, untuk memastikan bahwa aplikasi Anda berjalan dengan benar dan stabil.
---
> #### Grouping
> - Grouping dalam Laravel Collection adalah proses mengelompokkan elemen-elemen koleksi berdasarkan kriteria tertentu, seperti properti atau hasil dari sebuah closure. Misalnya, Anda dapat mengelompokkan data berdasarkan umur, nama, atau kriteria lainnya.
>  - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([
>    ['name' => 'lUlu', 'age' => 30],
>    ['name' => 'ilham', 'age' => 25],
>    ['name' => 'aldizar', 'age' => 30],
> ]);
>
> // Mengelompokkan koleksi berdasarkan umur
> $grouped = $collection->groupBy('age');
>
> // Hasilnya: [30 => [['name' => 'lUlu', 'age' => 30], ['name' => 'aldizar', 'age' => 30]], 25 => [['name' => 'ilham', 'age' => 25]]]
> $grouped->toArray();
> ```
---
> #### Retrieve
> - "Retrieve" dalam Laravel Collection merujuk pada proses pengambilan data dari koleksi. Ini dapat dilakukan dengan menggunakan metode seperti `get()`, `first()`, `last()`, `find()`, dan lainnya, sesuai kebutuhan.
---
> #### Random
> - Dalam Laravel Collection, "Random" merujuk pada metode yang memungkinkan Anda untuk memilih satu atau beberapa elemen secara acak dari koleksi tanpa perlu menulis kode tambahan. Ini berguna saat Anda perlu mendapatkan elemen acak untuk keperluan seperti pengujian atau menampilkan konten acak kepada pengguna.
> - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
>
> // Memilih satu elemen secara acak dari koleksi
> $randomElement = $collection->random();
>```
---
> #### Checking Existence
> - "Checking Existence" dalam Laravel Collection adalah proses memeriksa apakah elemen atau kriteria tertentu ada dalam koleksi. Ini dilakukan dengan menggunakan metode seperti `contains()`, `has()`, atau `containsStrict()`, tergantung pada jenis pemeriksaan yang Anda perlukan. Metode-metode ini memudahkan Anda untuk memeriksa keberadaan elemen dalam koleksi tanpa menulis kode yang rumit.
---
> #### Ordering
> - "Ordering" dalam Laravel Collection adalah proses mengurutkan elemen-elemen koleksi berdasarkan kriteria tertentu, seperti nilai atau kunci. Ini dilakukan dengan menggunakan metode seperti sortBy(), sortByDesc(), atau sort(), yang memungkinkan Anda untuk mengatur urutan elemen dalam koleksi sesuai kebutuhan Anda.
> - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([
>    ['name' => 'lulu', 'age' => 30],
>    ['name' => 'ilham', 'age' => 25],
>    ['name' => 'aldizar', 'age' => 35],
> ]);
>
> // Mengurutkan koleksi berdasarkan umur secara menaik
> $sortedByAge = $collection->sortBy('age');
>
> // Mengurutkan koleksi berdasarkan umur secara menurun
> $sortedByAgeDesc = $collection->sortByDesc('age');
>
> // Mengurutkan koleksi secara default (ascending)
> $sorted = $collection->sort();
>
> // Menampilkan hasil
> $sortedByAge->all();
> $sortedByAgeDesc->all();
> $sorted->all();
> ```
---
> #### Aggregate
> - Aggregation dalam Laravel Collection adalah proses pengumpulan atau perhitungan nilai-nilai dalam koleksi. Ini dapat dilakukan dengan metode-metode seperti `sum()`, `avg()`, `max()`, `min()`, dan `count()`, yang memungkinkan Anda untuk melakukan operasi agregasi dengan mudah.
> - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
>
> // Menjumlahkan semua nilai dalam koleksi
> $sum = $collection->sum();
> 
> // Menghitung rata-rata nilai dalam koleksi
> $average = $collection->avg();
> 
> // Mencari nilai maksimum dalam koleksi
> $maxValue = $collection->max();
> 
> // Mencari nilai minimum dalam koleksi
> $minValue = $collection->min();
> 
> // Menghitung jumlah elemen dalam koleksi
> $totalCount = $collection->count();
>```
---
> #### Reduce
> - Metode `reduce()` dalam Laravel Collection digunakan untuk mereduksi koleksi menjadi satu nilai tunggal berdasarkan operasi yang ditentukan dalam fungsi callback. Dengan `reduce()`, Anda dapat melakukan operasi seperti menjumlahkan semua nilai atau menggabungkan string dalam koleksi.
> - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\Collection;
>
> // Membuat koleksi data
> $collection = collect([1, 2, 3, 4, 5]);
> 
> // Menjumlahkan semua nilai dalam koleksi
> $total = $collection->reduce(function ($carry, $item) {
>     return $carry + $item;
> }, 0);
> 
> // Hasilnya: 15
>```
---
> #### Lazy Collection
> - Lazy Collection dalam Laravel adalah koleksi yang dievaluasi hanya saat dibutuhkan, tidak sekaligus. Ini membantu meningkatkan kinerja dengan menghindari evaluasi seluruh koleksi pada satu waktu, cocok untuk data besar atau operasi yang memakan waktu.
> - berikut adalah contoh sintaks :
> ```
> use Illuminate\Support\LazyCollection;
>
> // Membuat Lazy Collection dari file besar
> $collection = LazyCollection::make(function () {
>    $handle = fopen('large_file.csv', 'r');
>
>    while (($line = fgets($handle)) !== false) {
>        yield $line;
>    }
>
>    fclose($handle);
> });
> 
> // Membatasi jumlah baris yang dievaluasi
> $limitedCollection = $collection->take(100);
> 
> // Melakukan operasi map pada elemen-elemen yang dievaluasi secara malas
> $modifiedCollection = $limitedCollection->map(function ($line) {
>     return strtoupper($line);
> });
>
> // Memproses elemen-elemen secara perantara
> $modifiedCollection->each(function ($line) {
>    // Lakukan sesuatu dengan setiap baris
> });
>```
---
<b>TERIMA KASIH</b>
