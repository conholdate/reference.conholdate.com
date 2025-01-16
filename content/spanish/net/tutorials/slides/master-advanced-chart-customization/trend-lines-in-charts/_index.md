---
title: Líneas de tendencia en gráficos con Aspose.Slides para .NET
linktitle: Líneas de tendencia en gráficos con Aspose.Slides para .NET
second_title: API de procesamiento de PowerPoint Aspose.Slides .NET
description: Aprenda a agregar y personalizar líneas de tendencia en gráficos con Aspose.Slides para .NET. Esta guía completa cubre líneas de tendencia exponenciales, lineales, logarítmicas, polinómicas y de promedio móvil para mejorar la visualización de datos.
type: docs
weight: 12
url: /es/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Introducción  

Agregar líneas de tendencia a los gráficos es una técnica clave para analizar tendencias de datos y pronosticar valores futuros. Con Aspose.Slides para .NET, puede agregar y personalizar sin problemas líneas de tendencia a los gráficos de sus presentaciones, lo que mejora la visualización de los datos. Esta guía proporciona un tutorial detallado para agregar líneas de tendencia a varios tipos de gráficos en una presentación de PowerPoint con Aspose.Slides para .NET.  

## Prerrequisitos  

Antes de sumergirnos en la implementación, asegúrese de tener la siguiente configuración:  

1.  Aspose.Slides para .NET: Descargue e instale la biblioteca desde[página de descarga](https://releases.aspose.com/slides/net/).  
2. Entorno de desarrollo: utilice un IDE como Visual Studio para codificar.  
3. Conocimientos básicos de C#: es necesario estar familiarizado con la programación en C# para seguir este tutorial.  

## Importación de los espacios de nombres necesarios  

Para comenzar, importe los espacios de nombres esenciales a su proyecto:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Paso 1: Configuración de la presentación  

En primer lugar, inicialice una presentación vacía. Esta servirá como contenedor para su gráfico.  

```csharp
string dataDir = "Your/Documents/Directory";

// Asegúrese de que el directorio exista
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Crear una nueva presentación
Presentation presentation = new Presentation();
```

## Paso 2: Agregar un gráfico a una diapositiva  

Ahora, agregue una diapositiva e incluya un gráfico de columnas agrupadas para visualizar sus datos.  

```csharp
// Agregar una diapositiva en blanco
ISlide slide = presentation.Slides[0];

// Agregar un gráfico de columnas agrupadas
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Paso 3: Rellenar los datos del gráfico  

Llene el gráfico con datos de muestra.  

```csharp
// Acceda al libro de trabajo de datos de gráficos predeterminado
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Actualizar las categorías y los valores de las series predeterminados
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Paso 4: Agregar líneas de tendencia  

### Línea de tendencia exponencial  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Línea de tendencia lineal  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Línea de tendencia logarítmica  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Línea de tendencia de media móvil  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Línea de tendencia polinómica  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Línea de tendencia de potencia  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Paso 5: Guardar la presentación  

Por último, guarde la presentación con todas las líneas de tendencia agregadas a su gráfico.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Conclusión  

Con Aspose.Slides para .NET, agregar líneas de tendencia a sus gráficos se convierte en una tarea sencilla. Esta función le permite presentar tendencias de datos de manera eficaz y agregar toques profesionales a sus presentaciones. Siga los pasos anteriores para incorporar varios tipos de líneas de tendencia y mejorar la visualización de sus datos.  

## Preguntas frecuentes  

### ¿Puedo personalizar la apariencia de las líneas de tendencia?  
 Sí, puedes personalizar el color, el grosor y el estilo de las líneas de tendencia usando el`Format.Line` propiedad.  

### ¿Hay soporte para otros tipos de gráficos?  
Sí, Aspose.Slides para .NET admite varios tipos de gráficos, incluidos gráficos de barras, circulares y de líneas.  

### ¿Cómo muestro ecuaciones y valores R-cuadrado?  
 Permitir`DisplayEquation` y`DisplayRSquaredValue` Propiedades de una línea de tendencia para mostrar estos valores en el gráfico.  

### ¿Puedo usar Aspose.Slides para .NET con otros lenguajes?  
Sí, la biblioteca es compatible con cualquier lenguaje compatible con .NET, incluidos VB.NET y F#.  

### ¿Dónde puedo encontrar más documentación?  
 Visita el[Documentación de Aspose.Slides para .NET](https://reference.aspose.com/slides/net/) Para más información.