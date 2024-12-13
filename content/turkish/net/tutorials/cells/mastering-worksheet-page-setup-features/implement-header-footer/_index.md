---
title: .NET için Aspose.Cells ile Başlık ve Altbilgiyi Uygulayın
linktitle: .NET için Aspose.Cells ile Başlık ve Altbilgiyi Uygulayın
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells for .NET kullanarak başlıkları ve alt bilgileri programlı olarak özelleştirerek Excel belgelerinizi nasıl yükselteceğinizi keşfedin. Bu kapsamlı kılavuz, çalışma kitabınızı kurmaktan çalışma sayfası adını dinamik olarak eklemeye kadar her adımda size yol gösterir.
type: docs
weight: 22
url: /tr/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## giriiş

Başlıklar ve altbilgiler, Excel elektronik tablolarında dosya adları, tarihler ve sayfa numaraları gibi kritik bağlamsal bilgiler sağlayan temel öğelerdir. İster raporları otomatikleştirin ister dinamik dosyalar oluşturun, Aspose.Cells for .NET, başlıkları ve altbilgileri programatik olarak özelleştirme sürecini basitleştirir. Bu kılavuz, Excel dosyalarınızı cilalı ve profesyonel başlıklar ve altbilgilerle geliştirmek için adım adım bir yaklaşım sunar.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Cells for .NET: Buradan indirin ve kurun[Burada](https://releases.aspose.com/cells/net/).
2. IDE Kurulumu: Visual Studio'yu veya .NET framework'ü kullanarak tercih ettiğiniz IDE'yi kullanın.
3.  Lisans: Ücretsiz denemeyle başlayın, ancak tüm işlevler için tam veya geçici bir lisans edinmeyi düşünün.[geçici lisans almak](https://purchase.aspose.com/temporary-license/).

## Gerekli Paketleri İçe Aktarma

Öncelikle projenize gerekli ad alanlarını içe aktarın:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Bu, Aspose.Cells'de başlıklar, altbilgiler ve diğer Excel işlevleriyle çalışmak için gereken sınıflara ve yöntemlere erişmenizi sağlayacaktır.

## Adım 1: Bir Çalışma Kitabı Oluşturun ve Sayfa Kurulumuna Erişin

Yeni bir çalışma kitabı oluşturarak ve çalışma sayfasının sayfa düzenine erişerek başlayın. Burada başlık ve altbilgi ayarlarını değiştireceksiniz.

```csharp
// Belgenizi kaydetmek için yolu tanımlayın
string dataDir = "Your Document Directory";

// Bir Çalışma Kitabı nesnesi örneği oluşturun
Workbook excel = new Workbook();
```

 Burada, bir`Workbook` nesne Excel dosyanızı temsil eder.`PageSetup` Çalışma sayfasının özelliği, üstbilgileri ve altbilgileri özelleştirmenize olanak tanır.

## Adım 2: Çalışma Sayfası ve Sayfa Düzeni Özelliklerine Erişim

 Aspose.Cells'deki her çalışma sayfasının bir`PageSetup` Başlıklar ve altbilgiler dahil olmak üzere düzen özelliklerini yöneten özellik. Edinin`PageSetup` çalışma sayfanız için nesne:

```csharp
// İlk çalışma sayfasının PageSetup referansını edinin
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Şimdi,`pageSetup` Başlık ve altbilgileri özelleştirmek için gerekli ayarları içerir.

## Adım 3: Başlığın Sol Bölümünü Ayarlayın

Başlıklar üç bölümden oluşur: sol, orta ve sağ. Çalışma sayfası adını görüntülemek için sol bölümü ayarlayarak başlayalım.

```csharp
// Çalışma sayfası adını başlığın sol bölümüne ayarlayın
pageSetup.SetHeader(0, "&A");
```

 Kullanarak`&A`Özellikle çok sayfalı çalışma kitapları için kullanışlı olan çalışma sayfası adını dinamik olarak görüntüler.

## Adım 4: Başlığın Merkezine Tarih ve Saat Ekleyin

Daha sonra başlığın orta kısmına geçerli tarih ve saati ekleyin ve stil için özel bir yazı tipi uygulayın.

```csharp
// Başlığın orta kısmına kalın yazı tipiyle tarih ve saat ayarlayın
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

Bu satırda:
- `&D` geçerli tarihi ekler.
- `&T` geçerli saati ekler.
- `"Times New Roman,Bold"` Kalın Times New Roman yazı tipi kullanılmıştır.

## Adım 5: Dosya Adını Başlığın Sağ Bölümünde Görüntüle

Başlığı tamamlamak için dosya adını sağ tarafa belirtilen yazı tipi boyutuyla görüntüleyin.

```csharp
// Dosya adını başlığın sağ bölümünde özel yazı tipi boyutuyla görüntüle
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Burada,`&F` dosya adını temsil eder ve`&12` yazı tipi boyutunu 12'ye ayarlar.

## Adım 6: Sol Altbilgi Bölümüne Özel Metin Ekleyin

Şimdi sol altbilgi bölümünü özel metin ve belirli bir yazı tipi stiliyle ayarlayalım.

```csharp
// Altbilginin sol bölümüne yazı tipi stiliyle özel metin ekleyin
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

Bu örnekte metin`123` "Courier New" yazı tipiyle 14 puntoda tasarlanmıştır, geri kalanı ise varsayılan alt bilgi yazı tipinde kalır.

## Adım 7: Sayfa Numarasını Altbilginin Ortasına Ekleyin

Sayfa numaralarının alt bilgiye eklenmesi, okuyucuların çok sayfalı belgeleri takip etmelerine yardımcı olur.

```csharp
// Sayfa numarasını altbilginin orta bölümüne ekleyin
pageSetup.SetFooter(1, "&P");
```

 The`&P` kod, geçerli sayfa numarasını altbilginin orta bölümüne ekler.

## Adım 8: Sağ Alt Bilgi Bölümünde Toplam Sayfa Sayısını Göster

Toplam sayfa sayısını sağ bölümde görüntüleyerek alt bilgiyi tamamlayın.

```csharp
// Toplam sayfa sayısını altbilginin sağ bölümünde görüntüle
pageSetup.SetFooter(2, "&N");
```

 The`&N` Kod, okuyuculara belgenin uzunluğunu bildiren toplam sayfa sayısını sağlar.

## Adım 9: Çalışma Kitabını Kaydedin

Son olarak, çalışma kitabını kaydederek özelleştirilmiş üstbilgi ve altbilgilere sahip bir Excel dosyası oluşturun.

```csharp
// Çalışma Kitabını Kaydet
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Bu satır, dosyayı özelleştirmelerinizin yer aldığı şekilde kaydeder.

## Çözüm

Excel çalışma sayfalarındaki başlıkları ve alt bilgileri özelleştirmek belgelerinizin profesyonelliğini artırır. .NET için Aspose.Cells ile çalışma sayfası adlarını görüntülemekten özel metin, tarih, saat ve dinamik sayfa numaraları eklemeye kadar bu öğeleri kolayca kontrol edebilirsiniz. Artık adımları öğrendiğinize göre Excel otomasyon projelerinizi bir üst seviyeye taşıyabilirsiniz.

## SSS

### Başlık ve altbilgilerin farklı bölümleri için farklı yazı tipleri kullanabilir miyim?
Evet, Aspose.Cells, başlık ve altbilginin her bölümü için benzersiz yazı tipleri belirtmenize olanak tanır.

### Üstbilgi ve altbilgileri nasıl kaldırabilirim?
 Başlıkları ve altbilgileri, metinlerini boş bir dizeye ayarlayarak temizleyin`SetHeader` veya`SetFooter`.

### Aspose.Cells for .NET ile başlıklara veya altbilgilere resim ekleyebilir miyim?
Şu anda Aspose.Cells öncelikli olarak başlık ve altbilgilerdeki metni destekler. Görüntüler, doğrudan çalışma sayfasına eklemek gibi alternatif yöntemler gerektirebilir.

### Aspose.Cells başlık ve altbilgilerde dinamik verileri destekliyor mu?  
 Evet, çeşitli dinamik kodlar kullanabilirsiniz (örneğin`&D`tarih veya`&P` (sayfa numarası için) dinamik içerik eklemek için.

### Üstbilgi veya altbilgi yüksekliğini nasıl ayarlayabilirim?  
 Aspose.Cells, içinde seçenekler sunar`PageSetup` Başlık ve altbilgi kenar boşluklarını ayarlayarak aralıklar üzerinde kontrol sahibi olmanızı sağlayan sınıf.