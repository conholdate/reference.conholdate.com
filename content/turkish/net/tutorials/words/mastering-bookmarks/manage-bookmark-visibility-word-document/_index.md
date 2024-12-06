---
title: Word Belgelerinde Yer İşareti Görünürlüğünü Yönetin
linktitle: Word Belgelerinde Yer İşareti Görünürlüğünü Yönetin
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerindeki içerik görünürlüğünün nasıl uzmanca kontrol edileceğini keşfedin. Bu adım adım kılavuz.
type: docs
weight: 10
url: /tr/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## giriiş

Aspose.Words for .NET ile belge düzenleme becerilerinizi geliştirmeye hazır mısınız? İster belge görevlerini otomatikleştiren deneyimli bir geliştirici olun, ister Word dosyaları üzerinde programatik denetimi araştıran meraklı bir birey olun, bu kılavuz sizin için özel olarak hazırlanmıştır. Bugün, bir Word belgesindeki yer imlerine dayalı olarak içeriğin nasıl gösterileceğini ve gizleneceğini inceleyeceğiz. Başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Visual Studio: .NET ile uyumlu herhangi bir sürüm.
2.  Aspose.Words for .NET: İndirin[Burada](https://releases.aspose.com/words/net/).
3. Temel C# Bilgisi: Basit C# programları yazma konusunda bilgi sahibi olmak yeterli olacaktır.
4. Örnek Bir Word Belgesi: Bu eğitim için yer imlerini içeren bir Word belgesi hazırlayın (örneğin, "Bookmarks.docx").

### Yeni Bir Proje Oluştur

1. Visual Studio'yu açın ve yeni bir Konsol Uygulaması (.NET Core) projesi oluşturun. "BookmarkVisibilityManager" gibi bir isim verin.

### .NET için Aspose.Words'ü yükleyin

Aspose.Words'ü NuGet Paket Yöneticisi aracılığıyla projenize ekleyin:

1. Araçlar > NuGet Paket Yöneticisi > Çözüm için NuGet Paketlerini Yönet'e gidin.
2. "Aspose.Words" ifadesini arayın.
3. Paketi kurun.

Projeniz hazır olduğuna göre, belgeyi yüklemeye geçelim.

## Ad Alanlarını İçe Aktarma

Temel ad alanlarını içe aktararak başlayın. Bunlar, Word belgelerini Aspose.Words ile işlemek için gerekli sınıfları ve yöntemleri sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Adım 1: Belgeyi Yükleme

Word belgesini düzenlemek için önce yüklememiz gerekir. Bunu nasıl yapacağımızı anlatalım:

```csharp
// Belge dizininize giden yolu tanımlayın.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Bu kod parçacığı belge dizininize giden yolu ayarlar ve belgeyi bir`Document` nesne.

## Adım 2: Yer İşaretli İçeriği Göster/Gizle

 Şimdi, yer imlerine göre içerik görünürlüğünü değiştirmek için bir yöntem oluşturalım. Bu yöntemi çağıracağız`ShowHideBookmarkedContent`.

İşte yöntemin uygulanışı:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Yer İşareti Alma:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` belirtilen yer imini getirir.
- Düğüm Gezinmesi: Yer imi içindeki düğümler arasında yineleme yaparız.
-  Görünürlük Değiştirme: Her biri için`Run` (metnin bir bölümünü temsil eden) düğümü, onu ayarlıyoruz`Hidden` mülkiyete dayalı`isHidden` parametre.

## Adım 3: Yöntemin Uygulanması

Artık metodumuz hazır olduğuna göre, onu belirli bir yer imindeki içeriği göstermek veya gizlemek için kullanabiliriz:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // "MyBookmark1" içindeki içeriği gizler
```

Bu satır "MyBookmark1" adlı yer imiyle ilişkili içeriği gizleyecektir.

## Adım 4: Belgeyi Kaydetme

Değişikliklerinizi yaptıktan sonra, değiştirilmiş belgeyi kaydetmeyi unutmayın:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Bu, belgeyi güncellenmiş görünürlük ayarlarıyla kaydeder.

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak Word belgesinde yer imli içeriğin nasıl gösterileceğini ve gizleneceğini başarıyla öğrendiniz. Bu güçlü kütüphane belge düzenlemeyi basitleştirir ve raporları otomatikleştirmek, şablonlar oluşturmak veya Word dosyalarıyla denemeler yapmak için ideal hale getirir. İyi kodlamalar!

## SSS

### Birden fazla yer imini aynı anda açıp kapatabilir miyim?
 Evet, sadece arayın`ShowHideBookmarkedContent` Geçiş yapmak istediğiniz her yer imi için bir yöntem.

### İçeriği gizlemek belgenin yapısını etkiler mi?
Hayır, içeriği gizlemek yalnızca görünürlüğünü etkiler; içerik belge içerisinde bozulmadan kalır.

### Bu yöntemi diğer içerik türleri için de kullanabilir miyim?
Bu yöntem özellikle metin çalışmaları için tasarlanmıştır. Diğer içerik türleri için, düğüm geçiş mantığını buna göre uyarlamanız gerekir.

### Aspose.Words for .NET ücretsiz mi?
 Aspose.Words ücretsiz deneme sunuyor[Burada](https://releases.aspose.com/) , ancak üretim kullanımı için tam lisans gereklidir. Bunu satın alabilirsiniz[Burada](https://purchase.aspose.com/buy).

### Sorun yaşarsam nasıl destek alabilirim?
 Destek için Aspose topluluk forumunu ziyaret edin[Burada](https://forum.aspose.com/c/words/8).