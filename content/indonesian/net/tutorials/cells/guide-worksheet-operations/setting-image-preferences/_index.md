---
title: Mengatur Preferensi Gambar untuk HTML dengan Aspose.Cells di .NET
linktitle: Mengatur Preferensi Gambar untuk HTML dengan Aspose.Cells di .NET
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mengonversi lembar kerja Excel secara efektif menjadi halaman web HTML yang menarik secara visual menggunakan Aspose.Cells untuk .NET. Panduan langkah demi langkah ini mencakup semuanya, mulai dari pengaturan preferensi gambar hingga pengoptimalan tampilan teks.
type: docs
weight: 11
url: /id/net/tutorials/cells/guide-worksheet-operations/setting-image-preferences/
---
## Perkenalan

Mengubah lembar kerja Excel menjadi halaman web yang menarik secara visual dapat meningkatkan presentasi data online Anda secara signifikan. Dengan Aspose.Cells untuk .NET, Anda tidak hanya dapat mengubah lembar kerja menjadi HTML tetapi juga menyesuaikan berbagai pengaturan untuk mengoptimalkan gambar untuk web. Dalam panduan ini, kami akan memandu Anda melalui proses pengaturan preferensi gambar saat mengubah file Excel menjadi HTML. Mari kita mulai!

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

1. Visual Studio Terpasang: Lingkungan pengembangan seperti Visual Studio penting untuk menjalankan dan menguji aplikasi .NET Anda.
2.  Aspose.Cells untuk .NET: Unduh dan instal versi terbaru dari[Situs web Aspose](https://releases.aspose.com/cells/net/).
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda memahami contoh-contoh secara lebih efektif.
4.  Contoh File Excel: Siapkan file Excel bernama`Book1.xlsx` dan letakkan di folder khusus untuk referensi dalam kode Anda.

## Menyiapkan Proyek Anda

### 1. Buka Proyek Anda

Luncurkan Visual Studio dan buka proyek C# yang ada atau buat yang baru.

### 2. Tambahkan Referensi Aspose.Cells

- Klik kanan pada proyek Anda di Solution Explorer.
- Pilih “Kelola Paket NuGet.”
- Cari “Aspose.Cells” dan instal paketnya.

### 3. Sertakan Menggunakan Arahan

Di bagian atas berkas kode C# Anda, sertakan namespace Aspose.Cells yang diperlukan:

```csharp
using System.IO;
using Aspose.Cells;
```

Sekarang Anda siap memanfaatkan fitur-fitur hebat Aspose.Cells dalam proyek Anda!

## Langkah 1: Tentukan Direktori Dokumen

Tetapkan jalur ke direktori tempat dokumen Anda disimpan. Ini penting untuk akses berkas.

```csharp
string dataDir = "Your Document Directory";
```

 Pastikan untuk mengganti`"Your Document Directory"` dengan jalur sebenarnya di mesin Anda.

## Langkah 2: Tentukan Jalur File

Tentukan jalur file untuk dokumen Excel yang ingin Anda konversi:

```csharp
string filePath = Path.Combine(dataDir, "Book1.xlsx");
```

 Menggunakan`Path.Combine`memastikan jalur berkas dibangun dengan benar.

## Langkah 3: Muat Buku Kerja

 Muat file Excel Anda ke dalam`Workbook` objek, yang memungkinkan Anda berinteraksi dengan data spreadsheet Anda:

```csharp
Workbook book = new Workbook(filePath);
```

## Langkah 4: Buat Instansi HtmlSaveOptions

 Untuk menyesuaikan proses konversi, buat contoh`HtmlSaveOptions`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html);
```

Ini menetapkan format keluaran ke HTML.

## Langkah 5: Atur Format Gambar ke PNG

Tentukan format gambar untuk konversi. Di sini, kita akan mengaturnya ke PNG:

```csharp
saveOptions.ImageOptions.ImageType = Drawing.ImageType.Png;
```

Penggunaan PNG memastikan gambar berkualitas tinggi dalam keluaran Anda.

## Langkah 6: Konfigurasikan Mode Smoothing

Tingkatkan tampilan gambar dengan mengatur mode penghalusan:

```csharp
saveOptions.ImageOptions.SmoothingMode = System.Drawing.Drawing2D.SmoothingMode.AntiAlias;
```

Ini mengurangi tepi yang bergerigi, membuat gambar Anda tampak lebih halus.

## Langkah 7: Optimalkan Rendering Teks

Tingkatkan keterbacaan teks dalam gambar dengan mengoptimalkan tampilan teks:

```csharp
saveOptions.ImageOptions.TextRenderingHint = System.Drawing.Text.TextRenderingHint.AntiAlias;
```

Penyesuaian kecil ini dapat meningkatkan kualitas visual teks Anda secara signifikan.

## Langkah 8: Simpan Buku Kerja sebagai HTML

Terakhir, simpan buku kerja Anda sebagai file HTML menggunakan opsi yang dikonfigurasi:

```csharp
book.Save(Path.Combine(dataDir, "output.html"), saveOptions);
```

File HTML baru Anda akan disimpan di direktori yang ditentukan sebagai`output.html`.

## Kesimpulan

Selamat! Anda telah berhasil mempelajari cara mengatur preferensi gambar untuk ekspor HTML menggunakan Aspose.Cells untuk .NET. Konfigurasi ini tidak hanya menciptakan representasi data Excel yang menarik secara visual, tetapi juga mengoptimalkannya untuk penggunaan web. Baik Anda membuat laporan, dasbor, atau memvisualisasikan data, pengaturan praktis ini dapat membuat perbedaan yang signifikan dalam presentasi Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Cells untuk .NET?

Aspose.Cells untuk .NET adalah pustaka hebat yang dirancang untuk membuat, membaca, dan memanipulasi file Excel dalam aplikasi .NET.

### Bisakah saya menggunakan Aspose.Cells tanpa Visual Studio?

Ya, Aspose.Cells dapat digunakan di IDE atau aplikasi konsol apa pun yang kompatibel dengan .NET, bukan hanya Visual Studio.

### Apakah ada versi uji coba yang tersedia?

 Tentu saja! Anda dapat mengunduh versi uji coba gratis Aspose.Cells dari[Situs web Aspose](https://releases.aspose.com/).

### Format gambar apa yang dapat saya gunakan dengan Aspose.Cells?

Aspose.Cells mendukung berbagai format gambar untuk ekspor, termasuk PNG, JPEG, dan BMP.

### Bagaimana cara mendapatkan dukungan untuk Aspose.Cells?

 Untuk dukungan, kunjungi[Forum Aspose](https://forum.aspose.com/c/cells/9), di mana komunitas dan tim dukungan dapat membantu Anda.