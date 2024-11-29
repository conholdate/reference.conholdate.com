---
title: PDF Belgesine Onay Kutusu Bileşeni Ekleme
linktitle: PDF Belgesine Onay Kutusu Bileşeni Ekleme
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET SDK'sını kullanarak etkileşimli onay kutusu bileşenleri ekleyerek PDF belgelerinizi nasıl zenginleştireceğinizi keşfedin. Bu kapsamlı eğitim, net bir adım adım kılavuz sağlar.
type: docs
weight: 11
url: /tr/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## giriiş

Bu eğitimde, .NET SDK için GroupDocs.Annotation'ı kullanarak bir PDF belgesine Onay Kutusu Bileşeni ekleme sürecini adım adım anlatacağız. Bu özellik, PDF belgelerinizi etkileşimli öğelerle zenginleştirmenize ve kullanıcılar için daha ilgi çekici hale getirmenize olanak tanır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  GroupDocs.Annotation for .NET SDK: Buradan indirin[Burada](https://releases.groupdocs.com/annotation/net/).
2. Geliştirme Ortamı: Makinenize bir .NET geliştirme ortamı kurun.

## Adım 1: Gerekli Ad Alanlarını İçe Aktarın

Öncelikle projenize gerekli ad alanlarını ekleyin:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Adım 2: Çıktı Yolunu Tanımlayın

Değiştirilen PDF belgesinin nereye kaydedileceğini belirtin:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Adım 3: Açıklamayı Başlatın

 Bir örneğini oluşturun`Annotator` Giriş PDF belgenizin yolunu içeren sınıf:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## Adım 4: Onay Kutusu Bileşenini Oluşturun

Şimdi, Onay Kutusu Bileşenini oluşturalım ve özelleştirelim:

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // Pozisyonu ve boyutu tanımlayın
    PenColor = 65535, // Rengi ayarlayın (bu durumda sarı)
    Style = BoxStyle.Star, // Onay kutusu için bir stil seçin
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## Adım 5: Belgeye Onay Kutusunu Ekleyin

Oluşturulan onay kutusu bileşenini PDF'e ekleyin:

```csharp
annotator.Add(checkBox);
```

## Adım 6: Değiştirilen Belgeyi Kaydedin

Güncellenen PDF belgesini onay kutusuyla birlikte kaydedin:

```csharp
annotator.Save("result.pdf");
```

## Adım 7: Çıktı Yolunu Görüntüle

Son olarak, kullanıcıya değiştirilen belgenin nereye kaydedildiğini bildirin:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Çözüm

Bu eğitimde, .NET için GroupDocs.Annotation kullanarak bir PDF belgesine başarıyla bir Onay Kutusu Bileşeni ekledik. Bu işlevsellik, kullanıcı deneyimini ve etkileşimini artırabilecek etkileşimli PDF'ler oluşturmanıza olanak tanır.

## SSS

### Onay kutusunun görünümünü özelleştirebilir miyim?

Kesinlikle! Renk, stil ve boyut gibi çeşitli özellikleri özel ihtiyaçlarınızı karşılayacak şekilde değiştirebilirsiniz.

### GroupDocs.Annotation for .NET ticari kullanıma uygun mudur?

Evet, GroupDocs.Annotation for .NET işletmelere yönelik ticari lisanslar sağlar.

### Satın almadan önce GroupDocs.Annotation for .NET'i deneyebilir miyim?

 Evet, ücretsiz deneme mevcuttur. Erişim sağlayabilirsiniz[Burada](https://releases.groupdocs.com/).

### GroupDocs.Annotation for .NET desteğini nerede bulabilirim?

 Destek ve ek kaynaklar şu adreste mevcuttur:[GroupDocs forumu](https://forum.groupdocs.com/c/annotation/10).

### Test amaçlı geçici lisansa ihtiyacım var mı?

 Test için geçici lisansı şuradan alabilirsiniz:[Burada](https://purchase.groupdocs.com/temporary-license/).