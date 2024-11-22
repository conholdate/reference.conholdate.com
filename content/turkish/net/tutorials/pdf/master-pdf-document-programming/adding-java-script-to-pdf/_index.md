---
title: PDF Dosyasına Java Script Ekleme
linktitle: Java Script PDF Dosyası Ekle
second_title: Aspose.PDF for .NET API Referansı
description: Bu belge, Aspose.PDF for .NET kullanarak PDF belgelerine açılır uyarılar veya otomatik yazdırma işlevleri gibi etkileşimli öğeler eklemeye yönelik kapsamlı bir kılavuz sağlar.
type: docs
weight: 10
url: /tr/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## giriiş
Bu belge, Aspose.PDF for .NET kullanarak PDF belgelerine açılır uyarılar veya otomatik yazdırma işlevleri gibi etkileşimli öğeler eklemeye yönelik kapsamlı bir kılavuz sunar. Bu kitaplığın yeteneklerinden yararlanarak, çeşitli kullanıcı ihtiyaçlarını karşılayan dinamik ve ilgi çekici PDF'ler oluşturabilirsiniz.

## Ön koşullar
 Devam etmeden önce, .NET için Aspose.PDF'nin en son sürümünü indirdiğinizden emin olun.[Aspose Sürümleri](https://sürümler.aspose.com/pdf/net/) veya web siteleri üzerinden ücretsiz deneme sürümü edinebilirsiniz:[releases.aspose.com](http://releases.aspose.com).

Ayrıca C# hakkında temel bir anlayışa sahip olmalı ve kullandığınız geliştirme ortamına aşina olmalısınız. Ek olarak, geliştirme süreciniz sırasında sınırlamalardan kaçınmanız gerekiyorsa, Aspose'dan geçici bir lisans edinmeyi düşünün.

## Gerekli Paketleri İçe Aktarma
Kod yazmaya başlamak için Aspose.PDF kitaplığından gerekli ad alanlarını içe aktarın:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Adım 1: Mevcut bir PDF'yi Yükleme
Etkileşimli öğeler eklemek istediğiniz mevcut bir PDF belgesini yükleyin:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` PDF dosyanızın gerçek yolunu belirtin.

## Adım 2: Belge Düzeyinde JavaScript Ekleme

 Belge açıldığında tetiklenen bir betiği uygulamak için bir örnek oluşturun`JavascriptAction` nesne:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Adım 3: Sayfa Düzeyinde JavaScript Ekleme

 Sayfa açılışlarına veya kapanışlarına göre belirli eylemleri tetiklemek için bir örnek oluşturun`JavascriptAction` her sayfa için nesne:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Adım 4: PDF Belgesini Kaydetme

Değiştirilen PDF belgesini kaydetmek için çıktı dosyası yolunu belirtin:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Çözüm
Bu kılavuzu takip ederek ve Aspose.PDF for .NET'i kullanarak, PDF'lerinizi etkileşimli öğelerle etkili bir şekilde geliştirebilirsiniz. Bu kütüphane, çeşitli kullanıcı ihtiyaçlarını karşılayan dinamik ve ilgi çekici belgeler oluşturmak için kapsamlı bir çözüm sunar.

## SSS

### Bir PDF'deki farklı sayfalara birden fazla JavaScript eylemi ekleyebilir miyim?
Evet, farklı JavaScript eylemlerini tek tek sayfalara veya tüm belgeye atayabilirsiniz.

### PDF'e JavaScript eklendikten sonra JavaScript'i kaldırmak mümkün müdür?
 Evet, mevcut JavaScript eylemlerini temizleyerek kaldırabilir veya değiştirebilirsiniz.`Actions` Belgenin veya sayfanın özellikleri.

### PDF'de hangi tür JavaScript fonksiyonlarını kullanabilirim?
Yazdırma, uyarılar ve form düzenlemeleri gibi Adobe Acrobat'ın JavaScript motorunun desteklediği tüm JavaScript'leri kullanabilirsiniz.

### JavaScript tüm PDF görüntüleyicilerinde çalışır mı?
Çoğu JavaScript eylemi, Adobe Acrobat gibi etkileşimli PDF'leri destekleyen PDF görüntüleyicilerinde çalışır. Ancak, bazı temel PDF okuyucuları JavaScript'i desteklemeyebilir.