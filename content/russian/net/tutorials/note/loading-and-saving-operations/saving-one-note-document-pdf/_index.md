---
title: Сохранение документов OneNote в формате PDF с помощью Aspose.Note для .NET
linktitle: Сохранение документов OneNote в формате PDF
second_title: API Aspose.Note .NET
description: Узнайте, как эффективно сохранять документы Microsoft OneNote в виде файлов PDF с помощью Aspose.Note для .NET. Это руководство проведет вас через необходимые предварительные условия и предложит полезные часто задаваемые вопросы.
type: docs
weight: 26
url: /ru/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Введение

В этом уроке мы рассмотрим, как сохранять документы в формате PDF с помощью Aspose.Note для .NET. Aspose.Note — это мощная библиотека, которая позволяет разработчикам работать с файлами Microsoft OneNote программным способом. Мы рассмотрим предварительные условия, импортируем пространства имен и предоставим пошаговые руководства по сохранению документов в формате PDF в различных макетах страниц.

## Предпосылки
1. Visual Studio: убедитесь, что он установлен.
2. Aspose.Note для .NET: загрузите и установите библиотеку.
3. Знание C#: требуется базовое понимание языка.

## Импорт необходимых пространств имен
Прежде чем продолжить, импортируйте в свой код следующие пространства имен:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Шаг 1: Сохраните в формате PDF с настройками страницы Letter
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Обновить этот путь
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Загружает документ OneNote и сохраняет его как PDF-файл с использованием параметров размера страницы Letter.

## Шаг 2: Сохраните в формате PDF с параметрами страницы A4 (без ограничений по высоте)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Обновить этот путь
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Аналогично шагу 1, но использует параметры страницы А4 без ограничений по высоте.

## Заключение
В руководстве успешно демонстрируется, как преобразовать файлы OneNote в формат PDF с помощью Aspose.Note. Используя различные параметры страницы, разработчики получают гибкость в управлении документами.

## Часто задаваемые вопросы
### Может ли Aspose.Note обрабатывать сложные файлы OneNote?
Да, он эффективно обрабатывает различные функции сложных файлов OneNote.

### Подходит ли Aspose.Note для коммерческих проектов?
Да, вы можете использовать его в коммерческих целях после приобретения лицензии.

### Предлагает ли Aspose.Note бесплатную пробную версию?
Да, для ознакомления доступна бесплатная пробная версия.

### Где я могу найти документацию по Aspose.Note?
Подробная документация доступна на справочном сайте Aspose.

### Нужна дополнительная помощь?
Если у вас есть вопросы или вам нужна поддержка, обратитесь на форум Aspose.Note.
