---
title: Membuat Bookmark PDF untuk Lembar Bagan di Aspose.Cells
linktitle: Membuat Bookmark PDF untuk Lembar Bagan di Aspose.Cells
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara menyempurnakan dokumen Excel Anda dengan membuat penanda PDF interaktif untuk lembar bagan menggunakan Aspose.Cells for .NET. Tutorial langkah demi langkah ini memberikan panduan yang jelas bagi pengembang dari semua tingkat keterampilan.
type: docs
weight: 13
url: /id/net/tutorials/cells/mastering-rendering-and-exporting/creating-pdf-bookmark-for-chart-sheet/
---
## Perkenalan

Aspose.Cells untuk .NET adalah pustaka canggih yang memungkinkan pengembang untuk memanipulasi file Excel secara terprogram. Salah satu fiturnya yang menonjol adalah kemampuan untuk membuat penanda PDF untuk lembar bagan individual, yang meningkatkan navigasi dan kegunaan dokumen. Tutorial ini akan memandu Anda langkah demi langkah melalui proses ini, sehingga dapat diakses tanpa memandang pengalaman pemrograman Anda. Ambil editor kode Anda, dan mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  Aspose.Cells untuk .NET: Unduh pustaka dari[Di Sini](https://releases.aspose.com/cells/net/).
2. Visual Studio atau IDE .NET apa pun: Anda memerlukan lingkungan pengembangan untuk menulis dan mengeksekusi kode C# Anda.
3. Pemahaman Dasar C#: Pemahaman terhadap dasar-dasar C# akan membantu saat kita mempelajari kode tersebut.
4. Contoh Berkas Excel: Siapkan contoh berkas Excel yang menyertakan bagan untuk latihan ini.

Setelah Anda memiliki prasyarat ini, Anda siap membuat penanda PDF untuk lembar bagan!

## Langkah 1: Buat Proyek Baru
1. Buka Visual Studio dan buat aplikasi konsol C# baru. Beri nama AsposePDFBookmarkExample.
   
## Langkah 2: Tambahkan Referensi Aspose.Cells
1. Klik kanan pada proyek Anda di Solution Explorer.
2. Pilih Kelola Paket NuGet.
3. Cari Aspose.Cells dan instal versi terbaru.

## Langkah 3: Sertakan Petunjuk Penggunaan yang Diperlukan
 Di dalam kamu`Program.cs` file, tambahkan baris berikut di bagian atas untuk mengimpor namespace yang diperlukan:

```csharp
using System;
using System.Collections;
using System.Linq;
using System.Text;
using Aspose.Cells;
using Aspose.Cells.Rendering;
```

Ruang nama ini akan memungkinkan Anda bekerja dengan berkas Excel dan menyajikannya dalam bentuk PDF dengan penanda halaman.

## Langkah 4: Tentukan Jalur Direktori Anda
Atur kode Anda dengan menentukan jalur untuk file Anda:
```csharp
string sourceDir = "Your Document Directory"; // Sesuaikan dengan direktori sumber Anda
string outputDir = "Your Document Directory"; // Sesuaikan dengan direktori keluaran Anda
```

## Langkah 5: Muat Buku Kerja Excel
Muat buku kerja Excel yang ingin Anda manipulasi:
```csharp
Workbook wb = new Workbook(sourceDir + "sampleCreatePdfBookmarkEntryForChartSheet.xlsx");
```
Pastikan nama berkasnya sesuai dengan berkas Anda yang sebenarnya.

## Langkah 6: Akses Lembar Kerja
Akses lembar kerja dalam buku kerja:
```csharp
Worksheet sheet1 = wb.Worksheets[0];
Worksheet sheet2 = wb.Worksheets[1];
Worksheet sheet3 = wb.Worksheets[2];
Worksheet sheet4 = wb.Worksheets[3];
```
Pastikan berkas Excel Anda berisi setidaknya empat lembar.

## Langkah 7: Buat Entri Bookmark PDF
Sekarang, buat entri penanda untuk setiap lembar:
```csharp
PdfBookmarkEntry ent1 = new PdfBookmarkEntry {
    Destination = sheet1.Cells["A1"],
    Text = "Bookmark-I"
};
PdfBookmarkEntry ent2 = new PdfBookmarkEntry {
    Destination = sheet2.Cells["A1"],
    Text = "Bookmark-II-Chart1"
};
PdfBookmarkEntry ent3 = new PdfBookmarkEntry {
    Destination = sheet3.Cells["A1"],
    Text = "Bookmark-III"
};
PdfBookmarkEntry ent4 = new PdfBookmarkEntry {
    Destination = sheet4.Cells["A1"],
    Text = "Bookmark-IV-Chart2"
};
```
 Setiap`PdfBookmarkEntry` objek menentukan sel tujuan dan label teks untuk penanda buku.

## Langkah 8: Atur Entri Bookmark
Untuk membuat struktur hierarki penanda buku, susunlah sebagai berikut:
```csharp
ArrayList lst = new ArrayList();
ent1.SubEntry = lst;
lst.Add(ent2);
lst.Add(ent3);
lst.Add(ent4);
```
Struktur ini memungkinkan penanda utama dengan sub-penanda, sehingga meningkatkan navigasi dalam PDF.

## Langkah 9: Buat Opsi Penyimpanan PDF dengan Entri Bookmark
Siapkan opsi penyimpanan PDF untuk menyertakan penanda buku:
```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = ent1;
```

## Langkah 10: Simpan PDF Output
Terakhir, simpan buku kerja Anda sebagai PDF:
```csharp
wb.Save(outputDir + "outputCreatePdfBookmarkEntryForChartSheet.pdf", opts);
```
Perintah ini menyimpan buku kerja ke berkas PDF di jalur keluaran yang ditentukan, lengkap dengan penanda halaman.

## Langkah 11: Konfirmasi Eksekusi
Cetak pesan sukses untuk mengonfirmasi eksekusi:
```csharp
Console.WriteLine("CreatePdfBookmarkEntryForChartSheet executed successfully.");
```

## Kesimpulan
Membuat penanda PDF untuk lembar bagan menggunakan Aspose.Cells for .NET adalah proses mudah yang secara signifikan meningkatkan kegunaan dokumen Excel Anda. Hanya dengan beberapa baris kode, Anda dapat meningkatkan navigasi dalam PDF Anda, menghemat waktu dan menyederhanakan alur kerja.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Cells?
Aspose.Cells adalah pustaka .NET tangguh yang dirancang untuk menangani manipulasi file Excel, termasuk membaca, menulis, dan mengonversi lembar kerja.

### Bisakah saya membuat penanda untuk sel tertentu saja?
Ya, penanda buku dapat diatur untuk menunjuk ke sel mana saja di lembar kerja Anda.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Cells?
Sementara Aspose.Cells menawarkan uji coba gratis, lisensi berbayar diperlukan untuk fungsionalitas penuh dalam lingkungan produksi.

### Bisakah saya membuat penanda halaman untuk lebih dari empat lembar?
Tentu saja! Anda dapat membuat penanda halaman untuk sebanyak mungkin lembar sesuai kebutuhan dengan mengikuti struktur serupa dalam kode.

### Di mana saya dapat menemukan bantuan lebih lanjut?
 Untuk dukungan tambahan, lihat[Forum dukungan komunitas Aspose](https://forum.aspose.com/c/cells/9) untuk masalah atau pertanyaan apa pun.