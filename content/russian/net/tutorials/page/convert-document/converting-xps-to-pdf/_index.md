---
title: Преобразование XPS в PDF с помощью Aspose.Page для .NET
linktitle: Преобразование XPS в PDF
second_title: API Aspose.Page .NET
description: Узнайте, как легко преобразовать документы XPS (XML Paper Specification) в PDF (Portable Document Format) с помощью мощной библиотеки Aspose.Page для .NET.
type: docs
weight: 11
url: /ru/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Введение

В этом уроке мы рассмотрим, как преобразовать документы XPS (XML Paper Specification) в PDF (Portable Document Format) с помощью универсальной библиотеки Aspose.Page для .NET. Эта мощная библиотека упрощает преобразование документов и предлагает различные варианты настройки, что делает ее отличным выбором для разработчиков.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующее:

-  Библиотека Aspose.Page для .NET: Загрузите и установите библиотеку Aspose.Page для .NET с сайта[Документация Aspose.Page](https://reference.aspose.com/page/net/).
  
- Среда разработки: настройте среду разработки .NET с помощью Visual Studio или другой совместимой IDE.

- Документ XPS: Подготовьте файл XPS, который вы хотите преобразовать, и сохраните его в указанном каталоге.

## Шаг 1: Импорт требуемых пространств имен

Начните с импорта необходимого пространства имен для доступа к функциям Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Шаг 2: Инициализация каталога документов

Определите путь к каталогу, в котором хранятся ваши документы:

```csharp
string dataDir = "Your Document Directory";
```

 Обязательно замените`"Your Document Directory"` с фактическим путем к каталогу, содержащему ваш XPS-документ.

### Шаг 3: Откройте потоки PDF и XPS

Далее инициализируем потоки для входного XPS-файла и выходного PDF-файла:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Убедитесь, что вы указали правильный путь для своих файлов.

### Шаг 4: Загрузите XPS-документ

Теперь загрузите ваш XPS-документ с помощью библиотеки Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Шаг 5: Настройте параметры сохранения PDF-файла

Настройте параметры сохранения вашего PDF-файла, включая качество изображения и параметры сжатия:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Установите уровень качества JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Используйте сжатие JPEG для изображений
    TextCompression = PdfTextCompression.Flate, // Применить сжатие Flate для текста
    PageNumbers = new int[] { 1, 2, 6 } // Укажите номера страниц, которые нужно включить
};
```

Вы можете свободно изменять эти параметры в соответствии с вашими требованиями.

### Шаг 6: Создайте устройство для рендеринга PDF-файлов

Создайте устройство рендеринга для формата PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Шаг 7: Сохраните документ как PDF.

Наконец, сохраните документ XPS в формате PDF, используя указанное устройство и параметры:

```csharp
document.Save(device, options);
```

## Заключение

Поздравляем! Вы успешно преобразовали документ XPS в PDF с помощью Aspose.Page for .NET. Эта библиотека не только упрощает преобразование документов, но и предлагает обширные возможности для обработки различных форматов.

## Часто задаваемые вопросы

### Можно ли конвертировать несколько файлов XPS в один PDF?

Конечно! Вы можете перебрать несколько файлов XPS и объединить их в один документ PDF, выполнив те же шаги конвертации.

### Какие еще форматы вывода поддерживает Aspose.Page for .NET?

Помимо PDF, Aspose.Page для .NET поддерживает ряд форматов, включая TIFF, JPEG и PNG.

### Как настроить внешний вид преобразованного PDF-файла?

 Вы можете настроить параметры в`PdfSaveOptions` объекта, например, качество JPEG и настройки сжатия, чтобы добиться желаемого вида.

### Существует ли пробная версия Aspose.Page для .NET?

 Да, вы можете попробовать Aspose.Page для .NET с помощью бесплатной пробной версии.[здесь](https://releases.aspose.com/).

### Где я могу найти поддержку сообщества для Aspose.Page for .NET?

Для обсуждения в сообществе и поддержки посетите[Форум Aspose.Page](https://forum.aspose.com/c/page/39).