---
title: Ekstrak Data Buku Kerja dari Bagan dengan Aspose.Slides untuk .NET
linktitle: Ekstrak Data Buku Kerja dari Bagan dengan Aspose.Slides untuk .NET
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Manfaatkan potensi presentasi PowerPoint Anda dengan mempelajari cara memulihkan data buku kerja dari bagan menggunakan Aspose.Slides for .NET. Tutorial langkah demi langkah ini memandu Anda melalui prosesnya, sehingga memudahkan Anda mengekstrak dan memanfaatkan data bagan secara efektif.
type: docs
weight: 12
url: /id/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## Perkenalan

Bekerja dengan presentasi PowerPoint bisa jadi menantang, terutama saat mengekstrak data penting dari bagan yang disematkan. Untungnya, Aspose.Slides for .NET menyediakan solusi tangguh yang menyederhanakan proses ini. Dalam tutorial ini, kami akan memandu Anda langkah demi langkah tentang cara memulihkan buku kerja dari bagan dalam presentasi PowerPoint.

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda telah menyiapkan hal berikut:

### Aspose.Slides untuk .NET

Anda perlu memasang Aspose.Slides for .NET di lingkungan pengembangan Anda. Jika Anda belum melakukannya, Anda dapat mengunduhnya dari situs web:

[Unduh Aspose.Slides untuk .NET](https://releases.aspose.com/slides/net/)

### Presentasi PowerPoint

Siapkan berkas presentasi PowerPoint Anda, khususnya yang berisi bagan dengan data terkait yang ingin Anda pulihkan.

## Langkah 1: Impor Namespace yang Diperlukan

Untuk bekerja secara efektif dengan Aspose.Slides, pertama-tama Anda perlu mengimpor namespace yang diperlukan:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Langkah 2: Tentukan Direktori Dokumen

Tentukan direktori tempat file presentasi Anda berada:

```csharp
string dataDir = "Your Document Directory"; // Sesuaikan jalur ini sesuai kebutuhan
```

## Langkah 3: Muat Presentasi

Anda dapat memuat presentasi PowerPoint sambil mengaktifkan pemulihan buku kerja dari cache bagan. Berikut cara melakukannya:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // Akses dan bekerja dengan data grafik
    // Kode Anda akan berada di sini
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 Pada langkah ini,`LoadOptions` objek memungkinkan Anda mengaktifkan pemulihan buku kerja menggunakan`RecoverWorkbookFromChartCache` milik.

## Langkah 4: Ambil Bagan dan Akses Buku Kerjanya

Sekarang saatnya untuk menggali grafik dan mengambil data terkaitnya:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // Sesuaikan indeks sesuai kebutuhan
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// Sekarang Anda dapat bekerja dengan data buku kerja sesuai kebutuhan Anda
```

Dengan mengakses bentuk pertama dari slide pertama (yang diharapkan berupa bagan), Anda memperoleh buku kerja data bagan dan dapat memanipulasi atau mengekstrak data sebagaimana diperlukan.

## Kesimpulan

Dalam tutorial ini, kami menunjukkan cara memulihkan buku kerja secara efektif dari bagan dalam presentasi PowerPoint menggunakan Aspose.Slides for .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengekstrak dan memanfaatkan data bagan untuk kebutuhan analitis Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Slides untuk .NET?

Aspose.Slides untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi presentasi Microsoft PowerPoint secara terprogram.

### Dapatkah saya mencoba Aspose.Slides untuk .NET sebelum membeli?

 Ya! Aspose menawarkan versi uji coba gratis Aspose.Slides untuk .NET. Anda dapat mengevaluasi kemampuannya sebelum melakukan pembelian.[Dapatkan uji coba gratis di sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Slides for .NET?

 Anda dapat mengakses dokumentasi lengkap untuk Aspose.Slides untuk .NET[Di Sini](https://reference.aspose.com/slides/net/), yang mencakup contoh dan referensi API.

### Bagaimana cara membeli lisensi Aspose.Slides untuk .NET?

 Untuk membeli lisensi, kunjungi situs web Aspose dan gunakan tautan berikut:[Beli Aspose.Slides untuk .NET](https://purchase.aspose.com/buy).