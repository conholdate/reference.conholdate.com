---
title: Word Belgelerinde İşaretli Bölümlerden Metin Ekleme
linktitle: Word Belgelerinde İşaretli Bölümlerden Metin Ekleme
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET ile Word belgesinin yer imli bölümlerinden sorunsuz bir şekilde metin eklemeyi öğrenin. Bu adım adım eğitim.
type: docs
weight: 10
url: /tr/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## giriiş

Word belgesinde yer imli bir bölümden metin eklemeyi hiç zor buldunuz mu? Doğru yerdesiniz! Bu eğitim, Aspose.Words for .NET kullanarak sizi adım adım süreç boyunca yönlendirecektir. Sonunda, yer imli metni bir profesyonel gibi ekleyebileceksiniz. Başlayalım!

## Ön koşullar

Başlamadan önce, aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET: Eğer henüz yüklemediyseniz,[buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio benzeri bir .NET geliştirme ortamı.
- Temel C# Bilgisi: Temel C# programlama kavramlarına aşinalık faydalı olacaktır.
- Yer İşaretleri İçeren Word Belgesi: Metin eklemek için kullanacağımız yer işaretlerini içeren bir Word belgesi.

## Gerekli Ad Alanlarını İçe Aktar

Öncelikle Aspose.Words işlevlerine erişmek için gerekli ad alanlarını içe aktarmamız gerekiyor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## Adım 1: Belgeyi Yükleyin ve Değişkenleri Başlatın

Kaynak ve hedef Word belgelerimizi yükleyerek ve gerekli değişkenleri başlatarak başlayalım.

```csharp
//Kaynak ve hedef belgeleri yükleyin.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Belge içe aktarıcısını başlatın.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Kaynak belgede yer imini bulun.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Adım 2: Başlangıç ve Bitiş Paragraflarını Belirleyin

Sonra, yer iminin başladığı ve bittiği paragrafları bulmamız gerekiyor. Bu, doğru metni çıkarmak için önemlidir.

```csharp
// Ayraçların başında ve sonunda bulunan paragrafları belirleyin.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Paragrafları doğrulayın.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## Adım 3: Paragraf Ebeveynlerini Doğrulayın

Hem başlangıç hem de bitiş paragraflarının aynı ana düğümü paylaştığından emin olmamız gerekir. Bu, karmaşıklıklardan kaçınmak için basitleştirilmiş bir yaklaşımdır.

```csharp
// Başlangıç ve bitiş paragraflarının aynı ebeveyne sahip olup olmadığını kontrol edin.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## Adım 4: Durdurulacak Düğümü Belirleyin

Şimdi, metin kopyalamayı nerede durduracağımızı belirlememiz gerekiyor; bu, paragrafın sonundan hemen sonraki düğüm olacak.

```csharp
// Son paragraftan hemen sonraki düğümü tanımlayın.
Node endNode = endPara.NextSibling;
```

## Adım 5: Hedef Belgeye İşaretlenmiş Metni Ekleyin

Son olarak, başlangıç paragrafından bitiş paragrafından sonraki düğüme kadar düğümler arasında dolaşacağız ve bunları hedef belgeye ekleyeceğiz.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Geçerli düğümü hedef belgeye aktarın.
    Node newNode = importer.ImportNode(curNode, true);

    // İçe aktarılan düğümü hedef belgeye ekleyin.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Güncellenen hedef belgeyi kaydedin.
dstDoc.Save("appended_document.docx");
```

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak Word belgesinde yer imli bir bölümden metni başarıyla eklediniz. Bu güçlü kütüphane belge düzenlemeyi basit hale getiriyor ve artık araç setinizde başka bir kullanışlı beceriniz var. İyi kodlamalar!

## SSS

### Birden fazla yer iminden aynı anda metin ekleyebilir miyim?
Evet, her yer imi için işlemi tekrarlayabilir ve ihtiyacınıza göre metin ekleyebilirsiniz.

### Başlangıç ve bitiş paragraflarının farklı ebeveynleri varsa ne olur?
Mevcut örnek, aynı ebeveyne sahip olduklarını varsayar. Eğer sahip değillerse, daha karmaşık bir işleme uygulamanız gerekecektir.

### Eklenen metnin orijinal biçimi korunacak mı?
 Kesinlikle! Kullanarak`ImportFormatMode.KeepSourceFormatting`orijinal biçimlendirmenin korunmasını sağlar.

### Hedef belgede belirli bir konuma metin eklemek mümkün müdür?
Evet, hedef belgedeki uygun düğüme giderek istediğiniz herhangi bir konuma metin ekleyebilirsiniz.

### Yer imlerinden yeni bir bölüme metin ekleyebilir miyim?
Evet, hedef belgede yeni bir bölüm oluşturabilir ve metni oraya ekleyebilirsiniz.