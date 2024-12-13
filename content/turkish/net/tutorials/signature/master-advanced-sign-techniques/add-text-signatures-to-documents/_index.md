---
title: GroupDocs.Signature Kullanarak Belgelere Metin İmzaları Ekleyin
linktitle: Belgelere Metin İmzaları Ekleyin
second_title: GroupDocs.Signature .NET API
description: GroupDocs.Signature for .NET kullanarak belgeleri metinle nasıl imzalayacağınızı öğrenin. Metin imzalarını program aracılığıyla eklemek için adım adım kılavuz.
type: docs
weight: 17
url: /tr/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## giriiş

Günümüzün dijital ortamında, elektronik belge imzalama iş akışlarını kolaylaştırmak ve kaynakları korumak için olmazsa olmaz hale geldi. GroupDocs.Signature for .NET, çeşitli belge biçimlerine programatik olarak metin imzaları eklemek için güçlü bir çözüm sunar. Bu eğitim, GroupDocs.Signature for .NET kullanarak bir belgeyi metinle imzalama adımlarında size rehberlik edecektir.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  GroupDocs.Signature for .NET: Kütüphaneyi şu adresten indirin ve yükleyin:[Burada](https://releases.groupdocs.com/signature/net/).
2. Geliştirme Ortamı: .NET geliştirme ortamınızı kurun.
3. Belge: İmzalamak istediğiniz belgeyi hazırlayın (örneğin PDF, Word).

## Gerekli Ad Alanlarını İçe Aktarma

Öncelikle gerekli ad alanlarını .NET projenize aktarın:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Adım 1: Belgeyi Yükleyin

İmzalamak istediğiniz belgeyi yükleyerek başlayın:

```csharp
string filePath = "sample.pdf"; // Belgenize giden yol
string fileName = Path.GetFileName(filePath);
```

## Adım 2: Çıktı Dosya Yolunu Tanımlayın

Ardından imzalanan belgenin kaydedileceği çıktı dosyası yolunu ayarlayın:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Adım 3: İmza Seçenekleri Oluşturun

İçerik, konum, boyut, renk ve yazı tipi stili dahil olmak üzere metin imzanız için seçenekleri yapılandırın:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // pozisyonu
    Top = 200, // Y pozisyonu
    Width = 100, // İmzanın genişliği
    Height = 30, // İmzanın yüksekliği
    ForeColor = Color.Red, // Metin rengi
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Yazı tipi ayarları
};
```

## Adım 4: Belgeyi İmzalayın

Son olarak, metin imzasını uygulamak ve imzalanmış belgeyi kaydetmek için GroupDocs.Signature'ı kullanın:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Belgeyi imzala
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Çözüm

Bu eğitimde, .NET için GroupDocs.Signature kullanarak bir belgeye programatik olarak metin imzası eklemeyi gösterdik. Bu adımları izleyerek belgelerinizin güvenliğini ve özgünlüğünü etkili bir şekilde artırabilirsiniz.

## SSS

### Metin imzasının görünümünü özelleştirebilir miyim?
Evet, metin imzanızın rengi, yazı tipi, boyutu ve konumu gibi çeşitli niteliklerini ihtiyaçlarınıza uyacak şekilde özelleştirebilirsiniz.

### GroupDocs.Signature birden fazla belge formatıyla uyumlu mudur?
Kesinlikle! GroupDocs.Signature, PDF, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere çok çeşitli formatları destekler.

### Tek bir belgeye birden fazla metin imzası ekleyebilir miyim?
Evet, her biri kendine özgü özelleştirme seçeneklerine sahip birden fazla metin imzası ekleyebilirsiniz.

### GroupDocs.Signature imzalamadan sonra belge bütünlüğünü garanti ediyor mu?
Evet, kütüphane belge bütünlüğünü garanti altına almak ve imzalamadan sonra belgede herhangi bir değişiklik yapılmasını önlemek için güçlü şifreleme algoritmaları kullanmaktadır.

### Satın almadan önce test etmek için deneme sürümü mevcut mu?
 Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[Burada](https://releases.groupdocs.com/) Satın alma işlemi yapmadan önce özelliklerini keşfetmek için.