---
title: PDF Belgesine İçindekiler Tablosu Ekleme
linktitle: PDF Belgesine İçindekiler Tablosu Ekleme
second_title: Aspose.PDF for .NET API Referansı
description: Bu eğitimde Aspose.Pdf for .NET kullanılarak bir PDF belgesine İçindekiler Tablosu'nun (TOC) nasıl ekleneceğini gösteriyoruz.
type: docs
weight: 40
url: /tr/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## giriiş

Bir PDF belgesinde içerik tablosu (TOC) oluşturmak, gezinme ve erişilebilirliğini büyük ölçüde artırabilir. Bu kılavuzda, .NET için Aspose.Pdf kullanarak bir PDF dosyasına TOC'nin nasıl ekleneceğini göstereceğiz.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.   Aspose.PDF for .NET: En son sürümü şu adresten indirin ve yükleyin:[Burada](https://releases.aspose.com/pdf/net/).
2.  Geliştirme Ortamı: Visual Studio gibi bir .NET geliştirme ortamı kurun.
3.   Lisans: Gerekirse geçici bir lisans talep edin; lütfen şu adresi ziyaret edin:[Aspose.Pdf Lisanslama Sayfası](https://asposepdf.com/developers) Daha fazla bilgi için.

Gerekli Kütüphaneleri İçeri Aktarma

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Adım 1: PDF Belgesini Yükleyin

İçindekiler bölümünü eklemek istediğiniz mevcut PDF dosyanızı yükleyin. Belge dizininize giden yolu belirtin.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Adım 2: İçindekiler için Yeni Bir Sayfa Ekleyin

PDF belgesinin başına yeni bir sayfa ekleyin. Bu sayfa İçindekiler Tablosu (TOC) olarak hizmet edecektir.

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Adım 3: İçindekiler Bilgi Nesnesi Oluşturun

İçindekiler bilgisini temsil edecek bir nesne oluşturun. Daha iyi gezinme için bir başlık ve bağlantı ekleyin.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Adım 4: İçindekiler Öğelerini Tanımlayın

İçindekiler bölümünde görüntülenecek öğeleri (veya başlıkları) tanımlayın. Bu öğeler okuyucuların belgenin belirli bölümlerine gitmelerine yardımcı olabilir.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Adım 5: İçindekiler Başlıklarını Oluşturun

İçindekiler tablosundaki ilk iki öğe için başlıklar oluşturun. Bu başlıklar ilgili sayfalara bağlantı verecektir.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Adım 6: PDF'yi İçindekiler tablosuyla birlikte kaydedin

Son olarak güncellenen PDF dosyasını kaydedin.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Onay Mesajı

Kullanıcıya işlemin tamamlandığını bildirmek için bir onay mesajı görüntüleyin.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Çözüm

Aspose.PDF for .NET ile bir PDF'e İçindekiler Tablosu eklemek yalnızca kolay değil, aynı zamanda özelleştirilebilir. Basit gezinme bağlantıları veya karmaşık yapılar oluşturmanız gerekip gerekmediğine bakılmaksızın, bu araç sizin için her şeyi yapar. Bu nedenle, bir dahaki sefere uzun bir PDF üzerinde çalıştığınızda, profesyonel bir dokunuş için bir İçindekiler Tablosu eklemeyi unutmayın.

## SSS

### Aspose.PDF'deki İçindekiler bölümünün görünümünü özelleştirebilir miyim?

Evet, yazı tipi, boyutu ve hizalama dahil olmak üzere İçindekiler tablosunun görünümünü tamamen özelleştirebilirsiniz.

### İçindekiler tablosuna alt başlıklar nasıl eklenir?

 Alt başlıkları ayarlayarak ekleyebilirsiniz.`Heading` seviye (örneğin,`Heading(2)`).

### Belge değiştiğinde İçindekiler tablosunun otomatik olarak güncellenmesi mümkün müdür?

Hayır, İçindekiler tablosu otomatik olarak güncellenmeyecek. Belge yapısı değişirse yeniden oluşturmanız gerekecek.

### İçindekiler girişlerini harici belgelere bağlayabilir miyim?

Evet, İçindekiler girişlerini harici PDF'lere veya URL'lere bağlamak için köprü metinleri kullanabilirsiniz.

### Aspose.PDF çok seviyeli İçindekiler tablosunu destekliyor mu?

Evet, Aspose.PDF alt bölümlere sahip karmaşık belgeler için çok seviyeli İçindekiler tablosunu destekler.
