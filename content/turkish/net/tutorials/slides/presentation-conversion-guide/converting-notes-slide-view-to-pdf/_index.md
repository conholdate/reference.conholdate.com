---
title: Aspose.Slides for .NET ile Not Slayt Görünümünü PDF'ye Dönüştürme
linktitle: Aspose.Slides for .NET ile Not Slayt Görünümünü PDF'ye Dönüştürme
second_title: Aspose.Slides .NET PowerPoint İşleme API'si
description: Aspose.Slides for .NET kullanarak Notes Slide View ile PowerPoint sunumlarını zahmetsizce PDF formatına nasıl dönüştüreceğinizi öğrenin. Bu kılavuz ayrıntılı talimatlar içerir.
type: docs
weight: 15
url: /tr/net/tutorials/slides/presentation-conversion-guide/converting-notes-slide-view-to-pdf/
---
## giriiş

PowerPoint sunumlarıyla sık sık çalışıyorsanız, sunumları ayrıntılı notlarla paylaşmanın ne kadar önemli olabileceğini biliyorsunuzdur. Bu sunumları Notlar Slayt Görünümü ile PDF'ye dönüştürmek, bunları kolayca erişilebilir hale getirmenin pratik bir yoludur. Aspose.Slides for .NET, sunumlarınızı verimli bir şekilde özelleştirmenize ve dışa aktarmanıza olanak tanıyarak bu görevi kolaylaştıran güçlü bir kütüphanedir.

## Ön koşullar

Başlamadan önce aşağıdaki gereksinimleri karşıladığınızdan emin olun:

-  Geliştirme Ortamı: Kurulum[Görsel Stüdyo](https://visualstudio.microsoft.com/) veya herhangi bir C# IDE'si.
- Aspose.Slides for .NET Kütüphanesi: Kütüphaneyi şu adresten indirin:[Burada](https://releases.aspose.com/slides/net/).
-  Sunum Dosyası: Bir PowerPoint dosyanız olsun (örneğin,`NotesFile.pptx`) dönüşüme hazır.

## Ortamınızı Kurma

Geliştirme ortamınızı kurmak için şu adımları izleyin:

1. Yeni Bir Proje Oluşturun: IDE'nizi açın ve yeni bir C# Konsol Uygulaması projesi oluşturun.
2. Aspose.Slides Referansını Ekle: 
- NuGet Paket Yöneticisini kullanarak kütüphaneyi yükleyin:
 ```
 Install-Package Aspose.Slides.NET
 ```
- Alternatif olarak, Aspose.Slides DLL'ini projenize manuel olarak ekleyebilirsiniz.

```csharp
using Aspose.Slides;
```
Projeniz artık Aspose.Slides for .NET ile çalışmaya hazır.

## Sunumu Yükleme

Başlamak için PowerPoint dosyanızı uygulamanıza yükleyin. Bunu yapmak için kod şu şekilde:

```csharp
string dataDir = "Your Document Directory";
using (Presentation presentation = new Presentation(dataDir + "NotesFile.pptx"))
{
	// Daha fazla kod buraya gelir
}

```

 Yer değiştirmek`"Your Document Directory"` sunum dosyanızı içeren klasörün yolunu belirtin.

## PDF Seçeneklerini Yapılandırma

 Notlar Slayt Görünümünü PDF'nize eklemek için,`PdfOptions` Aşağıda gösterildiği gibi nesne:

```csharp
PdfOptions pdfOptions = new PdfOptions();
INotesCommentsLayoutingOptions options = pdfOptions.NotesCommentsLayouting;

// Çıktı PDF'indeki notların konumunu ayarlayın
options.NotesPosition = NotesPositions.BottomFull;
```

Bu yapılandırma, notların PDF çıktısında slaytların altında görüntülenmesini sağlar.

## Sunumu PDF Olarak Kaydetme

Seçenekleriniz yapılandırıldıktan sonra sunumu PDF olarak kaydedin. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```csharp
presentation.Save(dataDir + "Pdf_Notes_out.pdf", SaveFormat.Pdf, pdfOptions);
```

 Bu, şu adlı bir PDF dosyası oluşturacaktır:`Pdf_Notes_out.pdf` Belirtilen dizinde, slaytlar ve notlarını içeren.

## Çözüm

Ve işte bu kadar! Notes Slide View ile bir PowerPoint sunumunu Aspose.Slides for .NET kullanarak başarıyla PDF'ye dönüştürdünüz. Bu yaklaşım yalnızca zamandan tasarruf sağlamakla kalmaz, aynı zamanda uygulamalarınızda PowerPoint'ten PDF'e dönüştürmeyi ele almak için güvenilir ve ölçeklenebilir bir yol da sağlar.

## SSS

### S1: Aspose.Slides for .NET büyük sunumları yönetebilir mi?
Evet, Aspose.Slides for .NET her boyuttaki sunumu verimli bir şekilde işleyecek şekilde tasarlanmıştır.

### S2: Aspose.Slides for .NET'in ücretsiz deneme sürümünü nasıl edinebilirim?
 Ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Burada](https://releases.aspose.com/).

### S3: Başka PDF dışa aktarma seçenekleri mevcut mu?
Evet, yazı tiplerini, sayfa düzenini, sıkıştırmayı ve daha fazlasını kullanarak özelleştirebilirsiniz.`PdfOptions`sınıf.

### S4: Yalnızca belirli slaytları dışa aktarabilir miyim?
 Kesinlikle! Belirli slaytları kullanarak seçebilirsiniz.`Slides` koleksiyonda`Presentation`sınıf.

### S5: Ek örnekleri nerede bulabilirim?
 Ziyaret edin[Aspose.Slides .NET Belgeleri için](https://reference.aspose.com/slides/net/) Daha fazla örnek ve kullanım durumu için.