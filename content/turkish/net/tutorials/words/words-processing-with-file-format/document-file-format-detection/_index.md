---
title: Belge Dosya Biçimi Algılama
linktitle: Belge Dosya Biçimi Algılama
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak çeşitli belge dosya biçimlerini sorunsuz bir şekilde nasıl algılayıp yöneteceğinizi öğrenin. Pratik örnekler, ipuçları ve SSS içeren ayrıntılı kılavuzumuzu takip edin.
type: docs
weight: 10
url: /tr/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## giriiş

Günümüzün dijital ortamında çeşitli belge biçimlerini etkin bir şekilde yönetmek ve düzenlemek kritik öneme sahiptir. Aspose.Words for .NET, farklı dosya türlerini algılamak ve işlemek için sağlam bir çözüm sunar. Bu kılavuzda, belge biçimlerini algılama, doğruluğu sağlama ve değerli zamandan tasarruf etme adım adım sürecini ele alıyoruz.

## Belge Algılamanın Ön Koşulları

Başlamadan önce aşağıdaki şartların karşılandığından emin olun:

1. Aspose.Words for .NET Kütüphanesi  
    Kütüphaneyi şu adresten indirin:[Aspose Words Yayınları](https://releases.aspose.com/words/net/)ve geçerli bir lisans kullanarak etkinleştirin. Geçici lisanslar için şu adresi ziyaret edin:[Aspose Geçici Lisans](https://purchase.aspose.com/temporary-license/).

2. Geliştirme Ortamı  
   .NET Framework yüklü olarak Visual Studio'yu (herhangi bir güncel sürüm) kullanın.

3. Temel Dosya Kurulumu  
   Giriş dosyalarınızı düzenleyin ve algılanan biçimleri sıralamak için dizinleri hazırlayın.

## Temel Ad Alanlarını İçe Aktar

Programınızın başına şu ad alanlarını ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Bu içe aktarımlar, dosya biçimi algılama için gerekli sınıflara ve yöntemlere erişim sağlar.

## Adım 1: Düzenli Çıktı için Dizinleri Başlatın

Algılanan formata göre dosyaların saklanacağı dizinleri oluşturun.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

// Dizinlerin var olduğundan emin olun
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

Bu yapı dosya yönetimini kolaylaştırır.

## Adım 2: Dosya Listesini Alın

İşlemleri kolaylaştırmak için bozuk veya desteklenmeyen belgeleri filtreleyin.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

Filtrelenmiş liste yalnızca geçerli dosyalarla çalışmanızı sağlar.

## Adım 3: Dosya Biçimlerini Algılayın ve Sınıflandırın

Her dosyanın biçimini belirlemek ve uygun dizine taşımak için her dosyanın içinde dolaşın.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    // Çıkış algılanan format
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

 The`FileFormatUtil.DetectFileFormat`Yöntem, belgenin özelliklerinin belirlenmesinde merkezi bir öneme sahiptir.

## Çözüm

Aspose.Words for .NET'i kullanarak, belge dosya biçimlerini algılamak zahmetsiz bir görev haline gelir. Çeşitli biçimleri tanımlama ve kategorilere ayırma yeteneği, sorunsuz belge yönetimini garanti ederek üretkenliği ve iş akışı verimliliğini artırır.

## SSS

### Belge formatlarının tespitinin temel amacı nedir?  
Biçimlerin algılanması, dosyaları belirli iş akışları veya uygulamalar için kategorilere ayırarak belge işlemeyi kolaylaştırmaya yardımcı olur.

### Aspose.Words şifreli dosyaları destekliyor mu?  
Evet, şifrelemeyi algılayabilir ve şifrelenmiş belgeleri buna göre işleyebilir.

### Bu çözümü diğer dosya türleri için de genişletebilir miyim?  
Evet, ek formatları eklemek veya diğer Aspose kütüphanelerini entegre etmek için kodu değiştirebilirsiniz.

### Bilinmeyen formatları nasıl idare edebilirim?  
Bilinmeyen formatları, manuel inceleme veya özel araçlarla daha ileri işleme için ayrı ayrı saklayın.

### Ek belgeleri nerede bulabilirim?  
 Ziyaret edin[Aspose.Words Belgeleri](https://reference.aspose.com/words/net/) Kapsamlı kılavuzlar ve örnekler için.
