# Jawaban Praktikum: Asep Dida Permana (10224040)

> Folder dan identitas telah disesuaikan untuk pengumpulan.

## Bagian 1: Pemanasan
1. Selector: `nav a.active:hover`. Deklarasi: `color: red;`. Property: `color`. Value: `red`. Pseudo-class: `:hover`.
2. Block: `p`, `li`, `h2`. Inline: `span`, `a`, `strong`.
3. A dan B menjadi hijau. Selector `.box p` memilih paragraf keturunan elemen ber-class `box`; C memiliki class itu sendiri tetapi bukan keturunannya.
4. Merah, karena selector ID `#title` memiliki specificity lebih tinggi daripada `.heading` dan `h1`.
5. Tag bersarang tidak ditutup dengan urutan yang benar. `<strong>` harus ditutup sebelum `</p>`: `<p>Hello <strong>world</strong></p>`.

## Bagian 3: Prediksi Selector Golf
P1. (a) hijau, (b) orange, (c) biru.
P2. `#tech p` > `.club p` > `main section p` > `p`.
Setelah diuji (hasil sebenarnya): (a) hijau, (b) orange, (c) biru. Pada B, `.note` menang atas `section p` karena selector class memiliki specificity lebih tinggi. Footer tidak cocok dengan `section p` maupun `.note`, jadi tetap biru.

## Bagian 4: Box model
Q1 (content-box): Lebar terlihat = 300 + (16 Ã— 2) + (1 Ã— 2) = **334 px**. Margin 24 px berada di luar border dan tidak masuk lebar terlihat.
Q2 (border-box): Lebar dari tepi border ke tepi border menjadi **300 px**; area content menyusut menjadi 300 âˆ’ 32 âˆ’ 2 = **266 px**. Margin tetap di luar ukuran 300 px.
Pengecekan DevTools: Pada section `.card`, panel Computed memperlihatkan padding 16 px di tiap sisi, border 1 px di tiap sisi, dan margin bawah 24 px. Lebar content untuk `width: auto` mengikuti ruang yang tersedia di dalam wadah; nilai tepatnya bergantung pada lebar viewport.

## Bagian 5: Tabel debug
| # | Baris | Bug | Perbaikan | Cara menemukannya |
|---|-------|-----|-----------|-------------------|
| 1 | CSS `body` | `colour` bukan nama property CSS | Ganti menjadi `color` | DevTools menandai property tidak dikenal |
| 2 | CSS `header` | Tidak ada titik koma setelah nilai `background` | Tambahkan `;` | Membaca blok deklarasi / DevTools |
| 3 | CSS `.Card` | Huruf besar tidak cocok dengan class `card` | Ganti selector menjadi `.card` | Membandingkan selector dan atribut class |
| 4 | CSS `#news-list` | Spasi di `18 px` membuat nilai `font-size` tidak valid | Ganti menjadi `18px` | DevTools menampilkan deklarasi dicoret |
| 5 | CSS `footer` | `centre` bukan nilai `text-align` | Ganti menjadi `center` | DevTools menampilkan nilai tidak valid |
| 6 | Heading | `<h1>` ditutup dengan `</h2>` | Tutup dengan `</h1>` | Validator HTML |
| 7 | Link About | Tanda kutip penutup `href` hilang | Gunakan `href="about.html"` | Validator HTML |
| 8 | Gambar | Tidak memiliki teks alternatif | Tambahkan `alt` deskriptif | Validator / pemeriksaan aksesibilitas |
| 9 | Daftar berita | Selector `#news-list` tidak cocok dengan id `newsList` | Samakan id menjadi `news-list` | Membandingkan selector dan id |

## Bagian 6: Tabel Code Review
| # | Baris | Masalah | Mengapa penting | Perbaikan saya |
|---|-------|---------|-----------------|----------------|
| 1 | Dokumen | Tidak ada doctype dan atribut bahasa | Mode render dan bahasa dokumen tidak dinyatakan dengan benar | Tambahkan `<!DOCTYPE html>` dan `<html lang="id">` |
| 2 | Head | Tidak ada charset dan viewport | Karakter dan tampilan layar kecil bisa bermasalah | Tambahkan meta charset dan viewport |
| 3 | Header | Elemen `div` dipakai sebagai header, tanpa landmark semantik | Struktur halaman lebih sulit dipahami pembaca dan teknologi bantu | Gunakan `<header>` dan `<nav>` |
| 4 | Judul | Nama kampus dibuat dengan `<b>` di dalam `div`, bukan heading | Struktur heading tidak tersedia untuk navigasi | Gunakan satu `<h1>` |
| 5 | Konten | Semua konten memakai `div` dan pemisah `<br>` untuk tata letak | Makna tiap bagian tidak terwakili dan jarak sulit dirawat | Gunakan `<main>`, `<section>`, heading, paragraf, dan margin CSS |
| 6 | CSS `.header` | Lebar tetap 1200px dapat melampaui layar kecil | Menyebabkan scroll horizontal | Pakai `max-width: 960px; margin: 0 auto;` |
| 7 | CSS nav | `!important` membuat aturan sulit ditimpa | Menyulitkan pemeliharaan cascade | Hapus `!important` dan atur specificity secukupnya |
| 8 | CSS `.content`, `.sidebar`, `.title` | `.sidebar` dan `.title` tidak digunakan; `.content` memakai abu-abu muda dengan kontras rendah | Kode mati membingungkan dan teks sulit dibaca | Hapus aturan tak terpakai dan gunakan warna teks kontras |
| 9 | About/Contact | Judul bagian adalah `div` dengan inline style | Tidak dapat dinavigasi sebagai heading dan styling bercampur dengan konten | Gunakan `<h2>` dan aturan CSS |
| 10 | Form | Input tidak punya label; email bertipe text | Label aksesibel tidak ada dan validasi email tidak digunakan | Hubungkan `<label for>` dan gunakan `type="email"` |
| 11 | Form | Tombol menjalankan inline JavaScript `alert`, tanpa form yang dapat dikirim | Tidak menyediakan formulir yang semantik atau jalur pengiriman | Gunakan `<form>`, tombol submit, dan pesan submit yang sesuai kebutuhan |
| 12 | Gambar | Tidak ada `alt` | Informasi gambar tidak tersedia bagi pembaca layar atau saat gambar gagal dimuat | Tambahkan alt yang menjelaskan gambar |
| 13 | Footer | Footer hanya sebuah `div` dan tidak rata tengah | Landmark footer tidak dikenali | Gunakan `<footer>` dan styling khusus |

Refleksi:
1. Masalah yang paling sulit disadari hanya dari tampilan adalah input tanpa label dan gambar tanpa alt. Keduanya bisa terlihat normal, tetapi pengguna pembaca layar tidak mendapat konteks yang sama.
2. Validitas, semantik, responsivitas, dan aksesibilitas memengaruhi cara halaman digunakan oleh perangkat dan pengguna yang berbeda. Kode yang terstruktur juga lebih mudah dirawat saat konten bertambah.
3. Sebelum mengumpulkan, saya akan memeriksa struktur dan atribut dengan validator, lalu menguji tampilan di layar kecil serta mengecek label dan alt.

## Bagian 7: Exit ticket
1. Aturan CSS terdiri dari selector yang memilih elemen, lalu blok deklarasi berisi pasangan property dan value.
2. Specificity beberapa selector yang sama-sama memiliki pseudo-class masih perlu latihan.
3. Saya bisa membuat link navigasi ke section memakai id dan atribut `href="#..."`.

