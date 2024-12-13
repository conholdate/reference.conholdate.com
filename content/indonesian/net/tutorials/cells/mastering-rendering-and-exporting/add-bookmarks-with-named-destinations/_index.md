---
title: Tambahkan Bookmark dengan Tujuan Bernama dalam PDF dari File Excel
linktitle: Tambahkan Bookmark dengan Tujuan Bernama dalam PDF dari File Excel
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mudah membuat PDF interaktif dari file Excel menggunakan Aspose.Cells for .NET. Tutorial ini membahas penambahan bookmark dengan tujuan bernama untuk meningkatkan navigasi PDF.
type: docs
weight: 10
url: /id/net/tutorials/cells/mastering-rendering-and-exporting/add-bookmarks-with-named-destinations/
---
## Perkenalan

Menjelajahi berkas PDF yang besar sering kali terasa seperti mencari jarum dalam tumpukan jerami, terutama jika berkas tersebut dibuat dari lembar kerja Excel yang banyak. Bookmark dalam dokumen PDF menawarkan cara yang mudah untuk berpindah di antara bagian-bagian yang relevan dari suatu berkas, sehingga meningkatkan pengalaman pengguna. Panduan terperinci ini akan memandu Anda melalui proses penambahan bookmark dengan tujuan yang diberi nama ke PDF yang dibuat dari berkas Excel menggunakan Aspose.Cells for .NET.

## Prasyarat untuk Bekerja dengan Aspose.Cells untuk .NET

Sebelum kita menyelami kodenya, penting untuk memastikan bahwa Anda telah menyiapkan semua alat untuk implementasi yang berhasil. Berikut ini adalah prasyaratnya:

