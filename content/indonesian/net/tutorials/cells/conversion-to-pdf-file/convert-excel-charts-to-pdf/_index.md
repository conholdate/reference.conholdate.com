---
title: Konversi Grafik Excel ke PDF Menggunakan Aspose.Cells untuk .NET
linktitle: Konversi Grafik Excel ke PDF Menggunakan Aspose.Cells untuk .NET
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mudah mengonversi grafik Excel ke format PDF dalam .NET menggunakan Aspose.Cells. Panduan langkah demi langkah kami mencakup prasyarat, penyiapan, contoh kode, dan Tanya Jawab Umum.
type: docs
weight: 11
url: /id/net/tutorials/cells/conversion-to-pdf-file/convert-excel-charts-to-pdf/
---
## Perkenalan

Apakah Anda memerlukan panduan untuk mengonversi grafik dari lembar kerja Excel ke format PDF dalam lingkungan .NET? Artikel ini adalah sumber daya lengkap Anda, yang mencakup setiap detail untuk membantu Anda menguasai proses dengan Aspose.Cells untuk .NET. Ikuti panduan terstruktur ini untuk mengonversi grafik Excel ke PDF berkualitas tinggi dengan mudah.

## Prasyarat

### Pengaturan Lingkungan .NET
Pastikan Anda telah menginstal .NET Framework atau .NET Core. Kedua lingkungan ini kompatibel dengan Aspose.Cells, sehingga Anda dapat menggunakan mana pun yang paling sesuai dengan proyek Anda.

### Instalasi Pustaka Aspose.Cells
 Pustaka Aspose.Cells sangat penting untuk konversi bagan ke PDF. Dapatkan versi terbaru dari[Halaman unduhan Aspose](https://releases.aspose.com/cells/net/).

### Pengetahuan Dasar C#
Memiliki pemahaman dasar tentang C# akan mempermudah proses pengodean. Jangan khawatir jika Anda seorang pemula; panduan ini menyertakan contoh kode yang mudah diikuti.

### Siapkan Visual Studio
Anda memerlukan Visual Studio atau IDE lain yang kompatibel. Siapkan IDE Anda untuk menangani aplikasi .NET, pastikan semuanya dikonfigurasi dengan benar untuk menulis dan menjalankan kode Anda tanpa masalah.

## Impor Paket yang Diperlukan dalam Proyek Anda

Setelah prasyarat terpenuhi, mulailah dengan mengimpor pustaka yang diperlukan ke dalam proyek Anda. Buka proyek Visual Studio Anda dan instal pustaka Aspose.Cells melalui NuGet:

1. Klik kanan proyek Anda di Solution Explorer.
2. Pilih Kelola Paket NuGet.
3. Cari Aspose.Cells dan klik Instal.

 Tambahkan yang berikut ini`using` direktif di awal file kode Anda:

```csharp
using System;
using System.IO;
using Aspose.Cells;
using Aspose.Cells.Charts;
```

Pustaka ini menyediakan kelas dan metode untuk menangani bagan Excel dan mengonversinya menjadi PDF.

## Langkah 1: Tentukan Direktori File

Mulailah dengan menentukan jalur ke direktori tempat dokumen Excel Anda disimpan. Ini memberi tahu Aspose.Cells tempat menemukan file .xls atau .xlsx yang berisi bagan Anda.

```csharp
// Tentukan jalur direktori
string dataDir = "Your Document Directory Path";
```

 Mengganti`"Your Document Directory Path"` dengan jalur sebenarnya ke berkas Anda.

## Langkah 2: Muat Buku Kerja Excel

Sekarang, muat berkas Excel yang berisi bagan yang ingin Anda konversi.

```csharp
// Memuat file Excel
Workbook workbook = new Workbook(dataDir + "Sample1.xls");
```

Pastikan jalur dan nama berkas sesuai dengan lokasi berkas Anda sebenarnya.

## Langkah 3: Akses Lembar Kerja dengan Bagan

Buku kerja Excel dapat berisi beberapa lembar, jadi tentukan lembar yang berisi bagan yang ingin Anda konversi.

```csharp
// Akses lembar kerja tertentu
Worksheet worksheet = workbook.Worksheets[0];
```

Kode ini mengakses lembar kerja pertama. Ubah indeks jika bagan Anda ada di lembar lain.

## Langkah 4: Pilih Bagan untuk Dikonversi

Berikutnya, akses bagan tertentu yang ingin Anda ubah dari lembar kerja yang dipilih.

```csharp
// Akses bagan pertama di lembar kerja
Chart chart = worksheet.Charts[0];
```

Kode ini memilih grafik pertama. Jika ada beberapa grafik, sesuaikan indeksnya.

## Langkah 5: Ubah Bagan ke PDF

Sekarang, mari ubah bagan yang dipilih menjadi berkas PDF.

```csharp
// Konversi grafik ke format PDF
chart.ToPdf(dataDir + "ChartOutput.pdf");
```

Perintah ini menginstruksikan Aspose.Cells untuk menyimpan bagan sebagai PDF di direktori yang ditentukan.

## Langkah 6: Simpan Bagan sebagai PDF di Aliran Memori (Opsional)

 Jika Anda ingin menyimpan grafik dalam`MemoryStream` alih-alih langsung ke berkas, gunakan kode berikut. Ini sangat berguna untuk aplikasi web atau saat Anda perlu menyajikan PDF secara dinamis.

```csharp
// Simpan grafik ke dalam aliran memori
MemoryStream pdfStream = new MemoryStream();
chart.ToPdf(pdfStream);
```

 Menggunakan`MemoryStream` memberi Anda fleksibilitas dalam menangani berkas PDF dalam aplikasi Anda.

## Kesimpulan

Mengonversi grafik Excel ke PDF dengan Aspose.Cells untuk .NET merupakan proses yang sederhana setelah Anda mengetahui langkah-langkahnya. Mulai dari menyiapkan lingkungan dan mengimpor pustaka yang diperlukan hingga mengonversi dan menyimpan file, setiap langkahnya mudah dan sederhana untuk diterapkan. Sekarang, Anda memiliki pengetahuan yang dibutuhkan untuk membuat file PDF dari grafik Excel secara efisien dalam aplikasi .NET Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Cells?

Aspose.Cells adalah pustaka .NET komprehensif yang dirancang untuk membuat, memanipulasi, dan mengonversi file Excel dalam berbagai format.

### Bisakah saya menggunakan Aspose.Cells tanpa lisensi?

 Ya, Anda dapat mencoba Aspose.Cells secara gratis menggunakan versi uji coba yang tersedia di[Situs web Aspose](https://releases.aspose.com/cells/net/).

### Apa yang harus saya lakukan jika saya menemui kesalahan selama konversi?

 Jika Anda mengalami masalah, periksa[Forum dukungan Aspose](https://forum.aspose.com/c/cells/9) untuk mendapatkan bantuan pemecahan masalah atau panduan dari pengguna lain.

### Apakah mungkin untuk mengonversi grafik ke format lain dengan Aspose.Cells?

Ya, Aspose.Cells mendukung berbagai format keluaran, termasuk gambar dan HTML, selain PDF.

### Bisakah saya mendapatkan lisensi untuk Aspose.Cells?

 Ya kamu bisa[membeli lisensi](https://purchase.conholdate.com/buy) untuk membuka kemampuan penuh Aspose.Cells.