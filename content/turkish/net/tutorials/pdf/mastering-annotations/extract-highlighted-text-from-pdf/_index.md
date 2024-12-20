---
title: Aspose.PDF for .NET Kullanarak PDF'lerden Vurgulanan Metni Çıkarma
linktitle: Aspose.PDF for .NET Kullanarak PDF'lerden Vurgulanan Metni Çıkarma
second_title: Aspose.PDF for .NET API Referansı
description: Aspose.PDF for .NET ile vurgulanan metni nasıl çıkaracağınızı öğrenerek PDF belgelerinizin potansiyelini ortaya çıkarın. Bu kapsamlı kılavuz, kurulumdan uygulamaya kadar her adımda size yol gösterir.
type: docs
weight: 60
url: /tr/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## giriiş

PDF dosyalarıyla çalışırken, vurgulanan metni çıkarmak veri analizi, içerik incelemesi veya notları düzenlemek için önemli olabilir. .NET için Aspose.PDF kullanıyorsanız, şanslısınız. Bu eğitim, bir PDF belgesinden vurgulanan metni etkili bir şekilde nasıl çıkaracağınıza dair net, adım adım talimatlar sağlar.

## Ön koşullar

Başlamadan önce aşağıdakilerin mevcut olduğundan emin olun:

-  .NET için Aspose.PDF Kitaplığı: Kitaplığı şu adresten indirin:[yayın sayfası](https://releases.aspose.com/pdf/net/).
- Geliştirme Ortamı: Visual Studio benzeri bir çalışma ortamı.
- Temel C# Bilgisi: C# ve nesne yönelimli programlamaya aşinalık gereklidir.
-  Aspose Lisansı: Ücretsiz denemeyle başlayabilmenize rağmen,[geçici lisans](https://purchase.aspose.com/temporary-license/) veya tam lisans[Burada](https://purchase.aspose.com/buy) sınırsız erişim sağlanacak.

## Gerekli Ad Alanlarını İçe Aktar

Öncelikle C# projenize gerekli ad alanlarını içe aktararak başlayın:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Bu ad alanları, PDF belgelerini ve açıklamalarını işlemek için gereken sınıflara ve yöntemlere erişim sağlar.

## Adım 1: Proje Dizininizi Ayarlayın

PDF dosyanızın bulunduğu dizini belirtin:

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

PDF dosyanızın yolunu gerçek diziniyle değiştirdiğinizden emin olun.

## Adım 2: PDF Belgesini Yükleyin

Aşağıdaki kodla PDF belgesini yükleyin:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Belirtilen dosyanın belirtilen dizinde mevcut olduğundan emin olun.

## Adım 3: Sayfadaki Açıklamalara Erişim

Açıklamalara erişmek için, istediğiniz sayfadaki (bu durumda ilk sayfa) açıklamalar arasında dolaşın:

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 Bu kod şunları filtreler:`TextMarkupAnnotation` vurguları temsil eden tipler.

## Adım 4: Vurgulanan Metni Çıkarın

Şimdi vurgulanan açıklamalardan metni çıkartıp görüntüleyelim:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

Bu, vurgulamayla ilişkili tüm işaretli metin parçalarını alır ve bunları konsola yazdırır.

## Çözüm

Aspose.PDF for .NET kullanarak bir PDF'den vurgulanan metni çıkarmak basittir ve belge işleme sürecinizi önemli ölçüde iyileştirebilir. Yukarıda belirtilen adımları izleyerek, rapor hazırlama veya veri analizi gibi çeşitli uygulamalar için vurgulanan metni verimli bir şekilde toplayabilirsiniz.

## SSS

### Başka türde açıklamaları da çıkarabilir miyim?
 Evet, sadece ayarlayın`if` farklı açıklama türlerini içerme koşulu`TextAnnotation` veya`StampAnnotation`.

### Tüm PDF sayfalarından vurgulanan metni nasıl çıkarabilirim?
Aşağıdakini kullanarak tüm sayfalarda dolaşabilirsiniz:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Aspose.PDF for .NET için lisans gerekli mi?
 Ücretsiz deneme mevcuttur, ancak bir[geçici lisans](https://purchase.aspose.com/temporary-license/) veya tam erişim için tam lisans.

### Çıkarılan metni bir dosyaya kaydedebilir miyim?
Kesinlikle! Kodu, çıkarılan metni bir metin dosyasına yazacak şekilde değiştirebilirsiniz.

### Aspose.PDF diğer platformları destekliyor mu?
Evet, Aspose.PDF Java ve diğer platformları da destekleyerek benzer işlevler sunuyor.