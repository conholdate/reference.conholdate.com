---
title: Расширенная настройка диаграмм с помощью Aspose.Slides для .NET
linktitle: Расширенная настройка диаграмм с помощью Aspose.Slides для .NET
second_title: API обработки PowerPoint Aspose.Slides .NET
description: Раскройте весь потенциал Aspose.Slides для .NET, освоив передовые методы настройки диаграмм. Это пошаговое руководство охватывает все от создания базовых диаграмм до сложных деталей, таких как линии сетки, названия осей и пользовательские цвета.
type: docs
weight: 10
url: /ru/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Введение

Создание визуально привлекательных и информативных диаграмм имеет решающее значение для эффективного представления данных. Aspose.Slides for .NET предлагает мощные инструменты для настройки диаграмм, позволяя вам настраивать каждый аспект ваших диаграмм. В этом уроке мы рассмотрим передовые методы настройки диаграмм с использованием Aspose.Slides for .NET.

## Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

1.  Библиотека Aspose.Slides для .NET: Загрузите и установите библиотеку Aspose.Slides с сайта[здесь](https://releases.aspose.com/slides/net/).
2. Среда разработки .NET: настройте среду разработки .NET, например Visual Studio.
3. Базовые знания C#: знакомство с программированием на C# будет преимуществом, поскольку мы будем писать код на C#.

Теперь давайте разберем расширенный процесс настройки диаграммы на понятные шаги.

## Шаг 1: Создайте новую презентацию

Начните с создания новой презентации для вашей диаграммы.

```csharp
// Путь к каталогу документов.
string dataDir = "Your Document Directory";

// Создайте каталог, если он не существует.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Создайте презентацию
Presentation pres = new Presentation();
```

## Шаг 2: Получите доступ к первому слайду

Далее перейдите к первому слайду, на который вы хотите добавить диаграмму.

```csharp
// Доступ к первому слайду
ISlide slide = pres.Slides[0];
```

## Шаг 3: Добавьте образец диаграммы

Теперь добавим на слайд линейную диаграмму с маркерами.

```csharp
// Добавить образец диаграммы
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Шаг 4: Задайте заголовок диаграммы

Заголовок диаграммы обеспечивает необходимый контекст.

```csharp
// Установите заголовок диаграммы
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Шаг 5: Настройте основные линии сетки

Вы можете улучшить линии сетки оси значений для лучшей читаемости.

```csharp
// Настройте основные линии сетки для оси значений
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Шаг 6: Настройте второстепенные линии сетки

Аналогичным образом настройте второстепенные линии сетки для оси значений.

```csharp
// Настройте второстепенные линии сетки для оси значений
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Шаг 7: Определите числовой формат оси значений

Вы можете форматировать числа, отображаемые на оси значений.

```csharp
// Установить формат числа оси значений
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Шаг 8: Установите максимальные и минимальные значения

Определите максимальные и минимальные значения для диаграммы.

```csharp
// Установить максимальные и минимальные значения диаграммы
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Шаг 9: Настройте свойства текста оси значений

Улучшение свойств текста оси значений улучшает читабельность.

```csharp
// Настроить свойства текста оси значений
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Шаг 10: Добавьте заголовок оси ценности

Добавление заголовка к оси значений может прояснить, что представляют собой данные.

```csharp
// Установить заголовок оси значений
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Шаг 11: Настройте основные линии сетки для оси категорий

Теперь давайте улучшим основные линии сетки для оси категорий.

```csharp
// Настройте основные линии сетки для оси категорий
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Шаг 12: Настройте второстепенные линии сетки для оси категорий

Аналогичным образом настройте второстепенные линии сетки для оси категорий.

```csharp
// Настройте второстепенные линии сетки для оси категорий
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Шаг 13: Настройте свойства текста оси категорий

Улучшить стиль шрифта и внешний вид меток осей категорий.

```csharp
// Настроить свойства текста оси категорий
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Шаг 14: Добавьте заголовок оси категорий

При необходимости вы также можете добавить заголовок для оси категорий.

```csharp
// Установить заголовок оси категорий
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Шаг 15: Дополнительные настройки

Улучшите свою диаграмму с помощью дополнительных настроек, таких как легенды, цвета стен и параметры области построения.

```csharp
// Дополнительные настройки (необязательно)

// Настроить свойства текста легенд
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Показывать легенды диаграммы без перекрытия диаграммы
chart.Legend.Overlay = true;

// Настройка цвета задней стенки диаграммы
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Установить цвет пола диаграммы
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Установить цвет области графика
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Сохранить презентацию
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Заключение

В этом всеобъемлющем руководстве мы рассмотрели расширенные методы настройки диаграмм с использованием Aspose.Slides для .NET. Вы узнали, как создать презентацию, добавить диаграмму, улучшить ее внешний вид и настроить различные элементы диаграммы, такие как линии сетки, метки осей и легенды. 

## Часто задаваемые вопросы

### Какие версии .NET поддерживаются Aspose.Slides для .NET?
Aspose.Slides для .NET поддерживает различные версии .NET, включая .NET Framework и .NET Core. Полный список поддерживаемых версий см. в документации.

### Могу ли я создавать диаграммы из таких источников данных, как файлы Excel?
Да, Aspose.Slides позволяет создавать диаграммы из внешних источников данных, таких как таблицы Excel. Подробные примеры см. в документации.

### Как добавить пользовательские метки данных в серию диаграмм?
 Чтобы добавить пользовательские метки данных, перейдите к`DataLabels` свойство серии и подгоните метки по мере необходимости. Вы можете найти примеры кода в документации.

### Можно ли экспортировать диаграмму в другие форматы, например PDF или изображения?
Конечно! Aspose.Slides позволяет экспортировать презентации с диаграммами в различные форматы, включая PDF и форматы изображений.

### Где я могу найти больше руководств и примеров по Aspose.Slides для .NET?
 Посетите Aspose.Slides[веб-сайт](https://reference.aspose.com/slides/net/) для получения подробных учебных пособий, примеров кода и документации.