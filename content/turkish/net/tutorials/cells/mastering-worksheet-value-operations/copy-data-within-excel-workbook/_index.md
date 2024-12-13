---
title: Aspose.Cells for .NET kullanarak Excel Çalışma Kitabı İçindeki Verileri Kopyalama
linktitle: Aspose.Cells for .NET kullanarak Excel Çalışma Kitabı İçindeki Verileri Kopyalama
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells for .NET kullanarak bir Excel çalışma kitabındaki verileri nasıl etkili bir şekilde kopyalayacağınızı öğrenin. Sayfaları kolayca çoğaltmak, verileri aktarmak ve Excel dosyalarını kolayca yönetmek için bu adım adım kılavuzu izleyin.
type: docs
weight: 12
url: /tr/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## giriiş

Bu ayrıntılı kılavuzda, .NET için Aspose.Cells kullanarak aynı çalışma kitabı içinde verilerin nasıl kopyalanacağını göstereceğiz. Aşağıda özetlenen adım adım talimatları izleyerek, sayfaları programatik olarak nasıl çoğaltacağınızı, içeriklerini ve biçimlendirmelerini nasıl koruyacağınızı öğreneceksiniz.

## Aspose.Cells ile Excel'de Veri Kopyalamanın Ön Koşulları

Kodlama sürecine başlamadan önce her şeyin yerli yerinde olduğundan emin olalım:

