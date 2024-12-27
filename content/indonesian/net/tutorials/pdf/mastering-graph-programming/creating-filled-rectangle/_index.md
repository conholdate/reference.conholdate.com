---
title: Membuat Persegi Panjang Terisi
linktitle: Membuat Persegi Panjang Terisi
second_title: Referensi API Aspose.PDF untuk .NET
description: Buka kekuatan manipulasi PDF dengan Aspose.PDF untuk .NET dalam tutorial langkah demi langkah ini. Pelajari cara membuat dokumen PDF yang menarik secara visual secara terprogram dengan menggambar persegi panjang yang terisi.
type: docs
weight: 50
url: /id/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Perkenalan

Pernahkah Anda ingin membuat PDF yang memukau secara visual secara terprogram? Jika ya, Anda berada di tempat yang tepat! Dalam tutorial ini, kita akan menjelajahi Aspose.PDF untuk .NET, pustaka canggih yang menyederhanakan manipulasi dokumen PDF. Hari ini, kita akan fokus pada pembuatan persegi panjang yang terisi dalam file PDF. Baik Anda pengembang berpengalaman atau baru memulai, panduan ini akan memandu Anda melalui setiap langkah dengan cara yang ramah dan menarik. Jadi, ambil topi pengodean Anda, dan mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki hal berikut:

1. Visual Studio: Instal Visual Studio di komputer Anda, karena ini merupakan IDE yang sangat baik untuk pengembangan .NET.
2. Aspose.PDF untuk .NET: Unduh dan instal pustaka Aspose.PDF dari[Di Sini](https://releases.aspose.com/pdf/net/).
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda memahami potongan kode dengan lebih baik.

## Langkah 1: Buat Proyek Baru

1. Buka Visual Studio dan buat proyek Aplikasi Konsol baru.
2. Beri nama proyek Anda dengan tepat.

## Langkah 2: Tambahkan Referensi Aspose.PDF

1. Klik kanan pada proyek Anda di Solution Explorer.
2. Pilih Kelola Paket NuGet.
3. Cari Aspose.PDF dan instal versi terbaru.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Sekarang setelah semuanya disiapkan, mari masuk ke kodenya!

## Langkah 3: Siapkan Direktori Dokumen Anda

Tentukan jalur tempat PDF Anda akan disimpan:

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya pada komputer Anda tempat Anda ingin menyimpan PDF.

## Langkah 4: Buat Contoh Dokumen

Inisialisasi dokumen PDF baru:

```csharp
// Buat contoh Dokumen
Document doc = new Document();
```

## Langkah 5: Tambahkan Halaman ke Dokumen

Setiap PDF memerlukan setidaknya satu halaman. Mari kita tambahkan satu halaman:

```csharp
// Tambahkan halaman ke koleksi halaman file PDF
Page page = doc.Pages.Add();
```

## Langkah 6: Buat Contoh Grafik

 A`Graph` instance bertindak sebagai kanvas untuk menggambar bentuk:

```csharp
// Buat contoh Grafik
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Langkah 7: Tambahkan Grafik ke Halaman

Lampirkan grafik ke halaman:

```csharp
// Tambahkan objek grafik ke koleksi paragraf dari contoh halaman
page.Paragraphs.Add(graph);
```

## Langkah 8: Buat Instansi Persegi Panjang

Tentukan posisi dan ukuran persegi panjang:

```csharp
// Buat instance Persegi Panjang
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Langkah 9: Tentukan Warna Isi

Pilih warna untuk persegi panjang Anda. Untuk contoh ini, kita akan menggunakan warna merah:

```csharp
// Tentukan warna isian untuk objek Grafik
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Langkah 10: Tambahkan Persegi Panjang ke Grafik

Tambahkan persegi panjang ke grafik:

```csharp
// Tambahkan objek persegi panjang ke koleksi bentuk objek Grafik
graph.Shapes.Add(rect);
```

## Langkah 11: Simpan Dokumen PDF

Terakhir, simpan dokumen Anda ke direktori yang ditentukan:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Simpan file PDF
doc.Save(dataDir);
```

## Langkah 12: Pesan Konfirmasi

Cetak pesan konfirmasi untuk menunjukkan keberhasilan:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Kesimpulan

Selamat! Anda telah berhasil membuat persegi panjang yang terisi dalam dokumen PDF menggunakan Aspose.PDF untuk .NET. Pustaka canggih ini membuka banyak kemungkinan untuk manipulasi PDF, yang memungkinkan Anda membuat dokumen yang menakjubkan secara terprogram. Baik Anda membuat laporan, faktur, atau jenis PDF lainnya, Aspose.PDF siap membantu Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.PDF untuk .NET?
Aspose.PDF untuk .NET adalah pustaka yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen PDF secara terprogram.

### Dapatkah saya menggunakan Aspose.PDF secara gratis?
 Ya, Aspose menawarkan versi uji coba gratis yang dapat Anda gunakan untuk menjelajahi fitur-fitur pustaka. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/).

### Apakah ada cara untuk mendapatkan dukungan untuk Aspose.PDF?
 Tentu saja! Anda bisa mendapatkan dukungan melalui forum Aspose[Di Sini](https://forum.aspose.com/c/pdf/10).

### Bagaimana saya dapat membeli Aspose.PDF?
 Anda dapat membeli Aspose.PDF dengan mengunjungi halaman pembelian[Di Sini](https://purchase.aspose.com/buy).

### Jenis bentuk apa yang dapat saya buat dengan Aspose.PDF?
Anda dapat membuat berbagai bentuk, termasuk persegi panjang, lingkaran, garis, dan banyak lagi, menggunakan pustaka Aspose.PDF.