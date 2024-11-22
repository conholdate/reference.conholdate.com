---
title: Aspose.Zip for .NET ile Zip Dosyalarını Değiştirin
linktitle: Zip Dosyalarını Değiştir
second_title: Dosya Sıkıştırma ve Arşivleme için Aspose.Zip .NET API'si
description: Zip dosyalarına program aracılığıyla girdileri etkin bir şekilde nasıl çıkaracağınızı, sileceğinizi ve ekleyeceğinizi öğrenerek dosya düzenleme yeteneklerinizi geliştirin.
type: docs
weight: 15
url: /tr/net/tutorials/zip/file-compress/modify-zip-files/
---
## giriiş

Zip dosyaları veri organizasyonu ve sıkıştırma için hayati önem taşır, ancak içeriklerini programatik olarak nasıl değiştirirsiniz? Çözüm, C# ile zip dosyası manipülasyonunu basitleştiren sağlam bir kütüphane olan .NET için Aspose.Zip'te yatmaktadır. Bu eğitimde, zip dosyalarına girişleri adım adım çıkarma, silme ve ekleme konusunda size rehberlik edeceğiz.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Zip for .NET Library: Kütüphaneyi projenize yükleyin. İndirebilirsiniz[Burada](https://releases.aspose.com/zip/net/).
   
2. Belge Dizini: Zip dosyalarınızı depolamak için bir dizin ayarlayın. Değiştir`"Your Document Directory"` gerçek yolunuzla birlikte kodda.

## Gerekli Ad Alanlarını İçe Aktar

Gerekli ad alanlarını içe aktararak başlayın:

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## Adım 1: Dış Zip Dosyasını Açın

Öncelikle ana zip dosyanızı (dış zip) açın:

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    // İç zip girişlerini tanımlamaya devam edin
}
```

## Adım 2: İç Posta Kodu Girişlerini Tanımlayın

Daha sonra, iç zip dosyalarını tanımlayın ve silmeye hazırlanın:

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            // İç girdileri ayıkla
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## Adım 3: Dahili Arşiv Girişlerini Silin

İhtiyacınız olan girdileri topladıktan sonra, iç zip girdilerini silin:

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## Adım 4: Dış Zip'e Değiştirilmiş Girdileri Ekleyin

Artık yeni çıkartılan girdileri dış zip dosyanıza geri ekleyebilirsiniz:

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## Adım 5: Değiştirilen Zip Dosyasını Kaydedin

Son olarak değişikliklerinizi yeni bir zip dosyasına kaydedin:

```csharp
outer.Save(dataDir + "flatten.zip");
```

## Çözüm

.NET için Aspose.Zip, zip dosyalarını programatik olarak işlemek için güçlü ve basit bir yol sağlar. Bu eğitim, bir zip dosyasına girdi çıkarmayı, silmeyi ve eklemeyi ele alarak, kütüphanenin çok yönlülüğünü göstermektedir. Farklı senaryoları keşfedin ve dosya işleme becerilerinizi geliştirin!

## SSS

### Aspose.Zip for .NET'i diğer programlama dilleriyle birlikte kullanabilir miyim?
Aspose.Zip öncelikli olarak .NET uygulamaları için tasarlanmıştır, ancak Aspose çeşitli programlama dilleri için de benzer kütüphaneler sunmaktadır.

### Aspose.Zip for .NET için ücretsiz deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümü indirilebilir[Burada](https://releases.aspose.com/).

### Aspose.Zip for .NET desteğini nasıl alabilirim?
 Ziyaret edin[Aspose.Zip forumu](https://forum.aspose.com/c/zip/37) Destek ve tartışmalar için.

### Aspose.Zip for .NET için geçici bir lisans satın alabilir miyim?
 Evet, geçici bir lisans alabilirsiniz[Burada](https://purchase.conholdate.com/temporary-license/).

### Aspose.Zip for .NET'in belgelerini nerede bulabilirim?
 Tam dokümantasyon mevcuttur[Burada](https://reference.aspose.com/zip/net/).