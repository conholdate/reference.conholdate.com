---
title: Menambahkan Daftar Isi ke Dokumen PDF
linktitle: Menambahkan Daftar Isi ke Dokumen PDF
second_title: Referensi API Aspose.PDF untuk .NET
description: Tutorial ini menunjukkan cara menambahkan Daftar Isi (TOC) ke dokumen PDF menggunakan Aspose.Pdf untuk .NET.
type: docs
weight: 40
url: /id/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Perkenalan

Membuat daftar isi (TOC) dalam dokumen PDF dapat meningkatkan navigasi dan aksesibilitasnya. Dalam panduan ini, kami akan menunjukkan cara menambahkan TOC ke file PDF menggunakan Aspose.Pdf untuk .NET.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

1.   Aspose.PDF untuk .NET: Unduh dan instal versi terbaru dari[Di Sini](https://releases.aspose.com/pdf/net/).
2.  Lingkungan Pengembangan: Siapkan lingkungan pengembangan .NET seperti Visual Studio.
3.   Lisensi: Minta lisensi sementara jika diperlukan; silakan kunjungi[Halaman Lisensi Aspose.Pdf](https://asposepdf.com/developers) untuk informasi lebih lanjut.

Mengimpor Pustaka yang Diperlukan

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Langkah 1: Muat Dokumen PDF

Muat berkas PDF yang sudah ada di tempat Anda ingin menambahkan TOC. Tentukan jalur ke direktori dokumen Anda.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Langkah 2: Masukkan Halaman Baru untuk Daftar Isi

Sisipkan halaman baru di awal dokumen PDF. Halaman ini akan berfungsi sebagai Daftar Isi (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Langkah 3: Buat Objek Informasi TOC

Buat objek yang akan mewakili informasi TOC. Tambahkan judul dan tautan ke objek tersebut untuk navigasi yang lebih baik.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Langkah 4: Tentukan Elemen Daftar Isi

Tentukan elemen (atau judul) yang akan ditampilkan di TOC. Elemen-elemen ini dapat membantu pembaca menavigasi ke bagian-bagian tertentu dari dokumen.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Langkah 5: Buat Judul Daftar Isi

Buat judul untuk dua elemen pertama dalam TOC. Judul-judul ini akan ditautkan ke halaman masing-masing.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Langkah 6: Simpan PDF dengan TOC

Terakhir, simpan berkas PDF yang telah diperbarui.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Pesan Konfirmasi

Menampilkan pesan konfirmasi untuk memberi tahu pengguna bahwa proses telah selesai.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Kesimpulan

Dengan Aspose.PDF untuk .NET, menambahkan Daftar Isi ke PDF tidak hanya mudah tetapi juga dapat disesuaikan. Baik Anda perlu membuat tautan navigasi sederhana atau struktur yang rumit, alat ini dapat membantu Anda. Jadi, lain kali Anda mengerjakan PDF yang panjang, jangan lupa untuk menambahkan Daftar Isi untuk sentuhan profesional.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan TOC di Aspose.PDF?

Ya, Anda dapat sepenuhnya menyesuaikan tampilan TOC, termasuk gaya font, ukuran, dan perataan.

### Bagaimana cara menambahkan subjudul ke Daftar Isi?

 Anda dapat menambahkan subjudul dengan menyesuaikan`Heading` tingkat (misalnya,`Heading(2)`).

### Apakah mungkin untuk memperbarui TOC secara otomatis jika dokumen berubah?

Tidak, TOC tidak akan diperbarui secara otomatis. Anda perlu membuatnya ulang jika struktur dokumen berubah.

### Bisakah saya menautkan entri TOC ke dokumen eksternal?

Ya, Anda dapat menggunakan hyperlink untuk menautkan entri TOC ke PDF atau URL eksternal.

### Apakah Aspose.PDF mendukung TOC multi-level?

Ya, Aspose.PDF mendukung TOC multi-level untuk dokumen kompleks dengan sub-bagian.
