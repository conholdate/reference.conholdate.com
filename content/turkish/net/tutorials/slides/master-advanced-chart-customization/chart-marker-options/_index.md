---
title: Aspose.Slides .NET'te Veri Noktasında Grafik İşaretleyici Seçenekleri
linktitle: Aspose.Slides .NET'te Veri Noktasında Grafik İşaretleyici Seçenekleri
second_title: Aspose.Slides .NET PowerPoint İşleme API'si
description: Aspose.Slides for .NET kullanarak PowerPoint grafiklerinizi özelleştirilmiş işaretleyici seçenekleriyle nasıl geliştireceğinizi öğrenin. Bu adım adım kılavuz ön koşulları, grafik oluşturmayı, veri noktası biçimlendirmeyi ve daha fazlasını kapsar.
type: docs
weight: 11
url: /tr/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## giriiş

Sunumlara görsel yardımcılar eklemek etkili iletişim için olmazsa olmazdır. Aspose.Slides for .NET, grafikleri oluşturmak ve özelleştirmek için sağlam araçlar sunar ve geliştiricilerin veri sunumlarını geliştirmelerine olanak tanır. Öne çıkan özelliklerden biri, profesyonel görünümlü grafikler için hassas özelleştirmeye olanak tanıyan veri noktalarında grafik işaretleyici seçenekleri kullanma yeteneğidir. Bu makale, bunu başarmak için gereken her adımda size yol gösterecektir.

## Ön koşullar

Devam etmeden önce aşağıdakileri sağlayın:

-  .NET için Aspose.Slides Yüklendi: Buradan indirin[Burada](https://releases.aspose.com/slides/net/).
- Temel Kurulum: Çalışma dizininizde "Test.pptx" gibi bir sunum dosyası.
- Geliştirme Ortamı: .NET için yapılandırılmış Visual Studio veya eşdeğeri.

## Gerekli Ad Alanlarını İçe Aktarma

Sorunsuz geliştirme için projenize gerekli ad alanlarını ekleyin:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Adım 1: Sununuzda Bir Grafik Oluşturun

Sunumunuzun ilk slaydında varsayılan bir grafik oluşturarak başlayın:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Bu bir şey ekler`LineWithMarkers` Belirtilen ölçülerde grafiğinizi slaydınıza ekleyin.

## Adım 2: Grafik Veri Çalışma Sayfası Dizinini Alın

Varsayılan grafik veri çalışma sayfası dizini, daha fazla özelleştirme için önemlidir:

```csharp
int defaultWorksheetIndex = 0;
```

## Adım 3: Grafik Veri Çalışma Kitabına Erişim

Grafik verilerini düzenlemek için ilişkili çalışma kitabını alın:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Adım 4: Grafik Serilerini Yapılandırın ve Veri Noktalarını Ekleyin

Varsayılan seriyi temizleyin ve seriniz için yeni veri noktaları ekleyin:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Seriye veri noktaları ekleyin
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Adım 5: Veri Noktası İşaretleyicilerine Resim Dolguları Uygulayın

Özel görseller veri işaretleyicilerini görsel olarak çekici hale getirebilir:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// İşaretleyiciler için özel resimler ayarlayın
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Adım 6: İşaretçi Boyutunu Özelleştirin

Görünürlüğü artırmak için işaretçilerin boyutunu değiştirin:

```csharp
series.Marker.Size = 20;
```

## Adım 7: Güncellenen Sunumu Kaydedin

Özelleştirilmiş sunumu istediğiniz yere kaydedin:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Çözüm

Aspose.Slides for .NET, geliştiricilere zengin özelleştirme seçenekleriyle profesyonel grafikler oluşturmaları için araçlar sağlar. Grafik işaretleyici seçeneklerinden yararlanarak sunumlarınızın görsel çekiciliğini ve netliğini önemli ölçüde artırabilirsiniz. Bu adım adım kılavuz, karmaşık özelleştirmelerin bile uygulanmasının kolay olmasını sağlar.

## SSS

### İşaretçi özelleştirmesi için herhangi bir resim formatını kullanabilir miyim?
Evet, Aspose.Slides işaretçi özelleştirmesi için JPEG, PNG ve BMP dahil olmak üzere çeşitli resim formatlarını destekler.

### Grafik türünü oluşturduktan sonra nasıl değiştirebilirim?
 Grafik türünü değiştirmek için şuraya erişin:`chart.Type` mülkiyet ve farklı bir atama`ChartType`.

### Aspose.Slides for .NET eski PowerPoint sürümleriyle uyumlu mudur?
Evet, eski PowerPoint formatlarıyla geriye dönük uyumluluğu destekleyerek çok yönlülüğü garanti altına alır.

### Grafik verilerini dinamik olarak güncelleyebilir miyim?
 Kesinlikle. Şunu kullanın:`IChartDataWorkbook` grafik verilerini programlı olarak güncellemek için.

### Daha fazla kaynağı nerede bulabilirim?
 Keşfedin[Aspose.Slides belgeleri](https://reference.aspose.com/slides/net/)veya katılın[topluluk forumları](https://forum.aspose.com/) destek için.