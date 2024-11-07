# Next Js - Route (Adelfia)

## Apa itu Routing pada Next Js (Adelfia)

## App router & Page route (Alip)

Next.js menggunakan perutean file-system, yang artinya route dalam aplikasi yang kita ditentukan oleh cara kita sendiri dalam menyusun struktur file. Oleh karena itu, mengharuskan kita untuk membuat keputusan mengenai Route dalam  memulai suatu proyek menggunakan Next.js.

Mari kita berkenalan lebih dekat mengenai Route dalam Next.js, kelebihan dan kekurangan, dan kesesuaian dengan aplikasi yang akan kita kembangkan.
### Pages Router
Pages routing di Next.js sangatlah mudah, efektif, dan efisien. Tidak perlu berinteraksi secara langsung dengan router secara langsung  untuk membuat halaman, karena Next.js menggunakan konvensi yang memungkinkan route terbentuk otomatis hanya dengan membuat file baru, sehingga prosesnya sangat sederhana. 

Kita cukup menambahkan komponen react dalam folder yang bernama `/pages`. Next.js secara otomatis menganggap setiap file dalam direktori ini sebagai route. Nama file tersebut akan menjadi nama atau pola routenya, dan komponen yang diekspor adalah halaman yang ditampilkan.

#### Strukturnya : 
```
└── pages
    ├── about.jsx
    ├── index.jsx
    └── team.jsx
```

#### Implementasi : 
1. Pertama kita membuat route index dengan cara membuat sebuah file dengan nama : `pages/index.jsx`
2. Buat komponen react dan jangan lupa untuk mengekspornya
    ```jsx
    const index = () => {
        return <div>Hello World!</div>;
    };

    export default index;
    ```
3. Jalankan server local kita
    ```bash
        npm run dev
    ```
4. Sekarang kita dapat menavigasikan browser ke route index aplikasi kita, dan melihat konten yang kita buat pada file `index.jsx` tadi yakni **Hello World!**.
5. Selamat kita telah membuat route sederhana pada aplikasi kita.
#### Fitur pada Pages Routing
1. **Route Otomatis** : yakni dengan menambahkan file `.jsx` atau `.tsx` ke direktori `pages` secara otomatis membuat route.
2. **Komponen Dokumen dan Aplikasi Khusus** : memungkinkan kita untuk menyesuaikan struktur dan tata letak seluruh dokumen dengan fleksibel.
3. **Optimasi SEO** : Dengan komponen `next/head`, pengoptimalan SEO menjadi sangat mudah.

#### Kelebihan
1. **Efisiensi** : menyederhanakan proses pengembangan sehingga lebih hemat waktu.
2. **SEO Friendly** : Dengan rendering sisi server, konten lebih optimal dan siap diakses oleh pengguna maupun mesin pencari.

#### Kekurangan
1. **Route yang Kompleks**: Mungkin kurang cocok untuk kebutuhan route yang lebih kompleks.
2. **Konvensi Penamaan**: Struktur route bergantung pada nama file dan folder, sehingga penamaan harus tepat.
### App Router
Next.js versi 13 memperkenalkan app router yang bekerja dengan direktori `app/` pada aplikasi yang kita buat. App router adalah jawaban dari Next.js untuk kebutuhan Route tingkat lanjut, yang memungkinkan pengaturan yang lebih kompleks.

#### Strukturnya  
```
└── app
    ├── profile
    │   └── page.jsx
    ├── globals.css
    ├── layout.jsx
    ├── login
    │   └── page.jsx
    ├── page.jsx
```



## Tipe - tipe route pada Next Js (Gayuh)

## Route Lanjutan (Dzawil)

## Fitur pada route di Next Js (Surya)

## Penggunaan Route Next Js (Surya)

## Kesimpulan (Adelfia)