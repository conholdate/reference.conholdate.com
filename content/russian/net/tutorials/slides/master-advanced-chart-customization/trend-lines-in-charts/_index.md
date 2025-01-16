---
title: Линии тренда на диаграммах с Aspose.Slides для .NET
linktitle: Линии тренда на диаграммах с Aspose.Slides для .NET
second_title: API обработки PowerPoint Aspose.Slides .NET
description: Узнайте, как добавлять и настраивать линии тренда в диаграммах с помощью Aspose.Slides для .NET. Это всеобъемлющее руководство охватывает экспоненциальные, линейные, логарифмические, полиномиальные и скользящие средние линии тренда для улучшения визуализации данных.
type: docs
weight: 12
url: /ru/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Введение  

Добавление линий тренда к диаграммам — ключевой метод анализа тенденций данных и прогнозирования будущих значений. С помощью Aspose.Slides для .NET вы можете легко добавлять и настраивать линии тренда к диаграммам презентации, улучшая визуализацию данных. Это руководство содержит подробное пошаговое руководство по добавлению линий тренда к различным типам диаграмм в презентации PowerPoint с помощью Aspose.Slides для .NET.  

## Предпосылки  

Прежде чем приступить к реализации, убедитесь, что у вас есть следующие настройки:  

1.  Aspose.Slides для .NET: Загрузите и установите библиотеку с сайта[страница загрузки](https://releases.aspose.com/slides/net/).  
2. Среда разработки: для написания кода используйте IDE, например Visual Studio.  
3. Базовые знания C#: для прохождения этого руководства необходимы знания программирования на C#.  

## Импорт требуемых пространств имен  

Для начала импортируйте необходимые пространства имен в свой проект:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Шаг 1: Настройка презентации  

Сначала инициализируйте пустую презентацию. Она будет служить контейнером для вашей диаграммы.  

```csharp
string dataDir = "Your/Documents/Directory";

// Убедитесь, что каталог существует.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Создать новую презентацию
Presentation presentation = new Presentation();
```

## Шаг 2: Добавление диаграммы на слайд  

Теперь добавьте слайд и включите кластеризованную столбчатую диаграмму для визуализации ваших данных.  

```csharp
// Добавить пустой слайд
ISlide slide = presentation.Slides[0];

// Добавить кластеризованную столбчатую диаграмму
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Шаг 3: Заполнение диаграммы данными  

Заполните диаграмму образцами данных.  

```csharp
// Доступ к рабочей книге данных диаграммы по умолчанию
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Обновите категории и значения серий по умолчанию
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Шаг 4: Добавление линий тренда  

### Экспоненциальная линия тренда  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Линейная линия тренда  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Логарифмическая линия тренда  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Скользящая средняя линия тренда  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Полиномиальная линия тренда  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Линия тренда мощности  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Шаг 5: Сохранение презентации  

Наконец, сохраните презентацию со всеми линиями тренда, добавленными на диаграмму.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Заключение  

Используя Aspose.Slides для .NET, добавление линий тренда в ваши диаграммы становится простой задачей. Эта функция позволяет вам эффективно представлять тенденции данных и добавлять профессиональные штрихи в ваши презентации. Выполните указанные выше шаги, чтобы включить различные типы линий тренда и улучшить визуализацию данных.  

## Часто задаваемые вопросы  

### Могу ли я настроить внешний вид линий тренда?  
 Да, вы можете настроить цвет, толщину и стиль линий тренда с помощью`Format.Line` свойство.  

### Есть ли поддержка других типов диаграмм?  
Да, Aspose.Slides для .NET поддерживает различные типы диаграмм, включая столбчатые, круговые и линейные диаграммы.  

### Как отобразить уравнения и значения R-квадрата?  
 Давать возможность`DisplayEquation` и`DisplayRSquaredValue` свойства линии тренда для отображения этих значений на графике.  

### Могу ли я использовать Aspose.Slides для .NET с другими языками?  
Да, библиотека совместима с любым языком, поддерживаемым .NET, включая VB.NET и F#.  

### Где я могу найти дополнительную документацию?  
 Посетите[Документация Aspose.Slides для .NET](https://reference.aspose.com/slides/net/) для получения более подробной информации.