---
title: Menguasai Manipulasi File DGN dengan Aspose.CAD di .NET
linktitle: Menguasai Manipulasi File DGN
second_title: Aspose.CAD .NET - Format Berkas CAD dan BIM
description: Pelajari cara memuat file DGN, mengulangi elemen-elemennya, mengelola entitas 2D dan 3D, serta mengekspornya sebagai gambar raster—semuanya sambil memanfaatkan fitur-fitur hebat dari pustaka Aspose.CAD.
type: docs
weight: 18
url: /id/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Perkenalan

Apakah Anda seorang pengembang .NET yang ingin mengintegrasikan file DGN ke dalam aplikasi Anda? Aspose.CAD untuk .NET menawarkan pustaka canggih yang dirancang khusus untuk bekerja dengan format file DGN. Dalam tutorial ini, kita akan membahas cara menangani file DGN secara efisien, termasuk elemen yang didukung dan cara memanipulasinya dalam proyek .NET Anda.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki pengaturan berikut:

- Pengetahuan dasar pemrograman .NET: Keakraban dengan C# atau VB.NET akan bermanfaat.
- Visual Studio: Diinstal pada komputer Anda untuk pengembangan proyek.
-  Pustaka Aspose.CAD untuk .NET: Unduh dari[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Langkah 1: Impor Namespace yang Diperlukan

Untuk memanfaatkan fungsionalitas Aspose.CAD, mulailah dengan mengimpor namespace yang diperlukan ke dalam proyek Anda.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Langkah 2: Muat File DGN Anda

 Mulailah dengan memuat file DGN yang sudah ada ke dalam aplikasi Anda. Hal ini dilakukan dengan membuat instance`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Lanjutkan logika Anda di sini
}
```

## Langkah 3: Ulangi Melalui Elemen DGN

Setelah berkas DGN dimuat, Anda dapat mengulangi elemen-elemennya. Aspose.CAD menyediakan berbagai jenis elemen DGN untuk manipulasi Anda.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Memproses setiap elemen
}
```

## Langkah 4: Menangani Entitas 2D dan 3D

Anda dapat membedakan antara elemen DGN 2D dan 3D. Berikut adalah cara menanganinya secara efisien:

### Menangani Entitas 2D

Anda dapat mengelola entitas 2D yang sebelumnya didukung dengan blok switch-case.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Tambahkan logika pemrosesan Anda di sini
        break;
}
```

### Menangani Entitas 3D

Demikian pula, tangani entitas 3D sebagai berikut:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Tambahkan logika pemrosesan Anda di sini
        break;
}
```

## Langkah 5: Ekspor File DGN

Setelah memanipulasi elemen DGN, Anda mungkin ingin mengekspor berkas tersebut sebagai gambar raster. Hal ini dapat dilakukan dengan mudah menggunakan Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Tentukan jalur keluaran Anda
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Kesimpulan

Dalam tutorial ini, kita mempelajari cara menggunakan Aspose.CAD untuk .NET guna mengelola berkas DGN secara efektif. Dengan mengikuti langkah-langkah yang diuraikan, Anda dapat dengan mudah menangani elemen DGN 2D dan 3D serta mengekspornya sebagai gambar raster. Pustaka canggih ini memungkinkan integrasi pemrosesan DGN yang lancar ke dalam aplikasi .NET Anda, sehingga meningkatkan kemampuan proyek Anda.

## Pertanyaan yang Sering Diajukan

### Di mana saya dapat menemukan dokumentasi untuk Aspose.CAD untuk .NET?

 Dokumentasi lengkap tersedia[Di Sini](https://reference.aspose.com/cad/net/).

### Bagaimana cara mengunduh Aspose.CAD untuk .NET?

 Anda dapat mengunduh versi terbaru dari perpustakaan[Di Sini](https://releases.aspose.com/cad/net/).

### Apakah ada uji coba gratis yang tersedia untuk Aspose.CAD untuk .NET?

 Ya, uji coba gratis dapat diakses[Di Sini](https://releases.aspose.com/).

### Bagaimana cara memperoleh lisensi sementara untuk Aspose.CAD untuk .NET?

 Anda dapat meminta lisensi sementara[Di Sini](https://purchase.conholdate.com/temporary-license/).

### Butuh bantuan atau punya pertanyaan?

 Untuk dukungan atau mengajukan pertanyaan, kunjungi komunitas Aspose.CAD[forum dukungan](https://forum.aspose.com/c/cad/19).