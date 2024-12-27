---
title: Dolu Dikdörtgen Oluşturma
linktitle: Dolu Dikdörtgen Oluşturma
second_title: Aspose.PDF for .NET API Referansı
description: Bu adım adım eğitimde Aspose.PDF for .NET ile PDF düzenlemenin gücünü açığa çıkarın. Dolu dikdörtgenler çizerek görsel olarak çekici PDF belgelerini programatik olarak nasıl oluşturacağınızı öğrenin.
type: docs
weight: 50
url: /tr/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## giriiş

Görsel olarak çarpıcı PDF'leri programatik olarak oluşturmak istediniz mi hiç? Eğer öyleyse, doğru yerdesiniz! Bu eğitimde, PDF belge düzenlemeyi basitleştiren güçlü bir kütüphane olan .NET için Aspose.PDF'yi inceleyeceğiz. Bugün, bir PDF dosyası içinde dolu bir dikdörtgen oluşturmaya odaklanacağız. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuz sizi her adımda dostça ve ilgi çekici bir şekilde yönlendirecektir. O halde, kodlama şapkanızı alın ve başlayalım!

## Ön koşullar

Koda dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Visual Studio: .NET geliştirme için mükemmel bir IDE olduğundan, Visual Studio'yu makinenize yükleyin.
2. .NET için Aspose.PDF: Aspose.PDF kitaplığını şu adresten indirin ve yükleyin:[Burada](https://releases.aspose.com/pdf/net/).
3. Temel C# Bilgisi: C# programlamaya aşina olmak, kod parçacıklarını daha iyi anlamanıza yardımcı olacaktır.

## Adım 1: Yeni Bir Proje Oluşturun

1. Visual Studio'yu açın ve yeni bir Konsol Uygulaması projesi oluşturun.
2. Projenize uygun bir isim verin.

## Adım 2: Aspose.PDF Referansını Ekleyin

1. Çözüm Gezgini’nde projenizin üzerine sağ tıklayın.
2. NuGet Paketlerini Yönet'i seçin.
3. Aspose.PDF'i arayın ve en son sürümü yükleyin.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Artık her şeyi ayarladığımıza göre koda geçelim!

## Adım 3: Belge Dizininizi Ayarlayın

PDF'nizin kaydedileceği yolu belirtin:

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` PDF'yi kaydetmek istediğiniz makinenizdeki gerçek yol ile.

## Adım 4: Bir Belge Örneği Oluşturun

Yeni bir PDF belgesi başlatın:

```csharp
// Belge örneği oluştur
Document doc = new Document();
```

## Adım 5: Belgeye Bir Sayfa Ekleyin

Her PDF'in en az bir sayfaya ihtiyacı vardır. Bir tane ekleyelim:

```csharp
// PDF dosyasının sayfa sayfa koleksiyonunu ekle
Page page = doc.Pages.Add();
```

## Adım 6: Bir Grafik Örneği Oluşturun

 A`Graph` örnek, şekillerin çizilmesi için bir tuval görevi görür:

```csharp
// Grafik örneği oluştur
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Adım 7: Grafiği Sayfaya Ekleyin

Grafiği sayfaya ekleyin:

```csharp
// Sayfa örneğinin paragraf koleksiyonuna grafik nesnesi ekle
page.Paragraphs.Add(graph);
```

## Adım 8: Dikdörtgen Örneği Oluşturun

Dikdörtgenin konumunu ve boyutunu tanımlayın:

```csharp
// Dikdörtgen örneği oluştur
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Adım 9: Dolgu Rengini Belirleyin

Dikdörtgeniniz için bir renk seçin. Bu örnek için kırmızı kullanacağız:

```csharp
// Grafik nesnesi için dolgu rengini belirtin
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Adım 10: Dikdörtgeni Grafiğe Ekleyin

Dikdörtgeni grafiğe ekleyin:

```csharp
// Grafik nesnesinin şekiller koleksiyonuna dikdörtgen nesnesi ekle
graph.Shapes.Add(rect);
```

## Adım 11: PDF Belgesini Kaydedin

Son olarak belgenizi belirtilen dizine kaydedin:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// PDF dosyasını kaydet
doc.Save(dataDir);
```

## Adım 12: Onay Mesajı

Başarılı olduğunuzu belirtmek için bir onay mesajı yazdırın:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Çözüm

Tebrikler! Aspose.PDF for .NET kullanarak bir PDF belgesinde dolu bir dikdörtgeni başarıyla oluşturdunuz. Bu güçlü kütüphane, PDF manipülasyonu için bir olasılıklar dünyası açarak, çarpıcı belgeleri programatik olarak oluşturmanıza olanak tanır. İster raporlar, ister faturalar veya başka bir PDF türü oluşturun, Aspose.PDF sizin için her şeyi yapar.

## SSS

### Aspose.PDF for .NET nedir?
Aspose.PDF for .NET, geliştiricilerin PDF belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan bir kütüphanedir.

### Aspose.PDF'yi ücretsiz kullanabilir miyim?
 Evet, Aspose kütüphanenin özelliklerini keşfetmeniz için kullanabileceğiniz ücretsiz bir deneme sürümü sunuyor. İndirebilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.PDF desteği almanın bir yolu var mı?
 Kesinlikle! Aspose forumundan destek alabilirsiniz[Burada](https://forum.aspose.com/c/pdf/10).

### Aspose.PDF'i nasıl satın alabilirim?
 Aspose.PDF'yi satın alma sayfasını ziyaret ederek satın alabilirsiniz[Burada](https://purchase.aspose.com/buy).

### Aspose.PDF ile hangi tür şekiller oluşturabilirim?
Aspose.PDF kütüphanesini kullanarak dikdörtgenler, daireler, çizgiler ve daha fazlası dahil olmak üzere çeşitli şekiller oluşturabilirsiniz.