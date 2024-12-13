---
title: Çalışma Kitabında Sıkıştırma Düzeyini Ayarlama
linktitle: Çalışma Kitabında Sıkıştırma Düzeyini Ayarlama
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells for .NET kullanarak sıkıştırma seviyelerini ayarlayarak büyük Excel dosyalarını nasıl verimli bir şekilde yöneteceğinizi keşfedin. Bu adım adım kılavuz, dizinleri ayarlamaktan sıkıştırma sürelerini ölçmeye kadar her şeyi kapsar ve dosya boyutunu optimize etmenize ve performansı artırmanıza yardımcı olur.
type: docs
weight: 14
url: /tr/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## giriiş

Büyük Excel dosyalarını yönetmek, özellikle depolama ve aktarım verimliliği söz konusu olduğunda zor olabilir. Neyse ki, dosya sıkıştırma bu dosyaların boyutunu önemli ölçüde azaltabilir ve bunları yönetmeyi kolaylaştırabilir. .NET için Aspose.Cells kullanıyorsanız, çalışma kitaplarınızın sıkıştırma seviyesini kolayca ayarlayabilirsiniz. Bu kılavuz, kodun her bir parçası için net açıklamalar sağlayarak sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

Koda dalmadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

1. Temel C# Bilgisi: C# programlamaya aşina olmak, kod parçacıklarını daha iyi anlamanıza yardımcı olacaktır.
2.  Aspose.Cells Kütüphanesi: Aspose.Cells kütüphanesini şu adresten indirin ve yükleyin:[Burada](https://releases.aspose.com/cells/net/).
3. Visual Studio: Kodun çalıştırılabilmesi için Visual Studio benzeri bir geliştirme ortamına ihtiyaç vardır.
4. .NET Framework: Projenizin .NET Framework'ün uyumlu bir sürümüyle kurulduğundan emin olun.

## Gerekli Paketleri İçe Aktarma

Başlamak için, C# projenize gerekli paketleri içe aktarmanız gerekir. Kod dosyanızın en üstüne aşağıdaki satırları ekleyin:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Bu paketler, Aspose.Cells kitaplığını kullanarak Excel dosyalarıyla çalışmak için gereklidir.`Aspose.Cells` namespace, Excel dosyalarını yönetmek için gereken tüm sınıfları içerirken`Aspose.Cells.Xlsb` dosyaları XLSB formatında kaydetmek için seçenekler sunar.

## Adım 1: Kaynak ve Çıktı Dizinlerini Tanımlayın

Öncelikle kaynak dosyalarınızın bulunduğu ve çıktı dosyalarını kaydetmek istediğiniz dizinleri ayarlayın:

```csharp
// Kaynak ve çıktı dizinlerini tanımlayın
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Değiştirdiğinizden emin olun`"Your Document Directory\\"` dizinlerinize giden gerçek yollarla. Bu, programınızın çalışması gereken dosyaları bulabilmesini sağlar.

## Adım 2: Çalışma Kitabını Yükleyin

Ardından sıkıştırmak istediğiniz çalışma kitabını yükleyin:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Burada, yeni bir örnek oluşturuyoruz`Workbook` sınıfını açın ve mevcut bir Excel dosyasını yükleyin. Dosya adının kaynak dizininizdekiyle eşleştiğinden emin olun.

## Adım 3: Kaydetme Seçeneklerini Ayarlayın

Şimdi çalışma kitabınız için kaydetme seçeneklerini yapılandırın:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 The`XlsbSaveOptions`class, çalışma kitabınızı XLSB formatında kaydederken sıkıştırma düzeyleri de dahil olmak üzere çeşitli seçenekleri belirtmenize olanak tanır.

## Adım 4: Seviye 1 için Sıkıştırma Süresini Ölçün

İlk sıkıştırma seviyesinden başlayın ve çalışma kitabını kaydetmenin ne kadar sürdüğünü ölçün:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Bu kod parçası sıkıştırma türünü Düzey 1'e ayarlar, çalışma kitabını kaydeder ve geçen süreyi ölçer.

## Adım 5: Seviye 6 için Sıkıştırma Süresini Ölçün

Daha sonra Seviye 6 sıkıştırma ile performansı test edin:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Bu adım bir öncekine benzer, ancak sıkıştırma seviyesi daha yüksektir.

## Adım 6: Seviye 9 için Sıkıştırma Süresini Ölçün

Son olarak, en yüksek sıkıştırma seviyesine sahip performansı değerlendirin:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Bu adım sıkıştırma seviyesini Seviye 9'a ayarlar. Dosya boyutunda en büyük azalmayı muhtemelen bu seviyede görürsünüz, ancak işlenmesi daha uzun sürebilir.

## Adım 7: Son Çıktı

Tüm sıkıştırma düzeyleri tamamlandıktan sonra, işlemin başarıyla tamamlandığını belirten bir mesaj çıktısı alın:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Bu basit satır programınızın sorunsuz bir şekilde çalıştığını doğrular.

## Çözüm

Aspose.Cells for .NET kullanarak çalışma kitaplarınızın sıkıştırma seviyesini ayarlamak, dosya boyutunda ve performansta önemli iyileştirmelere yol açabilen basit bir işlemdir. Bu kılavuzda özetlenen adımları izleyerek, uygulamalarınızda sıkıştırmayı verimli bir şekilde uygulayabilir ve Excel dosya yönetimi yeteneklerinizi geliştirebilirsiniz.

## SSS

### Aspose.Cells Nedir?  
Aspose.Cells, geliştiricilerin Microsoft Excel'e ihtiyaç duymadan Excel dosyaları oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan güçlü bir .NET kütüphanesidir.

### Aspose.Cells'i nasıl kurarım?  
 Aspose.Cells'i şuradan indirip yükleyebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/cells/net/).

### Hangi sıkıştırma seviyeleri mevcut?  
Aspose.Cells, Seviye 1'den (en düşük sıkıştırma) Seviye 9'a (en yüksek sıkıştırma) kadar çeşitli sıkıştırma seviyelerini destekler.

### Aspose.Cells'i ücretsiz deneyebilir miyim?  
 Evet! Aspose.Cells'in ücretsiz denemesini alabilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Cells için desteği nerede bulabilirim?  
 Herhangi bir soru veya destek için Aspose destek forumunu ziyaret edin[Burada](https://forum.aspose.com/c/cells/9).