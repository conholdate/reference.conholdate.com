---
title: .NET için Aspose.Note'ta Dosya Ekleme ve Simge Ayarlama
linktitle: Aspose'da Dosya Ekle ve Simge Ayarla.Not
second_title: Aspose.Not .NET API'si
description: Aspose.Note for .NET kullanarak Microsoft OneNote belgelerine dosya eklemeyi ve özel simgeler ayarlamayı adım adım öğrenin. .NET uygulamanızı kusursuz belge yönetimi ve özelleştirme özellikleriyle geliştirin.
type: docs
weight: 10
url: /tr/net/tutorials/note/manage-attachments/attaching-files-setting-icons/
---
## giriiş

Aspose.Note for .NET, geliştiricilerin Microsoft OneNote dosyalarını programatik olarak oluşturması, düzenlemesi ve dönüştürmesi için tasarlanmış gelişmiş bir kütüphanedir. Bu kütüphanenin öne çıkan bir özelliği, OneNote belgelerine dosya ekleme ve simgelerini özelleştirme yeteneğidir. Bu kılavuzda, Aspose.Note for .NET'i sorunsuz bir şekilde dosya eklemek ve özel simgeler ayarlamak için nasıl kullanacağınızı keşfedeceğiz ve OneNote belge işlevselliğinizi zenginleştireceğiz.

## Ön koşullar

Çözümü uygulamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- Geliştirme Ortamı: .NET geliştirme için yapılandırılmış Visual Studio veya benzer bir IDE.
-  Kütüphane Kurulumu: Şunu kurun:[.NET için Aspose.Note](https://releases.aspose.com/words/net/) kütüphane.
- Programlama Bilgisi: C# hakkında temel bilgi.

## Gerekli Ad Alanlarını İçe Aktarma

Temel işlevsellik için projenize şu ad alanlarını ekleyin:

```csharp
using System.IO;
using Aspose.Note;
using System;
using System.Collections.Generic;
using System.Drawing.Imaging;
```

Aşağıda adım adım detaylı uygulama yer almaktadır.

## Adım 1: Yeni Bir OneNote Belgesi Oluşturun

 Yeni bir OneNote belgesini şu şekilde başlatın:`Document` sınıf.

```csharp
Document doc = new Document();
```

## Adım 2: Yeni Bir Sayfa Ekleyin

Notlarınızı ve eklerinizi düzenlemek için belgeye bir sayfa ekleyin.

```csharp
Aspose.Note.Page page = new Aspose.Note.Page(doc);
```

## Adım 3: Bir Ana Hat Oluşturun

 Bir tane oluştur`Outline` OneNote sayfanızdaki öğeler için kapsayıcı görevi gören nesne.

```csharp
Outline outline = new Outline(doc);
```

## Adım 4: Bir Anahat Elemanı Başlatın

 Bir`OutlineElement` eki ve ilişkili simgeyi tutacaktır.

```csharp
OutlineElement outlineElem = new OutlineElement(doc);
```

## Adım 5: Bir Dosya Ekleyin ve Simgesini Belirleyin

Eklenecek dosyayı belirtin ve ona bir simge ekleyin.

```csharp
string dataDir = "Your Document Directory";

using (var stream = File.OpenRead(dataDir + "icon.jpg"))
{
    AttachedFile attachedFile = new AttachedFile(doc, dataDir + "attachment.txt", stream, ImageFormat.Jpeg);
    outlineElem.AppendChildLast(attachedFile);
}
```

## Adım 6: Belge Yapısını Birleştirin

 Ekle`OutlineElement` için`Outline` ve`Outline` için`Page`.

```csharp
outline.AppendChildLast(outlineElem);
page.AppendChildLast(outline);
```

## Adım 7: Sayfayı Belgeye Ekleyin

Son olarak sayfayı OneNote belgenize ekleyin.

```csharp
doc.AppendChildLast(page);
```

## Adım 8: Belgeyi Kaydedin

Güncellenmiş belgenizi dosya eki ve simgesiyle birlikte dışarı aktarın.

```csharp
dataDir = dataDir + "AttachFileAndSetIcon_out.one";
doc.Save(dataDir);
```

## Çözüm

Bu kılavuzda özetlenen adımları izleyerek, Aspose.Note for .NET kullanarak OneNote belgelerine zahmetsizce dosya ekleyebilir ve özel simgeler ayarlayabilirsiniz. Bu işlevsellik, belge organizasyonunu ve kullanıcı deneyimini büyük ölçüde iyileştirebilir, uygulamalarınızı daha sağlam ve özellik açısından zengin hale getirebilir.

## SSS

### Tek bir nota birden fazla dosya eklenebilir mi?
Evet, her dosya için ekleme işlemini tekrarlayarak birden fazla dosya ekleyebilirsiniz.

### Simgeler için hangi resim biçimleri destekleniyor?
Aspose.Note, ek simgeleri için JPEG, PNG, BMP ve GIF formatlarını destekler.

### Harici URL'lerden dinamik olarak dosya eklemek mümkün müdür?
 .NET kütüphanelerini kullanarak dosyaları indirebilirsiniz.`HttpClient` ve sonra bunları Aspose.Note kullanarak ekleyin.

### Ekler için dosya boyutu sınırlaması var mı?
Aspose.Note tarafından belirlenmiş açık bir boyut sınırı yoktur, ancak sistem kaynaklarınızın büyük dosyaları kaldırabileceğinden emin olun.

### Simgeler ayarlanmadan önce yeniden boyutlandırılabilir mi?
 Evet, .NET'i kullanarak simge görüntüsünü düzenleyebilirsiniz.`System.Drawing` Eklemeden önce kütüphaneyi kontrol edin.

 Daha fazla yardım için, şunu keşfedin:[belgeleme](https://reference.aspose.com/words/net/) veya ulaşın[Aspose desteği](https://forum.aspose.com/c/words/8).