---
title: Ekspor CAD ke Konversi Gambar Raster dengan Aspose.CAD untuk .NET
linktitle: Ekspor CAD ke Konversi Gambar Raster
second_title: Aspose.CAD .NET - Format Berkas CAD dan BIM
description: Pelajari cara mengonversi tata letak CAD ke berbagai format gambar raster secara efisien menggunakan Aspose.CAD untuk .NET. Panduan komprehensif ini memandu Anda melalui proses tersebut dengan kode yang jelas.
type: docs
weight: 10
url: /id/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## Perkenalan

Apakah Anda ingin mengonversi tata letak CAD ke format gambar raster dengan mudah menggunakan Aspose.CAD untuk .NET? Panduan langkah demi langkah ini dirancang untuk membantu Anda menavigasi proses, lengkap dengan cuplikan kode ringkas untuk pengalaman yang lancar. Baik Anda pengembang berpengalaman atau baru memulai, tutorial ini memberikan wawasan berharga untuk semua tingkat keterampilan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

- Pustaka Aspose.CAD untuk .NET: Unduh dan instal pustaka dari[Situs web Aspose.CAD](https://releases.aspose.com/cad/net/).
-  File Gambar CAD: Miliki file gambar CAD Anda (misalnya,`conic_pyramid.dxf`) siap untuk dikonversi.

## Mengimpor Ruang Nama yang Diperlukan

Dalam proyek .NET Anda, Anda perlu mengimpor namespace yang diperlukan untuk memanfaatkan fungsi Aspose.CAD. Tambahkan yang berikut di bagian atas kode Anda:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Langkah 1: Muat Gambar CAD Anda

Pertama, tentukan direktori dan muat file CAD Anda ke dalam instance Gambar:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// Muat gambar CAD
using (var image = Image.Load(sourceFilePath))
{
    // Lanjutkan ke langkah berikutnya
}
```

## Langkah 2: Buat Opsi Rasterisasi

Berikutnya, atur opsi rasterisasi, tentukan dimensi yang diinginkan untuk gambar keluaran:

```csharp
// Inisialisasi CadRasterizationOptions
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Langkah 3: Tentukan Lapisan untuk Konversi

Jika Anda ingin mengonversi lapisan tertentu, tambahkan ke opsi rasterisasi Anda:

```csharp
// Tentukan lapisan yang akan dikonversi
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Langkah 4: Siapkan Opsi Ekspor JPEG

Sekarang, buat opsi untuk format gambar yang ingin Anda ekspor (JPEG dalam kasus ini):

```csharp
// Buat JpegOptions untuk mengekspor
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Langkah 5: Ekspor ke Format JPEG

Terakhir, simpan gambar yang dikonversi:

```csharp
// Tentukan jalur file keluaran dan simpan gambar
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Fitur Tambahan: Konversi Semua Lapisan

Untuk mengonversi semua lapisan pada gambar CAD Anda, Anda dapat menerapkan metode seperti ini:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Ulangi melalui lapisan dan simpan masing-masing sebagai file JPEG terpisah
    // Kode implementasi Anda di sini
}
```

## Kesimpulan

Selamat! Anda telah mempelajari cara mengonversi tata letak CAD ke format gambar raster secara efektif menggunakan Aspose.CAD untuk .NET. Panduan ini menawarkan pendekatan langsung yang cocok untuk pengembang yang ingin melakukan konversi CAD yang efisien.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengekspor ke format gambar yang berbeda?

 Tentu saja! Cukup tukar saja`JpegOptions` dengan pilihan format lainnya, seperti`PngOptions` atau`BmpOptions`, tergantung kebutuhan Anda.

### Apakah versi uji coba tersedia?

 Ya, Anda dapat mengunduh versi uji coba untuk menjelajahi fungsionalitas dengan mengikuti ini[link](https://releases.aspose.com/cad/net/).

### Di mana saya dapat menemukan dukungan untuk Aspose.CAD?

 Untuk dukungan komunitas, lihat Aspose.CAD[forum](https://forum.aspose.com/c/cad/19), atau pertimbangkan untuk membeli lisensi untuk bantuan yang lebih khusus.

### Apakah lisensi sementara mungkin?

 Ya, lisensi sementara tersedia; Anda dapat memintanya[Di Sini](https://purchase.conholdate.com/temporary-license/).

### Di mana saya dapat mengakses dokumentasi terperinci?

 Kunjungi dokumentasi lengkapnya[Di Sini](https://reference.aspose.com/cad/net/) untuk informasi lebih lanjut.