1. Visual Studio: IDE yang direkomendasikan untuk pengembangan .NET. Pastikan IDE tersebut terinstal dan dikonfigurasi dengan benar di sistem Anda.
2.  Aspose.Cells untuk .NET: Pustaka inti yang diperlukan untuk memanipulasi file Excel secara terprogram. Anda dapat[unduh disini](https://releases.aspose.com/cells/net/) Jika Anda baru mengenal Aspose, Anda dapat memulai dengan[uji coba gratis](https://releases.aspose.com/).
3. .NET Framework: Pastikan Anda menggunakan versi .NET Framework yang kompatibel. Aspose.Cells mendukung beberapa versi.
4. Pengetahuan Dasar C#: Pemahaman mendasar tentang C# akan membantu dalam mengikuti kode.

Dengan komponen-komponen ini, Anda siap untuk mulai membuat dokumen PDF dengan penanda buku!

## Menyiapkan Proyek Anda

Setelah lingkungan pengembangan Anda siap, Anda dapat melanjutkan untuk membuat proyek C# baru di Visual Studio. Agar dapat bekerja dengan fungsi Aspose.Cells, Anda perlu mengimpor namespace yang diperlukan.

## Mengimpor Ruang Nama yang Diperlukan

Di bagian atas file C# Anda, tambahkan yang berikut ini`using` pernyataan untuk memastikan bahwa proyek Anda dapat mengakses Aspose.Cells untuk .NET:

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

Ruang nama ini menyediakan akses ke kelas-kelas penting yang akan membantu Anda memanipulasi data Excel dan mengubahnya menjadi PDF.

## Langkah 1: Menyiapkan Direktori untuk File Input dan Output

Langkah pertama adalah menentukan direktori file input dan output. Ini memastikan bahwa file Excel sumber dan file PDF yang dihasilkan berada di lokasi yang tepat.

```csharp
string sourceDir = "Your Document Directory";  // Jalur ke file Excel Anda
string outputDir = "Your Document Directory"; // Jalur tempat menyimpan PDF keluaran
```

Hal ini mirip dengan menata ruang kerja Anda sebelum memulai suatu proyek.

## Langkah 2: Memuat Buku Kerja Excel

 Langkah selanjutnya adalah memuat file Excel sumber Anda. Aspose.Cells memungkinkan Anda memuat file Excel dengan mudah ke dalam`Workbook` objek, menyediakan akses ke semua lembar, sel, dan kontennya.

```csharp
Workbook wb = new Workbook(sourceDir + "sampleExcelFile.xlsx");
```

Ini akan membuka buku kerja dan mempersiapkannya untuk manipulasi. Anda sekarang dapat mulai mengekstrak data dan memformatnya untuk PDF.

## Langkah 3: Mengakses Lembar Kerja

Setelah buku kerja dimuat, saatnya mengakses lembar kerja tempat sel-sel terkait untuk penanda buku berada. Dalam contoh ini, kita akan bekerja dengan lembar kerja pertama:

```csharp
Worksheet ws = wb.Worksheets[0]; // Mengakses lembar kerja pertama
```

Langkah ini membuat kanvas untuk bookmark Anda. Setiap sel yang akan Anda rujuk untuk bookmark akan berasal dari lembar kerja ini.

## Langkah 4: Membuat Bookmark dengan Tujuan Bernama

Pada titik ini, kita dapat mulai membuat bookmark. Bookmark pada dasarnya adalah tautan yang menyediakan akses cepat ke area tertentu di dokumen Anda. Dalam contoh ini, kita akan membuat bookmark untuk sel "C5".

### Membuat Bookmark untuk Sel Tunggal

 Untuk membuat bookmark, Anda harus mengakses sel yang ingin Anda tautkan terlebih dahulu. Setelah itu, Anda akan membuat bookmark.`PdfBookmarkEntry` dan mengaitkannya dengan posisi sel.

```csharp
Cell cell = ws.Cells["C5"];
PdfBookmarkEntry bookmarkEntry = new PdfBookmarkEntry();
bookmarkEntry.Text = "Bookmark for C5"; // Teks untuk penanda buku
bookmarkEntry.Destination = cell;  // Menghubungkan penanda ke sel
bookmarkEntry.DestinationName = "AsposeCells--" + cell.Name; // Nama tujuan yang unik
```

Anggap saja ini sebagai penandaan titik dalam dokumen yang dapat Anda kunjungi kembali dengan satu klik. Anda dapat menetapkan teks apa pun ke penanda (seperti "Penanda untuk C5") dan menautkannya ke sel tertentu.

### Menambahkan Sub-Bookmark untuk Navigasi yang Lebih Baik

Anda dapat meningkatkan pengalaman pengguna dengan menambahkan sub-bookmark yang bercabang dari bookmark utama. Sub-bookmark ini dapat mengarah ke area berbeda dalam lembar kerja yang sama atau ke lembar lain.

```csharp
cell = ws.Cells["G56"];
PdfBookmarkEntry subbookmarkEntry1 = new PdfBookmarkEntry();
subbookmarkEntry1.Text = "Sub-Bookmark 1"; // Teks untuk sub-bookmark pertama
subbookmarkEntry1.Destination = cell;
subbookmarkEntry1.DestinationName = "AsposeCells--" + cell.Name;

cell = ws.Cells["L4"];
PdfBookmarkEntry subbookmarkEntry2 = new PdfBookmarkEntry();
subbookmarkEntry2.Text = "Sub-Bookmark 2"; // Teks untuk sub-bookmark kedua
subbookmarkEntry2.Destination = cell;
subbookmarkEntry2.DestinationName = "AsposeCells--" + cell.Name;
```

Sub-bookmark ini berfungsi sebagai penunjuk tambahan untuk menavigasi dokumen, seperti bab-bab dalam sebuah buku.

### Pengelompokan Sub-Bookmark di Bawah Bookmark Utama

Untuk membuat struktur hierarki, Anda dapat menambahkan sub-bookmark ini di bawah bookmark utama. Ini memudahkan pengguna untuk menavigasi ke berbagai bagian.

```csharp
ArrayList list = new ArrayList();
list.Add(subbookmarkEntry1);
list.Add(subbookmarkEntry2);
bookmarkEntry.SubEntry = list; // Menambahkan sub-bookmark ke bookmark utama
```

Ini menciptakan struktur seperti pohon di mana setiap penanda buku dapat memiliki beberapa sub-penanda buku.

## Langkah 5: Menyimpan PDF dengan Bookmark

### Mengatur Opsi Penyimpanan PDF

 Sebelum menyimpan dokumen sebagai PDF, kita perlu menentukan opsi penyimpanan dan memastikan bahwa penanda disertakan. Kita akan menggunakan`PdfSaveOptions` untuk tujuan ini.

```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = bookmarkEntry;  // Menetapkan penanda ke PDF
```

Ini memberitahu Aspose.Cells untuk membuat PDF yang menyertakan bookmark yang baru saja kita buat.

### Menyimpan Dokumen

Sekarang penanda buku telah ditetapkan, kita dapat menyimpan buku kerja sebagai PDF.

```csharp
wb.Save(outputDir + "outputWithBookmarks.pdf", opts);
```

Ini menghasilkan PDF final dengan penanda yang dapat diklik, yang memungkinkan pengguna untuk dengan cepat melompat ke bagian tertentu dari dokumen.

## Kesimpulan

Dengan mengikuti langkah-langkah sederhana ini, Anda telah berhasil membuat PDF dengan penanda dan tujuan bernama dari file Excel menggunakan Aspose.Cells untuk .NET. Kemampuan untuk menambahkan penanda tidak hanya meningkatkan pengalaman pengguna tetapi juga membuat navigasi dalam dokumen besar jauh lebih efisien. Baik Anda sedang mengerjakan laporan, panduan, atau presentasi, penanda bagian-bagian penting akan membantu pembaca Anda mendapatkan hasil maksimal dari dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Cells untuk .NET?
Aspose.Cells untuk .NET adalah API yang hebat untuk bekerja dengan file Excel, yang memungkinkan Anda membuat, mengedit, dan mengonversi dokumen Excel secara terprogram. Anda dapat memanipulasi data, bagan, dan pemformatan dengan mudah menggunakan alat ini.

### Bagaimana saya bisa mendapatkan uji coba gratis Aspose.Cells untuk .NET?
 Anda dapat mengunduh versi uji coba gratis Aspose.Cells untuk .NET dari[Di Sini](https://releases.aspose.com/).

### Format file apa yang dapat digunakan Aspose.Cells?
Aspose.Cells mendukung berbagai format file, termasuk XLSX, XLS, CSV, PDF, dan banyak lainnya.

### Bisakah saya mengotomatiskan proses pembuatan penanda buku dalam PDF?
Ya! Proses ini dapat diotomatisasi sepenuhnya dengan mengintegrasikan Aspose.Cells ke dalam aplikasi Anda, yang memungkinkan Anda untuk secara dinamis membuat PDF berbasis Excel dengan bookmark sebagai bagian dari alur kerja Anda.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Cells untuk .NET?
 Anda dapat mengunjungi[Forum Aspose](https://forum.aspose.com/c/cells/9) untuk mengajukan pertanyaan atau melaporkan masalah.