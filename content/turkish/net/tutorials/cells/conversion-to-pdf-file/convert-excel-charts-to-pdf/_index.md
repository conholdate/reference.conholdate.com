---
title: Aspose.Cells for .NET Kullanarak Excel Grafiklerini PDF'ye Dönüştürme
linktitle: Aspose.Cells for .NET Kullanarak Excel Grafiklerini PDF'ye Dönüştürme
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells kullanarak Excel grafiklerini .NET'te PDF formatına nasıl kolayca dönüştüreceğinizi öğrenin. Adım adım kılavuzumuz ön koşulları, kurulumu, kod örneklerini ve SSS'leri kapsar.
type: docs
weight: 11
url: /tr/net/tutorials/cells/conversion-to-pdf-file/convert-excel-charts-to-pdf/
---
## giriiş

Excel elektronik tablolarındaki grafikleri .NET ortamında PDF formatına dönüştürmek için bir kılavuza mı ihtiyacınız var? Bu makale, Aspose.Cells for .NET ile süreci ustalıkla yönetmenize yardımcı olmak için her ayrıntıyı kapsayan hepsi bir arada kaynağınızdır. Excel grafiklerini yüksek kaliteli PDF'lere kolayca dönüştürmek için bu yapılandırılmış açıklamayı izleyin.

## Ön koşullar

### .NET Ortam Kurulumu
.NET Framework veya .NET Core'un yüklü olduğundan emin olun. Bu ortamların ikisi de Aspose.Cells ile uyumludur, bu nedenle projenize en uygun olanı kullanabilirsiniz.

### Aspose.Cells Kütüphane Kurulumu
Aspose.Cells kütüphanesi, grafikten PDF'e dönüşümler için olmazsa olmazdır. En son sürümü şu adresten edinin:[Aspose indirme sayfası](https://releases.aspose.com/cells/net/).

### Temel C# Bilgisi
C# hakkında temel bir anlayışa sahip olmak kodlama sürecini kolaylaştıracaktır. Yeni başlayan biriyseniz endişelenmeyin; bu kılavuz takip etmesi kolay kod örnekleri içerir.

### Visual Studio'yu kurun
Visual Studio veya başka bir uyumlu IDE'ye ihtiyacınız olacak. IDE'nizi .NET uygulamalarını işleyecek şekilde ayarlayın ve kodunuzu sorunsuz bir şekilde yazmak ve çalıştırmak için her şeyin düzgün yapılandırıldığından emin olun.

## Projenize Gerekli Paketleri İçeri Aktarın

Ön koşullar işaretlendikten sonra, gerekli kütüphaneleri projenize içe aktararak başlayın. Visual Studio projenizi açın ve NuGet aracılığıyla Aspose.Cells kütüphanesini yükleyin:

1. Çözüm Gezgini'nde projenize sağ tıklayın.
2. NuGet Paketlerini Yönet'i seçin.
3. Aspose.Cells'i arayın ve Yükle'ye tıklayın.

 Aşağıdakileri ekleyin`using` Kod dosyanızın başındaki yönergeler:

```csharp
using System;
using System.IO;
using Aspose.Cells;
using Aspose.Cells.Charts;
```

Bu kütüphaneler Excel grafiklerini işlemek ve bunları PDF'lere dönüştürmek için gerekli sınıfları ve yöntemleri sağlar.

## Adım 1: Dosya Dizinini Tanımlayın

Excel belgenizin depolandığı dizine giden yolu belirterek başlayın. Bu, Aspose.Cells'e grafiğinizi içeren .xls veya .xlsx dosyasını nerede bulacağını söyler.

```csharp
// Dizin yolunu tanımlayın
string dataDir = "Your Document Directory Path";
```

 Yer değiştirmek`"Your Document Directory Path"` dosyanızın gerçek yolunu belirtin.

## Adım 2: Excel Çalışma Kitabını yükleyin

Şimdi dönüştürmek istediğiniz grafikleri içeren Excel dosyasını yükleyin.

