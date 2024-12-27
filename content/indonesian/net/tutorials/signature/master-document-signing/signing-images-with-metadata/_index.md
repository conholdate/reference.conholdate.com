---
title: Panduan Menandatangani Gambar dengan Metadata Menggunakan GroupDocs.Signature
linktitle: Panduan Menandatangani Gambar dengan Metadata
second_title: API Tanda Tangan GroupDocs.NET
description: Pelajari cara menandatangani gambar dengan metadata secara efisien di aplikasi .NET Anda menggunakan GroupDocs.Signature. Tutorial langkah demi langkah ini mencakup semuanya mulai dari instalasi hingga implementasi, yang memungkinkan Anda menyempurnakan dokumen Anda dengan tanda tangan metadata dengan mudah.
type: docs
weight: 10
url: /id/net/tutorials/signature/master-document-signing/signing-images-with-metadata/
---
## Perkenalan

GroupDocs.Signature untuk .NET adalah pustaka canggih yang memungkinkan pengembang untuk menandatangani gambar dengan metadata secara efisien. Tutorial ini akan memandu Anda melalui proses ini langkah demi langkah.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

1.  GroupDocs.Signature untuk .NET: Instal paket GroupDocs.Signature di proyek .NET Anda. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/signature/net/).
2. Berkas Gambar: Siapkan berkas gambar yang ingin Anda tandatangani dengan metadata.

## Impor Ruang Nama yang Diperlukan

Dalam kode C# Anda, impor namespace berikut:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Langkah 1: Muat File Gambar Anda

Mulailah dengan menentukan jalur ke berkas gambar Anda dan direktori keluaran untuk gambar yang ditandatangani:

```csharp
string filePath = "sample.png";            
string outputFilePath = Path.Combine("Your Document Directory", "SignImageWithMetadata", "SignedWithMetadata.png");
```

## Langkah 2: Buat Tanda Tangan Metadata

Berikutnya, buat tanda tangan metadata dan tambahkan ke opsi penandatanganan:

```csharp
using (Signature signature = new Signature(filePath))
{
    ushort imgsMetadataId = 41996; // ID Awal untuk metadata
    MetadataSignOptions options = new MetadataSignOptions();

    // Tambahkan berbagai jenis tanda tangan metadata
    options
        .Add(new ImageMetadataSignature(imgsMetadataId++, "Mr. Sherlock Holmes")) // Nilai string
        .Add(new ImageMetadataSignature(imgsMetadataId++, DateTime.Now))          // Nilai TanggalWaktu
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123456))                // Nilai integer
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456D))              // Nilai ganda
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456M))              // Nilai desimal
        .Add(new ImageMetadataSignature(imgsMetadataId++, 123.456F));             // Nilai mengapung

    // Tanda tangani dokumen dan simpan hasilnya
    SignResult result = signature.Sign(outputFilePath, options);
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at: {outputFilePath}");
}
```

## Kesimpulan

Dalam tutorial ini, Anda mempelajari cara menandatangani gambar dengan metadata menggunakan GroupDocs.Signature untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah menambahkan tanda tangan metadata ke aplikasi .NET Anda, yang akan meningkatkan fungsionalitas dan integritas gambar Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menandatangani beberapa gambar dengan metadata menggunakan GroupDocs.Signature untuk .NET?
Ya, Anda dapat menandatangani beberapa gambar dengan mengulangi setiap berkas gambar dan menerapkan tanda tangan metadata.

### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Signature untuk .NET?
 Ya, Anda dapat mengunduh versi uji coba dari[Di Sini](https://releases.groupdocs.com/).

### Apakah GroupDocs.Signature untuk .NET mendukung format file lain selain gambar?
Tentu saja! GroupDocs.Signature mendukung berbagai format, termasuk PDF, Word, Excel, dan banyak lagi.

### Bisakah saya menyesuaikan tampilan tanda tangan metadata?
Ya, Anda dapat menyesuaikan aspek seperti ukuran font, warna, dan posisi tanda tangan metadata.

### Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Signature untuk .NET?
 Untuk dukungan, kunjungi forum GroupDocs.Signature[Di Sini](https://forum.groupdocs.com/c/signature/13).