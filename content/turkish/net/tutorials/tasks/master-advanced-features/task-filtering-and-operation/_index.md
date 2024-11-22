---
title: Aspose.Tasks'ta Görev Filtreleme VE İşlemi
linktitle: Aspose.Tasks'ta Görev Filtreleme VE İşlemi
second_title: Aspose.Tasks .NET API
description: Proje görevlerini birden fazla koşula göre filtrelemek için Aspose.Tasks for .NET'teki sınıfı nasıl kullanacağınızı öğrenin. Özet görevler ve boş olmayan öznitelikler gibi ölçütleri birleştirerek.
type: docs
weight: 10
url: /tr/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## giriiş

Bu eğitimde, Aspose.Tasks for .NET'te proje görevlerinin gelişmiş filtrelemesinin nasıl gerçekleştirileceğini inceleyeceğiz.`Util.And` sınıf. Bu güçlü özellik, geliştiricilerin görevleri birden fazla kritere göre verimli bir şekilde filtrelemesine olanak tanır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. C# programlamanın temel bilgisi.
2.  Aspose.Tasks for .NET yüklü. Bunu henüz yapmadıysanız, şuradan indirebilirsiniz:[bu bağlantı](https://releases.aspose.com/tasks/net/).
3. Kod yazmak ve çalıştırmak için Visual Studio benzeri bir entegre geliştirme ortamı (IDE).

## Ad Alanlarını İçe Aktarma

Başlamak için, gerekli ad alanlarını C# projenize aktarmanız gerekir. Bu, Aspose.Tasks tarafından sağlanan işlevlere erişmenizi sağlayacaktır.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Adım 1: Projeyi Başlatın ve Görevleri Toplayın

 Öncelikle bir Aspose.Tasks projesi başlatın ve içindeki tüm görevleri toplayın. Gösterim amaçlı olarak, adında bir proje dosyası olduğunu varsayacağız`Project2.mpp`.

```csharp
// Belgeler dizinine giden yol
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Tüm alt görevleri topla
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Adım 2: Filtre Koşullarını Tanımlayın

Bu adımda, görevleri filtrelemek için koşulları tanımlayacağız. Örneğimizde, iki koşul oluşturacağız: biri özet görevleri filtrelemek için, diğeri ise görevlerin boş olmadığından emin olmak için.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Adım 3: Koşulları AND İşlemiyle Birleştirin

 Bir sonraki adım, bu koşulları birleştirmektir`Util.And` sınıf. Bu, her iki kriteri de zorunlu kılan bir bileşik koşul oluşturmamızı sağlar.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Adım 4: Birleşik Koşul ve Filtre Görevlerini Uygulayın

Şimdi, her iki koşulu da karşılayan belirli görevleri filtrelemek için, birleştirilmiş koşulu toplanan görevlere uygulayalım.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Adım 5: Filtrelenmiş Görevleri Çıktı Olarak Alın

Son olarak, filtrelenmiş görevlerimiz arasında yineleme yapacağız ve ilgili ayrıntıları çıktı olarak vereceğiz. Bu, kriterlerimizi karşılayan görevleri anlamamıza yardımcı olacaktır.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Çözüm

 Bu eğitimde, .NET için Aspose.Tasks'te gelişmiş filtreleme işlemlerinin nasıl gerçekleştirileceğini gösterdik.`Util.And`sınıf. Birden fazla koşulu birleştirerek görevleri etkili bir şekilde filtreleyebilir, böylece proje yönetimi uygulamalarımızın faydasını artırabiliriz.

## SSS

### Aspose.Tasks for .NET nedir?

Aspose.Tasks for .NET, geliştiricilerin .NET uygulamaları içerisinde Microsoft Project dosyalarını programlı bir şekilde düzenleyebilmeleri için tasarlanmış kapsamlı bir API'dir.

### Util.And kullanarak ikiden fazla koşulu birleştirebilir miyim?

 Evet!`Util.And` sınıfı, ihtiyaçlarınıza göre uyarlanmış karmaşık filtreleme mantığına olanak vererek birden fazla koşulu birleştirmenize olanak tanır.

### Aspose.Tasks için ücretsiz deneme sürümü mevcut mu?

 Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz:[bu bağlantı](https://releases.aspose.com/).

### Aspose.Tasks için detaylı dokümantasyonu nerede bulabilirim?

 Ayrıntılı dokümantasyon mevcuttur[Burada](https://reference.aspose.com/tasks/net/).

### Aspose.Tasks için nasıl destek alabilirim?

 Destek, erişilebilen Aspose.Tasks topluluk forumu aracılığıyla sağlanmaktadır.[Burada](https://forum.aspose.com/c/tasks/15).