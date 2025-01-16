---
title: Opsi Penanda Bagan pada Titik Data di Aspose.Slides .NET
linktitle: Opsi Penanda Bagan pada Titik Data di Aspose.Slides .NET
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Pelajari cara menyempurnakan bagan PowerPoint Anda dengan opsi penanda yang disesuaikan menggunakan Aspose.Slides for .NET. Panduan langkah demi langkah ini mencakup prasyarat, pembuatan bagan, pemformatan titik data, dan banyak lagi.
type: docs
weight: 11
url: /id/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Perkenalan

Memasukkan alat bantu visual ke dalam presentasi sangat penting untuk komunikasi yang berdampak. Aspose.Slides untuk .NET menyediakan alat yang tangguh untuk membuat dan menyesuaikan bagan, yang memungkinkan pengembang untuk menyempurnakan presentasi data mereka. Salah satu fitur yang menonjol adalah kemampuan untuk menggunakan opsi penanda bagan pada titik data, yang memungkinkan penyesuaian yang tepat untuk bagan yang tampak profesional. Artikel ini akan memandu Anda melalui setiap langkah yang diperlukan untuk mencapainya.

## Prasyarat

Sebelum melanjutkan, pastikan hal berikut:

-  Aspose.Slides untuk .NET Terpasang: Unduh dari[Di Sini](https://releases.aspose.com/slides/net/).
- Pengaturan Dasar: File presentasi, seperti "Test.pptx," di direktori kerja Anda.
- Lingkungan Pengembangan: Visual Studio atau setara, dikonfigurasi untuk .NET.

## Mengimpor Ruang Nama yang Diperlukan

Tambahkan namespace yang diperlukan ke proyek Anda untuk pengembangan yang lancar:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Langkah 1: Buat Bagan dalam Presentasi Anda

Mulailah dengan membuat bagan default pada slide pertama presentasi Anda:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Ini menambahkan`LineWithMarkers` bagan ke slide Anda dengan dimensi yang ditentukan.

## Langkah 2: Ambil Indeks Lembar Kerja Data Bagan

Indeks lembar kerja data grafik default sangat penting untuk penyesuaian lebih lanjut:

```csharp
int defaultWorksheetIndex = 0;
```

## Langkah 3: Akses Buku Kerja Data Bagan

Untuk memanipulasi data grafik, ambil buku kerja terkait:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Langkah 4: Konfigurasikan Seri Bagan dan Tambahkan Titik Data

Hapus seri default dan tambahkan titik data baru untuk seri Anda:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Tambahkan titik data ke seri
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Langkah 5: Terapkan Isi Gambar ke Penanda Titik Data

Gambar khusus dapat membuat penanda data menarik secara visual:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Tetapkan gambar khusus untuk penanda
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Langkah 6: Sesuaikan Ukuran Penanda

Ubah ukuran penanda untuk meningkatkan visibilitas:

```csharp
series.Marker.Size = 20;
```

## Langkah 7: Simpan Presentasi yang Diperbarui

Simpan presentasi yang disesuaikan ke lokasi yang Anda inginkan:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Kesimpulan

Aspose.Slides untuk .NET melengkapi pengembang dengan berbagai alat untuk membuat bagan profesional dengan berbagai opsi penyesuaian yang lengkap. Dengan memanfaatkan berbagai opsi penanda bagan, Anda dapat meningkatkan daya tarik visual dan kejelasan presentasi Anda secara signifikan. Panduan langkah demi langkah ini memastikan bahwa penyesuaian yang rumit pun mudah diterapkan.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan format gambar apa pun untuk kustomisasi penanda?
Ya, Aspose.Slides mendukung berbagai format gambar, termasuk JPEG, PNG, dan BMP, untuk kustomisasi penanda.

### Bagaimana cara mengubah jenis grafik setelah dibuat?
 Untuk mengubah jenis grafik, akses`chart.Type` properti dan menetapkan yang berbeda`ChartType`.

### Apakah Aspose.Slides untuk .NET kompatibel dengan versi PowerPoint yang lebih lama?
Ya, mendukung kompatibilitas mundur dengan format PowerPoint yang lebih lama, memastikan fleksibilitas.

### Bisakah saya memperbarui data grafik secara dinamis?
 Tentu saja. Gunakan`IChartDataWorkbook` untuk memperbarui data grafik secara terprogram.

### Di mana saya dapat menemukan lebih banyak sumber daya?
 Jelajahi[Dokumentasi Aspose.Slides](https://reference.aspose.com/slides/net/)atau bergabung dengan[forum komunitas](https://forum.aspose.com/) untuk dukungan.