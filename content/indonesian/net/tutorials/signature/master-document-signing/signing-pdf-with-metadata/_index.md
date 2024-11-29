---
title: Panduan Menandatangani PDF dengan Metadata Menggunakan GroupDocs.Signature
linktitle: Panduan Menandatangani PDF dengan Metadata
second_title: API Tanda Tangan GroupDocs.NET
description: Pelajari cara memperkuat dokumen PDF Anda dengan keamanan dan keterlacakan yang lebih baik dengan menandatanganinya menggunakan metadata menggunakan GroupDocs.Signature untuk .NET. Tutorial komprehensif ini memberikan penjelasan yang jelas.
type: docs
weight: 11
url: /id/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## Perkenalan

Dalam tutorial ini, kita akan mempelajari cara menandatangani dokumen PDF dan menambahkan metadata menggunakan GroupDocs.Signature untuk .NET. Menambahkan metadata akan menyempurnakan dokumen dengan memberikan informasi penting seperti kepengarangan, tanggal pembuatan, ID dokumen, dan banyak lagi.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  GroupDocs.Signature untuk .NET: Unduh dari[Di Sini](https://releases.groupdocs.com/signature/net/).
2. Dokumen PDF: Siapkan contoh file PDF untuk ditandatangani.
3. Pengetahuan Dasar Pemrograman C#: Keakraban dengan sintaksis C# diperlukan untuk memahami contoh kode.

## Mengimpor Ruang Nama

Mulailah dengan mengimpor namespace yang diperlukan untuk mengakses kelas dan metode yang diperlukan:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Langkah 1: Muat Dokumen PDF

Tentukan jalur dokumen PDF yang ingin Anda tandatangani:

```csharp
string filePath = "sample.pdf";
```

## Langkah 2: Tentukan Jalur File Output

Tentukan di mana PDF yang ditandatangani dengan metadata akan disimpan:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## Langkah 3: Buat Instansi Tanda Tangan

 Inisialisasi a`Signature` contoh dengan jalur ke dokumen PDF:

```csharp
using (Signature signature = new Signature(filePath))
{
    // Kode terkait tanda tangan akan ada di sini
}
```

## Langkah 4: Tentukan Opsi Metadata

 Membuat`MetadataSignOptions` dan tambahkan bidang metadata beserta nilainya:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // Nilai string
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // Nilai TanggalWaktu
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // Nilai integer
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // Nilai ganda
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // Nilai desimal
    .Add(new PdfMetadataSignature("Total", 123.456F));              // Nilai mengapung
```

## Langkah 5: Tandatangani Dokumen

Tanda tangani dokumen PDF dengan opsi metadata yang ditentukan dan simpan dokumen yang ditandatangani:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Kesimpulan

Dalam tutorial ini, kami membahas cara menandatangani dokumen PDF dengan metadata menggunakan GroupDocs.Signature untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah memperkaya berkas PDF Anda dengan metadata yang berharga, meningkatkan keterlacakan dan kegunaannya.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menambahkan bidang metadata khusus ke dokumen PDF saya?

Ya, Anda dapat menambahkan bidang metadata kustom dengan menentukan nama bidang dan nilainya yang sesuai menggunakan GroupDocs.Signature untuk .NET.

### Apakah GroupDocs.Signature untuk .NET kompatibel dengan semua versi .NET Framework?

GroupDocs.Signature untuk .NET kompatibel dengan berbagai versi .NET Framework, memastikan fleksibilitas dan kemudahan integrasi.

### Apakah GroupDocs.Signature mendukung penandatanganan format dokumen lain selain PDF?

Ya, GroupDocs.Signature mendukung berbagai format dokumen, termasuk Word, Excel, PowerPoint, dan banyak lagi.

### Bisakah saya menandatangani beberapa dokumen sekaligus menggunakan GroupDocs.Signature untuk .NET?

Tentu saja! Anda dapat menandatangani beberapa dokumen secara massal dengan mengulangi daftar file dan menerapkan proses tanda tangan secara terprogram.

### Apakah dukungan teknis tersedia untuk pengguna GroupDocs.Signature?

Ya, GroupDocs menyediakan dukungan teknis khusus melalui forumnya. Anda dapat mengakses forum dukungan[Di Sini](https://forum.groupdocs.com/c/signature/13).