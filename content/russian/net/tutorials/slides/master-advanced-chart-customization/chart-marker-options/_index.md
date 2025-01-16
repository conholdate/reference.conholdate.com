---
title: Параметры маркера диаграммы в точке данных в Aspose.Slides .NET
linktitle: Параметры маркера диаграммы в точке данных в Aspose.Slides .NET
second_title: API обработки PowerPoint Aspose.Slides .NET
description: Узнайте, как улучшить ваши диаграммы PowerPoint с помощью настраиваемых параметров маркеров с помощью Aspose.Slides для .NET. Это пошаговое руководство охватывает предварительные условия, создание диаграмм, форматирование точек данных и многое другое.
type: docs
weight: 11
url: /ru/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Введение

Включение визуальных средств в презентации имеет важное значение для эффективной коммуникации. Aspose.Slides для .NET предоставляет надежные инструменты для создания и настройки диаграмм, позволяя разработчикам улучшить свои презентации данных. Одной из выдающихся функций является возможность использования параметров маркеров диаграмм на точках данных, что позволяет выполнять точную настройку для получения профессионально выглядящих диаграмм. Эта статья проведет вас через каждый шаг, необходимый для достижения этого.

## Предпосылки

Прежде чем продолжить, убедитесь в следующем:

-  Aspose.Slides для .NET установлен: Загрузите его с[здесь](https://releases.aspose.com/slides/net/).
- Базовая настройка: файл презентации, например «Test.pptx», в вашем рабочем каталоге.
- Среда разработки: Visual Studio или эквивалент, настроенный для .NET.

## Импорт требуемых пространств имен

Добавьте необходимые пространства имен в свой проект для бесперебойной разработки:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Шаг 1: Создайте диаграмму в презентации

Начните с создания диаграммы по умолчанию на первом слайде вашей презентации:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Это добавляет`LineWithMarkers` диаграмму на слайде с указанными размерами.

## Шаг 2: Извлечение индекса рабочего листа данных диаграммы

Индекс рабочего листа данных диаграммы по умолчанию необходим для дальнейшей настройки:

```csharp
int defaultWorksheetIndex = 0;
```

## Шаг 3: Доступ к рабочей книге данных диаграммы

Для управления данными диаграммы извлеките связанную с ней рабочую книгу:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Шаг 4: Настройте ряд диаграмм и добавьте точки данных

Очистите ряд по умолчанию и добавьте новые точки данных для своего ряда:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Добавить точки данных в ряд
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Шаг 5: Примените заливку изображений к маркерам точек данных

Пользовательские изображения могут сделать маркеры данных визуально привлекательными:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Установить пользовательские изображения для маркеров
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Шаг 6: Настройте размер маркера

Измените размер маркеров для улучшения видимости:

```csharp
series.Marker.Size = 20;
```

## Шаг 7: Сохраните обновленную презентацию.

Сохраните настроенную презентацию в желаемом месте:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Заключение

Aspose.Slides for .NET предоставляет разработчикам инструменты для создания профессиональных диаграмм с богатыми возможностями настройки. Используя возможности маркеров диаграмм, вы можете значительно улучшить визуальную привлекательность и ясность своих презентаций. Это пошаговое руководство гарантирует, что даже сложные настройки будут простыми в реализации.

## Часто задаваемые вопросы

### Могу ли я использовать любой формат изображения для настройки маркера?
Да, Aspose.Slides поддерживает различные форматы изображений, включая JPEG, PNG и BMP, для настройки маркеров.

### Как изменить тип диаграммы после создания?
 Чтобы изменить тип диаграммы, перейдите к`chart.Type` свойство и назначить другое`ChartType`.

### Совместим ли Aspose.Slides для .NET со старыми версиями PowerPoint?
Да, он поддерживает обратную совместимость со старыми форматами PowerPoint, что обеспечивает универсальность.

### Могу ли я динамически обновлять данные диаграммы?
 Конечно. Используйте`IChartDataWorkbook` для программного обновления данных диаграммы.

### Где я могу найти больше ресурсов?
 Исследуйте[Документация Aspose.Slides](https://reference.aspose.com/slides/net/)или присоединяйтесь к[форумы сообщества](https://forum.aspose.com/) за поддержку.