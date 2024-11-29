---
title: Menambahkan Komponen Tombol dengan GroupDocs.Annotation untuk .NET
linktitle: Menambahkan Komponen Tombol
second_title: API .NET GroupDocs.Annotation
description: Temukan cara untuk meningkatkan dokumen PDF Anda dengan menambahkan Komponen Tombol interaktif menggunakan GroupDocs.Annotation untuk .NET. Tutorial langkah demi langkah ini.
type: docs
weight: 10
url: /id/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## Perkenalan

Dalam tutorial ini, kami akan memandu Anda melalui proses mudah untuk menambahkan Komponen Tombol ke dokumen PDF menggunakan pustaka GroupDocs.Annotation untuk .NET. Di akhir panduan ini, Anda akan diperlengkapi untuk menyempurnakan dokumen PDF Anda dengan fitur-fitur interaktif.

## Prasyarat

Sebelum memulai, pastikan Anda telah menyiapkan hal-hal berikut:

1.  GroupDocs.Annotation untuk .NET: Unduh dan instal pustaka GroupDocs.Annotation untuk .NET dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan yang sesuai dengan kerangka kerja .NET yang terpasang.

## Langkah 1: Impor Namespace yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan ke dalam proyek Anda:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Langkah 2: Inisialisasi Jalur Output

Tentukan jalur keluaran tempat PDF yang dimodifikasi akan disimpan:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 3: Tambahkan Komponen Tombol

Sekarang, mari buat dan tambahkan Komponen Tombol ke PDF Anda:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // Posisi dan ukuran tombol
        PenColor = 65535,                       // Warna batas tombol
        Style = BorderStyle.Dashed,             // Gaya perbatasan
        BorderWidth = 0,                        // Lebar perbatasan
        BorderColor = 0,                        // Warna batas
        AlternateName = "Name",                 //Nama alternatif untuk tombol
        PartialName = "Partial Name",           // Nama sebagian untuk tombol
        NormalCaption = "Caption",               // Teks yang ditampilkan pada tombol
        ButtonColor = 16761035,                 // Warna latar belakang tombol
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // Tambahkan tombol ke anotator
    annotator.Save("result.pdf"); // Simpan PDF yang dimodifikasi
}
```

## Langkah 4: Menampilkan Jalur Output

Terakhir, beri tahu pengguna di mana file keluaran disimpan:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Selamat! Anda telah berhasil menambahkan Komponen Tombol ke dokumen PDF menggunakan GroupDocs.Annotation for .NET.

## Kesimpulan

Dalam tutorial ini, kami menunjukkan cara menggabungkan Komponen Tombol ke dalam dokumen PDF dengan GroupDocs.Annotation untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat meningkatkan interaktivitas dokumen PDF Anda secara signifikan.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan tombol?

Tentu saja! Anda dapat mengubah berbagai properti seperti ukuran, warna, dan gaya sesuai kebutuhan Anda.

### Apakah GroupDocs.Annotation untuk .NET kompatibel dengan semua versi PDF?

Ya, GroupDocs.Annotation untuk .NET mendukung berbagai versi PDF, memastikan kompatibilitas dengan sebagian besar dokumen.

### Bisakah saya menambahkan beberapa komponen tombol ke satu dokumen PDF?

Ya, Anda dapat menambahkan komponen tombol sebanyak yang diperlukan ke dokumen PDF.

### Apakah GroupDocs.Annotation untuk .NET mendukung format file lain?

Ya, ia mendukung berbagai format dokumen, termasuk DOCX, PPTX, dan XLSX, selain PDF.

### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?

 Ya, Anda dapat mengakses uji coba gratis GroupDocs.Annotation untuk .NET dari[Di Sini](https://releases.groupdocs.com/).
