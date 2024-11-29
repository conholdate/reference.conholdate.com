---
title: Menambahkan Komponen Kotak Centang ke Dokumen PDF
linktitle: Menambahkan Komponen Kotak Centang ke Dokumen PDF
second_title: API .NET GroupDocs.Annotation
description: Temukan cara memperkaya dokumen PDF Anda dengan menambahkan komponen kotak centang interaktif menggunakan GroupDocs.Annotation for .NET SDK. Tutorial komprehensif ini menyediakan panduan langkah demi langkah yang jelas.
type: docs
weight: 11
url: /id/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## Perkenalan

Dalam tutorial ini, kami akan memandu Anda melalui proses penambahan Komponen Kotak Centang ke dokumen PDF menggunakan GroupDocs.Annotation for .NET SDK. Fitur ini memungkinkan Anda untuk menyempurnakan dokumen PDF Anda dengan elemen interaktif, sehingga lebih menarik bagi pengguna.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  GroupDocs.Annotation untuk .NET SDK: Unduh dari[Di Sini](https://releases.groupdocs.com/annotation/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET di komputer Anda.

## Langkah 1: Impor Namespace yang Diperlukan

Pertama, sertakan namespace yang diperlukan dalam proyek Anda:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Langkah 2: Tentukan Jalur Output

Tentukan di mana dokumen PDF yang dimodifikasi akan disimpan:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Langkah 3: Inisialisasi Anotator

 Buat contoh dari`Annotator` kelas dengan jalur ke dokumen PDF masukan Anda:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## Langkah 4: Buat Komponen Kotak Centang

Sekarang, mari kita buat dan sesuaikan Komponen Kotak Centang:

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // Tentukan posisi dan ukuran
    PenColor = 65535, // Mengatur warna (dalam hal ini, kuning)
    Style = BoxStyle.Star, // Pilih gaya untuk kotak centang
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## Langkah 5: Tambahkan Kotak Centang ke Dokumen

Tambahkan komponen kotak centang yang dibuat ke PDF:

```csharp
annotator.Add(checkBox);
```

## Langkah 6: Simpan Dokumen yang Dimodifikasi

Simpan dokumen PDF yang diperbarui dengan kotak centang disertakan:

```csharp
annotator.Save("result.pdf");
```

## Langkah 7: Menampilkan Jalur Output

Terakhir, beri tahu pengguna di mana dokumen yang dimodifikasi disimpan:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Kesimpulan

Dalam tutorial ini, kami berhasil menambahkan Komponen Kotak Centang ke dokumen PDF menggunakan GroupDocs.Annotation for .NET. Fungsionalitas ini memungkinkan Anda membuat PDF interaktif yang dapat meningkatkan pengalaman dan keterlibatan pengguna.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan kotak centang?

Tentu saja! Anda dapat mengubah berbagai properti seperti warna, gaya, dan ukuran untuk memenuhi kebutuhan spesifik Anda.

### Apakah GroupDocs.Annotation untuk .NET cocok untuk penggunaan komersial?

Ya, GroupDocs.Annotation untuk .NET menyediakan lisensi komersial untuk bisnis.

### Dapatkah saya mencoba GroupDocs.Annotation untuk .NET sebelum membeli?

 Ya, uji coba gratis tersedia. Anda dapat mengaksesnya[Di Sini](https://releases.groupdocs.com/).

### Di mana saya dapat menemukan dukungan untuk GroupDocs.Annotation untuk .NET?

 Dukungan dan sumber daya tambahan tersedia di[Forum GroupDocs](https://forum.groupdocs.com/c/annotation/10).

### Apakah saya memerlukan lisensi sementara untuk tujuan pengujian?

 Anda dapat memperoleh lisensi sementara untuk pengujian dari[Di Sini](https://purchase.groupdocs.com/temporary-license/).