---
title: Membuat Bookmark di Dokumen Word dengan Aspose.Words untuk .NET
linktitle: Membuat Bookmark di Dokumen Word dengan Aspose.Words untuk .NET
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyempurnakan dokumen Word Anda dengan membuat dan mengelola bookmark menggunakan Aspose.Words untuk .NET. Panduan tutorial langkah demi langkah ini.
type: docs
weight: 10
url: /id/net/tutorials/words/mastering-bookmarks/create-bookmark-in-word-document/
---
## Perkenalan

Menjelajahi dokumen besar bisa jadi sulit, tetapi bookmark memudahkan Anda! Tutorial ini akan memandu Anda membuat bookmark dalam dokumen Word menggunakan Aspose.Words untuk .NET. Anda akan mempelajari langkah demi langkah cara menyiapkan dokumen, menambahkan bookmark, dan menyimpannya sebagai PDF. Mari kita mulai!

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

1.  Aspose.Words untuk Pustaka .NET: Unduh dan instal dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Gunakan Visual Studio atau IDE apa pun yang kompatibel dengan .NET.
3. Pengetahuan Dasar C#: Keakraban dengan konsep pemrograman C# akan sangat membantu.

## Mengimpor Ruang Nama

Pertama, impor namespace yang diperlukan untuk bekerja dengan Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Dokumen dan DocumentBuilder

 Buat dokumen baru dan inisialisasi`DocumentBuilder`, yang memungkinkan Anda menambahkan konten dan penanda.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Buat Bookmark Utama

Untuk membuat bookmark, Anda perlu menentukan titik awal dan titik akhir. Berikut cara membuat bookmark bernama "My Bookmark":

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside the main bookmark.");
```
- `StartBookmark`: Menandai awal penanda buku.
- `Writeln`: Menambahkan teks dalam penanda buku.

## Langkah 3: Buat Bookmark Bersarang

Anda dapat menumpuk bookmark untuk pengaturan yang lebih baik. Berikut cara menambahkan "Bookmark Bertumpuk" di dalam "Bookmark Saya":

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside the nested bookmark.");
builder.EndBookmark("Nested Bookmark");
```
- Nesting memungkinkan Anda membuat struktur hierarkis. 
- `EndBookmark`: Menutup penanda saat ini.

## Langkah 4: Tambahkan Teks di Luar Bookmark Bersarang

Setelah membuat penanda bersarang, lanjutkan menambahkan konten dalam penanda utama:

```csharp
builder.Writeln("Text after the nested bookmark.");
builder.EndBookmark("My Bookmark");
```
Ini memastikan bahwa penanda utama mencakup penanda bertingkat dan teks tambahan apa pun.

## Langkah 5: Konfigurasikan Opsi Penyimpanan PDF

Untuk menyertakan bookmark dalam PDF, konfigurasikan opsi penyimpanan:

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```
- `PdfSaveOptions`: Menentukan bagaimana dokumen disimpan sebagai PDF.
- `BookmarksOutlineLevels`: Mengatur hierarki penanda dalam PDF.

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen sebagai PDF:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```
 Itu`Save` metode menyimpan dokumen dalam format dan lokasi yang ditentukan, lengkap dengan penanda halaman.

## Kesimpulan

Membuat bookmark dalam dokumen Word dengan Aspose.Words untuk .NET itu mudah dan meningkatkan navigasi dokumen. Baik Anda membuat laporan, eBook, atau mengelola dokumen yang banyak, bookmark sangatlah berguna. Ikuti tutorial ini, dan Anda akan memiliki PDF yang tertata rapi dan memiliki bookmark dalam waktu singkat!

## Pertanyaan yang Sering Diajukan

### Bisakah saya membuat beberapa penanda pada level yang berbeda?
Ya! Anda dapat membuat beberapa penanda halaman dan menentukan hierarkinya saat menyimpan sebagai PDF.

### Bagaimana cara memperbarui teks penanda buku?
 Menggunakan`DocumentBuilder.MoveToBookmark`untuk menavigasi ke penanda dan memperbarui teks.

### Apakah mungkin untuk menghapus penanda buku?
 Tentu saja! Gunakan`Bookmarks.Remove` metode dengan menentukan nama penanda.

### Bisakah saya membuat penanda buku dalam format lain selain PDF?
Ya, Aspose.Words mendukung bookmark dalam format seperti DOCX, HTML, dan EPUB.

### Bagaimana saya dapat memastikan penanda buku muncul dengan benar dalam PDF?
 Mendefinisikan`BookmarksOutlineLevels` benar di`PdfSaveOptions` untuk memastikan penanda buku disertakan dalam kerangka PDF.