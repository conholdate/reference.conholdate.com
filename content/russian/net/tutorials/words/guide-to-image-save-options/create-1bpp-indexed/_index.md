---
title: Создать 1Bpp индексированный
linktitle: Создать 1Bpp индексированный
second_title: API обработки документов Aspose.Words
description: В этом руководстве приведены пошаговые инструкции и примеры кода, которые помогут вам эффективно создавать индексированные изображения с разрешением 1 байт на пиксель для архивирования, печати или экономии места.
type: docs
weight: 10
url: /ru/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Введение

Вам когда-нибудь требовалось преобразовать документ Word в черно-белое изображение? Будь то для цифрового архивирования, печати или просто экономии места, преобразование ваших документов в индексированное изображение 1Bpp может быть невероятно полезным. В этом руководстве мы рассмотрим простой метод достижения этого с помощью Aspose.Words для .NET. Давайте начнем!

## Предпосылки

Прежде чем приступить к изучению кода, убедитесь, что у вас есть следующее:

-  Aspose.Words для .NET: Загрузите и установите библиотеку с[здесь](https://releases.aspose.com/words/net/).
- Среда разработки .NET: Хотя Visual Studio является популярным выбором, подойдет любая IDE, поддерживающая .NET.
- Базовые знания C#: знакомство с C# будет полезно, но мы постараемся упростить ситуацию.
- Образец документа Word: подготовьте документ к конвертации.

## Шаг 1: Импорт необходимых пространств имен

Для использования Aspose.Words вам необходимо импортировать соответствующие пространства имен. Это необходимо для доступа к классам и методам, необходимым для манипуляции документами.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Шаг 2: Настройте каталог документов

Укажите путь к каталогу, в котором хранится ваш документ Word и куда вы хотите сохранить преобразованное изображение.

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Шаг 3: Загрузите документ Word

Загрузите ваш документ Word в`Aspose.Words.Document` объект. Этот объект позволяет программно манипулировать документом.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Шаг 4: Настройте параметры сохранения изображения

 Далее настройте`ImageSaveOptions` чтобы определить, как документ будет сохранен как изображение. Мы настроим его для сохранения в формате PNG с индексированным цветовым режимом 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Конвертировать только первую страницу
    ImageColorMode = ImageColorMode.BlackAndWhite, // Установить черно-белый режим
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Использовать индексированный формат 1Bpp
};
```

- SaveFormat.Png: указывает, что выходным форматом будет PNG.
- PageSet(1): указывает, что будет преобразована только первая страница документа.
- ImageColorMode.BlackAndWhite: обеспечивает черно-белое изображение.
- ImagePixelFormat.Format1bppIndexed: устанавливает индексированный формат пикселей 1Bpp, оптимизируя пространство.

## Шаг 5: Сохраните документ как изображение

 Наконец, используйте`Save` Метод`Document` объект для сохранения преобразованного изображения.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Заключение

Поздравляем! Вы успешно преобразовали документ Word в индексированное изображение 1Bpp с помощью Aspose.Words for .NET. Этот метод не только эффективен, но и помогает создавать высококонтрастные изображения, подходящие для различных приложений. Не стесняйтесь интегрировать эту функциональность в свои проекты. Удачного кодирования!

## Часто задаваемые вопросы

### Что такое индексированное изображение 1Bpp?
Индексированное изображение 1Bpp (1 бит на пиксель) — это формат черно-белого изображения, в котором каждый пиксель представлен одним битом, 0 или 1. Этот формат очень экономичен, что делает его идеальным для архивирования.

### Можно ли конвертировать несколько страниц документа Word одновременно?
 Да! Просто измените`PageSet` недвижимость в`ImageSaveOptions` включить несколько страниц или настроить его на преобразование всего документа.

### Нужна ли мне лицензия для использования Aspose.Words для .NET?
 Да, для полной функциональности требуется лицензия. Вы можете получить[временная лицензия здесь](https://purchase.aspose.com/temporary-license/).

### В какие еще форматы изображений я могу конвертировать свой документ Word?
 Aspose.Words поддерживает различные форматы, включая JPEG, BMP и TIFF. Просто измените`SaveFormat`в`ImageSaveOptions` в желаемый вами формат.

### Где я могу найти дополнительную документацию по Aspose.Words для .NET?
 Для получения полной документации посетите[Страница документации Aspose.Words для .NET](https://reference.aspose.com/words/net/).