---
title: Parola Korumalı Belgeleri Yükleme
linktitle: Parola Korumalı Belgeleri Yükle
second_title: GroupDocs.Viewer .NET API
description: GroupDocs.Viewer ile belge görüntüleme yeteneklerini .NET uygulamalarınıza zahmetsizce nasıl entegre edeceğinizi keşfedin. Bu eğitim kapsamlı, adım adım bir kılavuz sunar.
type: docs
weight: 12
url: /tr/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## giriiş

Dijital ortamda, çeşitli belge biçimlerini yönetme ve görüntüleme yeteneği işletmeler ve bireyler için hayati önem taşır. .NET için GroupDocs.Viewer, geliştiricilerin belge görüntüleme yeteneklerini uygulamalarına zahmetsizce entegre etmeleri için sağlam bir çözüm sunar. Bu eğitim, parola korumalı belgeleri adım adım yükleme sürecinde size rehberlik edecek ve bu özelliği projelerinizde sorunsuz bir şekilde uygulayabilmenizi sağlayacaktır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  GroupDocs.Viewer for .NET Yüklendi: Şuradan indirin:[web sitesi](https://releases.groupdocs.com/viewer/net/).
2. Şifreyle Korunan Belge: Test için şifreyle korunan bir belgeyi hazır bulundurun.

## Gerekli Ad Alanlarını İçe Aktar

Öncelikle gerekli ad alanlarını projenize aktarın:

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Adım 1: Çıktı Dizinini Tanımlayın

İşlenen çıktının nereye kaydedilmesini istediğinizi belirtin:

```csharp
string outputDirectory = "Your Document Directory";
```
 Değiştirdiğinizden emin olun`"Your Document Directory"` kullanmak istediğiniz gerçek yol ile.

## Adım 2: Sayfa Dosyası Yolu Biçimini Ayarlayın

Her oluşturulan sayfanın dosya yollarının biçimini tanımlayın:

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

 Bu, şu şekilde yollar üretecektir:`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`, vesaire.

## Adım 3: Yükleme Seçeneklerini Yapılandırın

Parola dahil olmak üzere parola korumalı belgeniz için yükleme seçeneklerini ayarlayın:

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  // Belgenizin şifresiyle değiştirin
};
```

## Adım 4: Görüntüleyiciyi Başlatın

Belgeniz ve yükleme seçenekleriyle bir GroupDocs.Viewer örneği oluşturun:

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    // Görüntüleme seçenekleri için kod bir sonraki adımda eklenecektir.
}
```
 Değiştirdiğinizden emin olun`"Path_to_your_document"` belgenizin gerçek yolunu belirtin.

## Adım 5: HTML Görünüm Seçeneklerini Yapılandırın

Belgeyi gömülü kaynaklarla işlemek için HTML görünüm seçeneklerini ayarlayın:

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## Adım 6: Belgeyi Oluşturun

Şimdi, yapılandırılmış görüntüleyiciyi ve görünüm seçeneklerini kullanarak belgeyi işleyin:

```csharp
viewer.View(options);
```

## Adım 7: Başarılı Mesajını Göster

Son olarak, kullanıcıya belgenin başarıyla işlendiğini bildirin:

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Çözüm

Bu eğitimde, GroupDocs.Viewer for .NET kullanarak parola korumalı belgelerin nasıl yükleneceğini inceledik. Geliştiriciler bu adımları izleyerek bu işlevselliği uygulamalarına kolayca entegre edebilir ve kullanıcıların korumalı belgeleri zahmetsizce görüntülemesine olanak tanır.

## SSS

### GroupDocs.Viewer parola korumalı belgelerin yanı sıra diğer belge biçimlerini de işleyebilir mi?

Evet, GroupDocs.Viewer PDF, DOCX, XLSX, PPTX ve daha fazlası dahil olmak üzere çok çeşitli formatları destekler.

### GroupDocs.Viewer .NET Core ile uyumlu mudur?

Kesinlikle! GroupDocs.Viewer hem .NET Framework hem de .NET Core ortamlarıyla uyumludur.

### Belgelerin görüntüleme seçeneklerini özelleştirebilir miyim?

Evet, GroupDocs.Viewer çeşitli görüntüleme seçenekleri sunarak görüntüleme deneyiminizi ihtiyaçlarınıza göre uyarlamanıza olanak tanır.

### GroupDocs.Viewer belge açıklamalarını destekliyor mu?

Evet, belge açıklamalarını destekler ve kullanıcıların yorum, vurgulama ve diğer notları eklemesine olanak tanır.

### GroupDocs.Viewer için deneme sürümü mevcut mu?

 Evet, ücretsiz deneme sürümünü şu adresten edinebilirsiniz:[web sitesi](https://releases.groupdocs.com/).