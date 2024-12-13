---
title: Aspose.Cells for .NET ile Excel'de Harici Kaynakları Yönetin
linktitle: Aspose.Cells for .NET ile Excel'de Harici Kaynakları Yönetin
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells for .NET kullanarak Excel çalışma kitaplarındaki harici kaynakları sorunsuz bir şekilde nasıl kontrol edeceğinizi keşfedin. Bu kapsamlı kılavuz, özel bir akış sağlayıcısını uygulamaktan çalışma sayfalarını işlemeye kadar her adımda size yol gösterir.
type: docs
weight: 10
url: /tr/net/tutorials/cells/mastering-workbook-settings/manage-external-resources-in-excel/
---
## giriiş

Excel'de verilerle çalışırken, harici kaynakları sorunsuz bir şekilde yönetmek uygulamanızın işlevselliğini önemli ölçüde artırabilir. Aspose.Cells for .NET kullanarak Excel çalışma kitaplarındaki görüntüleri ve diğer harici öğeleri kontrol etmek istiyorsanız, doğru yerdesiniz! Bu kılavuz, bu kaynakları zahmetsizce yönetmek için özelleştirilmiş bir çözüm uygulamanıza olanak tanıyarak sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

Kodlama yönlerine dalmadan önce, aşağıdaki ayarların yapıldığından emin olun:

1. Visual Studio: .NET uygulamalarınızı yazmak ve test etmek için bir IDE. Visual Studio, kapsamlı desteği ve kullanıcı dostu arayüzü nedeniyle önerilir.
2.  Aspose.Cells for .NET: Kütüphaneyi şu adresten indirin:[Aspose Cells sürüm sayfası](https://releases.aspose.com/cells/net/).
3. Temel C# Bilgisi: C# ve .NET kavramlarına aşinalık, uygulamayı daha iyi anlamanıza yardımcı olacaktır.
4. Projenizi Kurun: Projenizin Visual Studio'daki NuGet Paket Yöneticisi aracılığıyla ekleyebileceğiniz Aspose.Cells kütüphanesine başvurduğundan emin olun.
5. Örnek Dosyalar: Gösterim amaçlı harici kaynaklar (örneğin bağlantılı resimler) içeren bir örnek Excel dosyası hazırlayın.

Tüm bu ön koşullar sağlandıktan sonra, Aspose.Cells ile harici kaynakları yönetmeye başlayalım.

## Paketleri İçe Aktar
Kodlamaya başlamak için, gerekli paketleri C# dosyanıza aktarmanız gerekir. İhtiyacınız olanlar şunlardır:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

## Adım 1: Dizinleri Tanımlayın

Öncelikle dosyalarınızın saklanacağı kaynak ve çıktı dizinlerini ve çıktı dosyalarınızın nereye kaydedilmesini istediğinizi belirtin.

```csharp
// Kaynak dizini tanımlayın
static string sourceDir = @"C:\Path\To\Your\Documents\"; // Yolu özelleştir
// Çıktı dizinini tanımlayın
static string outputDir = @"C:\Path\To\Your\Output\";
```

Yolları makinenizdeki gerçek dizinlerle değiştirdiğinizden emin olun.

### Adım 2: IStreamProvider Arayüzünü Uygulayın

 Sonra, aşağıdakileri uygulayan özel bir sınıf oluşturun:`IStreamProvider` arayüz. Bu sınıf, resimler gibi harici kaynaklara nasıl erişileceğini yönetecektir.

```csharp
class CustomStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        // Gerekirse kaynakları temizleyin
        options.Stream?.Close();
    }

    public void InitStream(StreamProviderOptions options)
    {
        // Harici kaynak için dosya akışını açın
        options.Stream = new FileStream(Path.Combine(sourceDir, "image.png"), FileMode.Open, FileAccess.Read);
    }
}
```

 İçinde`InitStream` yöntem, harici kaynağınız olarak hizmet veren dosyayı açar ve onu`Stream` mülk.

### Adım 3: Excel Dosyasını Yükleyin

Şimdi harici kaynağı içeren Excel çalışma kitabını yükleyelim.

```csharp
public static void Execute()
{
    // Excel dosyasını yükleyin
    Workbook workbook = new Workbook(Path.Combine(sourceDir, "sample.xlsx"));
    
    // Özel akış sağlayıcısını atayın
    workbook.Settings.StreamProvider = new CustomStreamProvider();
```

Bu kod parçası Excel dosyanızı yükler ve harici kaynakları işlemek için özel akış sağlayıcısını atar.

### Adım 4: Çalışma Sayfasına Erişim

Çalışma kitabını yükledikten sonra istediğiniz çalışma sayfasına kolayca ulaşın.

```csharp
    // İlk çalışma sayfasına erişin
    Worksheet worksheet = workbook.Worksheets[0];
```

Herhangi bir çalışma sayfasına indeksini belirterek erişebilirsiniz.

### Adım 5: Görüntü ve Yazdırma Seçeneklerini Yapılandırın

Görüntü veya yazdırma seçeneklerini yapılandırarak çıktı görüntüsünün nasıl görünmesini istediğinizi tanımlayın.

```csharp
    // Resim veya baskı seçeneklerini belirtin
    ImageOrPrintOptions options = new ImageOrPrintOptions
    {
        OnePagePerSheet = true,
        ImageType = Drawing.ImageType.Png
    };
```

PNG'yi tercih etmek net ve temiz bir çıktı almanızı sağlar.

### Adım 6: Çalışma Sayfasını Bir Görüntüye Dönüştürün

Şimdi heyecan verici kısma geldik: çalışma sayfasını bir resim dosyasına dönüştürmek!

```csharp
    // Bir sayfa oluşturma ve çalışma sayfasını bir görüntüye dönüştürme
    SheetRender sheetRender = new SheetRender(worksheet, options);
    sheetRender.ToImage(0, Path.Combine(outputDir, "output.png"));
    
    Console.WriteLine("Excel sheet rendered successfully to an image!");
}
```

Bu kod tüm çalışma sayfasını, belirttiğiniz çıktı dizinine kaydedilecek bir PNG resmine dönüştürür.

## Çözüm

Tebrikler! Artık Aspose.Cells for .NET kullanarak Excel dosyalarındaki harici kaynakları nasıl kontrol edeceğinizi öğrendiniz. Bu işlevsellik yalnızca uygulamanızın yeteneklerini geliştirmekle kalmaz, aynı zamanda veri kümelerini ve sunumları yönetme şeklinizi de basitleştirir. Yukarıda özetlenen adımları izleyerek bu çözümü projenizin benzersiz gereksinimlerine uyacak şekilde uyarlayabilirsiniz.

## SSS

### Aspose.Cells Nedir?
Aspose.Cells, .NET geliştiricilerinin Microsoft Excel'e ihtiyaç duymadan Excel dosyaları oluşturması, düzenlemesi ve yönetmesi için tasarlanmış sağlam bir kütüphanedir.

### Aspose.Cells for .NET'i nasıl indirebilirim?
 Bunu şuradan indirebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/cells/net/).

### Ücretsiz deneme imkanı var mı?
 Evet! Aspose, Aspose.Cells'in ücretsiz deneme sürümünü sunuyor.[yayın sayfası](https://releases.aspose.com/cells/net/).

### Aspose.Cells hangi dosya türlerini destekler?
Aspose.Cells, XLS, XLSX, CSV ve daha fazlası dahil olmak üzere çeşitli Excel formatlarını destekler.

### Aspose.Cells için desteği nerede bulabilirim?
 Ziyaret edin[Aspose Forum](https://forum.aspose.com/c/cells/9) yardım ve toplum desteği için.