---
title: Menambahkan Tanda Tangan Teks ke Dokumen Menggunakan GroupDocs.Signature
linktitle: Tambahkan Tanda Tangan Teks ke Dokumen
second_title: API Tanda Tangan GroupDocs.NET
description: Pelajari cara menandatangani dokumen dengan teks menggunakan GroupDocs.Signature untuk .NET. Panduan langkah demi langkah untuk menambahkan tanda tangan teks secara terprogram.
type: docs
weight: 17
url: /id/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Perkenalan

Dalam lanskap digital saat ini, penandatanganan dokumen elektronik telah menjadi hal penting untuk merampingkan alur kerja dan menghemat sumber daya. GroupDocs.Signature untuk .NET menyediakan solusi yang hebat untuk menambahkan tanda tangan teks secara terprogram ke berbagai format dokumen. Tutorial ini akan memandu Anda melalui langkah-langkah untuk menandatangani dokumen dengan teks menggunakan GroupDocs.Signature untuk .NET.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. GroupDocs.Signature untuk .NET: Unduh dan instal pustaka dari[Di Sini](https://releases.groupdocs.com/signature/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET Anda.
3. Dokumen: Siapkan dokumen yang ingin Anda tandatangani (misalnya, PDF, Word).

## Mengimpor Ruang Nama yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan ke proyek .NET Anda:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Langkah 1: Muat Dokumen

Mulailah dengan memuat dokumen yang ingin Anda tandatangani:

```csharp
string filePath = "sample.pdf"; // Jalur menuju dokumen Anda
string fileName = Path.GetFileName(filePath);
```

## Langkah 2: Tentukan Jalur File Output

Berikutnya, atur jalur file keluaran tempat dokumen yang ditandatangani akan disimpan:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Langkah 3: Buat Opsi Tanda Tangan

Konfigurasikan opsi untuk tanda tangan teks Anda, termasuk konten, posisi, ukuran, warna, dan gaya font:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // Posisi X
    Top = 200, // Posisi Y
    Width = 100, // Lebar tanda tangan
    Height = 30, // Tinggi tanda tangan
    ForeColor = Color.Red, // Warna teks
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Pengaturan font
};
```

## Langkah 4: Tandatangani Dokumen

Terakhir, gunakan GroupDocs.Signature untuk menerapkan tanda tangan teks dan menyimpan dokumen yang ditandatangani:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Tanda tangani dokumennya
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Kesimpulan

Dalam tutorial ini, kami menunjukkan cara menambahkan tanda tangan teks ke dokumen secara terprogram menggunakan GroupDocs.Signature for .NET. Dengan mengikuti langkah-langkah ini, Anda dapat meningkatkan keamanan dan keaslian dokumen Anda secara efisien.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan tanda tangan teks?
Ya, Anda dapat menyesuaikan berbagai atribut seperti warna, font, ukuran, dan posisi tanda tangan teks agar sesuai dengan kebutuhan Anda.

### Apakah GroupDocs.Signature kompatibel dengan berbagai format dokumen?
Tentu saja! GroupDocs.Signature mendukung berbagai format, termasuk PDF, Word, Excel, PowerPoint, dan banyak lagi.

### Bisakah saya menambahkan beberapa tanda tangan teks ke satu dokumen?
Ya, Anda dapat menambahkan beberapa tanda tangan teks, masing-masing dengan opsi penyesuaiannya sendiri.

### Apakah GroupDocs.Signature memastikan integritas dokumen setelah penandatanganan?
Ya, perpustakaan menggunakan algoritma kriptografi yang kuat untuk memastikan integritas dokumen dan mencegah gangguan setelah penandatanganan.

### Apakah ada versi uji coba yang tersedia untuk pengujian sebelum membeli?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/) untuk menjelajahi fitur sebelum melakukan pembelian.