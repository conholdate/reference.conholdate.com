---
title: Menambahkan Anotasi Tinta dengan Aspose.PDF untuk .NET
linktitle: Menambahkan Anotasi Tinta dengan Aspose.PDF untuk .NET
second_title: Referensi API Aspose.PDF untuk .NET
description: Pelajari cara membuat dokumen PDF Anda lebih interaktif dan menarik dengan menambahkan anotasi tinta menggunakan Aspose.PDF untuk .NET. Panduan lengkap ini memandu Anda melalui seluruh proses.
type: docs
weight: 20
url: /id/net/tutorials/pdf/mastering-annotations/adding-ink-annotations/
---
## Perkenalan

Selamat datang di dunia manipulasi PDF yang menarik dengan Aspose.PDF untuk .NET! Baik Anda menyempurnakan dokumen untuk penggunaan profesional, proyek pribadi, atau apa pun di antaranya, Anda berada di tempat yang tepat. Dalam panduan ini, kami akan membahas fitur praktis Aspose.PDF: menambahkan anotasi tinta ke berkas PDF Anda. Fungsionalitas ini sangat cocok untuk menyertakan catatan atau tanda tangan tulisan tangan, membuat dokumen Anda lebih interaktif dan menarik.

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda telah menyiapkan semuanya:

1. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda. Aspose.PDF berfungsi dengan lancar dengan berbagai versi, termasuk .NET Core.
2.  Pustaka Aspose.PDF: Unduh dan rujuk pustaka Aspose.PDF untuk .NET di proyek Anda. Anda dapat mengambil versi terbaru dari[tautan unduhan](https://releases.aspose.com/pdf/net/).
3. Editor Kode: Meskipun Anda dapat menggunakan editor kode apa pun, Visual Studio sangat direkomendasikan karena antarmukanya yang mudah digunakan dengan aplikasi .NET.
4. Pengetahuan Dasar C#: Keakraban dengan C# akan membantu Anda menavigasi contoh pengkodean dengan lancar.
5. Pengaturan Lingkungan Pengembangan: Pastikan IDE Anda dikonfigurasi untuk proyek .NET dan Anda telah mereferensikan pustaka Aspose.PDF dengan benar.

Setelah Anda memiliki prasyarat ini, Anda siap untuk mulai menambahkan anotasi tinta ke PDF Anda!

## Mengimpor Paket yang Diperlukan

Sebelum mulai membuat kode, mari impor paket-paket yang diperlukan. Di bagian atas berkas C# Anda, tambahkan pernyataan berikut:

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
using System.Collections.Generic;
```

Pernyataan ini akan menyediakan akses ke semua kelas dan metode yang diperlukan untuk bekerja dengan anotasi PDF.

Mari kita uraikan proses penambahan anotasi tinta ke dokumen PDF Anda ke dalam langkah-langkah yang jelas.

## Langkah 1: Siapkan Dokumen dan Direktori

Pertama, tentukan dokumen dan jalur untuk menyimpan file output:

```csharp
string dataDir = "YOUR DATA DIRECTORY";
Document doc = new Document();
```

 Di Sini,`dataDir` menunjuk ke direktori tempat PDF hasil Anda akan disimpan, dan kami membuat instance baru`Document` objek untuk diedit.

## Langkah 2: Tambahkan Halaman ke Dokumen Anda

Berikutnya, tambahkan halaman ke dokumen yang baru Anda buat:

```csharp
Page pdfPage = doc.Pages.Add();
```

Setiap PDF membutuhkan setidaknya satu halaman, jadi langkah ini penting.

## Langkah 3: Tentukan Persegi Panjang Gambar

Sekarang, tentukan di mana pada halaman Anda akan menempatkan anotasi tinta Anda:

```csharp
System.Drawing.Rectangle drect = new System.Drawing.Rectangle
{
    Height = (int)pdfPage.Rect.Height,
    Width = (int)pdfPage.Rect.Width,
    X = 0,
    Y = 0
};
Aspose.Pdf.Rectangle arect = Aspose.Pdf.Rectangle.FromRect(drect);
```

 Kode ini membuat`Rectangle` objek yang menentukan area pada halaman untuk anotasi tinta Anda, yang sesuai dengan seluruh halaman.

## Langkah 4: Siapkan Titik Tinta

Berikutnya, tentukan titik-titik yang akan membentuk anotasi tinta Anda:

```csharp
IList<Point[]> inkList = new List<Point[]>();
Aspose.Pdf.Point[] arrpt = new Aspose.Pdf.Point[3];
inkList.Add(arrpt);
arrpt[0] = new Aspose.Pdf.Point(100, 800);
arrpt[1] = new Aspose.Pdf.Point(200, 800);
arrpt[2] = new Aspose.Pdf.Point(200, 700);
```

Blok ini membuat daftar larik Titik, di mana setiap larik mewakili sekumpulan titik untuk goresan tinta Anda. Di sini, kami mendefinisikan tiga titik yang membentuk segitiga, tetapi Anda bebas menyesuaikan koordinat agar sesuai dengan desain Anda.

## Langkah 5: Buat Anotasi Tinta

Setelah poin Anda ditentukan, buatlah anotasi tinta:

```csharp
InkAnnotation ia = new InkAnnotation(pdfPage, arect, inkList)
{
    Title = "Your Title",
    Color = Aspose.Pdf.Color.LightBlue,
    CapStyle = CapStyle.Rounded
};
```

 Kami mewujudkan`InkAnnotation` objek, memasukkan halaman, persegi panjang, dan titik tinta. Sesuaikan properti seperti`Title`, `Color` , Dan`CapStyle` sesuai dengan kebutuhan Anda!

## Langkah 6: Mengatur Batas dan Opacity

Untuk membuat anotasi Anda menonjol, mari beri gaya:

```csharp
Border border = new Border(ia)
{
    Width = 25
};
ia.Border = border;
ia.Opacity = 0.5;
```

Kode ini menambahkan batas dengan lebar tertentu dan mengatur opasitas anotasi agar semi-transparan.

## Langkah 7: Tambahkan Anotasi ke Halaman

Sekarang, tambahkan anotasi Anda ke halaman PDF:

```csharp
pdfPage.Annotations.Add(ia);
```

Baris ini menambahkan anotasi tinta ke koleksi anotasi halaman.

## Langkah 8: Simpan Dokumen

Terakhir, simpan dokumen Anda yang telah dimodifikasi:

```csharp
dataDir = dataDir + "AddInkAnnotation_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nInk annotation added successfully.\nFile saved at " + dataDir);
```

 Di sini, kami memodifikasi`dataDir` untuk menyertakan nama berkas keluaran dan menyimpan dokumen. Pesan konfirmasi akan memberitahu Anda bahwa semuanya berjalan lancar.

## Kesimpulan

Selamat! Anda telah berhasil menambahkan anotasi tinta ke dokumen PDF Anda menggunakan Aspose.PDF untuk .NET. Fitur sederhana namun hebat ini dapat menyempurnakan dokumen Anda dan membuatnya interaktif. Baik Anda menambahkan tanda tangan, catatan, atau coretan, anotasi tinta menyediakan cara unik untuk memperkaya konten Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.PDF?
Aspose.PDF adalah pustaka untuk membuat, memanipulasi, dan mengonversi dokumen PDF dalam aplikasi .NET.

### Dapatkah saya menggunakan Aspose.PDF secara gratis?
Ya! Aspose menawarkan versi uji coba gratis untuk mengevaluasi produk mereka. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/).

### Apakah mungkin untuk menambahkan beberapa anotasi tinta?
 Tentu saja! Anda dapat membuat beberapa`InkAnnotation` objek dan menambahkannya ke halaman dokumen Anda.

### Di mana saya dapat menemukan lebih banyak contoh?
 Lihat di sini[dokumentasi](https://reference.aspose.com/pdf/net/) untuk tutorial dan contoh terperinci.

### Apa yang harus saya lakukan jika saya memerlukan dukungan?
 Jika Anda mengalami masalah, Anda dapat mencari bantuan di[forum dukungan](https://forum.aspose.com/c/pdf/10).