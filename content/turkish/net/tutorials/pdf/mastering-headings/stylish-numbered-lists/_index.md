---
title: .NET için Aspose.PDF Kullanarak Şık Numaralandırılmış Listeler
linktitle: .NET için Aspose.PDF Kullanarak Şık Numaralandırılmış Listeler
second_title: Aspose.PDF for .NET API Referansı
description: .NET için Aspose.PDF ile PDF belgelerinizde güzel numaralandırılmış listeler oluşturmayı keşfedin. Bu kılavuz, Roma rakamları gibi çeşitli numaralandırma stillerini uygulama sürecinde size yol gösterir.
type: docs
weight: 10
url: /tr/net/programming-with-headings/stylish-numbered-lists/
---
## giriiş

PDF belgelerinizde iyi yapılandırılmış, numaralandırılmış listeler oluşturmanız gerekti mi? İster yasal belgeler, raporlar veya sunumlar için olsun, etkili numaralandırma stilleri içeriğinizi düzenlemek için çok önemlidir. Aspose.PDF for .NET ile PDF başlıklarınıza çeşitli numaralandırma stillerini kolayca uygulayabilir, böylece cilalı ve profesyonel belgeler elde edebilirsiniz.

## Ön koşullar

Kodlamaya başlamadan önce aşağıdakilerin hazır olduğundan emin olun:

1.  Aspose.PDF for .NET: En son sürümü şu adresten indirin:[Burada](https://releases.aspose.com/pdf/net/).
2. Geliştirme Ortamı: Visual Studio'ya veya herhangi bir .NET uyumlu IDE'ye ihtiyacınız olacak.
3. .NET Framework: .NET Framework 4.0 veya üzeri sürümün yüklü olduğundan emin olun.
4.  Lisans: Geçici bir lisans kullanabilirsiniz.[Burada](https://purchase.aspose.com/temporary-license/) veya keşfedin[ücretsiz deneme](https://releases.aspose.com/) seçenekler.

## Gerekli Paketleri İçe Aktarma

Öncelikle projenize gerekli ad alanlarını içe aktarın:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Adım 1: Belgeyi Ayarlama

Yeni bir PDF belgesi oluşturarak ve sayfa boyutu ve kenar boşlukları da dahil olmak üzere düzenini yapılandırarak başlayalım.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Sayfa boyutlarını ve kenar boşluklarını ayarlayın
pdfDoc.PageInfo.Width = 612.0; // 8,5 inç
pdfDoc.PageInfo.Height = 792.0; // 11 inç
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // 1 inçlik kenar boşlukları
```

Bu kurulum, belgenize her tarafta bir inçlik kenar boşluklarıyla standart bir harf boyutu kazandırır.

## Adım 2: PDF'ye Sayfa Ekleme

Daha sonra PDF belgesine boş bir sayfa ekleyeceğiz ve numaralandırma stillerini bu sayfaya uygulayacağız.

```csharp
// PDF belgesine yeni bir sayfa ekleyin
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; //Belgeyle aynı ayarları kullanın
```

## Adım 3: Yüzen Kutu Oluşturma

FloatingBox, içeriği sayfanın akışından bağımsız olarak konumlandırmanıza olanak tanır ve böylece düzeniniz üzerinde daha fazla kontrol sahibi olursunuz.

```csharp
// Yapılandırılmış içerik için bir FloatingBox oluşturun
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Adım 4: Roma Rakamlarıyla Başlık Ekleme

Şimdi ilk başlığımızı küçük harfli Roma rakamlarıyla ekleyelim.

```csharp
// İlk başlığı Roma rakamlarıyla oluşturun
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Adım 5: Özel Başlangıç Numarasıyla İkinci Bir Başlık Ekleme

Daha sonra Roma rakamı 13'ten başlayarak ikinci bir başlık ekleyeceğiz.

```csharp
// Roma rakamı 13'ten başlayarak ikinci bir başlık oluşturun
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Adım 6: Alfabetik Numaralandırma ile Başlık Ekleme

Çeşitlilik olması açısından alfabetik numaralandırmayı küçük harflerle kullanarak üçüncü bir başlık ekleyelim.

```csharp
// Alfabetik numaralandırma ile bir başlık oluşturun
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Adım 7: PDF'yi kaydetme

Son olarak PDF dosyasını istediğiniz dizine kaydedelim.

```csharp
// PDF belgesini kaydedin
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Çözüm

Tebrikler! Aspose.PDF for .NET kullanarak bir PDF dosyasındaki başlıklara çeşitli numaralandırma stilleri (Romen rakamları ve alfabetik) başarıyla uyguladınız. Aspose.PDF'nin esnekliği, sayfa düzenini, numaralandırma stillerini ve içerik konumlandırmasını kontrol etmenizi sağlayarak iyi organize edilmiş ve profesyonel PDF belgeleri oluşturmanızı sağlar.

## SSS

### Aynı PDF belgesine farklı numara stilleri uygulayabilir miyim?  
Evet, aynı belge içerisinde Roma rakamları, Arap rakamları ve alfabetik numaralandırma gibi farklı numaralandırma stillerini karıştırabilirsiniz.

### Başlıkların başlangıç numarasını nasıl özelleştirebilirim?  
 Herhangi bir başlık için başlangıç numarasını kullanarak ayarlayabilirsiniz.`StartNumber` mülk.

### Numaralandırma sırasını sıfırlamanın bir yolu var mı?  
 Evet, numaralandırmayı ayarlayarak sıfırlayabilirsiniz.`StartNumber` Her başlık için özellik.

### Numaralandırmaya ek olarak başlıklara kalın veya italik stili uygulayabilir miyim?  
 Kesinlikle! Yazı tipi, boyut, kalın ve italik gibi özellikleri değiştirerek başlık stillerini özelleştirebilirsiniz.`TextState` nesne.

### Aspose.PDF için geçici lisansı nasıl alabilirim?  
 Geçici lisansı şuradan alabilirsiniz:[Burada](https://purchase.aspose.com/temporary-license/)Aspose.PDF'yi kısıtlama olmaksızın test etmek için.