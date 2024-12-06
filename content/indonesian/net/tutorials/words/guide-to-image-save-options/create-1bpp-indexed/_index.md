---
title: Buat 1Bpp Terindeks
linktitle: Buat 1Bpp Terindeks
second_title: API Pemrosesan Dokumen Aspose.Words
description: Panduan ini menyediakan petunjuk langkah demi langkah dan contoh kode untuk membantu Anda membuat gambar terindeks 1Bpp secara efisien untuk tujuan pengarsipan, pencetakan, atau penghematan ruang.
type: docs
weight: 10
url: /id/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Perkenalan

Pernahkah Anda perlu mengonversi dokumen Word menjadi gambar hitam putih? Baik untuk pengarsipan digital, pencetakan, atau sekadar menghemat ruang, mengonversi dokumen Anda menjadi gambar berindeks 1Bpp bisa sangat berguna. Dalam panduan ini, kami akan membahas metode mudah untuk mencapainya menggunakan Aspose.Words untuk .NET. Mari kita mulai!

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

-  Aspose.Words untuk .NET: Unduh dan instal pustaka dari[Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan .NET: Meskipun Visual Studio merupakan pilihan yang populer, IDE apa pun yang mendukung .NET akan berfungsi.
- Pengetahuan Dasar C#: Keakraban dengan C# akan membantu, tetapi kita akan membuatnya tetap sederhana.
- Contoh Dokumen Word: Siapkan dokumen untuk konversi.

## Langkah 1: Impor Namespace yang Diperlukan

Untuk menggunakan Aspose.Words, Anda perlu mengimpor namespace yang relevan. Hal ini penting untuk mengakses kelas dan metode yang diperlukan untuk manipulasi dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 2: Siapkan Direktori Dokumen Anda

Tentukan jalur ke direktori tempat dokumen Word Anda disimpan dan tempat Anda ingin menyimpan gambar yang dikonversi.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Langkah 3: Muat Dokumen Word

Muat dokumen Word Anda ke dalam`Aspose.Words.Document` objek. Objek ini memungkinkan Anda untuk memanipulasi dokumen secara terprogram.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 4: Konfigurasikan Opsi Penyimpanan Gambar

 Selanjutnya, atur`ImageSaveOptions` untuk menentukan bagaimana dokumen akan disimpan sebagai gambar. Kami akan mengonfigurasinya untuk disimpan dalam format PNG dengan mode warna indeks 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Konversi hanya halaman pertama
    ImageColorMode = ImageColorMode.BlackAndWhite, // Diatur ke hitam dan putih
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Gunakan format indeks 1Bpp
};
```

- SaveFormat.Png: Menentukan bahwa format keluaran akan menjadi PNG.
- PageSet(1): Menunjukkan bahwa hanya halaman pertama dokumen yang akan dikonversi.
- ImageColorMode.BlackAndWhite: Memastikan gambar hitam putih.
- ImagePixelFormat.Format1bppIndexed: Mengatur format piksel ke indeks 1Bpp, mengoptimalkan ruang.

## Langkah 5: Simpan Dokumen sebagai Gambar

 Terakhir, gunakan`Save` metode dari`Document` objek untuk menyimpan gambar yang dikonversi.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Kesimpulan

Selamat! Anda telah berhasil mengonversi dokumen Word menjadi gambar terindeks 1Bpp menggunakan Aspose.Words untuk .NET. Metode ini tidak hanya efisien tetapi juga membantu Anda membuat gambar kontras tinggi yang sesuai untuk berbagai aplikasi. Jangan ragu untuk mengintegrasikan fungsionalitas ini ke dalam proyek Anda. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu gambar terindeks 1Bpp?
Citra berindeks 1Bpp (1 Bit Per Pixel) adalah format citra hitam putih yang tiap pikselnya direpresentasikan oleh satu bit, baik 0 maupun 1. Format ini sangat hemat ruang, sehingga ideal untuk pengarsipan.

### Bisakah saya mengonversi beberapa halaman dokumen Word sekaligus?
 Ya! Cukup ubah`PageSet` properti di`ImageSaveOptions` untuk menyertakan beberapa halaman atau mengaturnya untuk mengonversi seluruh dokumen.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?
 Ya, lisensi diperlukan untuk fungsionalitas penuh. Anda dapat memperoleh lisensi[lisensi sementara di sini](https://purchase.aspose.com/temporary-license/).

### Format gambar apa lagi yang dapat saya ubah ke dokumen Word saya?
 Aspose.Words mendukung berbagai format, termasuk JPEG, BMP, dan TIFF. Cukup ubah`SaveFormat`di dalam`ImageSaveOptions` ke format yang Anda inginkan.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?
 Untuk dokumentasi lengkap, kunjungi[Halaman dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/).