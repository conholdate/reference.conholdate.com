---
title: Konversi Excel ke PDF Menggunakan Aspose.Cells di .NET
linktitle: Konversi Excel ke PDF Menggunakan Aspose.Cells di .NET
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Konversi file Excel ke PDF dalam format .NET dengan mudah menggunakan Aspose.Cells. Panduan langkah demi langkah ini menyediakan cuplikan kode, kiat pengaturan, dan FAQ pemecahan masalah bagi pengembang .NET.
type: docs
weight: 10
url: /id/net/tutorials/cells/conversion-to-pdf-file/convert-excel-to-pdf/
---
## Perkenalan

Bagi pengembang .NET dan bisnis yang bekerja secara ekstensif dengan file Excel, mengonversi lembar kerja ke PDF sangat penting untuk memastikan pembagian yang aman dan menjaga format data. File PDF menjaga integritas dokumen di berbagai perangkat dan platform, menjadikannya ideal untuk laporan bisnis, analitik, dan kebutuhan pengarsipan. Dengan Aspose.Cells untuk .NET, pengembang dapat mengonversi file Excel ke PDF dengan lancar sambil mempertahankan format, gaya, dan integritas visual. Dalam panduan ini, kami akan membahas semua langkah yang diperlukan untuk mengonversi lembar kerja Excel menjadi dokumen PDF yang disempurnakan menggunakan Aspose.Cells untuk .NET.

## Prasyarat

### Lingkungan Pengembangan .NET
- Visual Studio: Pastikan Visual Studio (versi terbaru) diinstal untuk pengalaman pengkodean yang efisien.
- .NET Framework: Kode dalam panduan ini memerlukan .NET Framework 4.0 atau yang lebih tinggi.

### Pustaka Aspose.Cells untuk .NET
-  Unduh Aspose.Cells: Dapatkan versi terbaru Aspose.Cells untuk .NET[Di Sini](https://releases.aspose.com/cells/net/).
- Lisensi Uji Coba: Jika Anda menguji pustaka, Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.conholdate.com/temporary-license/).

Dengan prasyarat ini, Anda siap untuk mulai mengubah file Excel Anda menjadi PDF menggunakan Aspose.Cells!

## Menyiapkan Proyek

Mari kita mulai dengan mengonfigurasi lingkungan pengembangan untuk mengaktifkan fungsionalitas Aspose.Cells.

### Membuat Proyek .NET Baru
1. Buka Visual Studio dan pilih “Buat proyek baru.”
2. Pilih templat Aplikasi Konsol (.NET Framework).
3. Beri nama proyek Anda, misalnya, "ExcelToPDFConverter," dan atur kerangka kerjanya ke .NET 4.0 atau lebih tinggi.

### Menambahkan Aspose.Cells ke Proyek
1. Klik kanan proyek Anda di Solution Explorer dan pilih Kelola Paket NuGet.
2. Di NuGet Package Manager, cari "Aspose.Cells" dan instal untuk menambahkannya ke proyek Anda.

### Mengimpor Ruang Nama yang Diperlukan
 Di dalam kamu`Program.cs`, tambahkan namespace berikut untuk mengakses fungsionalitas Aspose.Cells:
```csharp
using System.IO;
using Aspose.Cells;
```

Dengan pengaturan ini, Anda sekarang siap untuk memulai proses pengkodean.

Ikuti langkah-langkah ini untuk mengonversi berkas Excel ke dokumen PDF, dengan tetap mempertahankan format aslinya.

## Langkah 1: Tentukan Jalur File
Atur jalur ke direktori tempat file Excel Anda disimpan dan tempat Anda ingin menyimpan keluaran PDF.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "Your Document Directory";
```

 Mengganti`"C:\ExcelFiles\"` dengan jalur direktori pada sistem Anda.

## Langkah 2: Muat File Excel ke Objek Buku Kerja
Buat objek Workbook baru dengan memuat file Excel Anda. Objek Workbook ini akan menampung data dan format spreadsheet Anda.

```csharp
// Buat instance objek Buku Kerja untuk membuka file Excel
Workbook workbook = new Workbook(dataDir + "sample.xlsx");
```

 Memastikan`sample.xlsx` ada di dalam kamu`dataDir`.

## Langkah 3: Konversi dan Simpan Excel sebagai PDF
Simpan Buku Kerja sebagai PDF, tentukan jalur file dan opsi penyimpanan.

```csharp
// Simpan buku kerja ke format PDF
workbook.Save(dataDir + "Output.pdf", pdfOptions);
```

 Kode di atas mengonversi`sample.xlsx` berkas ke`Output.pdf` di direktori yang ditentukan, menerapkan opsi yang Anda tetapkan sebelumnya.

## Langkah 4: Konfirmasi Penyelesaian
Setelah konversi, cetak pesan yang menunjukkan bahwa PDF telah berhasil dibuat.

```csharp
// Beritahu pengguna tentang penyelesaiannya
Console.WriteLine("Excel to PDF conversion completed successfully.");
```

## Kesimpulan

Dengan Aspose.Cells untuk .NET, mengubah lembar kerja Excel menjadi dokumen PDF menjadi proses yang efisien, yang memungkinkan pengembang untuk menjaga kualitas dan integritas data mereka. Aspose.Cells adalah pustaka tangguh yang menawarkan opsi penyesuaian yang luas, yang memungkinkan pengembang untuk membuat dokumen PDF yang disesuaikan yang memenuhi kebutuhan bisnis yang tepat.

## Pertanyaan yang Sering Diajukan

### Versi .NET mana yang didukung Aspose.Cells?
Aspose.Cells mendukung .NET Framework 4.0 dan yang lebih tinggi, termasuk .NET Core dan .NET 5/6.

### Bisakah saya mengonversi beberapa file Excel sekaligus?
Ya, dengan melakukan pengulangan melalui daftar jalur file, Anda dapat mengonversi beberapa file Excel ke PDF secara batch.

### Apakah ada versi gratis Aspose.Cells?
 Ya, versi uji coba gratis tersedia untuk evaluasi, yang dapat Anda[unduh disini](https://releases.aspose.com/cells/net/).

### Bisakah saya menentukan lembar kerja tertentu untuk dikonversi?
 Ya, dengan pengaturan`OnePagePerSheet` di dalam`PdfSaveOptions`Anda dapat mengonversi lembar tertentu pada halaman tunggal dalam PDF.

### Di mana saya dapat menemukan dokumentasi lebih lanjut untuk Aspose.Cells?
 Kunjungi[Dokumentasi Aspose.Cells](https://reference.aspose.com/cells/net/) untuk panduan terperinci dan contoh kode. 