---
title: Verimli Belge Özetleme Açık AI Modeli
linktitle: Verimli Belge Özetleme Açık AI Modeli
second_title: Aspose.Words Belge İşleme API'si
description: Önkoşulları, kurulumu ve kodlama örneklerini kapsayan bu kapsamlı eğitimle büyük belgeleri nasıl hızlı ve doğru bir şekilde özetleyeceğinizi öğrenin.
type: docs
weight: 10
url: /tr/net/tutorials/words/advanced-ai-document-processing/efficient-document-summarization-openai-model/
---
## giriiş

Günümüzün dijital dünyasında verimli belge yönetimi vazgeçilmez hale geldi. Aspose.Words for .NET ile belge özetleme, özellikle OpenAI modellerinin yetenekleriyle birleştirildiğinde daha kolay ve daha üretken hale geliyor. Bu kılavuz, Aspose.Words for .NET ve OpenAI modellerini kullanarak belgeleri otomatik olarak özetleme, zamandan tasarruf etme ve hızlı içgörüler sağlama adım adım sürecini size anlatacak. İster raporları, ister akademik makaleleri veya kapsamlı belgeleri özetliyor olun, bu kılavuz araçlarınızdan en iyi şekilde yararlanmanıza yardımcı olacak.

## Ön koşullar

### .NET Ortam Kurulumu
Uyumlu bir .NET framework sürümünüz olduğundan emin olun. Bu eğitim .NET 5.0 ve üzeri ile uyumludur.

### .NET için Aspose.Words'ü yükleyin
 Aspose.Words for .NET paketini şu adresten indirin:[Aspose web sitesi](https://releases.aspose.com/words/net/)ve Visual Studio'daki NuGet Paket Yöneticisi'ni kullanarak projenize yükleyin.

### Bir OpenAI API Anahtarı edinin
 OpenAI'nin dil modellerine erişmek için bir API anahtarına ihtiyacınız olacak.[OpenAI web sitesi](https://openai.com/)anahtarınızı alın ve entegrasyon için güvenli bir yerde saklayın.

### Entegre Geliştirme Ortamı
Visual Studio'yu IDE olarak kullanmak kodlama ve hata ayıklama sürecini basitleştirecektir.

## Gerekli Kütüphaneleri İçeri Aktarma

Projenizde, belge düzenleme ve özetleme için gerekli sınıflara ve yöntemlere erişebildiğinizden emin olmak için gerekli kütüphaneleri içe aktarın.

### Aspose.Words Paketini İçe Aktarma

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;
using System.Text;
```

OpenAI'ye API çağrılarını işlemek için harici bir kütüphane kullanıyorsanız, kurulu ve yapılandırılmış olduğundan emin olun. Şimdi, belge özetlemenin nasıl ayarlanacağına bir göz atalım.

## Adım 1: Belge Yollarını Tanımlayın

Belge kaynaklarınızı düzenlemek ve oluşturulan özetleri kaydetmek için dizinler tanımlayın.

```csharp
string MyDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
string ArtifactsDir = "YOUR_OUTPUT_DIRECTORY_PATH";
```

## Adım 2: Özetlenecek Belgeyi/Belgeleri Yükleyin

Aspose.Words kullanarak uygulamanıza bir veya daha fazla belge yükleyin. Bu örnek, gösterim amaçlı iki belge yükler:

```csharp
Document doc1 = new Document(MyDir + "BigDocument.docx");
Document doc2 = new Document(MyDir + "AnotherDocument.docx");
```

## Adım 3: OpenAI API Anahtarını Ayarlayın

Güvenlik için OpenAI API anahtarınızı sabit kodlamak yerine ortam değişkenlerinden alın.

```csharp
string apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
```

## Adım 4: OpenAI Modelini Başlatın

 Özetleme için OpenAI modelinin bir örneğini oluşturun. Burada, şunu kullanıyoruz`Gpt4OMini` Özetleri kısa ama öz tutmak.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

## Adım 5: Tek Bir Belgeyi Özetleyin

Oluşturulan model örneği ile tek bir belgenin özetini oluşturun.

```csharp
Document summaryDoc = model.Summarize(doc1, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
summaryDoc.Save(ArtifactsDir + "SingleDocSummary.docx");
```

 Bu, kısa bir özeti kaydedecektir`doc1` belirlenen çıktı dizininde.

## Adım 6: Birden Fazla Belgeyi Özetleyin

Birden fazla belgeden birleşik bir özet oluşturmak istiyorsanız, özetleme yöntemini değiştirmeniz yeterlidir.

```csharp
Document combinedSummary = model.Summarize(new Document[] { doc1, doc2 }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
combinedSummary.Save(ArtifactsDir + "CombinedSummary.docx");
```

Bu yaklaşım, toplu olarak kapsamlı raporlardan veya ilgili belgelerden özetler oluşturmak için idealdir.

## Çözüm

Belge özetleme için Aspose.Words for .NET ve OpenAI modellerini kullanmak muazzam üretkenlik avantajları sunar. İster tek bir belge ister birden fazla dosya işleyin, bu entegrasyon hızlı, güvenilir özetler sunarak karmaşık belgeleri özlü, sindirilebilir içgörülere dönüştürür.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, Word belgelerini programatik olarak yönetmek için sağlam bir kütüphanedir. Çok sayıda formatta oluşturma, düzenleme ve dönüştürmeyi destekler.

### Neden bir OpenAI API Anahtarına ihtiyacım var?
Özetler veya diğer doğal dil işleme görevleri oluşturmak için OpenAI'nin dil modellerine erişmek için bir API anahtarı gereklidir.

### Birden fazla belge özetini birleştirebilir miyim?
Evet, Aspose.Words birden fazla belgeden aynı anda özet oluşturmanıza olanak tanır; proje raporları veya vaka çalışmaları için idealdir.

### Aspose.Words for .NET'i nasıl kurabilirim?
Visual Studio'da NuGet Paket Yöneticisi'ni kullanarak Aspose.Words paketini arayıp "Yükle"yi seçerek yükleyin.

### Aspose.Words ücretsiz olarak kullanılabilir mi?
 Yeteneklerini test etmek için Aspose.Words'ün ücretsiz deneme sürümünü indirebilirsiniz.[Aspose web sitesi](https://releases.aspose.com/).