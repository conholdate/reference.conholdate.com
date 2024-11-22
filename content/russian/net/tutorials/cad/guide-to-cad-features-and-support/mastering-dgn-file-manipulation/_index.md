---
title: Освоение манипуляций с файлами DGN с помощью Aspose.CAD в .NET
linktitle: Освоение манипуляций с файлами DGN
second_title: Aspose.CAD .NET — формат файла CAD и BIM
description: Узнайте, как загружать файлы DGN, перебирать их элементы, управлять 2D- и 3D-объектами и экспортировать их в виде растровых изображений — и все это с использованием мощных функций библиотеки Aspose.CAD.
type: docs
weight: 18
url: /ru/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Введение

Вы разработчик .NET, стремящийся интегрировать файлы DGN в свои приложения? Aspose.CAD для .NET предлагает мощную библиотеку, разработанную специально для работы с форматами файлов DGN. В этом уроке мы рассмотрим, как эффективно обрабатывать файлы DGN, включая поддерживаемые элементы, и как манипулировать ими в ваших проектах .NET.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующие настройки:

- Базовые знания программирования .NET: знакомство с C# или VB.NET будет преимуществом.
- Visual Studio: устанавливается на вашем компьютере для разработки проектов.
-  Библиотека Aspose.CAD для .NET: Загрузите ее с[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Шаг 1: Импорт необходимых пространств имен

Чтобы использовать функциональные возможности Aspose.CAD, начните с импорта необходимых пространств имен в свой проект.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Шаг 2: Загрузите ваш файл DGN

 Начните с загрузки существующего файла DGN в ваше приложение. Это делается путем создания экземпляра`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Продолжайте свою логику здесь
}
```

## Шаг 3: Перебор элементов DGN

После загрузки файла DGN вы можете перебирать его элементы. Aspose.CAD предоставляет множество типов элементов DGN для ваших манипуляций.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Обработать каждый элемент
}
```

## Шаг 4: Обработка 2D и 3D объектов

Вы можете различать элементы DGN 2D и 3D. Ниже показано, как эффективно с ними работать:

### Обработка 2D-объектов

Вы можете управлять ранее поддерживаемыми 2D-сущностями с помощью блока switch-case.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Добавьте сюда свою логику обработки
        break;
}
```

### Обработка 3D-объектов

Аналогично обрабатывайте 3D-объекты следующим образом:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Добавьте сюда свою логику обработки
        break;
}
```

## Шаг 5: Экспортируйте файл DGN

После манипуляций с элементами DGN вы можете захотеть экспортировать файл как растровое изображение. Это можно легко сделать с помощью Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Определите свой выходной путь
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Заключение

В этом уроке мы узнали, как использовать Aspose.CAD для .NET для эффективного управления файлами DGN. Следуя изложенным шагам, вы сможете без усилий обрабатывать как 2D, так и 3D элементы DGN и экспортировать их как растровые изображения. Эта мощная библиотека обеспечивает бесшовную интеграцию обработки DGN в ваши приложения .NET, расширяя возможности вашего проекта.

## Часто задаваемые вопросы

### Где я могу найти документацию по Aspose.CAD для .NET?

 Подробная документация доступна[здесь](https://reference.aspose.com/cad/net/).

### Как загрузить Aspose.CAD для .NET?

 Вы можете скачать последнюю версию библиотеки[здесь](https://releases.aspose.com/cad/net/).

### Существует ли бесплатная пробная версия Aspose.CAD для .NET?

 Да, доступна бесплатная пробная версия.[здесь](https://releases.aspose.com/).

### Как получить временные лицензии на Aspose.CAD для .NET?

 Вы можете запросить временные лицензии[здесь](https://purchase.conholdate.com/temporary-license/).

### Нужна помощь или есть вопросы?

 Чтобы получить поддержку или задать вопросы, посетите сообщество Aspose.CAD[форум поддержки](https://forum.aspose.com/c/cad/19).