```csharp
// Excel dosyasını yükleyin
Workbook workbook = new Workbook(dataDir + "Sample1.xls");
```

Dosya yolunun ve adının gerçek dosya konumunuzla eşleştiğinden emin olun.

## Adım 3: Tablonun bulunduğu Çalışma Sayfasına erişin

Excel çalışma kitapları birden fazla sayfa içerebilir, bu nedenle dönüştürmek istediğiniz grafiğin bulunduğu sayfayı belirtin.

```csharp
// Belirli çalışma sayfasına erişin
Worksheet worksheet = workbook.Worksheets[0];
```

Bu kod ilk çalışma sayfasına erişir. Grafiğiniz başka bir sayfadaysa dizini değiştirin.

## Adım 4: Dönüştürülecek Grafiği Seçin

Daha sonra, seçtiğiniz çalışma sayfasından dönüştürmek istediğiniz belirli grafiğe erişin.

```csharp
//Çalışma sayfasındaki ilk tabloya erişin
Chart chart = worksheet.Charts[0];
```

Bu kod ilk grafiği seçer. Birden fazla grafik varsa, endeksi buna göre ayarlayın.

## Adım 5: Tabloyu PDF'ye Dönüştürün

Şimdi seçili grafiği PDF dosyasına dönüştürelim.

```csharp
// Tabloyu PDF formatına dönüştürün
chart.ToPdf(dataDir + "ChartOutput.pdf");
```

Bu komut Aspose.Cells'e grafiği belirtilen dizine PDF olarak kaydetmesini söyler.

## Adım 6: Tabloyu Bellek Akışında PDF Olarak Kaydedin (İsteğe Bağlı)

 Eğer grafiği bir`MemoryStream` doğrudan bir dosyaya göndermek yerine, aşağıdaki kodu kullanın. Bu özellikle web uygulamaları için veya PDF'yi dinamik olarak sunmanız gerektiğinde kullanışlıdır.

```csharp
// Tabloyu bir bellek akışına kaydedin
MemoryStream pdfStream = new MemoryStream();
chart.ToPdf(pdfStream);
```

 Birini kullanarak`MemoryStream` PDF dosyasını uygulamanız içerisinde yönetmenizde esneklik sağlar.

## Çözüm

Aspose.Cells for .NET ile Excel grafiklerini PDF'ye dönüştürmek, adımları öğrendikten sonra basit bir işlemdir. Ortamı kurmaktan ve gerekli kitaplıkları içe aktarmaktan dosyayı dönüştürmeye ve kaydetmeye kadar her adım basit ve uygulanması kolaydır. Artık, .NET uygulamalarınızda Excel grafiklerinden PDF dosyalarını verimli bir şekilde oluşturmak için gereken bilgiye sahipsiniz.

## SSS

### Aspose.Cells Nedir?

Aspose.Cells, çeşitli formatlardaki Excel dosyalarını oluşturmak, düzenlemek ve dönüştürmek için tasarlanmış kapsamlı bir .NET kütüphanesidir.

### Lisans olmadan Aspose.Cells'i kullanabilir miyim?

 Evet, Aspose.Cells'i web sitemizde bulunan deneme sürümünü kullanarak ücretsiz deneyebilirsiniz.[Aspose web sitesi](https://releases.aspose.com/cells/net/).

### Dönüştürme sırasında bir hatayla karşılaşırsam ne yapmalıyım?

 Herhangi bir sorunla karşılaşırsanız, şunu kontrol edin:[Aspose destek forumu](https://forum.aspose.com/c/cells/9) Diğer kullanıcılardan sorun giderme yardımı veya rehberlik almak için.

### Aspose.Cells ile grafikleri başka formatlara dönüştürmek mümkün müdür?

Evet, Aspose.Cells PDF'in yanı sıra resim ve HTML gibi çeşitli çıktı formatlarını da destekler.

### Aspose.Cells için lisans alabilir miyim?

 Evet yapabilirsin[lisans satın al](https://purchase.conholdate.com/buy) Aspose.Cells'in tüm yeteneklerinin kilidini açmak için.