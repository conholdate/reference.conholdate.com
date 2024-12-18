---
title: Защита строк на рабочем листе с помощью Aspose.Cells
linktitle: Защита строк на рабочем листе с помощью Aspose.Cells
second_title: API обработки Excel Aspose.Cells .NET
description: Узнайте, как защитить конфиденциальную информацию в ваших рабочих листах Excel, защищая определенные строки с помощью Aspose.Cells для .NET. Это всеобъемлющее руководство охватывает все, от настройки вашей среды.
type: docs
weight: 18
url: /ru/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Введение

Работа с файлами Excel программным способом часто требует не только манипулирования данными, но и защиты данных. Защита определенных строк на листе может иметь решающее значение для защиты конфиденциальной информации или предотвращения случайных правок. В этом руководстве мы рассмотрим, как защитить строки на листе Excel с помощью Aspose.Cells для .NET. Мы проведем вас через необходимые шаги, от настройки среды до реализации функций защиты строк простым способом.

## Предпосылки
Прежде чем начать, убедитесь, что у вас есть следующее:

1.  Aspose.Cells для .NET: Загрузите и установите его с сайта[Страница загрузки Aspose Cells](https://releases.aspose.com/cells/net/).
2. Visual Studio или любая .NET IDE: Вам нужна среда разработки. Рекомендуется Visual Studio, но подойдет любая совместимая с .NET IDE.
3. Базовые знания C#: знакомство с программированием на C# поможет вам следить за ходом разработки и при необходимости изменять код примера.
4.  Документация API Aspose.Cells: ознакомьтесь с[Документация Aspose.Cells для .NET](https://reference.aspose.com/cells/net/) для обзора структуры и методов класса.

Как только все необходимые условия будут готовы, мы сможем приступить к реализации.

## Импорт необходимых пакетов
Начните с импорта необходимых пакетов в ваш проект C#. Эти библиотеки необходимы для взаимодействия с файлами Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## Шаг 1: Создайте новую рабочую книгу и рабочий лист
Прежде чем применять какие-либо настройки защиты, создайте новую рабочую книгу и выберите лист, с которым вы хотите работать.

```csharp
// Определите путь к каталогу документов.
string dataDir = "Your Document Directory";
// Создайте каталог, если он не существует.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Создайте новую рабочую книгу и выберите первый рабочий лист.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Шаг 2: Определение объектов Style и StyleFlag
Определите объекты стиля и флага стиля, которые позволят вам изменять свойства ячеек, например, блокировать или разблокировать их.

```csharp
// Определите стиль и объекты флага стиля.
Style style;
StyleFlag flag;
```

## Шаг 3: Разблокируйте все столбцы на рабочем листе.
По умолчанию все ячейки на листе Excel заблокированы. Чтобы защитить только определенные строки, сначала разблокируйте все столбцы.

```csharp
// Пройдитесь по всем столбцам и разблокируйте их.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Шаг 4: Заблокируйте определенные строки
Теперь заблокируйте строки, которые вы хотите защитить. В этом примере мы заблокируем первую строку.

```csharp
// Заблокируйте первый ряд.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Вы можете повторить этот шаг для любых дополнительных строк, которые вы хотите заблокировать.

## Шаг 5: Защитите лист
Когда необходимые строки заблокированы, пора защитить рабочий лист. Это предотвратит изменения заблокированных строк, если только защита не будет снята.

```csharp
// Защитите лист.
sheet.Protect(ProtectionType.All);
```

## Шаг 6: Сохраните рабочую книгу
Наконец, сохраните книгу с примененными изменениями. Вы можете выбрать из различных форматов, таких как Excel 97-2003 или более новых версий.

```csharp
// Сохраните файл Excel.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Заключение
Поздравляем! Вы успешно научились защищать строки в листе Excel с помощью Aspose.Cells for .NET. Выполнив эти шаги, вы сможете разблокировать или заблокировать строки или столбцы по мере необходимости и применять защиту для сохранения целостности ваших данных.

## Часто задаваемые вопросы
### Как защитить несколько строк одновременно?
Вы можете перебрать несколько индексов строк и применить стиль блокировки к каждому из них по отдельности.

### Могу ли я установить пароль для защиты листа?
 Да, вы можете передать пароль`sheet.Protect()` метод обеспечения защиты паролем.

### Можно ли разблокировать определенные ячейки, а не целые столбцы?
Да, вы можете разблокировать отдельные ячейки, изменив свойства их стиля, а не разблокировать целые столбцы.

### Что произойдет, если я попытаюсь отредактировать защищенную строку?
Если строка защищена, Excel не позволит вносить изменения в заблокированные ячейки, если только лист не будет защищен.

### Могу ли я защитить определенные диапазоны внутри строки?
 Да! Вы можете заблокировать отдельные диапазоны в строке, установив`IsLocked` свойство для определенных ячеек в этом диапазоне.