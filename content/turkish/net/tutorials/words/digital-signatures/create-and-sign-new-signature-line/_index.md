---
title: Yeni İmza Satırı Oluşturun ve İmzalayın
linktitle: Yeni İmza Satırı Oluşturun ve İmzalayın
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerinize sorunsuz bir şekilde dijital imza eklemeyi öğrenin. Bu kapsamlı eğitim, ortamınızı kurmaktan ve bir imza satırı eklemekten imzalı belgelerinizi kaydetmeye ve doğrulamaya kadar her şeyi kapsar.
type: docs
weight: 10
url: /tr/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## giriiş

Bir Word belgesine dijital imza eklemek mi istiyorsunuz? Aspose.Words for .NET ile düşündüğünüzden daha kolay! Bu eğitim, ortamınızı kurma, imza satırı ekleme ve belgenizi dijital olarak imzalama adımlarında size rehberlik edecektir. Hadi başlayalım!

## Ön koşullar

Koda dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Words .NET için -[Buradan indirin](https://releases.aspose.com/words/net/).
2. .NET Geliştirme Ortamı - Visual Studio bu görev için idealdir.
3. İmzalanacak Belge - Yeni bir Word belgesi oluşturabilir veya mevcut bir belgeyi kullanabilirsiniz.
4.  Sertifika Dosyası - A`.pfx` Dijital imzalar için dosya gereklidir.
5. İmza Satırı Görseli (İsteğe bağlı) - İmza için bir resim dosyası ekleyebilirsiniz.

## Gerekli Ad Alanlarını İçe Aktar

Aspose.Words'ün işlevlerini kullanmak için aşağıdaki ad alanlarını içe aktarmanız gerekir:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Adım 1: Belge Dizinini Ayarlama

Belge dizininize giden yolu tanımlayarak başlayın. Bu, belgelerinizi kaydedeceğiniz ve geri alacağınız yer olacaktır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Belge dizin yolunuzu belirtin
```

## Adım 2: Yeni Bir Belge Oluşturma

Şimdi yeni bir Word belgesi oluşturalım. Bu belge imza satırınız için tuval görevi görecek.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: İmza Satırını Ekleme

 Şimdi şunu kullanın:`DocumentBuilder` Belgenize imza satırı eklemek için sınıf:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Adım 4: Belgeyi Kaydetme

İmza satırını ekledikten sonra belgeyi kaydedin. Bu, imzalamadan önce önemli bir adımdır.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Adım 5: İmzalama Seçeneklerini Yapılandırma

İmzalama süreci için seçenekleri ayarlayın. Bu, imza satırı kimliğini ve imzayla birlikte görüntülenecek isteğe bağlı resmi belirtmeyi içerir.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // İmajınıza giden yol
};
```

## Adım 6: Sertifikanın Yüklenmesi

Belgeyi imzalamak için gerekli sertifika dosyasını yükleyin:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Dosya adını ve şifreyi ayarlayın
```

## Adım 7: Belgenin İmzalanması

 Son olarak, belgeyi kullanarak imzalayın`DigitalSignatureUtil` Sınıf. İmzalanmış belgeyi gelecekte referans olması için yeni bir adla kaydedin.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Çözüm

Tebrikler! Başarılı bir şekilde bir Word belgesi oluşturdunuz, bir imza satırı eklediniz ve Aspose.Words for .NET kullanarak dijital olarak imzaladınız. Bu güçlü araç, sözleşmelerinizin ve resmi belgelerinizin güvenli bir şekilde imzalanmasını ve doğrulanmasını sağlayarak belge otomasyonunu basitleştirir.

## SSS

### İmza satırında başka resim formatları kullanabilir miyim?

Evet, PNG, JPG ve BMP dahil olmak üzere çeşitli resim formatlarını kullanabilirsiniz.

###  Birini kullanmak gerekli mi?`.pfx` file for the certificate?

 Evet, bir`.pfx` Dosya, dijital imzalar için sertifikaları ve özel anahtarları depolamak için kullanılan standart bir formattır.

### Tek bir belgeye birden fazla imza satırı ekleyebilir miyim?

Kesinlikle! Gerektiğinde ekleme adımını tekrarlayarak birden fazla imza satırı ekleyebilirsiniz.

### Dijital sertifikam yoksa ne olur?

Güvenilir bir sertifika kuruluşundan dijital sertifika almanız veya OpenSSL gibi araçları kullanarak bir sertifika oluşturmanız gerekecektir.

### Belgedeki dijital imzayı nasıl doğrularım?

İmzalanmış belgeyi Word'de açıp imza ayrıntılarını kontrol ederek dijital imzanın doğruluğunu ve bütünlüğünü doğrulayabilirsiniz.