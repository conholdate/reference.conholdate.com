---
title: PDF Sayfa Yönünü Değiştir
linktitle: PDF Sayfa Yönünü Değiştir
second_title: Aspose.PDF for .NET API Referansı
description: Aspose.PDF for .NET kullanarak PDF dosyalarının sayfa yönünü kolayca nasıl ayarlayacağınızı keşfedin. Bu adım adım kılavuz, belgelerinizi yükleme, döndürme ve kaydetme konusunda net talimatlar sağlar.
type: docs
weight: 10
url: /tr/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## giriiş

Sayfa yönlendirmesi tamamen yanlış olan bir PDF dosyasıyla hiç karşılaştınız mı? Yanlış taranmış bir belge veya sadece farklı bir düzene ihtiyaç duyan bir belge olsun, yönlendirmeyi ayarlamak çok büyük fark yaratabilir. Neyse ki, .NET için Aspose.PDF, sayfaların yönlendirmesini değiştirmek de dahil olmak üzere PDF dosyalarını düzenlemek için güçlü ve kullanıcı dostu bir yol sunar. Bu kılavuzda, ister dikeyden yataya ister tam tersine geçmek isteyin, süreci adım adım anlatacağız.

## Ön koşullar

Ayrıntılara girmeden önce aşağıdakilerin mevcut olduğundan emin olun:

-  .NET için Aspose.PDF: Aspose.PDF kütüphanesinin yüklü olduğundan emin olun. Bunu henüz yapmadıysanız,[buradan indirin](https://releases.aspose.com/pdf/net/).
- .NET Geliştirme Ortamı: .NET geliştirmesi için Visual Studio, JetBrains Rider veya tercih ettiğiniz herhangi bir IDE'yi kullanabilirsiniz.
- Temel C# Bilgisi: C#'a aşina olmak, konuyu daha kolay takip etmenize yardımcı olacaktır.
- PDF Dosyası: Test için hazır bir örnek PDF dosyanız olsun. Bir tane oluşturabilir veya çevrimiçi bir örnek indirebilirsiniz.

 Eğer yeni başlıyorsanız, Aspose.PDF'yi bir denemeyi düşünün[ücretsiz geçici lisans](https://purchase.aspose.com/temporary-license/) karar vermeden önce[tam sürümü satın al](https://purchase.aspose.com/buy).

## Ad Alanlarını İçe Aktar

PDF sayfalarını düzenlemek için öncelikle C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Kod dosyanızın en üstüne aşağıdaki satırları ekleyin:

```csharp
using System.IO;
using Aspose.Pdf;
```

Artık her şeyi ayarladığımıza göre, başlayalım!

## Adım 1: PDF Belgesini Yükleyin

 İlk adım, değiştirmek istediğiniz PDF dosyasını yüklemektir.`Document` Aspose.PDF ad alanından sınıf:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Değiştirdiğinizden emin olun`"YOUR DOCUMENT DIRECTORY"` PDF dosyanızın gerçek yolunu belirtin.

## Adım 2: Her Sayfada Döngü Yapın

Sonra, PDF belgesindeki her sayfada döngü yapacağız. Bu, yön değişikliğini tüm sayfalara uygulamamızı sağlar:

```csharp
foreach (Page page in doc.Pages)
{
    // Her sayfayı düzenleyin
}
```

## Adım 3: Sayfanın MediaBox'ına erişin

 Her PDF sayfasının bir`MediaBox` sınırlarını tanımlayan. Mevcut yönelimi kontrol etmek ve ayarlamalar yapmak için buna erişmemiz gerekiyor:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 The`MediaBox` sayfanın genişlik ve yükseklik dahil boyutlarını sağlar.

## Adım 4: Genişlik ve Yüksekliği Değiştirin

Sayfa yönünü değiştirmek için genişlik ve yükseklik değerlerini değiştireceğiz. Bu ayarlama sayfanın boyutlarını değiştirecektir:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Burada, yeni boyutları hesaplıyoruz ve sol alt köşeyi yeniden konumlandırıyoruz (`LLY`) buna göre.

## Adım 5: MediaBox ve CropBox'ı güncelleyin

 Artık yeni boyutlara sahip olduğumuza göre, bu değişiklikleri şuraya uygulayacağız:`MediaBox` Ve`CropBox` sayfanın doğru görüntülenmesini sağlamak için:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Adım 6: Sayfayı Döndürün

Yönlendirme değişikliğini tamamlamak için sayfayı döndüreceğiz. Bu Aspose.PDF ile basittir:

```csharp
page.Rotate = Rotation.on90; // 90 derece döndür
```

Bu çizgi, sayfayı istenen yöne çevirir.

## Adım 7: Çıktı PDF'ini Kaydedin

Tüm sayfaların yönlendirmesini değiştirdikten sonra güncellenen belgeyi yeni bir dosyaya kaydedin:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Orijinal belgenin üzerine yazılmasını önlemek için yeni bir dosya adı sağladığınızdan emin olun.

## Çözüm

Ve işte karşınızda! Aspose.PDF for .NET kullanarak bir PDF dosyasının sayfa yönünü değiştirmek basit bir işlemdir. Belgeyi yükleyerek, sayfalar arasında dolaşarak, MediaBox'ı güncelleyerek ve dosyayı kaydederek düzeni ihtiyaçlarınıza göre kolayca ayarlayabilirsiniz. İster kötü taranmış bir belgeyi düzeltiyor olun, ister sayfaları sunum için biçimlendiriyor olun, bu kılavuz işi verimli bir şekilde yapmanıza yardımcı olacaktır.

## SSS

### PDF'deki tüm sayfalar yerine belirli sayfaları döndürebilir miyim?  
Evet, tüm sayfalarda yineleme yapmak yerine, döngüyü belirli sayfaları dizinlerine göre hedefleyecek şekilde değiştirebilirsiniz.

### Nedir?`MediaBox`?  
 The`MediaBox` PDF dosyasındaki sayfanın boyutunu ve şeklini tanımlayarak içeriğin nereye yerleştirileceğini belirler.

### Aspose.PDF for .NET diğer dosya formatlarıyla çalışır mı?  
Evet, Aspose.PDF HTML, XML, XPS ve daha fazlası dahil olmak üzere çeşitli dosya biçimlerini işleyebilir.

### Aspose.PDF'in .NET için ücretsiz bir sürümü var mı?  
 Evet, bir ile başlayabilirsiniz[ücretsiz deneme](https://releases.aspose.com/) veya bir talepte bulunun[geçici lisans](https://purchase.aspose.com/temporary-license/).

### Kaydettiğim değişiklikleri geri alabilir miyim?  
Belgeyi kaydettiğinizde değişiklikler kalıcı olur. Orijinal dosyanın bir kopyası üzerinde çalışmanız veya yedeğini tutmanız önerilir.