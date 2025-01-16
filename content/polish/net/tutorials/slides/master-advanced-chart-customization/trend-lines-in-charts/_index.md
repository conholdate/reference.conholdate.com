---
title: Linie trendu na wykresach z Aspose.Slides dla .NET
linktitle: Linie trendu na wykresach z Aspose.Slides dla .NET
second_title: Aspose.Slides .NET API przetwarzania programu PowerPoint
description: Dowiedz się, jak dodawać i dostosowywać linie trendu na wykresach za pomocą Aspose.Slides dla .NET. Ten kompleksowy przewodnik obejmuje linie trendu wykładnicze, liniowe, logarytmiczne, wielomianowe i średniej ruchomej, aby ulepszyć wizualizację danych.
type: docs
weight: 12
url: /pl/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Wstęp  

Dodawanie linii trendu do wykresów jest kluczową techniką analizy trendów danych i prognozowania przyszłych wartości. Dzięki Aspose.Slides for .NET możesz bezproblemowo dodawać i dostosowywać linie trendu do wykresów prezentacji, ulepszając wizualizację danych. Ten przewodnik zawiera szczegółowy opis dodawania linii trendu do różnych typów wykresów w prezentacji PowerPoint przy użyciu Aspose.Slides for .NET.  

## Wymagania wstępne  

Zanim przejdziemy do implementacji, upewnij się, że masz następującą konfigurację:  

1.  Aspose.Slides dla .NET: Pobierz i zainstaluj bibliotekę z[strona do pobrania](https://releases.aspose.com/slides/net/).  
2. Środowisko programistyczne: Użyj środowiska IDE, np. Visual Studio, do kodowania.  
3. Podstawowa wiedza o języku C#: Aby móc uczestniczyć w tym samouczku, wymagana jest znajomość programowania w języku C#.  

## Importowanie wymaganych przestrzeni nazw  

Aby rozpocząć, zaimportuj do swojego projektu podstawowe przestrzenie nazw:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Krok 1: Konfigurowanie prezentacji  

Najpierw zainicjuj pustą prezentację. Będzie ona służyć jako kontener dla Twojego wykresu.  

```csharp
string dataDir = "Your/Documents/Directory";

// Upewnij się, że katalog istnieje
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Utwórz nową prezentację
Presentation presentation = new Presentation();
```

## Krok 2: Dodawanie wykresu do slajdu  

Teraz dodaj slajd i dołącz wykres kolumnowy, aby zwizualizować swoje dane.  

```csharp
// Dodaj pusty slajd
ISlide slide = presentation.Slides[0];

// Dodaj wykres kolumnowy klastrowany
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Krok 3: Wypełnianie danych wykresu  

Wypełnij wykres przykładowymi danymi.  

```csharp
// Uzyskaj dostęp do domyślnego skoroszytu danych wykresu
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Zaktualizuj domyślne kategorie i wartości serii
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Krok 4: Dodawanie linii trendu  

### Linia trendu wykładniczego  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Linia trendu liniowego  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Linia trendu logarytmicznego  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Linia trendu średniej ruchomej  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Linia trendu wielomianowego  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Linia trendu mocy  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Krok 5: Zapisywanie prezentacji  

Na koniec zapisz prezentację ze wszystkimi liniami trendu dodanymi do wykresu.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Wniosek  

Używając Aspose.Slides dla .NET, dodawanie linii trendu do wykresów staje się prostym zadaniem. Ta funkcja pozwala na skuteczne prezentowanie trendów danych i dodawanie profesjonalnych akcentów do prezentacji. Wykonaj powyższe kroki, aby włączyć różne typy linii trendu i podnieść poziom wizualizacji danych.  

## Najczęściej zadawane pytania  

### Czy mogę dostosować wygląd linii trendu?  
 Tak, możesz dostosować kolor, grubość i styl linii trendu za pomocą`Format.Line` nieruchomość.  

### Czy są obsługiwane inne typy wykresów?  
Tak, Aspose.Slides dla platformy .NET obsługuje różne typy wykresów, w tym wykresy słupkowe, kołowe i liniowe.  

### Jak wyświetlić równania i wartości R-kwadrat?  
 Włączać`DisplayEquation` I`DisplayRSquaredValue` właściwości linii trendu, aby wyświetlić te wartości na wykresie.  

### Czy mogę używać Aspose.Slides dla .NET z innymi językami?  
Tak, biblioteka jest zgodna z dowolnym językiem obsługiwanym przez platformę .NET, w tym VB.NET i F#.  

### Gdzie mogę znaleźć dalszą dokumentację?  
 Odwiedź[Dokumentacja Aspose.Slides dla .NET](https://reference.aspose.com/slides/net/) Aby uzyskać więcej informacji.