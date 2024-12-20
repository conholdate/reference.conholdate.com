---
title: Membuat Hyperlink Lokal Dalam File PDF
linktitle: Membuat Hyperlink Lokal Dalam File PDF
second_title: Referensi API Aspose.PDF untuk .NET
description: Temukan cara meningkatkan navigasi dalam dokumen PDF Anda dengan membuat hyperlink lokal menggunakan Aspose.PDF untuk .NET. Tutorial langkah demi langkah ini memandu Anda melalui seluruh proses.
type: docs
weight: 40
url: /id/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Perkenalan

Dalam panduan ini, kami akan memandu Anda melalui proses pembuatan hyperlink lokal dalam file PDF menggunakan Aspose.PDF untuk .NET. Kami akan menguraikan setiap langkah dengan jelas, memastikan bahwa meskipun Anda baru dalam manipulasi PDF, Anda akan dapat mengikutinya dengan mudah.

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

1.  Visual Studio: Unduh dari[Situs web Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.PDF untuk .NET: Unduh pustaka melalui[Situs web Aspose](https://releases.aspose.com/pdf/net/)Pustaka ini menyediakan serangkaian fitur lengkap untuk manipulasi PDF.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu, tetapi jangan khawatir; kami akan menjelaskan kode baris demi baris.
4. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda. Periksa persyaratan di Aspose.PDF[dokumentasi](https://reference.aspose.com/pdf/net/).

Dengan prasyarat ini, Anda siap mempelajari cara membuat hyperlink lokal dalam dokumen PDF Anda!

## Mengimpor Paket yang Diperlukan

Sekarang setelah semuanya siap, saatnya mengimpor paket yang diperlukan ke proyek C# Anda.

### Buka Proyek Anda

Buka proyek .NET yang sudah ada atau buat yang baru di Visual Studio. Jika Anda memulai dari awal, pilih “Buat proyek baru” dari layar awal.

### Tambahkan Referensi ke Aspose.PDF

 Klik kanan pada "Dependencies" di folder proyek Anda di Solution Explorer. Pilih "Manage NuGet Packages," cari`Aspose.PDF`, dan instal versi terbaru yang tersedia. Ini akan menyediakan semua alat yang Anda butuhkan untuk membuat dan memanipulasi PDF.

### Mengimpor Ruang Nama

Di bagian atas file .cs Anda, tambahkan perintah penggunaan berikut:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Arahan ini memungkinkan Anda mengakses fitur perpustakaan dengan lancar.

Mari kita uraikan proses pembuatan hyperlink lokal ke dalam langkah-langkah sederhana.

## Langkah 1: Siapkan Instansi Dokumen

 Buat contoh baru dari`Document` kelas, yang mewakili berkas PDF yang akan Anda kerjakan.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Atur direktori dokumen Anda
Document doc = new Document(); //Buat contoh Dokumen
```

 Mengganti`"YOUR_DOCUMENT_DIRECTORY"` dengan jalur sebenarnya pada sistem Anda tempat PDF akan disimpan.

## Langkah 2: Tambahkan Halaman ke Dokumen

Berikutnya, tambahkan halaman ke dokumen PDF Anda.

```csharp
Page page = doc.Pages.Add(); // Tambahkan halaman baru
```

Baris ini menambahkan halaman baru ke dokumen, tempat semua konten Anda akan ditempatkan.

## Langkah 3: Buat Fragmen Teks

Sekarang, mari kita membuat sepotong teks yang akan berfungsi sebagai tautan yang dapat diklik.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Membuat fragmen teks
```

 Ini`TextFragment` akan menampilkan teks yang dapat diklik pengguna.

## Langkah 4: Buat Hyperlink Lokal

Sekarang, buat hyperlink lokal yang mengarah ke halaman 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Buat hyperlink lokal
link.TargetPageNumber = 7; // Tetapkan halaman target untuk tautan
text.Hyperlink = link; // Mengatur hyperlink untuk fragmen teks
```

 Itu`LocalHyperlink` kelas memungkinkan Anda menentukan nomor halaman target untuk hyperlink.

## Langkah 5: Tambahkan Fragmen Teks ke Halaman

Tambahkan teks yang dapat diklik ke halaman yang Anda buat.

```csharp
page.Paragraphs.Add(text); // Tambahkan fragmen teks ke halaman
```

Baris ini menambahkan teks Anda ke kumpulan paragraf halaman.

## Langkah 6: Buat Fragmen Teks Lain (Opsional)

Mari tambahkan hyperlink lain untuk menavigasi kembali ke halaman 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Buat fragmen teks baru
textBack.IsInNewPage = true; // Tunjukkan bahwa itu harus ada di halaman baru
```

## Langkah 7: Siapkan Hyperlink Lokal Kedua

Buat hyperlink lokal lain untuk halaman 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Buat hyperlink lokal lainnya
linkBack.TargetPageNumber = 1; // Tetapkan halaman target untuk hyperlink kedua
textBack.Hyperlink = linkBack; // Mengatur hyperlink untuk fragmen teks kedua
```

## Langkah 8: Tambahkan Fragmen Teks Kedua ke Halaman Baru

Tambahkan fragmen teks kedua ke halamannya.

```csharp
Page newPage = doc.Pages.Add(); // Tambahkan halaman baru untuk tautan kedua
newPage.Paragraphs.Add(textBack); // Tambahkan fragmen teks ke halaman baru
```

## Langkah 9: Simpan Dokumen

Terakhir, simpan dokumen Anda.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Tentukan nama file keluaran
doc.Save(dataDir); // Simpan dokumen yang diperbarui
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Baris ini menggabungkan jalur direktori Anda dengan nama file, dan`Save()` metode menyimpan dokumen Anda.

## Kesimpulan

Membuat hyperlink lokal dalam file PDF menggunakan Aspose.PDF untuk .NET merupakan fitur praktis yang meningkatkan navigasi dan pengalaman pengguna. Kini Anda memiliki pengetahuan untuk memandu pembaca secara langsung ke informasi yang mereka butuhkan, menjadikan PDF Anda lebih interaktif dan mudah digunakan.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.PDF untuk .NET?
Aspose.PDF untuk .NET adalah pustaka yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen PDF secara terprogram menggunakan kerangka kerja .NET.

### Bisakah saya membuat hyperlink ke halaman web eksternal?
Ya, Aspose.PDF juga mendukung pembuatan hyperlink ke URL eksternal selain hyperlink lokal dalam PDF.

### Apakah ada uji coba gratis untuk Aspose.PDF?
 Tentu saja! Anda dapat mengakses uji coba gratis dari[Situs web Aspose](https://releases.aspose.com/).

### Bahasa pemrograman apa yang didukung Aspose?
Aspose menawarkan pustaka untuk berbagai bahasa pemrograman, termasuk Java, CBahasa Indonesia: ++, dan Python, antara lain.

### Bagaimana cara mendapatkan dukungan untuk produk Aspose?
 Anda dapat mencari dukungan melalui[Forum Aspose](https://forum.aspose.com/c/pdf/10).