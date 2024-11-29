---
title: Konversi DGN ke PDF di Aspose.CAD untuk .NET
linktitle: Konversi DGN ke PDF di Aspose.CAD untuk .NET
second_title: Aspose.CAD .NET - Format Berkas CAD dan BIM
description: Pelajari cara mengonversi file DGN ke PDF dengan mudah menggunakan pustaka Aspose.CAD yang canggih untuk .NET. Panduan langkah demi langkah ini dirancang untuk pengembang dari semua tingkatan.
type: docs
weight: 12
url: /id/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Perkenalan

Menjelajahi dunia file CAD bisa jadi menantang, tetapi dengan Aspose.CAD untuk .NET, pengembang dapat dengan mudah memanipulasi dan mengonversi berbagai format CAD. Salah satu kebutuhan umum adalah mengonversi file DGN ke PDF, yang akan kita bahas langkah demi langkah dalam tutorial ini.

## Prasyarat

Untuk mengikutinya, pastikan Anda memiliki hal berikut:

- Kemampuan dasar dalam C# dan kerangka kerja .NET.
-  Pustaka Aspose.CAD untuk .NET telah terinstal. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/cad/net/).
- Contoh file DGN (misalnya, Nikon_D90_Camera.dgn). 

## Langkah 1: Impor Namespace yang Diperlukan

Mulailah dengan mengimpor namespace yang relevan dalam proyek C# Anda:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Langkah 2: Muat File DGN

Tentukan direktori untuk file DGN Anda dan muat menggunakan kode berikut:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Pemrosesan tambahan akan dilakukan di sini...
}
```

## Langkah 3: Konfigurasikan Opsi Rasterisasi

Berikutnya, atur opsi rasterisasi untuk menentukan bagaimana DGN Anda akan ditampilkan dalam PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Sesuaikan lebar sesuai kebutuhan
    PageHeight = 300, // Sesuaikan tinggi sesuai kebutuhan
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Langkah 4: Buat Opsi PDF

Tentukan opsi PDF, integrasikan pengaturan rasterisasi yang dikonfigurasi sebelumnya:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Langkah 5: Simpan DGN sebagai PDF

Terakhir, simpan file DGN sebagai PDF menggunakan opsi yang telah Anda konfigurasikan:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Kesimpulan

Selamat! Anda telah berhasil mengonversi file DGN menjadi PDF menggunakan Aspose.CAD untuk .NET. Tutorial sederhana ini memandu Anda memuat file DGN, mengatur opsi rasterisasi, dan menyimpan output sebagai PDF.

## Pertanyaan yang Sering Diajukan

### Apakah saya perlu pengetahuan CAD sebelumnya untuk menggunakan Aspose.CAD?  
Tentu saja! Aspose.CAD dirancang untuk menyederhanakan tugas CAD yang rumit, sehingga dapat diakses oleh semua pengembang, apa pun pengetahuan CAD mereka.

### Di mana saya dapat menemukan lebih banyak sumber daya dan dokumentasi untuk Aspose.CAD?  
 Anda dapat menjelajahi panduan dan contoh lengkap di[Dokumentasi Aspose.CAD](https://reference.aspose.com/cad/net/).

### Apakah ada uji coba gratis yang tersedia untuk Aspose.CAD?  
 Ya, uji coba gratis dapat diperoleh[Di Sini](https://releases.aspose.com/).

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.CAD?  
 Anda dapat meminta lisensi sementara[Di Sini](https://purchase.conholdate.com/temporary-license/).

### Butuh bantuan atau punya pertanyaan?  
 Bergabunglah dalam percakapan di[Forum Aspose.CAD](https://forum.aspose.com/c/cad/19) untuk dukungan dan pertanyaan komunitas.