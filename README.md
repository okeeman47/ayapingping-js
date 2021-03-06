# What is AyaPingPing?

AyaPingPing is the `basename` of my starter pack framework for building REST API applications. The goal is to create a simple, clean, and maintainable application environment that also has advantages in performance and security. The first AyaPingPing was made only for building REST API in NodeJS. It was around 2018/2019, when NodeJS became the only one programming language I worked with. But now, I learn and work with some new programming languages. So, I implement AyaPingPing in other programming languages.

# AyaPingPing JS (ayapingping-js)

And this is the implementation of AyaPingPing in NodeJS. The name become AyaPingPing JS, or called `ayapingping-js`.

> English documentation would be available soon.

# `ayapingping-js v3`

Kenapa versi 3?

`ayapingping-js v3` adalah versi pertama yang saya rilis untuk umum. AyaPingPing pada awalnya saya buat untuk memenuhi kebutuhan *development* di tempat kerja. Mulai dari `v0.1` hingga terakhir `v2.1` dengan serangkaian optimasi yang terus dilakukan untuk menangani kelemahan-kelematan pada versi sebelumnya. Hingga `v2.1`, AyaPingPing masih bersifat *private*.

AyaPingPing bisa terus berkembang adalah karena kontribusi dari rekan-rekan *developer* di kantor. Mereka mendukung saya, memberikan kritik dan masukan, serta melaporkan *issue*, bahkan rela mengembangkan sistem baru di dalam AyaPingPing&mdash;yang semuanya itu bertujuan membantu agar *framework* ini menjadi lebih baik.

Kontribusi *developer* lain sangatlah penting. Oleh karena itu, saya akhirnya memutuskan merilis AyaPingPing untuk umum. Dengan harapan, AyaPingPing dapat digunakan untuk membantu pekerjaan rekan-rekan *developer* lain di luar sana. Saya juga berharap mendapatkan *feedback*, sehingga kita bisa berkontribusi bersama untuk membuat *framework* ini menjadi lebih baik lagi kedepannya.

# Welcome to `v3`

`ayapingping-js v3` merupakan pengembangan dari `v2.1`. Meskipun sebagian besar fungsinya masih mirip dengan `v2.1`, namun *problem* & kelemahan yang muncul di `v2.1` telah diperbaiki di `v3`. Selain itu, `v3` menggunakan konsep & mekanisme yang benar-benar baru&mdash;tidak seperti `v0.1` - `v2.1`.

Pada `v3`, AyaPingPing menawarkan mekanisme *custom plugin* dan *built in plugin*. Kita bisa membuat *plugin* kita sendiri atau menggunakan *built in plugin* yang tersedia, kemudian mengaktifkan atau menonaktifkannya, sehingga memudahkan kita mengatur jalannya aplikasi. Setiap proses dari fungsi `ayapingping-js` yang dipanggil tidak akan langsung dijalankan, melainkan akan didaftarkan dulu kedalam sebuah `stack` sampai fungsi `listen` atau *executor function* dipanggil. *Executor function* digunakan untuk menjalankan semua proses yang ada dan terdaftar di dalam `stack`.

# Getting started

### Installation

`ayapingping-js` tersedia di *NPM package manager*. Untuk meng*install*, pertama buat dulu *folder project* Anda dan masuk kedalam *folder* tersebut:

```bash
mkdir my-project
cd my-project
```

Kemudian, install `ayapingping-js` dengan perintah berikut:

```bash
npm install ayapingping-js
```

Setelah proses *install* berhasil, eksekusi perintah berikut untuk membuat *working directory* dari `ayapingping-js`:

```bash
./node_modules/.bin/ayapingping-js-create
```

Perintah diatas akan membuat *folders* dan *files* baru seperti: `app.js`, `.env`, `controllers`, dll yang dibutuhkan untuk memulai menggunakan `ayapingping-js`.

### Basic usage

`ayapingping-js` berbasis `ExpressJS`. Bagi yang familiar dengan `ExpressJS` tentu akan lebih mudah. Untuk menggunakan `ayapingping-js`, silahkan *install* terlebih dahulu sesuai dengan petunjuk *installation* diatas. Masuk ke *folder project* Anda, kemudian buka terminal baru dan eksekusi file `app.js` menggunakan perintah berikut ini untuk menjalankan aplikasi:

