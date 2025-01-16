---
title: Garis Tren dalam Grafik dengan Aspose.Slides untuk .NET
linktitle: Garis Tren dalam Grafik dengan Aspose.Slides untuk .NET
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Pelajari cara menambahkan dan menyesuaikan garis tren dalam bagan menggunakan Aspose.Slides for .NET. Panduan komprehensif ini mencakup garis tren eksponensial, linier, logaritmik, polinomial, dan rata-rata bergerak untuk menyempurnakan visualisasi data Anda.
type: docs
weight: 12
url: /id/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Perkenalan  

Menambahkan garis tren ke bagan merupakan teknik utama untuk menganalisis tren data dan memperkirakan nilai di masa mendatang. Dengan Aspose.Slides for .NET, Anda dapat menambahkan dan menyesuaikan garis tren ke bagan presentasi dengan mudah, sehingga meningkatkan visualisasi data Anda. Panduan ini menyediakan panduan terperinci untuk menambahkan garis tren ke berbagai jenis bagan dalam presentasi PowerPoint menggunakan Aspose.Slides for .NET.  

## Prasyarat  

Sebelum kita mulai implementasinya, pastikan Anda memiliki pengaturan berikut:  

1.  Aspose.Slides untuk .NET: Unduh dan instal pustaka dari[halaman unduhan](https://releases.aspose.com/slides/net/).  
2. Lingkungan Pengembangan: Gunakan IDE seperti Visual Studio untuk pengkodean.  
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# diperlukan untuk mengikuti tutorial ini.  

## Mengimpor Ruang Nama yang Diperlukan  

Untuk memulai, impor namespace penting ke dalam proyek Anda:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Langkah 1: Menyiapkan Presentasi  

Pertama, buat presentasi kosong. Ini akan berfungsi sebagai wadah untuk diagram Anda.  

```csharp
string dataDir = "Your/Documents/Directory";

// Pastikan direktori tersebut ada
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Buat presentasi baru
Presentation presentation = new Presentation();
```

## Langkah 2: Menambahkan Bagan ke Slide  

Sekarang, tambahkan slide dan sertakan bagan kolom berkelompok untuk memvisualisasikan data Anda.  

```csharp
// Tambahkan slide kosong
ISlide slide = presentation.Slides[0];

// Tambahkan bagan kolom berkelompok
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Langkah 3: Mengisi Data Bagan  

Isi bagan dengan data sampel.  

```csharp
// Mengakses buku kerja data grafik default
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Perbarui kategori default dan nilai seri
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Langkah 4: Menambahkan Garis Tren  

### Garis Tren Eksponensial  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Garis Tren Linier  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Garis Tren Logaritma  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Garis Tren Rata-rata Bergerak  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Garis Tren Polinomial  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Garis Tren Daya  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Langkah 5: Menyimpan Presentasi  

Terakhir, simpan presentasi dengan semua garis tren yang ditambahkan ke bagan Anda.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Kesimpulan  

Dengan menggunakan Aspose.Slides for .NET, menambahkan garis tren ke diagram Anda menjadi tugas yang mudah. Fitur ini memungkinkan Anda menyajikan tren data secara efektif dan menambahkan sentuhan profesional ke presentasi Anda. Ikuti langkah-langkah di atas untuk menggabungkan berbagai jenis garis tren dan meningkatkan visualisasi data Anda.  

## Pertanyaan yang Sering Diajukan  

### Bisakah saya menyesuaikan tampilan garis tren?  
 Ya, Anda dapat menyesuaikan warna, ketebalan, dan gaya garis tren menggunakan`Format.Line` milik.  

### Apakah ada dukungan untuk jenis grafik lainnya?  
Ya, Aspose.Slides untuk .NET mendukung berbagai jenis bagan, termasuk bagan batang, bagan pai, dan bagan garis.  

### Bagaimana cara menampilkan persamaan dan nilai R-kuadrat?  
 Memungkinkan`DisplayEquation` Dan`DisplayRSquaredValue` properti untuk garis tren untuk menampilkan nilai-nilai ini pada bagan.  

### Bisakah saya menggunakan Aspose.Slides untuk .NET dengan bahasa lain?  
Ya, pustaka ini kompatibel dengan bahasa apa pun yang mendukung .NET, termasuk VB.NET dan F#.  

### Di mana saya dapat menemukan dokumentasi lebih lanjut?  
 Kunjungi[Dokumentasi Aspose.Slides untuk .NET](https://reference.aspose.com/slides/net/) untuk informasi lebih lanjut.