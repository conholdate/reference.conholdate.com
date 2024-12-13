---
title: Mengonversi Metafile ke SVG
linktitle: Konversi Metafile ke SVG
second_title: API Pemrosesan Dokumen Aspose.Words
description: Temukan cara menyempurnakan dokumen Word Anda dengan mengonversi metafile ke SVG menggunakan pustaka Aspose.Words for .NET yang canggih. Tutorial komprehensif ini memandu Anda melalui setiap langkah, mulai dari menginisialisasi dokumen hingga memasukkan grafik SVG.
type: docs
weight: 10
url: /id/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-svg/
---
## Perkenalan

Halo, para penggemar coding! Pernahkah Anda ingin menyempurnakan dokumen Word Anda dengan grafik vektor yang dapat diskalakan? Jika ya, Anda berada di tempat yang tepat! Dalam tutorial ini, kita akan membahas cara mengonversi metafile ke SVG dalam dokumen Word Anda menggunakan pustaka Aspose.Words for .NET yang canggih. Pada akhirnya, Anda akan memiliki keterampilan untuk membuat dokumen Anda menarik secara visual dan serbaguna. Mari kita mulai!

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Unduh dari[Aspose merilis halaman](https://releases.aspose.com/words/net/).
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework.
3. Lingkungan Pengembangan: Anda dapat menggunakan IDE apa pun, seperti Visual Studio.
4. Pengetahuan Dasar C#: Keakraban dengan C# akan bermanfaat, tetapi jangan khawatir jika Anda baru—kami akan memandu Anda melalui setiap langkah.

## Mengimpor Ruang Nama

Pertama, mari impor namespace yang diperlukan dalam proyek C# Anda. Langkah ini penting untuk mengakses fungsi Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Setelah prasyarat dan namespace kita beres, mari beralih ke panduan langkah demi langkah untuk mengonversi metafile ke SVG.

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

 Kita akan mulai dengan membuat dokumen Word baru dan menginisialisasi`DocumentBuilder` objek, yang akan membantu kami menambahkan konten.

```csharp
// Tentukan jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Kode ini menginisialisasi dokumen baru dan pembangun dokumen.`dataDir` Variabel ini menyimpan jalur tempat Anda menyimpan berkas.

## Langkah 2: Tambahkan Teks ke Dokumen

Berikutnya, mari tambahkan beberapa konteks ke dokumen kita dengan deskripsi teks.

```csharp
builder.Write("Here is an SVG image: ");
```

Baris ini menambahkan teks "Berikut adalah gambar SVG: " ke dokumen Anda, menyediakan konteks untuk SVG yang akan Anda masukkan.

## Langkah 3: Masukkan Gambar SVG

Sekarang tibalah bagian yang menarik! Kita akan memasukkan gambar SVG ke dalam dokumen kita menggunakan`InsertHtml` metode.

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg>");
```

Cuplikan ini menyisipkan poligon SVG sederhana dengan titik dan gaya yang ditentukan. Jangan ragu untuk menyesuaikan kode SVG sesuai kebutuhan Anda!

## Langkah 4: Tentukan HtmlSaveOptions

 Untuk memastikan bahwa metafile kita disimpan sebagai SVG, kita akan mendefinisikan`HtmlSaveOptions` dan mengatur`MetafileFormat` properti untuk`HtmlMetafileFormat.Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

Konfigurasi ini memberitahu Aspose.Words untuk mengonversi metafile apa pun dalam dokumen ke format SVG saat mengekspor ke HTML.

## Langkah 5: Simpan Dokumen

 Terakhir, mari kita simpan dokumen kita menggunakan`Save` metode dari`Document`kelas.

```csharp
doc.Save(dataDir + "ConvertMetafilesToSvg.html", saveOptions);
```

 Baris ini menyimpan dokumen ke direktori yang ditentukan dengan nama file`ConvertMetafilesToSvg.html` , menerapkan`saveOptions` untuk memastikan metafile dikonversi ke SVG.

## Kesimpulan

Selamat! Anda telah berhasil mengonversi metafile ke SVG dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET. Hanya dengan beberapa baris kode, Anda dapat menyempurnakan dokumen Anda dengan grafik vektor yang dapat diskalakan, membuatnya lebih dinamis dan menarik secara visual. Cobalah di proyek Anda, dan selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka tangguh yang memungkinkan Anda membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram menggunakan C#.

### Dapatkah saya menggunakan Aspose.Words untuk .NET dengan .NET Core?
Tentu saja! Aspose.Words untuk .NET mendukung .NET Core, sehingga serbaguna untuk berbagai aplikasi .NET.

### Bagaimana saya bisa mendapatkan uji coba gratis Aspose.Words untuk .NET?
 Anda dapat mengunduh uji coba gratis dari[Aspose merilis halaman](https://releases.aspose.com/).

### Bisakah saya mengonversi format gambar lain ke SVG menggunakan Aspose.Words?
Ya, Aspose.Words mendukung konversi berbagai format gambar, termasuk metafile, ke SVG.

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Words untuk .NET?
 Dokumentasi terperinci tersedia di[Halaman dokumentasi Aspose](https://reference.aspose.com/words/net/).