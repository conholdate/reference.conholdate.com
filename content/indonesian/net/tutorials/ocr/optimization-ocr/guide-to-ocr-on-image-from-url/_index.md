---
title: Panduan OCR pada Gambar dari URL dalam Pengenalan Gambar OCR
linktitle: Panduan OCR pada Gambar dari URL dalam Pengenalan Gambar OCR
second_title: API Aspose.OCR .NET
description: Temukan cara mudah menerapkan Optical Character Recognition (OCR) di aplikasi .NET Anda menggunakan Aspose.OCR. Panduan langkah demi langkah ini akan memandu Anda melalui seluruh proses.
type: docs
weight: 10
url: /id/net/tutorials/ocr/optimization-ocr/guide-to-ocr-on-image-from-url/
---
## Perkenalan

Pengenalan Karakter Optik (OCR) merupakan teknologi penting untuk mengekstrak teks dari gambar, yang memungkinkan pengembang untuk membuat aplikasi yang dapat membaca dan memproses informasi tekstual dengan lancar. Aspose.OCR untuk .NET merupakan pustaka tangguh yang dirancang untuk menyederhanakan integrasi kemampuan OCR ke dalam aplikasi .NET Anda. Panduan ini akan mengilustrasikan cara melakukan OCR pada gambar langsung dari URL hanya dalam beberapa langkah sederhana.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki prasyarat berikut:

-  Aspose.OCR untuk .NET: Unduh dan integrasikan pustaka Aspose.OCR ke dalam proyek .NET Anda dari[halaman rilis](https://releases.aspose.com/ocr/net/).
- Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET di komputer Anda (Visual Studio direkomendasikan).

## Langkah 1: Impor Namespace yang Diperlukan

Untuk memanfaatkan fitur yang ditawarkan oleh Aspose.OCR, impor namespace yang diperlukan dalam proyek Anda:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
using Aspose.OCR.Models;
```

## Langkah 2: Tentukan Direktori Dokumen

 Tentukan direktori untuk dokumen Anda. Ganti`"Your Document Directory"` dengan jalur ke direktori kerja Anda:

```csharp
string dataDir = "Your Document Directory";
```

## Langkah 3: Berikan URL Gambar

Tentukan URL gambar tempat Anda ingin mengekstrak teks. Pastikan gambar tersebut dapat diakses publik:

```csharp
string uri = "https://contoh.com/gambar.jpg";
```

## Langkah 4: Inisialisasi Aspose.OCR

 Buat contoh dari`AsposeOcr` kelas, yang akan Anda gunakan untuk melakukan operasi OCR:

```csharp
AsposeOcr api = new AsposeOcr();
```

## Langkah 5: Mengenali Teks dari Gambar

 Gunakan`RecognizeImageFromUri` metode untuk mengekstrak teks dari URL gambar. Anda dapat menyesuaikan berbagai pengaturan pengenalan berdasarkan kebutuhan spesifik Anda:

```csharp
RecognitionResult result = api.RecognizeImageFromUri(uri, new RecognitionSettings
{
    DetectAreas = true,
    RecognizeSingleLine = false,
    AutoSkew = true,
    RecognitionAreas = new List<Rectangle>
    {
        new Rectangle(1, 3, 390, 70),
        new Rectangle(1, 72, 390, 70)
    }
});
```

## Langkah 6: Menampilkan Hasil Pengenalan

Keluarkan teks yang dikenali beserta informasi relevan, termasuk area yang dikenali dan peringatan:

```csharp
Console.WriteLine($"Text:\n {result.RecognitionText}");
Console.WriteLine("Areas:");
result.RecognitionAreasText.ForEach(a => Console.WriteLine($"{a}"));
Console.WriteLine("Warnings:");
result.Warnings.ForEach(w => Console.WriteLine($"{w}"));
Console.WriteLine($"JSON: {result.GetJson()}");
```

## Langkah 7: Jalankan Aplikasi Anda

Jalankan aplikasi Anda. Jika semuanya dikonfigurasi dengan benar, Anda akan melihat eksekusi proses OCR yang berhasil:

```csharp
Console.WriteLine("OCR process executed successfully.");
```

## Kesimpulan

Mengintegrasikan kemampuan OCR ke dalam aplikasi .NET Anda mudah dilakukan dengan Aspose.OCR. Panduan ini telah memandu Anda melalui langkah-langkah penting untuk melakukan OCR pada gambar dari URL, yang menjadi dasar untuk mengembangkan aplikasi yang memanfaatkan teknologi pengenalan teks.

## Pertanyaan yang Sering Diajukan

### Apakah Aspose.OCR cocok untuk mengenali banyak bahasa?

Ya, Aspose.OCR mendukung berbagai bahasa, membuatnya ideal untuk aplikasi yang menargetkan pengguna internasional.

### Bisakah Aspose.OCR menangani pengenalan teks satu baris dan beberapa baris?

Tentu saja! Pustaka ini serbaguna, memungkinkan pengenalan teks baris tunggal dan multibaris sesuai kebutuhan proyek Anda.

### Pilihan lisensi apa yang tersedia untuk Aspose.OCR?

 Anda dapat mempelajari tentang berbagai pilihan lisensi dan melakukan pembelian dari[Toko Aspose](https://purchase.conholdate.com/buy).

### Apakah ada versi uji coba Aspose.OCR?

 Ya, uji coba gratis tersedia. Anda dapat menjelajahinya di[halaman rilis](https://releases.aspose.com/).

### Di mana saya dapat menemukan dukungan untuk Aspose.OCR?

Untuk bantuan atau diskusi komunitas tentang Aspose.OCR, kunjungi[Forum Aspose.OCR](https://forum.aspose.com/c/ocr/16).