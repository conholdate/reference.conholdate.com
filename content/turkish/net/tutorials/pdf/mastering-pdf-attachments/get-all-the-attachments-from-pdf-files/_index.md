---
title: PDF Dosyalarından Tüm Ekleri Alın
linktitle: PDF Dosyalarından Tüm Ekleri Alın
second_title: Aspose.PDF for .NET API Referansı
description: Bu adım adım kılavuzda, Aspose.PDF for .NET'i kullanarak PDF dosyalarından gömülü ekleri nasıl kolayca çıkaracağınızı keşfedin.
type: docs
weight: 40
url: /tr/net/tutorials/pdf/mastering-pdf-attachments/get-all-the-attachments-from-pdf-files/
---
## giriiş

Dijital dünyamızda, PDF dosyaları belgeleri paylaşmak için olmazsa olmazdır; çok yönlüdürler, güvenlidirler ve gömülü ekler de dahil olmak üzere çeşitli bilgi türleri içerebilirler. Hiç bir PDF'den gizli hazineleri çıkarmanız gerekti mi? Doğru yerdesiniz! Bu eğitimde, bir PDF dosyasından tüm ekleri çıkarmak için Aspose.PDF for .NET'i nasıl kullanacağınızı keşfedeceğiz. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, bu kılavuz sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

Koda dalmadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Visual Studio: Bilgisayarınızda yüklü olduğundan emin olun.
2.  .NET için Aspose.PDF: Kütüphaneyi şu adresten indirin ve kurun:[Burada](https://releases.aspose.com/pdf/net/).
3. Temel C# Bilgisi: C# programlamaya aşina olmak, kod parçacıklarını daha kolay anlamanıza yardımcı olacaktır.

## Ortamınızı Kurma

Başlamak için C# projenizi kurmak üzere şu adımları izleyin:

### Yeni Bir Proje Oluştur

Visual Studio'yu açın ve yeni bir Konsol Uygulaması projesi oluşturun.

### Aspose.PDF Referansını Ekle

- Çözüm Gezgini’nde projenizin üzerine sağ tıklayın.
- “NuGet Paketlerini Yönet” seçeneğini seçin.
- “Aspose.PDF” dosyasını arayın ve en son sürümü yükleyin.

## Gerekli Ad Alanlarını İçe Aktar

Program dosyanızın en üstüne gerekli ad alanlarını içe aktarın:

```csharp
using System.IO;
using Aspose.Pdf;
using System;
```

Artık her şey ayarlandığına göre, PDF'den ekleri çıkarma işlemine geçebiliriz.

## Adım 1: Belge Dizininizi Belirleyin

PDF dosyanızın depolandığı dizini tanımlayın. Bu, programa PDF'nizi nerede bulacağını söyler.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Değiştirdiğinizden emin olun`YOUR DOCUMENT DIRECTORY` gerçek yol ile.

## Adım 2: PDF Belgesini açın

PDF belgenizi açmak için Aspose.PDF kitaplığını kullanın:

```csharp
Document pdfDocument = new Document(dataDir + "GetAlltheAttachments.pdf");
```

Dosya yolunun ve adının doğru olduğundan emin olun.

## Adım 3: Gömülü Dosyalar Koleksiyonuna Erişim

PDF'deki eklere erişmek için gömülü dosyalar koleksiyonunu alın:

```csharp
EmbeddedFileCollection embeddedFiles = pdfDocument.EmbeddedFiles;
```

## Adım 4: Gömülü Dosyaları Say

Kaç adet ek bulunduğunu bilmek faydalıdır:

```csharp
Console.WriteLine("Total files : {0}", embeddedFiles.Count);
```

## Adım 5: Ekler Arasında Döngü Oluşturun

Bir döngü kullanarak her bir ekin ayrıntılarını çıkarın:

```csharp
int count = 1;

foreach (FileSpecification fileSpecification in embeddedFiles)
{
    Console.WriteLine("Name: {0}", fileSpecification.Name);
    Console.WriteLine("Description: {0}", fileSpecification.Description);
    Console.WriteLine("Mime Type: {0}", fileSpecification.MIMEType);
```

## Adım 6: Ek Dosya Parametrelerini Çıkarın

Ek parametrelere sahip ekler için şu bilgileri kontrol edip yazdırabilirsiniz:

```csharp
if (fileSpecification.Params != null)
{
    Console.WriteLine("CheckSum: {0}", fileSpecification.Params.CheckSum);
    Console.WriteLine("Creation Date: {0}", fileSpecification.Params.CreationDate);
    Console.WriteLine("Modification Date: {0}", fileSpecification.Params.ModDate);
    Console.WriteLine("Size: {0}", fileSpecification.Params.Size);
}
```

## Adım 7: Ekleri Çıkarın ve Kaydedin

Son olarak, çıkartılan her eki bir dosyaya kaydedelim:

```csharp
byte[] fileContent = new byte[fileSpecification.Contents.Length];
fileSpecification.Contents.Read(fileContent, 0, fileContent.Length);

using (FileStream fileStream = new FileStream(dataDir + count + "_out" + ".txt", FileMode.Create))
{
    fileStream.Write(fileContent, 0, fileContent.Length);
}
count += 1;
```

Bu kod, her bir ekin içeriğini bir bayt dizisine okur ve bunları sırayla adlandırarak yeni bir metin dosyasına kaydeder (örneğin,`1_out.txt`, `2_out.txt`, vesaire.).

## Çözüm

Tebrikler! Aspose.PDF for .NET kullanarak bir PDF dosyasından tüm ekleri çıkardınız. Bu güçlü kütüphane PDF belge düzenlemeyi basitleştirir ve gömülü dosyalara erişimi kolaylaştırır; hem kişisel projeler hem de profesyonel çabalar için paha biçilmez bir beceridir.

## SSS

### Aspose.PDF for .NET nedir?
Aspose.PDF for .NET, geliştiricilerin PDF belgelerini programlı bir şekilde oluşturması, düzenlemesi ve dönüştürmesi için tasarlanmış bir kütüphanedir.

### Aspose.PDF'in ücretsiz deneme sürümü var mı?
 Evet, Aspose özelliklerini keşfetmek için kullanabileceğiniz ücretsiz bir deneme sürümü sağlar. Erişim[Burada](https://releases.aspose.com/).

### Aspose.PDF için nasıl destek alabilirim?
 Destek, bulabileceğiniz Aspose forumu aracılığıyla sağlanmaktadır.[Burada](https://forum.aspose.com/c/pdf/10).

### Geçici ehliyet alabilir miyim?
 Evet, Aspose.PDF için geçici bir lisans talep edebilirsiniz[Burada](https://purchase.aspose.com/temporary-license/).

### Aspose.PDF'in dokümanlarını nerede bulabilirim?
 .NET için Aspose.PDF için kapsamlı dokümanları bulabilirsiniz[Burada](https://reference.aspose.com/pdf/net/).