---
title: Mengekstrak Garis Persegi Panjang dari Pengenalan Gambar
linktitle: Mengekstrak Garis Persegi Panjang dari Pengenalan Gambar
second_title: API Aspose.OCR .NET
description: Pelajari cara menerapkan Optical Character Recognition (OCR) di aplikasi .NET Anda menggunakan Aspose.OCR. Panduan komprehensif ini memandu Anda melalui proses mengekstraksi persegi panjang untuk garis yang dikenali.
type: docs
weight: 10
url: /id/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Perkenalan

Selamat datang di dunia Aspose.OCR untuk .NET, alat yang mengagumkan yang dirancang untuk mengintegrasikan Pengenalan Karakter Optik (OCR) ke dalam aplikasi .NET Anda. Apakah Anda seorang pengembang berpengalaman atau pendatang baru yang penasaran, panduan ini akan memandu Anda melalui langkah-langkah untuk memperoleh persegi panjang yang mewakili garis dari teks yang dikenali dalam gambar.

## Prasyarat

Sebelum memulai, pastikan Anda telah menyiapkan hal-hal berikut:

- Pengetahuan dasar tentang pengembangan C# dan .NET.
- Lingkungan pengembangan terpadu (IDE) seperti Visual Studio.
-  Pustaka Aspose.OCR untuk .NET telah terinstal. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/ocr/net/).
- Contoh gambar yang berisi teks untuk pengenalan.

## Ruang Nama yang Diperlukan

Untuk memulai, Anda perlu menambahkan namespace yang diperlukan ke proyek Anda. Sertakan baris berikut di bagian atas berkas C# Anda:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Ikuti langkah-langkah ini untuk mengambil persegi panjang untuk garis dalam gambar OCR.

## Langkah 1: Siapkan Direktori Dokumen Anda

Tentukan direktori tempat berkas gambar Anda berada:

```csharp
// Tentukan jalur ke direktori dokumen Anda
string dataDir = "Your Document Directory";
```

 Pastikan untuk mengganti`"Your Document Directory"` dengan jalur sebenarnya.

## Langkah 2: Inisialisasi Aspose.OCR

 Buat contoh dari`AsposeOcr` kelas untuk mengakses fitur-fiturnya:

```csharp
// Inisialisasi API Aspose.OCR
AsposeOcr api = new AsposeOcr();
```

## Langkah 3: Tentukan Jalur Gambar

Tentukan jalur lengkap ke berkas gambar yang ingin Anda proses:

```csharp
// Tentukan jalur lengkap ke gambar
string fullPath = dataDir + "sample.png";
```

## Langkah 4: Kenali Gambar dan Dapatkan Persegi Panjang untuk Garis

 Sekarang, Anda dapat menggunakan`GetRectangles` metode untuk mengekstrak persegi panjang dari baris teks yang dikenali:

```csharp
// Ambil persegi panjang untuk garis pada gambar yang ditentukan
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## Langkah 5: Keluarkan Hasilnya

Terakhir, cetak koordinat setiap persegi panjang garis yang terdeteksi ke konsol:

```csharp
// Menampilkan koordinat persegi panjang yang terdeteksi
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Kesimpulan

Selamat! Anda telah berhasil mengambil persegi panjang untuk garis dalam gambar OCR menggunakan Aspose.OCR untuk .NET. Teknologi ini membuka banyak kemungkinan untuk ekstraksi dan pemrosesan teks dalam aplikasi Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.OCR untuk .NET dengan jenis gambar apa pun?

Ya, Aspose.OCR mendukung berbagai format gambar, memberikan fleksibilitas untuk aplikasi OCR Anda.

### Berapa tingkat akurasi pengenalan OCR?

Aspose.OCR menggunakan algoritma canggih untuk mencapai akurasi tinggi dalam pengenalan teks, cocok untuk beragam skenario.

### Apakah versi uji coba tersedia?

 Ya, Anda dapat menjelajahi fitur Aspose.OCR untuk .NET dengan mengunduh[uji coba gratis](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi terperinci?

 Dokumentasi lengkap dapat ditemukan[Di Sini](https://reference.aspose.com/ocr/net/), menawarkan informasi dan panduan yang mendalam.

### Butuh bantuan lebih lanjut atau punya pertanyaan?

 Bergabunglah dalam diskusi di[Forum Aspose.OCR](https://forum.aspose.com/c/ocr/16) untuk dukungan komunitas.