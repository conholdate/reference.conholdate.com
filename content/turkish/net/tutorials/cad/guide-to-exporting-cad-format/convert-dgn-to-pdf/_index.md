---
title: Aspose.CAD for .NET'te DGN'yi PDF'ye dönüştürün
linktitle: Aspose.CAD for .NET'te DGN'yi PDF'ye dönüştürün
second_title: Aspose.CAD .NET - CAD ve BIM Dosya Biçimi
description: .NET için güçlü Aspose.CAD kütüphanesini kullanarak DGN dosyalarını zahmetsizce PDF'ye nasıl dönüştüreceğinizi öğrenin. Bu adım adım kılavuz, her seviyedeki geliştirici için tasarlanmıştır.
type: docs
weight: 12
url: /tr/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## giriiş

CAD dosyalarının dünyasında gezinmek zor olabilir, ancak Aspose.CAD for .NET ile geliştiriciler çeşitli CAD formatlarını kolayca işleyebilir ve dönüştürebilir. Yaygın ihtiyaçlardan biri, bu eğitimde adım adım inceleyeceğimiz DGN dosyalarını PDF'lere dönüştürmektir.

## Ön koşullar

Takip edebilmek için aşağıdakilere sahip olduğunuzdan emin olun:

- C# ve .NET framework'ünde temel yeterlilik.
-  Aspose.CAD for .NET kütüphanesi yüklü. İndirebilirsiniz[Burada](https://releases.aspose.com/cad/net/).
- Örnek bir DGN dosyası (örneğin, Nikon_D90_Camera.dgn). 

## Adım 1: Gerekli Ad Alanlarını İçe Aktarın

Öncelikle ilgili ad alanlarını C# projenize aktararak başlayın:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Adım 2: DGN Dosyasını Yükleyin

DGN dosyanız için dizini belirtin ve aşağıdaki kodu kullanarak yükleyin:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Ek işlem buraya yapılacak...
}
```

## Adım 3: Rasterleştirme Seçeneklerini Yapılandırın

Ardından, DGN'nizin PDF'de nasıl işleneceğini tanımlamak için rasterleştirme seçeneklerini ayarlayın:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Genişliği gerektiği gibi ayarlayın
    PageHeight = 300, // Yüksekliği gerektiği gibi ayarlayın
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Adım 4: PDF Seçenekleri Oluşturun

Daha önce yapılandırılan rasterleştirme ayarlarını entegre ederek PDF seçeneklerini tanımlayın:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Adım 5: DGN'yi PDF olarak kaydedin

Son olarak, yapılandırdığınız seçenekleri kullanarak DGN dosyasını PDF olarak kaydedin:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Çözüm

Tebrikler! Aspose.CAD for .NET kullanarak bir DGN dosyasını başarıyla PDF'ye dönüştürdünüz. Bu basit eğitim, DGN dosyasını yükleme, rasterleştirme seçeneklerini ayarlama ve çıktıyı PDF olarak kaydetme konusunda size rehberlik etti.

## SSS

### Aspose.CAD'i kullanmak için önceden CAD bilgisine sahip olmam gerekir mi?  
Kesinlikle! Aspose.CAD, karmaşık CAD görevlerini basitleştirmek ve CAD bilgisine bakılmaksızın tüm geliştiricilerin erişimine açmak için tasarlanmıştır.

### Aspose.CAD için daha fazla kaynak ve dokümanı nerede bulabilirim?  
 Kapsamlı kılavuzları ve örnekleri şu adreste inceleyebilirsiniz:[Aspose.CAD dokümantasyonu](https://reference.aspose.com/cad/net/).

### Aspose.CAD için ücretsiz deneme sürümü mevcut mu?  
 Evet, ücretsiz deneme alınabilir[Burada](https://releases.aspose.com/).

### Aspose.CAD için geçici lisansı nasıl alabilirim?  
 Geçici lisans talebinde bulunabilirsiniz[Burada](https://purchase.conholdate.com/temporary-license/).

### Yardıma mı ihtiyacınız var veya sorularınız mı var?  
 Sohbete katılın[Aspose.CAD forumu](https://forum.aspose.com/c/cad/19) Topluluk desteği ve sorularınız için.