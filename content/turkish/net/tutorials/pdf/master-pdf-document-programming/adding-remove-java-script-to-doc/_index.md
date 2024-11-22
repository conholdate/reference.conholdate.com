---
title: PDF Belgesine Javascript'i Kaldırma Ekleme
linktitle: PDF Belgesine Javascript'i Kaldırma Ekleme
second_title: Aspose.PDF for .NET API Referansı
description: Bu kapsamlı kılavuz, özel davranışların nasıl ekleneceğini, hesaplamaların veya doğrulamaların dinamik olarak nasıl gerçekleştirileceğini ve diğer yazılım uygulamalarıyla nasıl entegre edileceğini gösterir.
type: docs
weight: 30
url: /tr/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## giriiş

Bu kapsamlı kılavuzda, .NET için Aspose.PDF dünyasına dalacağız ve PDF belgelerinize özel JavaScript işlevselliği eklemek için tüm potansiyelini açığa çıkaracağız. Bu güçlü özellik, dinamik öğeleri birleştirmenize, kullanıcı deneyimini geliştirmenize ve iş akışlarını düzenlemenize olanak tanır.

## Ön koşullar

Takip etmek için şunlara ihtiyacınız olacak:

1. Projenize .NET için Aspose.PDF yüklendi (buradan indirin)[Aspose.PDF for .NET indirme sayfası](https://releases.aspose.com/pdf/net/))
2. Kütüphaneyi kullanmak için geçerli bir lisans
3. AC# IDE veya metin düzenleyici

## Paketleri İçe Aktar

Başlamak için gerekli ad alanlarını projenize aktarın:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## Adım 1: Yeni bir PDF Belgesi Başlatın

Yeni bir PDF belgesi oluşturun ve tuvalinize ekleyin:

```csharp
Document doc = new Document();
doc.Pages.Add();
```

JavaScript ağırlıklı PDF'inizi oluşturmaya burada başlayacaksınız.

## Adım 2: PDF'ye JavaScript ekleyin

 JavaScript işlevlerini belgenize eklemek için:`doc.JavaScript` koleksiyon. İşte bir örnek:

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## Adım 3: PDF'yi JavaScript ile kaydedin

Güncellenmiş belgenizi diske kaydedin:

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

Artık mevcut bir PDF içindeki JavaScript koduna erişebilir ve onu değiştirebilirsiniz.

## Adım 4: Mevcut PDF'de JavaScript'i Yükleyin ve Görüntüleyin

 JavaScript içeren bir PDF dosyasını yükleyin ve anahtarlarına erişmek için şu adımları izleyin:`Keys` mülk:

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## Adım 5: JavaScript Fonksiyonlarını Görüntüle

JavaScript anahtarlarını yineleyin ve bunlara karşılık gelen kodu konsola yazdırın:

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

Bu, hangi JavaScript fonksiyonlarının şu anda mevcut olduğunu nasıl doğrulayabileceğinizi gösterir.

## Adım 6: PDF'den JavaScript'i kaldırın

İstenilen JavaScript fonksiyonunu ismine göre bulun ve kaldırın:

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

Kalan fonksiyonları yeniden yazdırarak fonksiyonun başarıyla silindiğini doğrulayın.

## Çözüm

Bu kapsamlı kılavuzda, Aspose.PDF for .NET'in özelleştirilebilir JavaScript işlevselliğinin gücünü nasıl açığa çıkaracağınızı keşfettiniz. Bu özellik sayesinde dinamik PDF'ler oluşturabilir, kullanıcı deneyimlerini iyileştirebilir ve iş akışlarını kolaylaştırabilirsiniz. Bu adımlarda ustalaşarak ve kütüphanenin yeteneklerini daha fazla keşfederek, uygulamalarınızda yeni olasılıkların kilidini açma yolunda iyi bir mesafe kat edeceksiniz.

## SSS

### Tek bir PDF'e birden fazla JavaScript fonksiyonu ekleyebilir miyim?
 Evet! İhtiyacınız olduğu kadar çok JavaScript işlevi ekleyebilirsiniz.`doc.JavaScript` koleksiyon.

### Varolmayan bir JavaScript fonksiyonunu kaldırmaya çalışırsam ne olur?
 Eğer fonksiyon mevcut değilse,`Remove` method bir hata atmaz, ancak hiçbir şeyi de kaldırmaz. Varolmayan işlevleri işlemek için ek hata işleme ekleyebilir veya kodu bunları yok sayacak şekilde değiştirebilirsiniz.

### PDF açılır açılmaz JavaScript'i çalıştırmak mümkün müdür?
Evet! JavaScript'i, belgeyi açmak veya bir düğmeye tıklamak gibi belirli tetikleyicilerde çalışacak şekilde yapılandırabilirsiniz.

### JavaScript'i PDF'e ekledikten sonra düzenleyebilir miyim?
Evet, mevcut bir PDF'yi yükleyebilir, JavaScript'ine erişebilir, kodu değiştirebilir ve belgeyi tekrar kaydedebilirsiniz.

### JavaScript'i kaldırmak PDF içeriğinin geri kalanını etkiler mi?
Hayır, JavaScript'i kaldırmak yalnızca betiği etkiler. PDF'in içeriği değişmeden kalır.