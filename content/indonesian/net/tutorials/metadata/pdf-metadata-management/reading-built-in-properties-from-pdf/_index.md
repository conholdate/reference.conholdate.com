---
title: Membaca Properti Bawaan dari PDF di .NET
linktitle: Membaca Properti Bawaan dari PDF di .NET
second_title: API GroupDocs.Metadata.NET
description: Pelajari cara memanfaatkan GroupDocs.Metadata for .NET secara efektif untuk membaca, mengedit, dan mengelola metadata dalam file PDF. Tutorial ini menyediakan panduan langkah demi langkah.
type: docs
weight: 10
url: /id/net/tutorials/metadata/pdf-metadata-management/reading-built-in-properties-from-pdf/
---
## Perkenalan
Dalam tutorial ini, kita akan menjelajahi cara menggunakan GroupDocs.Metadata for .NET untuk membaca dan memanipulasi metadata dalam file PDF. Pustaka canggih ini memungkinkan pengembang untuk mengakses berbagai atribut metadata, seperti penulis, tanggal pembuatan, dan subjek, yang meningkatkan kemampuan manajemen dokumen dalam aplikasi.

## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:

- Visual Studio: Pastikan telah terinstal di sistem Anda.
-  GroupDocs.Metadata untuk .NET: Unduh dan instal dari[situs web resmi](https://releases.groupdocs.com/metadata/net/).
- Pengetahuan Dasar C#: Disarankan untuk terbiasa dengan C# dan kerangka kerja .NET.

## Mengimpor Ruang Nama
Mulailah dengan menyertakan namespace yang diperlukan dalam proyek C# Anda:

```csharp
using System;
using Formats.Document;
```

## Langkah 1: Muat Metadata PDF
Untuk membaca metadata dari berkas PDF, muat dokumen dan ekstrak propertinya menggunakan kode berikut:

```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    //Akses paket root file PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    
    // Mengambil dan menampilkan properti bawaan
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Akses properti lain sesuai kebutuhan
}
```

Dengan pendekatan langsung ini, Anda dapat dengan mudah melihat atribut metadata penting yang tertanam dalam berkas PDF Anda.

## Kesimpulan
Dalam tutorial ini, kami telah menunjukkan cara menggunakan GroupDocs.Metadata for .NET untuk mengekstrak dan mengelola properti bawaan dari file PDF dengan C#. Mengintegrasikan pustaka ini ke dalam proyek Anda akan meningkatkan penanganan metadata dokumen, membuatnya lebih efisien dan efisien.

## Pertanyaan yang Sering Diajukan
### Bisakah GroupDocs.Metadata bekerja dengan format dokumen lain?
Ya, ia mendukung berbagai format, termasuk DOCX, XLSX, PPTX, PDF, JPG, PNG, dan banyak lagi.

### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Metadata?
 Tentu saja! Anda dapat mengakses uji coba gratis dari[Situs web GroupDocs.Metadata](https://releases.groupdocs.com/).

### Bagaimana cara mengubah properti metadata menggunakan GroupDocs.Metadata?
Anda dapat mengubah properti metadata dengan mengakses paket dokumen relevan dan menetapkan nilai baru sesuai kebutuhan.

### Apakah GroupDocs.Metadata mendukung .NET Core?
Ya, ini kompatibel dengan .NET Framework dan .NET Core.

### Di mana saya dapat menemukan dukungan atau mengajukan pertanyaan terkait GroupDocs.Metadata?
 Untuk dukungan dan diskusi komunitas, kunjungi[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).