1. Aspose.Cells for .NET Kütüphanesi: Aspose.Cells for .NET kütüphanesinin yüklü olması gerekir. En son sürümü şu adresten indirebilirsiniz:[Aspose.Cells for .NET indirme sayfası](https://releases.aspose.com/cells/net/).
2. Geliştirme Ortamı: Kodunuzu yazmak ve çalıştırmak için Visual Studio gibi .NET uyumlu bir IDE'ye ihtiyacınız vardır.
3.  Aspose Lisansı: Ücretsiz deneme veya satın alınmış lisans kullanabilirsiniz. Daha fazla bilgi için şu adresi ziyaret edin:[Burada](https://purchase.aspose.com/temporary-license/).

Ön koşullar sağlandıktan sonra kütüphaneyle çalışmaya başlamaya hazırsınız.

## Gerekli Paketleri İçe Aktarma

Başlamak için, ilgili ad alanlarını Aspose.Cells'den içe aktarmanız gerekir. Bu, Aspose.Cells tarafından sağlanan sınıfları ve yöntemleri kullanarak Excel dosyalarıyla çalışmanıza olanak tanır.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Bu ad alanları size şuraya erişim sağlayacaktır:`Workbook` sınıf (Excel dosyalarıyla çalışmak için) ve`WorksheetCollection` (bir çalışma kitabındaki birden fazla sayfaya erişim için).

## Adım 1: Çalışma Kitabı için Dosya Yollarını Başlatın

Kodunuzu düzenli tutmak için, çalışma kitabınızın bulunduğu ve değiştirilmiş dosyayı kaydetmeyi planladığınız dosya yollarını tanımlamanız önemlidir. Yolları şu şekilde belirtebilirsiniz:

```csharp
// Excel dosyasının bulunduğu dizin yolunu tanımlayın.
string dataDir = "Your Directory Path";

// Giriş çalışma kitabına giden tam yolu tanımlayın.
string inputPath = dataDir + "book1.xls";
```

 Yer değiştirmek`"Your Directory Path"` çalışma kitabını içeren dizininize giden gerçek yol ile. Bu, kodun esnek olmasını ve yolları etkili bir şekilde yönetebilmenizi sağlar.

## Adım 2: Verilere Erişmek İçin Çalışma Kitabını Açın

 Artık dosya yolları ayarlandığına göre, bir sonraki adım Excel çalışma kitabını bir bilgisayara yüklemektir.`Workbook` nesne. Bu, içeriğine erişip düzenleme yapmanıza olanak tanır.

```csharp
// Excel dosyasını Çalışma Kitabı nesnesine yükleyin.
Workbook wb = new Workbook(inputPath);
```

 Bu satırla başarıyla yüklediniz`book1.xls` içine`wb` nesne, verilerini erişilebilir hale getirir.

## Adım 3: Çalışma Sayfaları Koleksiyonuna Erişim

 Çalışma kitabı yüklendikten sonra, içinde bulunan sayfalara erişebilirsiniz. Aspose.Cells şunları sağlar:`Worksheets`Çalışma kitabındaki her çalışma sayfasıyla etkileşime girmenizi sağlayan koleksiyon.

```csharp
// Çalışma kitabından çalışma sayfaları koleksiyonunu alın.
WorksheetCollection sheets = wb.Worksheets;
```

 The`sheets` nesne artık size içindeki tüm çalışma sayfalarına erişim sağlıyor`book1.xls`ve bunlar üzerinde çeşitli işlemler gerçekleştirebilirsiniz; örneğin bir sayfadan diğerine veri kopyalamak gibi.

## Adım 4: Verileri Bir Sayfadan Başka Bir Sayfaya Kopyalayın

 Aynı çalışma kitabındaki bir çalışma sayfasından diğerine veri kopyalamak için Aspose.Cells, kullanımı kolay bir yöntem sunar`AddCopy`Bu yöntem belirtilen çalışma sayfasının bir kopyasını oluşturur ve çalışma kitabına ekler.

```csharp
// Çalışma kitabındaki "Sayfa1"deki verileri yeni bir sayfaya kopyalayın.
sheets.AddCopy("Sheet1");
```

 Bu örnekte, "Sheet1"den yeni bir sayfaya veri kopyalıyoruz.`AddCopy` Bu yöntem, formüller, biçimlendirme ve değerler dahil olmak üzere tüm içeriğini koruyarak sayfanın tamamını kopyalayacaktır.

## Adım 5: Değiştirilen Çalışma Kitabını Kaydedin

 Verileri kopyaladıktan sonra, değiştirilen çalışma kitabını yeni bir ad veya konumla kaydedebilirsiniz. Bu, şu şekilde yapılır:`Save`yöntem üzerinde`Workbook` nesne.

```csharp
//Değiştirilen çalışma kitabını yeni bir adla kaydedin.
wb.Save(dataDir + "book1_copy.xls");
```

 Bu, kopyalanan sayfayla birlikte çalışma kitabını kaydedecektir`book1_copy.xls` belirtilen dizinde. Dosya adını ve yolunu ihtiyaçlarınıza göre değiştirebilirsiniz.

## Çözüm

Aspose.Cells for .NET kullanarak bir Excel çalışma kitabındaki verileri kopyalamak kolay bir iştir ve bu kılavuz bunu verimli bir şekilde yapmak için gereken adımları sağlar. İster tüm sayfaları ister belirli veri aralıklarını kopyalayın, Aspose.Cells Excel otomasyonunu basit ve etkili hale getiren sağlam ve esnek bir API sunar.

## SSS

### Birden fazla sayfayı aynı anda kopyalayabilir miyim?

Aspose.Cells tek bir çağrıda birden fazla sayfayı kopyalamayı desteklemez. Ancak, kopyalamak istediğiniz sayfalar arasında dolaşabilir ve bunları tek tek kopyalayabilirsiniz.

### Kopyalanan sayfanın adını nasıl değiştirebilirim?

Sayfayı kopyaladıktan sonra aşağıdaki gibi adını değiştirebilirsiniz:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells .NET Core ile uyumlu mu?

Evet, Aspose.Cells hem .NET Framework hem de .NET Core ortamlarıyla tamamen uyumludur.

### Aspose.Cells kopyalama sırasında biçimlendirmeyi nasıl işler?

 The`AddCopy`Bu yöntem, sayfaları kopyalarken tüm içeriği ve biçimlendirmeyi koruyarak kopyalanan verilerin orijinaliyle aynı görünmesini sağlar.

### Bir sayfayı farklı bir çalışma kitabına kopyalayabilir miyim?

 Evet, bir sayfayı farklı bir çalışma kitabına kopyalamak için şunu kullanabilirsiniz:`Copy` Hedef çalışma kitabına referansı olan yöntem.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```