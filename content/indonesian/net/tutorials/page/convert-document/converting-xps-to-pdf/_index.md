---
title: Mengonversi XPS ke PDF dengan Aspose.Page untuk .NET
linktitle: Mengonversi XPS ke PDF
second_title: API Aspose.Halaman .NET
description: Temukan cara mengonversi dokumen XPS (XML Paper Specification) ke PDF (Portable Document Format) secara mudah menggunakan pustaka Aspose.Page for .NET yang canggih.
type: docs
weight: 11
url: /id/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Perkenalan

Dalam tutorial ini, kita akan menjelajahi cara mengonversi dokumen XPS (XML Paper Specification) ke PDF (Portable Document Format) menggunakan pustaka Aspose.Page for .NET yang serbaguna. Pustaka canggih ini menyederhanakan konversi dokumen dan menawarkan berbagai opsi penyesuaian, menjadikannya pilihan yang sangat baik bagi para pengembang.

## Prasyarat

Sebelum kita memulai, pastikan Anda telah menyiapkan hal-hal berikut:

-  Pustaka Aspose.Page untuk .NET: Unduh dan instal pustaka Aspose.Page untuk .NET dari[Dokumentasi Aspose.Page](https://reference.aspose.com/page/net/).
  
- Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET menggunakan Visual Studio atau IDE lain yang kompatibel.

- Dokumen XPS: Siapkan file XPS yang ingin Anda konversi, simpan di direktori yang ditentukan.

## Langkah 1: Impor Namespace yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan untuk mengakses fungsionalitas Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Langkah 2: Inisialisasi Direktori Dokumen

Tentukan jalur direktori tempat dokumen Anda disimpan:

```csharp
string dataDir = "Your Document Directory";
```

 Pastikan untuk mengganti`"Your Document Directory"` dengan jalur sebenarnya ke direktori yang berisi dokumen XPS Anda.

### Langkah 3: Buka Aliran PDF dan XPS

Berikutnya, inisialisasi aliran untuk file XPS masukan dan file PDF keluaran:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Pastikan Anda telah menetapkan jalur yang benar untuk berkas Anda.

### Langkah 4: Muat Dokumen XPS

Sekarang, muat dokumen XPS Anda menggunakan pustaka Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Langkah 5: Konfigurasikan Opsi Penyimpanan PDF

Siapkan opsi penyimpanan untuk PDF Anda, termasuk kualitas gambar dan parameter kompresi:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Mengatur tingkat kualitas JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Gunakan kompresi JPEG untuk gambar
    TextCompression = PdfTextCompression.Flate, // Terapkan kompresi Flate untuk teks
    PageNumbers = new int[] { 1, 2, 6 } // Tentukan nomor halaman yang akan disertakan
};
```

Jangan ragu untuk menyesuaikan parameter ini menurut kebutuhan Anda.

### Langkah 6: Buat Perangkat Rendering PDF

Buat perangkat rendering untuk format PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Langkah 7: Simpan Dokumen sebagai PDF

Terakhir, simpan dokumen XPS ke PDF menggunakan perangkat dan opsi yang ditentukan:

```csharp
document.Save(device, options);
```

## Kesimpulan

Selamat! Anda telah berhasil mengonversi dokumen XPS ke PDF menggunakan Aspose.Page for .NET. Pustaka ini tidak hanya menyederhanakan konversi dokumen tetapi juga menawarkan kemampuan ekstensif untuk menangani berbagai format.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengonversi beberapa file XPS menjadi satu PDF?

Tentu saja! Anda dapat mengulang beberapa file XPS dan menggabungkannya menjadi satu dokumen PDF dengan mengikuti langkah konversi yang sama.

### Format keluaran apa lagi yang didukung Aspose.Page untuk .NET?

Selain PDF, Aspose.Page untuk .NET mendukung berbagai format, termasuk TIFF, JPEG, dan PNG.

### Bagaimana saya dapat menyesuaikan tampilan PDF yang dikonversi?

 Anda dapat menyesuaikan parameter di`PdfSaveOptions` objek, seperti pengaturan kualitas dan kompresi JPEG, untuk mencapai tampilan yang Anda inginkan.

### Apakah ada versi uji coba yang tersedia untuk Aspose.Page untuk .NET?

Ya, Anda dapat mencoba Aspose.Page untuk .NET dengan uji coba gratis yang tersedia[Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dukungan komunitas untuk Aspose.Page for .NET?

 Untuk diskusi dan dukungan komunitas, kunjungi[Forum Aspose.Halaman](https://forum.aspose.com/c/page/39).