```bash
node app.js
```

Anda juga bisa menggunakan `pm2` untuk menjalankan `ayapingping-js`. Contoh:

```bash
pm2 start app.js
```

Jika berhasil, maka akan muncul keterangan "Application is live!" seperti ini:

![https://lh3.googleusercontent.com/pw/ACtC-3ffSa48lu1Ae3tyAXAYgZqw2EMO7KVueikLpKUAkH3Y3fyMR89KMQfgaQ832MFtjsIPNwzFQM1oCfWjLtpA3SBHy3Tpag6XDO70BIxo4tewcIABU7q3pDVxKj4tpPqmMGQzpp0kYtEqCyQSQouqVffA=w714-h240-no](https://lh3.googleusercontent.com/pw/ACtC-3ffSa48lu1Ae3tyAXAYgZqw2EMO7KVueikLpKUAkH3Y3fyMR89KMQfgaQ832MFtjsIPNwzFQM1oCfWjLtpA3SBHy3Tpag6XDO70BIxo4tewcIABU7q3pDVxKj4tpPqmMGQzpp0kYtEqCyQSQouqVffA=w714-h240-no)

Anda kemudian dapat melakukan *request* ke `url` dan `port` tersebut&mdash;Anda juga bisa *test* dengan membuka browser -> http://localhost:3000.

### Simple routing (`ayapingping-js` style)

Anda bisa membuat *route* sederhana di `app.js` dengan format seperti berikut:

```javascript
appjs.get('/my-route', 'myRouteController');
```

Di *folder* `controller` buat *file* bernama `myRouteController.js` dan isikan:

```javascript
'use strict';

module.exports = function(proto, req, res, next) {
  res.send('Hello world!');
};
```

*Route* baru berhasil dibuat. Jika Anda mengakses *route* `GET '/my-route'`, maka Anda akan mendapatkan *respon* "Hello world!".

### Simple routing (`ExpressJS` style)

Anda juga bisa membuat *route* di `app.js` dengan gaya `ExpressJS` seperti berikut ini:

```javascript
appjs.express((proto, app) => {
  // ExpressJS style
  app.get('/my-route', (req, res, next) => {
    res.send('Hello world!');
  });
  app.get('/my-route-2', (req, res, next) => {
    res.send('Hello world! Again!');
  });
});
```

# Working directory

Secara *default* `ayapingping-js` membagi tempat kerja menjadi bagian-bagian berikut:

-  **`app.js`**
  *File* utama `ayapingping-js` untuk *start/listen*/mengatur jalannya aplikasi. Selain itu, `app.js` juga tempat untuk membuat *routes* aplikasi.
-  **`.env`**
  *File* untuk konfigurasi *environment variables*.
-  **`controllers`**
  *Folder* untuk menaruh *file* `controller` dari *route* yang Anda buat.
-  **`middlewares`** *(OPTIONAL)*
  *Folder* untuk menaruh *file*  `middleware` dari *route* yang Anda buat. `middleware` disini bersifat *optional*, karena Anda boleh membuat *route* tanpa `middleware`.
-  **`models`** *(OPTIONAL)*
  *Folder* untuk menaruh *file* `model` *database*, misalnya: *Sequelize model* untuk MySQL atau *Mongoose model* untuk Mongo. `model` disini bersifat *optional*, karena Anda mungkin menggunakan mekanisme *raw* daripada model *database*, atau Anda mungkin tidak menggunakan *database* sama sekali.
- **`plugin`** *(OPTIONAL)*
  *Folder* untuk menaruh `plugin` yang Anda buat (*custom plugin*). `plugin` disini bersifat *optional*, karena Anda mungkin tidak menggunakan *custom plugin* sama sekali.
- **`public`** *(OPTIONAL)*
  *Folder* untuk menaruh file-file statis. `public` disini bersifat *optional*, karena Anda mungkin tidak menggunakan file-file statis.

# Application

*File* utama `ayapingping-js` untuk mengatur jalannya aplikasi adalah *file* `app.js`. Disinilah tempat kita inisialisasi fungsi-fungsi `ayapingping-js`, membuat *routes*, *listen* aplikasi, me-*load plugin*, dan lain sebagainya. `app.js` juga adalah *file* yang dieksekusi untuk menjalankan aplikasi. Untuk menggunakan fungsi `ayapingping-js`, Anda harus inisialisasi modulnya terlebih dahulu. Silahkan buka *file* `app.js`, kemudian gunakan *script* berikut (lihat contohnya di `app.js`):

```javascript
const appjs = require('ayapingping-js')(__dirname);
```

*Script* diatas akan menginisialisasi & mengunggah fungsi-fungsi bawaan `ayapingping-js`sehingga dapat diakses secara *public*. Pada *script* diatas, fungsi-fungsi tersebut disimpan kedalam *variable* `appjs`. Anda kemudian dapat memanggil fungsinya dengan mengakses objeknya, misalnya:

```javascript
appjs.get('/example');
```

> `(__dirname)` bersifat *required*, dan diperlukan oleh sistem `ayapingping-js` untuk mendapatkan *root path* dari aplikasi yang dibuat.

### Available `ayapingping-js`'s functions

Berikut adalah fungsi-fungsi bawaan `ayapingping-js` yang tersedia dengan kegunaannya masing-masing:

- **`env()`**
- **`set()`**
- **`load()`**
- **`get()`**
- **`post()`**
- **`put()`**
- **`delete()`**
- **`group()`**
- **`express()`**
- **`listen()`**

# Environment variables

*Environment variables* menentukan bagaimana sistem aplikasi berjalan tergantung pada jenis *environment server* atau komputer yang dipakai. `ayapingping-js` memiliki 3 *environment variables* utama berikut ini yang digunakan ketika aplikasi di *start*:

```
NODE_ENV=development
SERVICE_NAME=AyaPingPing JS
PORT=3000
```

*Environment variables* di `ayapingping-js` disimpan didalam file `.env`. Anda harus membaca dan me-*load file* `.env` pada saat aplikasi di *start* agar sistem dapat menggunakan *variable-variable*nya. Ada banyak cara, tapi Anda bisa melakukan hal ini dengan memanggil fungsi *environment variables* setelah inisialisasi `ayapingping-js system`: (lihat contohnya di `app.js`)

```javascript
appjs.env();
```

Sangat direkomendasikan menjalankan fungsi untuk membaca file `.env` setelah inisialisasi `ayapingping-js`. Contoh:

```javascript
const appjs = require('ayapingping-js')(__dirname);
appjs.env();
// Some stuff...
```

### Application environment

`NODE_ENV` mengatur mode *environment* aplikasi yang sedang berjalan, *default*: "development". Untuk merubah *environment* aplikasi ke mode `production`, ubah nilai `NODE_ENV` menjadi "production":

```
NODE_ENV=production
```

> `NODE_ENV` dipakai oleh ExpressJS untuk menentukan *environment* aplikasi.
> 
> Selalu gunakan mode `production` apabila Anda ingin melakukan *deployment* ke arsitektur atau *environment production*.

### Service name

`SERVICE_NAME` adalah nama dari aplikasi `ayapingping-js`, *default*: "AyaPingPing JS". Anda bisa merubahnya sesuai dengan nama aplikasi yang sedang Anda buat, misalnya:

```
SERVICE_NAME=My Application
```

> `SERVICE_NAME` dipakai untuk beberapa hal di dalam sistem aplikasi, misalnya: nama aplikasi yang ditampilkan di `console`.

### Port

`PORT` menentukan *port* yang akan di listen pada saat aplikasi dijalankan, default: "3000". Anda bisa merubah pengaturan *port*nya sesuai dengan kebutuhan, misalnya:

```
PORT=8000
```

> `PORT` diperlukan oleh sistem (server) untuk mengidentifikasi proses aplikasi atau *service* yang sedang berjalan. Jika `port` tidak di *set*, maka akan di *set default* menjadi "3000".

# Routing

### Route functions

### Route controller

### Route middleware

### Grouping

### ExpressJS style

# Controllers

### Using controller

### Using controller method

# Middlewares

### Using middleware

### Using middleware method

# Models

### MySQL model

### Mongo model

# Plugins

### How to create plugins

### How to use plugins

### Built in plugins

# Public
