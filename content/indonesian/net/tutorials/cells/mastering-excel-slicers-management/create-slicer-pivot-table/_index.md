---
title: Membuat Slicer untuk Pivot Table di Aspose.Cells .NET
linktitle: Membuat Slicer untuk Tabel Pivot di Aspose.Cells .NET
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Temukan cara mengubah tabel pivot Excel Anda dengan pemotong interaktif menggunakan Aspose.Cells untuk .NET. Panduan lengkap ini memandu Anda melalui prosesnya.
type: docs
weight: 12
url: /id/net/tutorials/cells/mastering-excel-slicers-management/creating-slicer-for-pivot-table/
---
## Perkenalan

Dalam lanskap yang digerakkan oleh data saat ini, tabel pivot sangat penting untuk meringkas dan menganalisis kumpulan data besar. Namun, mengapa membatasi diri Anda pada ringkasan dasar? Dengan pemotong, Anda dapat menambahkan interaktivitas ke tabel pivot Anda, yang memungkinkan pengguna untuk memfilter data dengan mudah—seperti memiliki kendali jarak jauh untuk laporan Excel Anda! Dalam panduan ini, kami akan memandu Anda melalui langkah-langkah untuk membuat pemotong untuk tabel pivot menggunakan Aspose.Cells untuk .NET. Jadi, ambil kopi Anda, dan mari kita mulai!

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

1. Aspose.Cells untuk .NET: Unduh dari[Aspose merilis halaman](https://releases.aspose.com/cells/net/).
2. Visual Studio atau IDE: Gunakan IDE apa pun yang mendukung pengembangan .NET, dengan Visual Studio menjadi pilihan yang populer.
3. Pengetahuan Dasar C#: Keakraban dengan C# akan membantu Anda menavigasi pengkodean dengan lancar.
4.  Contoh File Excel: Kami akan menggunakan file bernama`sampleCreateSlicerToPivotTable.xlsx` berisi tabel pivot.

Setelah semuanya siap, mari impor paket yang diperlukan.

## Mengimpor Paket

Di bagian atas berkas kode Anda, sertakan namespace berikut untuk mengakses fungsionalitas Aspose.Cells:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Langkah 1: Tentukan Direktori Sumber dan Output

Pertama, tentukan jalur untuk file input dan output Anda:

```csharp
// Direktori sumber
string sourceDir = "Your Document Directory"; // Ganti dengan jalur direktori sumber Anda
// Direktori keluaran
string outputDir = "Your Document Directory"; // Ganti dengan jalur direktori keluaran Anda
```

## Langkah 2: Muat Buku Kerja

Berikutnya, muat buku kerja Excel yang berisi tabel pivot Anda:

```csharp
// Muat contoh file Excel yang berisi tabel pivot.
Workbook wb = new Workbook(sourceDir + "sampleCreateSlicerToPivotTable.xlsx");
```

## Langkah 3: Akses Lembar Kerja Pertama

Sekarang, mari kita mengakses lembar kerja tempat tabel pivot berada:

```csharp
// Akses lembar kerja pertama.
Worksheet ws = wb.Worksheets[0];
```

## Langkah 4: Akses Tabel Pivot

Kita akan mengambil tabel pivot tempat kita ingin menambahkan slicer:

```csharp
// Akses tabel pivot pertama di lembar kerja.
Aspose.Cells.Pivot.PivotTable pt = ws.PivotTables[0];
```

## Langkah 5: Tambahkan Slicer

Sekarang untuk bagian yang menarik—menambahkan slicer! Langkah ini mengikat slicer ke bidang dasar tabel pivot:

```csharp
// Tambahkan pemotong yang terkait dengan tabel pivot di sel B22.
int idx = ws.Slicers.Add(pt, "B22", pt.BaseFields[0]);
```

## Langkah 6: Akses Slicer yang Baru Ditambahkan

Merupakan praktik yang baik untuk menyimpan referensi ke pemotong yang baru dibuat untuk modifikasi apa pun di masa mendatang:

```csharp
// Akses pemotong yang baru ditambahkan dari koleksi pemotong.
Aspose.Cells.Slicers.Slicer slicer = ws.Slicers[idx];
```

## Langkah 7: Simpan Buku Kerja

Terakhir, simpan pekerjaan Anda dalam format yang diinginkan:

```csharp
// Simpan buku kerja dalam format XLSX.
wb.Save(outputDir + "outputCreateSlicerToPivotTable.xlsx", SaveFormat.Xlsx);
// Simpan buku kerja dalam format XLSB.
wb.Save(outputDir + "outputCreateSlicerToPivotTable.xlsb", SaveFormat.Xlsb);
```

## Langkah 8: Jalankan Kode

Untuk mengonfirmasi bahwa semuanya berhasil dijalankan, tampilkan pesan:

```csharp
Console.WriteLine("CreateSlicerToPivotTable executed successfully.");
```

## Kesimpulan

Selamat! Anda telah berhasil membuat slicer untuk tabel pivot menggunakan Aspose.Cells for .NET. Fitur ini meningkatkan interaktivitas laporan Excel Anda, membuatnya lebih mudah digunakan dan menarik secara visual. 

## Pertanyaan yang Sering Diajukan

### Apa itu slicer di Excel?
Slicer adalah filter visual yang memungkinkan pengguna untuk dengan cepat memfilter data dalam tabel pivot.

### Bisakah saya menambahkan beberapa pemotong ke tabel pivot?
Ya, Anda dapat menambahkan beberapa pemotong untuk memfilter bidang yang berbeda dalam tabel pivot.

### Apakah Aspose.Cells gratis untuk digunakan?
Aspose.Cells adalah pustaka berbayar, tetapi Anda dapat mencobanya secara gratis selama masa uji coba.

### Di mana saya dapat menemukan lebih banyak dokumentasi Aspose.Cells?
 Kunjungi[Dokumentasi Aspose.Cells](https://reference.aspose.com/cells/net/) untuk informasi lebih lanjut.

### Bagaimana saya bisa mendapatkan dukungan untuk Aspose.Cells?
 Anda dapat mencari bantuan di[Forum Aspose](https://forum.aspose.com/c/cells/9).