---
title: Çalışma Sayfasında Sayfa Sırası ayarlarını uygulayın
linktitle: Çalışma Sayfasında Sayfa Sırası ayarlarını uygulayın
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells for .NET kullanarak Excel'de sayfa sırası ayarlarının nasıl yapılandırılacağını öğrenin. Bu adım adım kılavuz, önce satırlar boyunca ve sonra sütunlar boyunca nasıl yazdırılacağını gösterir ve büyük elektronik tablolarınızın kağıt üzerinde düzgün görünmesini sağlar.
type: docs
weight: 24
url: /tr/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-page-order-settings/
---
## giriiş

Büyük Excel elektronik tablolarıyla çalışırken, yazdırma düzenini kontrol etmek netlik ve organizasyon açısından çok önemlidir. Aspose.Cells for .NET, çalışma sayfalarınızın yazdırma ayarlarını zahmetsizce özelleştirmenize olanak tanıyan sağlam özellikler sunar. Bu kılavuzda, önce satırlar boyunca ve sonra sütunlar boyunca yazdırmak için sayfa sırasını ayarlama adımlarını ele alacağız.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. .NET için Aspose.Cells: Şuradan indirin:[Aspose web sitesi](https://releases.aspose.com/cells/net/) ve projenize kurun.
2. Geliştirme Ortamı: Visual Studio gibi herhangi bir .NET uyumlu IDE kullanın.
3. Temel C# Bilgisi: C#'a aşina olmak kod parçacıklarını anlamanıza yardımcı olacaktır.

 Ayrıca şunu da deneyebilirsiniz[.NET için Aspose.Cells ücretsiz deneme sürümüyle](https://releases.aspose.com/) veya bir tane al[geçici lisans](https://purchase.aspose.com/temporary-license/) Tüm özelliklere erişim için.

## Gerekli Paketleri İçe Aktar

Aspose.Cells işlevlerine erişmek için gerekli ad alanlarını içe aktararak başlayın:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

## Adım 1: Bir Çalışma Kitabı Oluşturun

Öncelikle Excel dosyanızı temsil eden yeni bir çalışma kitabı örneği oluşturun.

```csharp
// Yeni bir Çalışma Kitabı nesnesi oluşturun
Workbook workbook = new Workbook();
```

Bu satır özelleştirmeye hazır, boş bir Excel çalışma kitabı başlatır.

## Adım 2: Çalışma Sayfasının Sayfa Düzenine Erişim

 Yazdırma ayarlarını düzenlemek için şuraya erişin:`PageSetup` çalışma sayfasının nesnesi.

```csharp
// İlk çalışma sayfasının Sayfa Kurulumuna erişin
PageSetup pageSetup = workbook.Worksheets[0].PageSetup;
```

 Burada, şunu alıyoruz:`PageSetup` İlk çalışma kağıdımız için, yazdırma düzenini yapılandıracağız.

## Adım 3: Sayfa Sırasını OverThenDown Olarak Ayarlayın

Şimdi sayfa sırasını ayarlayalım. Varsayılan olarak, Excel önce her sütunu aşağı doğru yazdırır; bunu önce satırlar boyunca yazdıracak şekilde değiştireceğiz.

```csharp
// Yazdırma sırasını OverThenDown olarak ayarlayın
pageSetup.Order = PrintOrderType.OverThenDown;
```

Bu ayar, yazdırma sırasında verilerin bir sonraki satıra geçmeden önce yatay olarak akmasını sağlar; bu özellikle geniş veri kümeleri için oldukça kullanışlıdır.

## Adım 4: Çalışma Kitabını Kaydedin

Son olarak değişiklikleri uygulamak için çalışma kitabınızı kaydedin.

```csharp
// Çalışma kitabını kaydetmek için yolu tanımlayın
string dataDir = "Your Document Directory/";
// Çalışma kitabını kaydet
workbook.Save(dataDir + "SetPageOrder_out.xls");
```

 Yer değiştirmek`"Your Document Directory"`istediğiniz dosya yolu ile. Ayrıca, bunu diğer biçimlerde de kaydedebilirsiniz, örneğin`.xlsx`, dosya uzantısını değiştirerek.

## Çözüm

Tebrikler! Aspose.Cells for .NET kullanarak bir Excel çalışma sayfasında sayfa sırasını başarıyla ayarladınız. Bu basit ayarlama, yazdırıldığında büyük veri kümelerinin sunumunu önemli ölçüde iyileştirebilir. Aspose.Cells, birçok başka özelleştirilebilir yazdırma ayarı sunarak onu rapor hazırlama ve belge düzenleme için paha biçilmez bir araç haline getirir.

## SSS

### Birden fazla çalışma sayfasının sayfa sırasını aynı anda değiştirebilir miyim?

 Evet, çalışma kitabındaki her çalışma sayfasını dolaşabilir ve aynısını uygulayabilirsiniz`PageSetup.Order` ayar.

### Baskı siparişi için başka hangi seçenekler mevcut?

 Ayrıca`OverThenDown` , kullanabilirsiniz`DownThenOver`, önce sütunları aşağıya doğru yazdırır, sonra satırlar arasında hareket eder.

### Bu kod lisans gerektiriyor mu?

 Lisans olmadan bazı özellikler sınırlı olabilir. Deneyebilirsiniz[.NET için Aspose.Cells ücretsiz deneme sürümüyle](https://releases.aspose.com/).

### Yazdırmadan önce sayfa sırasını önizleyebilir miyim?

Aspose.Cells yazdırma yapılandırmalarını ayarlamanıza izin verse de, düzeni önizlemek için kaydedilen dosyayı Excel'de açmanız gerekir.

### Bu sayfa sırası ayarı PDF çıktılarıyla uyumlu mu?

Evet, sayfa sırası ayarları PDF dışa aktarımlarına ve desteklenen diğer formatlara uygulanarak tutarlı sayfa akışı sağlanır.