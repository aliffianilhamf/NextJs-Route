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
## Advanced Routing
Dalam pengembangan web dengan Next.js, konsep *catch all routes* dan *optional catch all routes* adalah cara untuk menangani rute dinamis (dynamic routing) dengan lebih fleksibel, terutama ketika kita tidak tahu secara pasti berapa banyak segmen URL yang akan ada. Fitur ini sangat berguna dalam kasus aplikasi yang membutuhkan fleksibilitas dalam menangkap berbagai pola URL tanpa harus mendefinisikan masing-masing satu per satu.

Mari kita bahas satu per satu tentang *catch all routes* dan *optional catch all routes* beserta contohnya.

### 1. Catch All Routes

*Catch all routes* menangkap semua segmen URL setelah rute tertentu, terlepas dari jumlah segmen tersebut. Untuk membuat *catch all route*, gunakan tanda `[...slug]` pada nama file di dalam folder `pages`. 

#### Contoh Struktur Folder

Misalnya, kita memiliki struktur folder berikut di dalam folder `pages`:

```
pages/
└── blog/
    └── [...slug].jsx
```

Dengan struktur ini, Next.js akan menangkap semua URL yang dimulai dengan `/blog/` diikuti dengan segmen apa pun. Misalnya:

- `/blog/one`
- `/blog/one/two`
- `/blog/one/two/three`

Semua URL tersebut akan diarahkan ke file `[...slug].jsx`.

#### Contoh Implementasi

Di dalam file `[...slug].jsx`, kita bisa mengakses parameter `slug` sebagai array, di mana setiap elemen array adalah segmen dari URL tersebut. Berikut adalah contoh kode untuk menangkap parameter `slug`:

```javascript
import { useRouter } from 'next/router';

const BlogPost = () => {
  const router = useRouter();
  const { slug } = router.query;

  return (
    <div>
      <h1>Blog Post</h1>
      <p>Slug: {slug ? slug.join('/') : 'No Slug'}</p>
    </div>
  );
};

export default BlogPost;
```

Jika URL yang diakses adalah `/blog/one/two`, maka output `slug` akan berupa `Slug: one/two`. Tetapi jika URL yang diakses adalah `/blog`, maka output `slug` berupa `Slug: No Slug`.

### 2. Optional Catch All Routes

*Optional catch all routes* mirip dengan *catch all routes*, tetapi lebih fleksibel karena parameter ini bersifat opsional. Kita dapat membuatnya dengan menambahkan tanda `[[...slug?]]`, yang berarti bahwa rute tersebut dapat dipanggil dengan atau tanpa parameter tambahan.

#### Contoh Struktur Folder

Misalnya, jika kita ingin menangani URL di bawah `/docs/` baik dengan atau tanpa segmen tambahan, kita bisa membuat file seperti ini:

```
pages/
└── docs/
    └── [[...slug]].jsx
```

Dalam hal ini, URL yang ditangani bisa berupa:

- `/docs` (tanpa segmen tambahan)
- `/docs/intro`
- `/docs/intro/getting-started`

Semua URL tersebut akan diarahkan ke file `[[...slug]].jsx`.

#### Contoh Implementasi

Di dalam file `[[...slug]].jsx`, parameter `slug` bisa berupa `undefined` (jika tidak ada segmen tambahan) atau array (jika ada segmen tambahan). Contoh implementasinya:

```javascript
import { useRouter } from 'next/router';

const Docs = () => {
  const router = useRouter();
  const { slug } = router.query;

  return (
    <div>
      <h1>Documentation</h1>
      <p>Slug: {slug ? slug.join('/') : 'Home Page'}</p>
    </div>
  );
};

export default Docs;
```

Jika URL yang diakses adalah `/docs` (Tidak ada segment tambahan), maka `slug` akan tampil `Home Page`. Jika URL yang diakses adalah `/docs/intro/getting-started`, maka `slug` akan berupa `["intro", "getting-started"]`.

### Kapan Menggunakan Catch All Routes dan Optional Catch All Routes?

- **Catch All Routes (`[...slug]`)** cocok ketika kita ingin menangkap semua segmen yang muncul setelah rute dasar, tetapi selalu mengharapkan adanya parameter tambahan.
- **Optional Catch All Routes (`[[...slug]]`)** cocok ketika kita ingin menangani baik URL dengan maupun tanpa parameter tambahan.

Dengan cara ini, Kita dapat membuat rute yang fleksibel dan dinamis tanpa harus menentukan setiap rute secara eksplisit di Next.js.

### Navigasi Antar Halaman

Di Next.js, kita dapat melakukan navigasi antar halaman dengan menggunakan komponen `Link` dari modul `next/link`. Komponen ini memungkinkan navigasi sisi-klien (client-side) antara halaman-halaman di aplikasi Next.js. Penggunaan komponen `Link` memberikan pengalaman lebih lancar dan cepat bagi pengguna dibandingkan dengan metode navigasi tradisional yang memuat ulang seluruh halaman.

**Contoh Penggunaan Komponen `Link`:**

```javascript
import Link from 'next/link';

function HomePage() {
  return (
    <div>
      <h1>Halaman Utama</h1>
      <Link href="/about">
        <a>Ke Halaman Tentang Kami</a>
      </Link>
    </div>
  );
}
```

Pada contoh di atas, pengguna akan diarahkan ke halaman `/about` tanpa memuat ulang seluruh halaman saat mengklik tautan.

### Hook `useRouter`

`useRouter` adalah hook yang disediakan oleh Next.js untuk mengakses objek router. Hook ini memungkinkan kita mendapatkan informasi tentang rute saat ini, parameter query, dan berbagai detail terkait rute lainnya. Dengan `useRouter`, kita dapat membuat logika yang bergantung pada lokasi halaman atau parameter yang disediakan dalam URL.

**Contoh Penggunaan `useRouter`:**

```javascript
import { useRouter } from 'next/router';

function MyComponent() {
  // Menggunakan hook useRouter
  const router = useRouter();

  // Mengakses informasi rute menggunakan objek router
  console.log(router.pathname); // Menampilkan rute halaman saat ini
  console.log(router.query);    // Menampilkan parameter query dalam URL

  return (
    <div>
      <h1>Contoh Penggunaan useRouter</h1>
      <p>Rute Saat Ini: {router.pathname}</p>
      <p>Query: {JSON.stringify(router.query)}</p>
    </div>
  );
}

export default MyComponent;
```

**Penjelasan Contoh di Atas:**

- `router.pathname`: Menampilkan rute halaman saat ini (misalnya, `/about` jika berada di halaman tentang kami).
- `router.query`: Menampilkan parameter query yang ada di URL. Misalnya, jika URL adalah `/products?id=5`, maka `router.query` akan bernilai `{ id: '5' }`.

Dengan `useRouter`, kita dapat mengembangkan komponen dinamis yang merespons perubahan rute dan query dalam URL, yang sangat berguna dalam aplikasi dengan rute dinamis atau yang memerlukan logika khusus untuk halaman tertentu.


## Fitur pada route di Next Js (Surya)

## Penggunaan Route Next Js (Surya)

## Kesimpulan (Adelfia)