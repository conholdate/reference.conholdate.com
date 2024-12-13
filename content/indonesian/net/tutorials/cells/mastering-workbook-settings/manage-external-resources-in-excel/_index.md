---
title: Kelola Sumber Daya Eksternal di Excel dengan Aspose.Cells untuk .NET
linktitle: Kelola Sumber Daya Eksternal di Excel dengan Aspose.Cells untuk .NET
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Temukan cara mengontrol sumber daya eksternal di buku kerja Excel dengan mudah menggunakan Aspose.Cells untuk .NET. Panduan lengkap ini memandu Anda melalui setiap langkah—mulai dari penerapan penyedia aliran kustom hingga merender lembar kerja.
type: docs
weight: 10
url: /id/net/tutorials/cells/mastering-workbook-settings/manage-external-resources-in-excel/
---
## Perkenalan

Saat bekerja dengan data di Excel, mengelola sumber daya eksternal dengan lancar dapat meningkatkan fungsionalitas aplikasi Anda secara signifikan. Jika Anda ingin mengontrol gambar dan elemen eksternal lainnya di buku kerja Excel menggunakan Aspose.Cells for .NET, Anda berada di tempat yang tepat! Panduan ini akan memandu Anda melalui proses ini langkah demi langkah, sehingga Anda dapat menerapkan solusi khusus untuk menangani sumber daya ini dengan mudah.

## Prasyarat

Sebelum kita menyelami aspek pengkodean, pastikan Anda telah menyiapkan hal berikut:

1. Visual Studio: IDE untuk menulis dan menguji aplikasi .NET Anda. Visual Studio direkomendasikan karena dukungannya yang luas dan antarmuka yang mudah digunakan.
2.  Aspose.Cells untuk .NET: Unduh pustaka dari[Halaman rilis Aspose Cells](https://releases.aspose.com/cells/net/).
3. Pengetahuan Dasar C#: Keakraban dengan konsep C# dan .NET akan membantu Anda memahami implementasinya dengan lebih baik.
4. Siapkan Proyek Anda: Pastikan proyek Anda merujuk ke pustaka Aspose.Cells, yang dapat Anda tambahkan melalui NuGet Package Manager di Visual Studio.
5. File Contoh: Siapkan file Excel contoh yang berisi sumber daya eksternal (misalnya, gambar tertaut) untuk tujuan demonstrasi.

Setelah Anda memiliki semua prasyarat ini, mari mulai mengelola sumber daya eksternal dengan Aspose.Cells.

## Paket Impor
Untuk memulai pengkodean, Anda perlu mengimpor paket yang diperlukan ke dalam berkas C# Anda. Berikut ini yang Anda perlukan:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

## Langkah 1: Tentukan Direktori

Pertama, tentukan direktori sumber dan keluaran tempat file Anda disimpan dan tempat Anda ingin file keluaran Anda disimpan.

```csharp
// Tentukan direktori sumber
static string sourceDir = @"C:\Path\To\Your\Documents\"; // Sesuaikan jalur
// Tentukan direktori keluaran
static string outputDir = @"C:\Path\To\Your\Output\";
```

Pastikan untuk mengganti jalur dengan direktori sebenarnya di komputer Anda.

### Langkah 2: Terapkan Antarmuka IStreamProvider

 Selanjutnya, buat kelas khusus yang mengimplementasikan`IStreamProvider` antarmuka. Kelas ini akan mengelola cara mengakses sumber daya eksternal seperti gambar.

```csharp
class CustomStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        // Bersihkan sumber daya jika perlu
        options.Stream?.Close();
    }

    public void InitStream(StreamProviderOptions options)
    {
        // Buka aliran file untuk sumber daya eksternal
        options.Stream = new FileStream(Path.Combine(sourceDir, "image.png"), FileMode.Open, FileAccess.Read);
    }
}
```

 Di dalam`InitStream` metode, kami membuka file yang berfungsi sebagai sumber daya eksternal Anda dan menetapkannya ke`Stream` milik.

### Langkah 3: Muat File Excel

Sekarang, mari muat buku kerja Excel yang menyertakan sumber daya eksternal.

```csharp
public static void Execute()
{
    // Memuat file Excel
    Workbook workbook = new Workbook(Path.Combine(sourceDir, "sample.xlsx"));
    
    // Tetapkan penyedia aliran kustom
    workbook.Settings.StreamProvider = new CustomStreamProvider();
```

Cuplikan ini memuat berkas Excel Anda dan menetapkan penyedia aliran kustom untuk menangani sumber daya eksternal.

### Langkah 4: Akses Lembar Kerja

Setelah memuat buku kerja, akses lembar kerja yang diinginkan dengan mudah.

```csharp
    // Akses lembar kerja pertama
    Worksheet worksheet = workbook.Worksheets[0];
```

Anda dapat mengakses lembar kerja apa pun dengan menentukan indeksnya.

### Langkah 5: Konfigurasikan Opsi Gambar dan Cetak

Tentukan bagaimana Anda ingin gambar keluaran terlihat dengan mengonfigurasi opsi gambar atau cetak.

```csharp
    // Tentukan pilihan gambar atau cetak
    ImageOrPrintOptions options = new ImageOrPrintOptions
    {
        OnePagePerSheet = true,
        ImageType = Drawing.ImageType.Png
    };
```

Memilih PNG memastikan hasil yang tajam dan jelas.

### Langkah 6: Render Lembar Kerja ke Gambar

Sekarang tibalah pada bagian yang menarik — merender lembar kerja ke dalam berkas gambar!

```csharp
    // Buat render lembar dan ubah lembar kerja menjadi gambar
    SheetRender sheetRender = new SheetRender(worksheet, options);
    sheetRender.ToImage(0, Path.Combine(outputDir, "output.png"));
    
    Console.WriteLine("Excel sheet rendered successfully to an image!");
}
```

Kode ini mengubah seluruh lembar kerja menjadi gambar PNG, yang akan disimpan ke direktori keluaran yang Anda tentukan.

## Kesimpulan

Selamat! Kini Anda telah mempelajari cara mengontrol sumber daya eksternal dalam file Excel menggunakan Aspose.Cells for .NET. Fungsionalitas ini tidak hanya meningkatkan kemampuan aplikasi Anda, tetapi juga menyederhanakan cara Anda mengelola kumpulan data dan presentasi. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat mengadaptasi solusi ini agar sesuai dengan persyaratan unik proyek Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Cells?
Aspose.Cells adalah pustaka tangguh yang dirancang bagi pengembang .NET untuk membuat, memanipulasi, dan mengelola file Excel tanpa memerlukan Microsoft Excel.

### Bagaimana cara mengunduh Aspose.Cells untuk .NET?
 Anda dapat mengunduhnya dari[Situs web Aspose](https://releases.aspose.com/cells/net/).

### Apakah ada uji coba gratis yang tersedia?
 Ya! Aspose menawarkan uji coba Aspose.Cells gratis, tersedia di situs web mereka[halaman rilis](https://releases.aspose.com/cells/net/).

### Jenis file apa yang didukung Aspose.Cells?
Aspose.Cells mendukung berbagai format Excel, termasuk XLS, XLSX, CSV, dan banyak lagi.

### Di mana saya dapat menemukan dukungan untuk Aspose.Cells?
 Kunjungi[Forum Aspose](https://forum.aspose.com/c/cells/9) untuk bantuan dan dukungan masyarakat.