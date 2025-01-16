---
title: Конвертировать DGN в PDF в Aspose.CAD для .NET
linktitle: Конвертировать DGN в PDF в Aspose.CAD для .NET
second_title: Aspose.CAD .NET — формат файла CAD и BIM
description: Узнайте, как легко конвертировать файлы DGN в PDF с помощью мощной библиотеки Aspose.CAD для .NET. Это пошаговое руководство предназначено для разработчиков всех уровней.
type: docs
weight: 12
url: /ru/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Введение

Навигация в мире файлов САПР может быть сложной, но с Aspose.CAD для .NET разработчики могут легко манипулировать и конвертировать различные форматы САПР. Одной из распространенных потребностей является конвертация файлов DGN в PDF, которую мы рассмотрим шаг за шагом в этом руководстве.

## Предпосылки

Для продолжения убедитесь, что у вас есть следующее:

- Базовые знания C# и фреймворка .NET.
-  Установлена библиотека Aspose.CAD for .NET. Вы можете скачать ее[здесь](https://releases.aspose.com/cad/net/).
- Пример файла DGN (например, Nikon_D90_Camera.dgn). 

## Шаг 1: Импорт требуемых пространств имен

Начните с импорта соответствующих пространств имен в ваш проект C#:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Шаг 2: Загрузите файл DGN

Укажите каталог для вашего файла DGN и загрузите его, используя следующий код:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Дополнительная обработка будет проходить здесь...
}
```

## Шаг 3: Настройка параметров растеризации

Затем настройте параметры растеризации, чтобы определить, как ваш DGN будет отображаться в PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Отрегулируйте ширину по мере необходимости.
    PageHeight = 300, // Отрегулируйте высоту по мере необходимости.
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Шаг 4: Параметры создания PDF-файла

Определите параметры PDF, интегрировав ранее настроенные параметры растеризации:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Шаг 5: Сохраните DGN как PDF

Наконец, сохраните файл DGN как PDF, используя настроенные вами параметры:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Заключение

Поздравляем! Вы успешно преобразовали файл DGN в PDF с помощью Aspose.CAD for .NET. Этот простой урок помог вам загрузить файл DGN, настроить параметры растеризации и сохранить вывод в формате PDF.

## Часто задаваемые вопросы

### Нужны ли мне предварительные знания САПР для использования Aspose.CAD?  
Безусловно! Aspose.CAD разработан для упрощения сложных задач САПР, делая его доступным для всех разработчиков, независимо от их знаний в области САПР.

### Где я могу найти больше ресурсов и документации по Aspose.CAD?  
 Вы можете изучить подробные руководства и примеры в[Документация Aspose.CAD](https://reference.aspose.com/cad/net/).

### Существует ли бесплатная пробная версия Aspose.CAD?  
 Да, можно получить бесплатную пробную версию.[здесь](https://releases.aspose.com/).

### Как получить временную лицензию на Aspose.CAD?  
 Вы можете запросить временные лицензии[здесь](https://purchase.conholdate.com/temporary-license/).

### Нужна помощь или есть вопросы?  
 Присоединяйтесь к обсуждению в[Форум Aspose.CAD](https://forum.aspose.com/c/cad/19) для поддержки сообщества и запросов.