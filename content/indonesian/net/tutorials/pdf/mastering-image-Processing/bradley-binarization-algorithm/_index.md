---
title: Algoritma Binarisasi Bradley
linktitle: Algoritma Binarisasi Bradley
second_title: Referensi API Aspose.PDF untuk .NET
description: Pelajari cara mengonversi halaman PDF menjadi gambar TIFF biner berkualitas tinggi menggunakan algoritma binarisasi Bradley di Aspose.PDF untuk .NET. Panduan langkah demi langkah ini menyertakan contoh kode.
type: docs
weight: 30
url: /id/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Perkenalan

Dalam tutorial ini, kami akan memandu Anda melalui proses mengonversi halaman PDF menjadi gambar TIFF menggunakan Algoritma Binarisasi Bradley. Aspose.PDF untuk .NET menyederhanakan tugas ini, sehingga Anda dapat mengotomatiskan dan menyederhanakan alur kerja dokumen dengan mudah.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

-  Aspose.PDF untuk .NET: Unduh pustaka dari[Di Sini](https://releases.aspose.com/pdf/net/).
- Visual Studio (atau IDE C# apa pun).
- Pengetahuan dasar tentang C#.
-  Lisensi yang valid atau[lisensi sementara](https://purchase.aspose.com/temporary-license/) dari Aspose.

## Langkah 1: Siapkan Proyek Anda

Pertama, buat proyek C# baru di IDE Anda dan impor namespace yang diperlukan:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Langkah 2: Tentukan Direktori Dokumen

Tentukan jalur ke direktori tempat dokumen PDF Anda berada, serta jalur keluaran untuk gambar TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Jalur ke file PDF Anda
```

Direktori ini akan menyimpan file PDF sumber dan file TIFF yang dikonversi.

## Langkah 3: Muat Dokumen PDF

Buka dokumen PDF yang ingin Anda konversi:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Mengganti`PageToTIFF.pdf` dengan nama berkas PDF Anda.

## Langkah 4: Tentukan Jalur Output

Tentukan jalur keluaran untuk file TIFF yang dihasilkan:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Langkah 5: Atur Resolusi Gambar

Atur resolusi untuk gambar TIFF. DPI yang lebih tinggi akan menghasilkan kualitas gambar yang lebih baik:

```csharp
Resolution resolution = new Resolution(300);
```

## Langkah 6: Konfigurasikan Pengaturan TIFF

Konfigurasikan pengaturan untuk gambar TIFF, termasuk kompresi dan kedalaman warna:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Menggunakan 1bpp (1-bit per piksel) mempersiapkan gambar untuk keluaran biner.

## Langkah 7: Buat Perangkat TIFF

Buat perangkat TIFF yang akan menangani konversi:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Langkah 8: Ubah Halaman PDF ke TIFF

Ubah halaman pertama PDF menjadi gambar TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Langkah 9: Terapkan Algoritma Binarisasi Bradley

Sekarang, terapkan Algoritma Bradley untuk mengubah gambar TIFF skala abu-abu menjadi gambar biner:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 Itu`BinarizeBradley` Metode ini mengambil dua aliran file (input dan output) dan nilai ambang batas. Sesuaikan ambang batas sesuai kebutuhan untuk hasil yang optimal.

## Langkah 10: Konfirmasikan Konversi Berhasil

Terakhir, konfirmasikan bahwa konversi berhasil:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Kesimpulan

Selamat! Anda telah berhasil mengonversi halaman PDF menjadi gambar TIFF dan menerapkan Algoritma Binarisasi Bradley menggunakan Aspose.PDF untuk .NET. Proses ini penting untuk pengarsipan dokumen, OCR, dan aplikasi profesional lainnya. Dengan resolusi berkualitas tinggi dan kompresi yang efisien, gambar dokumen Anda akan jernih dan ukurannya mudah diatur.

## Pertanyaan yang Sering Diajukan

### Apa itu Algoritma Bradley?
Algoritma Bradley adalah teknik binarisasi yang mengubah gambar skala abu-abu menjadi gambar biner dengan menentukan ambang batas adaptif untuk setiap piksel berdasarkan lingkungannya.

### Bisakah saya mengonversi beberapa halaman PDF ke TIFF menggunakan metode ini?
 Ya, Anda dapat memodifikasi`Process` metode untuk mengulang semua halaman dalam dokumen untuk konversi.

### Berapa resolusi optimal untuk mengonversi PDF ke TIFF?
Resolusi 300 DPI umumnya direkomendasikan untuk gambar berkualitas tinggi, tetapi Anda dapat menyesuaikannya berdasarkan kebutuhan spesifik Anda.

### Apa arti 1bpp dalam kedalaman warna?
1bpp (1 bit per piksel) menunjukkan bahwa gambar akan berwarna hitam dan putih, dengan setiap piksel sepenuhnya hitam atau sepenuhnya putih.

### Apakah Algoritma Bradley cocok untuk OCR?
Ya, Algoritma Bradley sering digunakan dalam praproses OCR karena meningkatkan kontras teks dalam dokumen yang dipindai, sehingga meningkatkan akurasi pengenalan.