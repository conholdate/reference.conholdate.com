---
title: Memuat Dokumen yang Dilindungi Kata Sandi
linktitle: Muat Dokumen yang Dilindungi Kata Sandi
second_title: API Penampil GroupDocs.NET
description: Temukan cara mudah untuk mengintegrasikan kemampuan melihat dokumen ke dalam aplikasi .NET Anda dengan GroupDocs.Viewer. Tutorial ini menyediakan panduan langkah demi langkah yang komprehensif.
type: docs
weight: 12
url: /id/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## Perkenalan

Dalam lanskap digital, kemampuan untuk mengelola dan melihat berbagai format dokumen sangat penting bagi bisnis dan individu. GroupDocs.Viewer untuk .NET menawarkan solusi yang tangguh bagi pengembang untuk mengintegrasikan kemampuan melihat dokumen ke dalam aplikasi mereka dengan mudah. Tutorial ini akan memandu Anda melalui proses memuat dokumen yang dilindungi kata sandi langkah demi langkah, memastikan Anda dapat menerapkan fitur ini dengan lancar dalam proyek Anda.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  GroupDocs.Viewer untuk .NET Terpasang: Unduh dari[situs web](https://releases.groupdocs.com/viewer/net/).
2. Dokumen yang Dilindungi Kata Sandi: Siapkan dokumen yang dilindungi kata sandi untuk pengujian.

## Mengimpor Ruang Nama yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan ke dalam proyek Anda:

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Langkah 1: Tentukan Direktori Output

Tentukan di mana Anda ingin hasil render disimpan:

```csharp
string outputDirectory = "Your Document Directory";
```
 Pastikan untuk mengganti`"Your Document Directory"` dengan jalur sesungguhnya yang ingin Anda gunakan.

## Langkah 2: Mengatur Format Jalur File Halaman

Tentukan format untuk jalur file setiap halaman yang ditampilkan:

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

 Ini akan menghasilkan jalur seperti`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`, dll.

## Langkah 3: Konfigurasikan Opsi Muat

Siapkan opsi muat untuk dokumen Anda yang dilindungi kata sandi, termasuk kata sandinya:

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  // Ganti dengan kata sandi dokumen Anda
};
```

## Langkah 4: Inisialisasi Penampil

Buat contoh GroupDocs.Viewer dengan dokumen Anda dan opsi muat:

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    // Kode untuk pilihan tampilan akan ditambahkan pada langkah berikutnya.
}
```
 Pastikan untuk mengganti`"Path_to_your_document"` dengan jalur sebenarnya ke dokumen Anda.

## Langkah 5: Konfigurasikan Opsi Tampilan HTML

Siapkan opsi tampilan HTML untuk merender dokumen dengan sumber daya tertanam:

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## Langkah 6: Render Dokumen

Sekarang, render dokumen menggunakan penampil dan opsi tampilan yang dikonfigurasi:

```csharp
viewer.View(options);
```

## Langkah 7: Menampilkan Pesan Sukses

Terakhir, informasikan kepada pengguna bahwa dokumen telah berhasil ditampilkan:

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Kesimpulan

Dalam tutorial ini, kami mempelajari cara memuat dokumen yang dilindungi kata sandi menggunakan GroupDocs.Viewer untuk .NET. Dengan mengikuti langkah-langkah ini, pengembang dapat dengan mudah mengintegrasikan fungsionalitas ini ke dalam aplikasi mereka, sehingga pengguna dapat melihat dokumen yang dilindungi dengan mudah.

## Pertanyaan yang Sering Diajukan

### Bisakah GroupDocs.Viewer menangani format dokumen lain selain dokumen yang dilindungi kata sandi?

Ya, GroupDocs.Viewer mendukung berbagai format, termasuk PDF, DOCX, XLSX, PPTX, dan banyak lagi.

### Apakah GroupDocs.Viewer kompatibel dengan .NET Core?

Tentu saja! GroupDocs.Viewer kompatibel dengan lingkungan .NET Framework dan .NET Core.

### Dapatkah saya menyesuaikan opsi rendering untuk dokumen?

Ya, GroupDocs.Viewer menawarkan berbagai opsi rendering, yang memungkinkan Anda menyesuaikan pengalaman menonton dengan kebutuhan Anda.

### Apakah GroupDocs.Viewer mendukung anotasi dokumen?

Ya, ini mendukung anotasi dokumen, yang memungkinkan pengguna menambahkan komentar, sorotan, dan catatan lainnya.

### Apakah ada versi uji coba yang tersedia untuk GroupDocs.Viewer?

 Ya, Anda bisa mendapatkan uji coba gratis dari[situs web](https://releases.groupdocs.com/).