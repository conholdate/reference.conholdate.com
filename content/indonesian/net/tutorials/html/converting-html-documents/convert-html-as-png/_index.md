---
title: Konversi HTML ke PNG dengan Aspose.HTML di .NET
linktitle: Konversi HTML ke PNG dengan Aspose.HTML di .NET
second_title: Aspose.HTML .NET API manipulasi HTML
description: Pelajari cara mengonversi dokumen HTML menjadi gambar PNG dalam .NET menggunakan pustaka Aspose.HTML. Ikuti tutorial langkah demi langkah kami untuk menyederhanakan konversi HTML ke gambar.
type: docs
weight: 10
url: /id/net/tutorials/html/converting-html-documents/convert-html-as-png/
---
## Perkenalan

Apakah Anda ingin mengonversi dokumen HTML menjadi gambar PNG dengan mudah? Nah, Anda berada di tempat yang tepat! Dalam tutorial ini, kita akan membahas cara menggunakan Aspose.HTML untuk .NET guna merender HTML sebagai gambar PNG. Pustaka canggih ini menyederhanakan proses penanganan konten HTML dalam aplikasi .NET, sehingga memudahkan untuk mengonversi halaman web atau templat dokumen ke dalam format gambar.

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda telah menyiapkan semuanya dengan benar:

1.  .NET Framework/ .NET Core: Pastikan Anda telah menginstal .NET Framework atau .NET Core di komputer Anda. Anda dapat mengunduh[.NET di sini](https://dotnet.microsoft.com/download).

2.  Pustaka Aspose.HTML untuk .NET: Anda harus memiliki pustaka Aspose.HTML. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/html/net/)atau coba gratis dengan[uji coba gratis](https://releases.aspose.com/).

3. IDE: Lingkungan pengembangan terintegrasi (IDE) yang sesuai seperti Visual Studio direkomendasikan untuk menulis dan menjalankan kode Anda.

4. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda mengikutinya dengan lancar, tetapi jangan khawatir, saya akan menjelaskan semuanya seiring berjalannya waktu!

Setelah Anda memiliki prasyarat ini, kita siap untuk memulai!

## Paket Impor

Untuk memanfaatkan fungsi Aspose.HTML, kita perlu mengimpor namespace yang diperlukan. Berikut cara menambahkan referensi dalam proyek Anda:

1. Buka proyek Anda di Visual Studio.
2. Klik kanan pada proyek Anda di Solution Explorer.
3. Pilih "Kelola Paket NuGet."
4.  Pencarian untuk`Aspose.HTML` dan menginstalnya.

Setelah paket terpasang, Anda dapat mulai membuat kode! Langkah pertama adalah menyiapkan ruang kerja dan menyertakan namespace yang relevan dalam file C# Anda.

```csharp
using Aspose.Html;
using Aspose.Html.Converters;
using Aspose.Html.Rendering;
using Aspose.Html.Rendering.Image;
```

Setelah kita bahas latarnya, mari kita uraikan proses merender HTML sebagai gambar PNG ke dalam langkah-langkah terperinci dan mudah diikuti.

## Langkah 1: Siapkan Direktori Data

Hal pertama yang ingin Anda lakukan adalah menyiapkan direktori tempat Anda akan menyimpan gambar. Direktori ini berfungsi sebagai tempat penyimpanan file PNG yang dihasilkan.

```csharp
string dataDir = "Your Data Directory"; // Tentukan jalur direktori Anda
```

-  Mengganti`"Your Data Directory"` dengan jalur tempat Anda ingin menyimpan file PNG keluaran Anda. Ini bisa berupa sesuatu seperti`@"C:\work\"`.

## Langkah 2: Buat Objek Dokumen HTML

Sekarang setelah direktori kita siap, mari buat objek dokumen HTML. Di sinilah kita akan menentukan konten HTML yang ingin kita ubah.

```csharp
using (var document = new Aspose.Html.HTMLDocument("<style>p { color: green; }</style><p>my first paragraph</p>", dataDir))
{
    // Langkah selanjutnya ada di sini
}
```

-  Pada kode di atas, kita menginisialisasi sebuah`HTMLDocument` sambil meneruskan beberapa konten HTML dasar yang memberi gaya pada paragraf agar berwarna hijau. Parameter kedua adalah jalur tempat sumber daya apa pun (jika diperlukan) akan disimpan.

## Langkah 3: Buat Renderer HTML

 Selanjutnya, kita akan membuat sebuah instance dari`HtmlRenderer` Kelas ini bertanggung jawab untuk mengubah dokumen HTML kita ke dalam format gambar yang diinginkan.

```csharp
using (HtmlRenderer renderer = new HtmlRenderer())
{
    // Lanjutkan ke langkah berikutnya
}
```

-  Itu`HtmlRenderer`adalah objek andalan Anda untuk mengubah konten HTML menjadi gambar. Objek ini menangani proses rendering secara mendalam, sehingga Anda dapat fokus pada apa yang Anda butuhkan!

## Langkah 4: Siapkan Perangkat Gambar

 Sekarang saatnya untuk mempersiapkan`ImageDevice`Ini adalah target proses rendering kami, tempat gambar PNG final akan dibuat.

```csharp
using (ImageDevice device = new ImageDevice(dataDir + @"document_out.png"))
{
    // Render dokumen HTML
}
```

- `ImageDevice` mengambil jalur lengkap dari file PNG yang akan dibuat. Di sini, kami menentukan bahwa file tersebut harus disimpan sebagai`document_out.png` di direktori yang telah kita definisikan sebelumnya.

## Langkah 5: Render Dokumen HTML ke PNG

Sekarang tibalah bagian yang menarik—merender dokumen HTML kita menjadi gambar PNG! Di sinilah kita memanggil metode render untuk menyelesaikan konversi.

```csharp
renderer.Render(device, document);
```

-  Menggunakan`Render` metode dari`HtmlRenderer` kamu melewati`ImageDevice` dan`HTMLDocument`Tindakan ini mengubah HTML yang kita tentukan menjadi gambar PNG, dan gambar tersebut disimpan ke direktori yang Anda tentukan sebelumnya.

## Kesimpulan

Nah, itu dia! Anda telah berhasil merender HTML sebagai gambar PNG menggunakan Aspose.HTML di .NET. Alat canggih ini menawarkan cara mudah untuk memanipulasi konten HTML secara terprogram, sehingga pembuatan dan penyajian dokumen menjadi lebih mudah dari sebelumnya. Baik Anda bekerja pada aplikasi web atau membuat laporan, metode ini akan mengubah segalanya.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.HTML untuk .NET?
Aspose.HTML untuk .NET adalah pustaka yang memungkinkan pengembang bekerja dengan dokumen HTML dalam aplikasi .NET, menawarkan fungsionalitas untuk rendering, konversi, dan pengeditan.

### Bisakah saya menggunakan Aspose.HTML tanpa lisensi?
Ya, Aspose menawarkan versi uji coba gratis yang dapat Anda gunakan untuk menjelajahi fitur-fiturnya sebelum melakukan pembelian.

### Jenis file apa yang dapat dikonversi Aspose.HTML?
Aspose.HTML terutama mengonversi dokumen HTML ke berbagai format, termasuk PNG, JPEG, PDF, dan masih banyak lagi.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.HTML?
 Anda bisa mendapatkan dukungan melalui forum Aspose[Di Sini](https://forum.aspose.com/c/html/29).

### Apakah Aspose.HTML kompatibel dengan .NET Core?
Ya, Aspose.HTML kompatibel dengan .NET Core dan dapat digunakan dalam aplikasi .NET Core tanpa masalah apa pun.