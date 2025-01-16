---
title: Aspose.Slides for .NET ile Grafiklerden Çalışma Kitabı Verilerini Çıkarma
linktitle: Aspose.Slides for .NET ile Grafiklerden Çalışma Kitabı Verilerini Çıkarma
second_title: Aspose.Slides .NET PowerPoint İşleme API'si
description: Aspose.Slides for .NET kullanarak grafiklerden çalışma kitabı verilerini nasıl kurtaracağınızı öğrenerek PowerPoint sunumlarınızın potansiyelini açığa çıkarın. Bu adım adım eğitim, grafik verilerini etkili bir şekilde çıkarmanızı ve kullanmanızı kolaylaştırarak sizi süreç boyunca yönlendirir.
type: docs
weight: 12
url: /tr/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## giriiş

PowerPoint sunumlarıyla çalışmak, özellikle gömülü grafiklerden değerli veriler çıkarırken zorlayıcı olabilir. Neyse ki, .NET için Aspose.Slides bu süreci basitleştiren sağlam bir çözüm sunar. Bu eğitimde, bir PowerPoint sunumundaki bir grafikten bir çalışma kitabını nasıl kurtaracağınız konusunda adım adım size rehberlik edeceğiz.

## Ön koşullar

Koda geçmeden önce aşağıdakilerin hazır olduğundan emin olun:

### .NET için Aspose.Slides

Geliştirme ortamınızda .NET için Aspose.Slides'ın yüklü olması gerekir. Bunu henüz yapmadıysanız, web sitesinden indirebilirsiniz:

[.NET için Aspose.Slides'ı indirin](https://releases.aspose.com/slides/net/)

### PowerPoint Sunumu

PowerPoint sunum dosyanızı, özellikle kurtarmak istediğiniz ilişkili verileri içeren bir grafik içeren dosyayı elinizin altında bulundurun.

## Adım 1: Gerekli Ad Alanlarını İçe Aktarın

Aspose.Slides ile etkili bir şekilde çalışmak için öncelikle gerekli ad alanlarını içe aktarmanız gerekir:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Adım 2: Belge Dizinini Tanımlayın

Sunum dosyanızın bulunduğu dizini belirtin:

```csharp
string dataDir = "Your Document Directory"; // Bu yolu gerektiği gibi ayarlayın
```

## Adım 3: Sunumu Yükleyin

Çalışma kitabı kurtarmayı grafiğin önbelleğinden etkinleştirirken PowerPoint sunumunu yükleyebilirsiniz. Bunu nasıl yapacağınız aşağıda açıklanmıştır:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // Grafik verilerine erişin ve bunlarla çalışın
    // Kodunuz buraya gelecek
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 Bu adımda,`LoadOptions` nesne, çalışma kitabı kurtarmayı etkinleştirmenize olanak tanır`RecoverWorkbookFromChartCache` mülk.

## Adım 4: Tabloyu Alın ve Çalışma Kitabına Erişin

Şimdi grafiğin derinliklerine inip ilişkili verileri alma zamanı:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // Gerektiğinde endeksi ayarlayın
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// Artık çalışma kitabı verileriyle gereksinimlerinize göre çalışabilirsiniz
```

İlk slaydın ilk şekline (bir grafik olması bekleniyor) erişerek, grafik veri çalışma kitabını elde edersiniz ve verileri gerektiği gibi işleyebilir veya çıkarabilirsiniz.

## Çözüm

Bu eğitimde, Aspose.Slides for .NET kullanarak bir PowerPoint sunumundaki bir grafikten bir çalışma kitabını etkili bir şekilde nasıl kurtaracağınızı gösterdik. Bu adımları izleyerek, analitik ihtiyaçlarınız için grafik verilerini kolayca çıkarabilir ve kullanabilirsiniz.

## SSS

### Aspose.Slides for .NET nedir?

Aspose.Slides for .NET, geliştiricilerin Microsoft PowerPoint sunumlarını programlı bir şekilde oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan güçlü bir kütüphanedir.

### Satın almadan önce Aspose.Slides for .NET'i deneyebilir miyim?

 Evet! Aspose, .NET için Aspose.Slides'ın ücretsiz deneme sürümünü sunar. Satın alma yapmadan önce yeteneklerini değerlendirebilirsiniz.[Ücretsiz denemeyi buradan edinin](https://releases.aspose.com/).

### Aspose.Slides for .NET'in belgelerini nerede bulabilirim?

 Aspose.Slides for .NET için kapsamlı belgelere erişebilirsiniz[Burada](https://reference.aspose.com/slides/net/)Örnekler ve API referansları içeren .

### Aspose.Slides for .NET için lisans nasıl satın alabilirim?

 Lisans satın almak için Aspose web sitesini ziyaret edin ve aşağıdaki bağlantıyı kullanın:[.NET için Aspose.Slides'ı satın alın](https://purchase.aspose.com/buy).