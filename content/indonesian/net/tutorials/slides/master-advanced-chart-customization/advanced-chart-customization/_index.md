---
title: Kustomisasi Bagan Lanjutan dengan Aspose.Slides untuk .NET
linktitle: Kustomisasi Bagan Lanjutan dengan Aspose.Slides untuk .NET
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Manfaatkan sepenuhnya potensi Aspose.Slides untuk .NET dengan menguasai teknik kustomisasi bagan tingkat lanjut. Panduan langkah demi langkah ini mencakup semuanya, mulai dari pembuatan bagan dasar hingga detail rumit seperti garis kisi, judul sumbu, dan warna khusus.
type: docs
weight: 10
url: /id/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Perkenalan

Membuat bagan yang menarik secara visual dan informatif sangat penting untuk penyajian data yang efektif. Aspose.Slides for .NET menawarkan berbagai alat canggih untuk kustomisasi bagan, yang memungkinkan Anda untuk menyesuaikan setiap aspek bagan Anda. Dalam tutorial ini, kita akan menjelajahi berbagai teknik lanjutan untuk kustomisasi bagan menggunakan Aspose.Slides for .NET.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

1.  Pustaka Aspose.Slides untuk .NET: Unduh dan instal pustaka Aspose.Slides dari[Di Sini](https://releases.aspose.com/slides/net/).
2. Lingkungan Pengembangan .NET: Siapkan lingkungan pengembangan .NET, seperti Visual Studio.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan bermanfaat, karena kita akan menulis kode C#.

Sekarang, mari kita uraikan proses penyesuaian grafik tingkat lanjut ke dalam langkah-langkah yang jelas.

## Langkah 1: Buat Presentasi Baru

Mulailah dengan membuat presentasi baru untuk menampung bagan Anda.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "Your Document Directory";

// Buat direktori jika belum ada.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Membuat contoh presentasi
Presentation pres = new Presentation();
```

## Langkah 2: Akses Slide Pertama

Berikutnya, akses slide pertama di mana Anda ingin menambahkan bagan.

```csharp
// Akses slide pertama
ISlide slide = pres.Slides[0];
```

## Langkah 3: Tambahkan Bagan Contoh

Sekarang, mari tambahkan diagram garis dengan penanda ke slide.

```csharp
// Tambahkan contoh bagan
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Langkah 4: Tetapkan Judul Bagan

Menetapkan judul untuk bagan Anda memberikan konteks yang penting.

```csharp
// Mengatur judul grafik
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Langkah 5: Sesuaikan Garis Grid Utama

Anda dapat meningkatkan garis kisi untuk sumbu nilai agar lebih mudah dibaca.

```csharp
// Sesuaikan garis kisi utama untuk sumbu nilai
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Langkah 6: Sesuaikan Garis Grid Kecil

Demikian pula, sesuaikan garis kisi minor untuk sumbu nilai.

```csharp
// Sesuaikan garis kisi minor untuk sumbu nilai
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Langkah 7: Tentukan Format Angka Sumbu Nilai

Anda dapat memformat angka yang ditampilkan pada sumbu nilai.

```csharp
// Atur format angka sumbu nilai
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Langkah 8: Tetapkan Nilai Maksimum dan Minimum

Tentukan nilai maksimum dan minimum untuk bagan.

```csharp
// Tetapkan nilai maksimum dan minimum grafik
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Langkah 9: Sesuaikan Properti Teks Sumbu Nilai

Meningkatkan properti teks pada sumbu nilai meningkatkan keterbacaan.

```csharp
// Sesuaikan Properti Teks Sumbu Nilai
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Langkah 10: Tambahkan Judul Sumbu Nilai

Menambahkan judul pada sumbu nilai dapat memperjelas apa yang diwakili oleh data.

```csharp
// Tetapkan judul sumbu nilai
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Langkah 11: Sesuaikan Garis Grid Utama untuk Sumbu Kategori

Sekarang, mari tingkatkan garis kisi utama untuk sumbu kategori.

```csharp
// Sesuaikan Garis Kisi Utama untuk sumbu Kategori
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Langkah 12: Sesuaikan Garis Kisi Minor untuk Sumbu Kategori

Demikian pula, sesuaikan garis kisi minor untuk sumbu kategori.

```csharp
// Sesuaikan Garis Kisi Minor untuk sumbu Kategori
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Langkah 13: Sesuaikan Properti Teks Sumbu Kategori

Tingkatkan gaya font dan tampilan label sumbu kategori.

```csharp
// Sesuaikan Properti Teks Sumbu Kategori
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Langkah 14: Tambahkan Judul Sumbu Kategori

Jika diperlukan, Anda juga dapat menambahkan judul untuk sumbu kategori.

```csharp
// Tetapkan Judul Sumbu Kategori
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Langkah 15: Kustomisasi Tambahan

Tingkatkan bagan Anda lebih jauh dengan penyesuaian tambahan, seperti legenda, warna dinding, dan pengaturan area plot.

```csharp
// Kustomisasi Tambahan (Opsional)

// Sesuaikan Properti Teks Legenda
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Tampilkan legenda bagan tanpa bagan yang tumpang tindih
chart.Legend.Overlay = true;

// Mengatur warna dinding belakang grafik
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Atur warna lantai grafik
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Atur warna area Plot
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Simpan presentasi
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Kesimpulan

Dalam panduan lengkap ini, kami membahas teknik kustomisasi bagan tingkat lanjut menggunakan Aspose.Slides for .NET. Anda mempelajari cara membuat presentasi, menambahkan bagan, menyempurnakan tampilannya, dan mengkustomisasi berbagai elemen bagan seperti garis kisi, label sumbu, dan legenda. 

## Pertanyaan yang Sering Diajukan

### Versi .NET apa yang didukung oleh Aspose.Slides untuk .NET?
Aspose.Slides untuk .NET mendukung berbagai versi .NET, termasuk .NET Framework dan .NET Core. Lihat dokumentasi untuk daftar lengkap versi yang didukung.

### Bisakah saya membuat bagan dari sumber data seperti file Excel?
Ya, Aspose.Slides memungkinkan Anda membuat bagan dari sumber data eksternal seperti lembar kerja Excel. Lihat dokumentasi untuk contoh terperinci.

### Bagaimana cara menambahkan label data khusus ke rangkaian bagan saya?
 Untuk menambahkan label data khusus, akses`DataLabels` properti seri dan sesuaikan label sesuai kebutuhan. Anda dapat menemukan contoh kode dalam dokumentasi.

### Apakah mungkin untuk mengekspor grafik ke format lain, seperti PDF atau gambar?
Tentu saja! Aspose.Slides memungkinkan Anda mengekspor presentasi Anda dengan diagram ke berbagai format, termasuk format PDF dan gambar.

### Di mana saya dapat menemukan lebih banyak tutorial dan contoh untuk Aspose.Slides for .NET?
 Kunjungi Aspose.Slides[situs web](https://reference.aspose.com/slides/net/) untuk tutorial lengkap, contoh kode, dan dokumentasi.