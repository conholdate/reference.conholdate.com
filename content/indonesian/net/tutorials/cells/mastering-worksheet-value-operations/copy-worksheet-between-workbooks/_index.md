---
title: Menyalin Lembar Kerja Antar Buku Kerja Excel menggunakan Aspose.Cells
linktitle: Menyalin Lembar Kerja Antar Buku Kerja Excel menggunakan Aspose.Cells
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mentransfer data antar-workbook Excel di aplikasi .NET Anda dengan mudah menggunakan Aspose.Cells. Tutorial komprehensif ini memandu Anda melalui setiap langkah penyalinan worksheet.
type: docs
weight: 13
url: /id/net/tutorials/cells/mastering-worksheet-value-operations/copy-worksheet-between-workbooks/
---
## Perkenalan

Mentransfer data antar workbook Excel merupakan tugas umum dalam aplikasi .NET, terutama untuk membuat laporan atau mengelola templat. Untungnya, menggunakan Aspose.Cells for .NET membuat proses ini mudah dan efisien. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk menyalin lembar kerja dari satu workbook ke workbook lain, memberi Anda kendali penuh atas pengelolaan data Anda.

## Prasyarat

Sebelum kita memulai, pastikan Anda memiliki alat berikut:

1.  Pustaka Aspose.Cells untuk .NET: Unduh pustakanya[Di Sini](https://releases.aspose.com/cells/net/).
2. Visual Studio atau IDE Serupa: Anda akan menggunakan ini untuk menulis dan mengeksekusi kode .NET Anda.
3.  Aspose Lisensi: Untuk melewati batasan evaluasi, Anda dapat[ajukan permohonan uji coba gratis](https://releases.aspose.com/) atau mendapatkan[lisensi sementara](https://purchase.aspose.com/temporary-license/).

## Paket Impor

Mulailah dengan mengimpor namespace yang diperlukan ke dalam proyek Anda:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Ruang nama ini akan memberi Anda akses ke kelas-kelas yang dibutuhkan untuk memanipulasi buku kerja dan lembar kerja Excel secara efektif.

## Langkah 1: Tetapkan Jalur Direktori

Pertama, tentukan direktori untuk menyimpan buku kerja Excel Anda. Ini akan menyederhanakan akses file nantinya.

```csharp
// Tetapkan jalur ke direktori dokumen Anda.
string dataDir = "Your Document Directory";
```
 Mengganti`"Your Document Directory"` dengan jalur Anda yang sebenarnya.

## Langkah 2: Buat Buku Kerja Pertama

Mari membuat buku kerja baru dan menambahkan lembar kerja ke dalamnya.

```csharp
// Buat Buku Kerja baru.
Workbook excelWorkbook0 = new Workbook();
// Akses lembar kerja pertama dalam buku kerja.
Worksheet ws0 = excelWorkbook0.Worksheets[0];
```

## Langkah 3: Tambahkan Data Header

Isi lembar kerja dengan baris tajuk untuk mewakili himpunan data Anda dengan jelas.

```csharp
// Mengisi baris header (A1:A4).
for (int i = 0; i < 5; i++)
{
    ws0.Cells[i, 0].PutValue($"Header Row {i}");
}
```

## Langkah 4: Mengisi Baris Data Detail

Tambahkan konten terperinci untuk menyediakan konteks bagi lembar kerja Anda.

```csharp
// Isi baris detail (A5:A999).
for (int i = 5; i < 1000; i++)
{
    ws0.Cells[i, 0].PutValue($"Detail Row {i}");
}
```

## Langkah 5: Konfigurasikan Pengaturan Pencetakan

Siapkan konfigurasi halaman untuk mengulang baris tajuk pada halaman cetak, yang sangat berguna untuk laporan besar.

```csharp
// Konfigurasikan pengaturan halaman untuk mengulang baris tajuk pada setiap halaman.
PageSetup pageSetup = ws0.PageSetup;
pageSetup.PrintTitleRows = "$1:$5";
```

## Langkah 6: Buat Buku Kerja Kedua

Berikutnya, buat buku kerja kedua yang akan menerima lembar kerja yang disalin.

```csharp
// Buat Buku Kerja lainnya.
Workbook excelWorkbook1 = new Workbook();
// Akses lembar kerja pertama dalam buku kerja.
Worksheet ws1 = excelWorkbook1.Worksheets[0];
```

## Langkah 7: Ubah Nama Lembar Kerja Tujuan

Ganti nama lembar kerja di buku kerja kedua untuk memudahkan identifikasi.

```csharp
// Ubah nama lembar kerja.
ws1.Name = "MySheet";
```

## Langkah 8: Salin Data ke Lembar Kerja Tujuan

 Memanfaatkan`Copy` metode untuk memindahkan seluruh lembar kerja dari buku kerja pertama ke buku kerja kedua.

```csharp
//Salin data dari lembar kerja pertama buku kerja pertama ke lembar kerja pertama buku kerja kedua.
ws1.Copy(ws0);
```

## Langkah 9: Simpan Buku Kerja Akhir

Terakhir, simpan buku kerja yang telah dimodifikasi.

```csharp
// Simpan buku kerja kedua.
excelWorkbook1.Save(dataDir + "CopyWorksheetFromWorkbookToOther_out.xls");
```

## Kesimpulan

Nah, itu dia! Anda dapat dengan mudah menyalin lembar kerja dari satu buku kerja ke buku kerja lain menggunakan Aspose.Cells for .NET. Metode ini ideal untuk kumpulan data besar, pembuatan templat, dan pembuatan laporan. 

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyalin beberapa lembar kerja sekaligus?  
Ya, Anda dapat mengulangi beberapa lembar kerja dan menyalinnya satu per satu ke buku kerja lain.

### Apakah Aspose.Cells mempertahankan format selama penyalinan?  
 Tentu saja!`Copy` metode mempertahankan semua format dan gaya.

### Bagaimana saya dapat mengakses sel tertentu dalam lembar kerja yang disalin?  
 Anda dapat mengakses sel tertentu menggunakan`Cells` properti dalam lembar kerja.

### Bagaimana jika saya hanya ingin menyalin nilai tanpa memformat?  
Anda dapat menerapkan metode khusus untuk menyalin nilai sel demi sel jika diinginkan.

### Bisakah saya menguji fitur ini tanpa lisensi?  
 Ya, Aspose menawarkan[uji coba gratis](https://releases.aspose.com/) untuk menjelajahi fitur-fiturnya.