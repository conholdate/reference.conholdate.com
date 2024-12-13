---
title: XLS ve XLSX Formatlarında Maksimum Satır ve Sütunları Bul
linktitle: XLS ve XLSX Formatlarında Maksimum Satır ve Sütunları Bul
second_title: Aspose.Cells .NET Excel İşleme API'si
description: Aspose.Cells for .NET kitaplığını kullanarak Excel'de büyük veri kümelerini nasıl verimli bir şekilde yöneteceğinizi keşfedin. Bu kılavuz, hem XLS hem de XLSX dosya biçimleri tarafından desteklenen maksimum satır ve sütun sayısını belirlemek için adım adım bir yaklaşım sağlar.
type: docs
weight: 11
url: /tr/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## giriiş

Excel'de büyük veri kümelerini yönetmek, özellikle çeşitli dosya biçimlerinin sınırları göz önüne alındığında, zorlayıcı olabilir. Bu eğitim, XLS (Excel 97-2003) ve XLSX (Excel 2007 ve sonrası) biçimleri tarafından desteklenen maksimum satır ve sütun sayısını belirlemek için Aspose.Cells for .NET kitaplığını kullanmanızda size rehberlik edecektir. Sonunda, Excel ile ilgili görevleri verimli bir şekilde halletmek için donanımlı olacaksınız.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. [.NET Çerçevesi](https://dotnet.microsoft.com/en-us/download) veya[.NET Çekirdeği](https://dotnet.microsoft.com/en-us/download) sisteminize yüklenmiştir.
2. [.NET için Aspose.Cells](https://releases.aspose.com/cells/net/) Projenizde indirilen ve referans verilen kütüphaneyi (bunu ayrıca şu şekilde de kurabilirsiniz)[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## Gerekli Paketleri İçe Aktarma

Aspose.Cells kütüphanesinden gerekli paketleri içe aktarmak için C# dosyanızın en üstüne aşağıdaki using ifadelerini ekleyin:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Adım 1: XLS Biçimi için Maksimum Satır ve Sütun Sayısı

XLS formatının desteklediği maksimum satır ve sütun sayısını bularak başlayalım.

```csharp
// XLS formatı hakkında mesaj yazdır.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// XLS formatında bir çalışma kitabı oluşturun.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Maksimum satır ve sütun sayısını al.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Sonuçları göster.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. XLS formatıyla çalıştığımızı belirtmek için bir mesaj yazdırın.
2.  Bir tane oluştur`Workbook` XLS formatı için örnek kullanımı`FileFormatType.Excel97To2003`.
3.  Maksimum satır ve sütun sayısını alın`wb.Settings.MaxRow` Ve`wb.Settings.MaxColumn`, bunlar sıfır tabanlı olduğundan 1 ekliyoruz.
4. Konsola maksimum satır ve sütun sayısını çıktı olarak gönder.

## Adım 2: XLSX Biçimi için Maksimum Satır ve Sütun Sayısı

Şimdi XLSX formatının desteklediği maksimum satır ve sütun sayısını inceleyeceğiz.

```csharp
// XLSX formatı hakkında mesaj yazdır.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// XLSX formatında bir çalışma kitabı oluşturun.
wb = new Workbook(FileFormatType.Xlsx);

// Maksimum satır ve sütun sayısını al.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Sonuçları göster.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. XLSX formatıyla çalıştığımızı belirten bir mesaj yazdırın.
2.  Bir tane oluştur`Workbook` XLSX formatı için örnek kullanımı`FileFormatType.Xlsx`.
3. Daha önce olduğu gibi maksimum satır ve sütun sayısını alıp çıktı olarak verin.

## Adım 3: Başarılı Mesajını Görüntüleme

Adımları uyguladıktan sonra başarıyı belirtelim.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Çözüm

Bu eğitimde, XLS ve XLSX dosya biçimleri tarafından desteklenen maksimum satır ve sütunları bulmak için Aspose.Cells for .NET kitaplığını nasıl kullanacağınızı öğrendiniz. Bu sınırları anlamak, veri kümelerinizin biçim yetenekleriyle uyumlu olmasını sağlayarak etkili Excel veri yönetimi için önemlidir.

## SSS

### XLS formatı tarafından desteklenen maksimum satır sayısı nedir?
XLS formatının desteklediği maksimum satır sayısı 65.536'dır.

### XLS formatı tarafından desteklenen maksimum sütun sayısı nedir?
XLS biçiminin desteklediği maksimum sütun sayısı 256'dır.

### XLSX formatı tarafından desteklenen maksimum satır sayısı nedir?
XLSX formatının desteklediği maksimum satır sayısı 1.048.576'dır.

### XLSX formatı tarafından desteklenen maksimum sütun sayısı nedir?
XLSX formatının desteklediği maksimum sütun sayısı 16.384'tür.

### Aspose.Cells for .NET kütüphanesini diğer Excel dosya formatlarıyla birlikte kullanabilir miyim?
 Evet, Aspose.Cells for .NET, XLS, XLSX, ODS ve daha fazlası dahil olmak üzere çeşitli dosya biçimlerini destekler.[belgeleme](https://reference.aspose.com/cells/net/) Desteklenen özellikler ve işlevler hakkında ayrıntılı bilgi için.