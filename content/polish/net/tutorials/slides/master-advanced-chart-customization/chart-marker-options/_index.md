---
title: Opcje znaczników wykresu w punkcie danych w Aspose.Slides .NET
linktitle: Opcje znaczników wykresu w punkcie danych w Aspose.Slides .NET
second_title: Aspose.Slides .NET API przetwarzania programu PowerPoint
description: Dowiedz się, jak ulepszyć wykresy programu PowerPoint za pomocą niestandardowych opcji znaczników przy użyciu Aspose.Slides dla .NET. Ten przewodnik krok po kroku obejmuje wymagania wstępne, tworzenie wykresów, formatowanie punktów danych i nie tylko.
type: docs
weight: 11
url: /pl/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Wstęp

Włączanie pomocy wizualnych do prezentacji jest niezbędne do skutecznej komunikacji. Aspose.Slides for .NET zapewnia solidne narzędzia do tworzenia i dostosowywania wykresów, umożliwiając programistom ulepszanie prezentacji danych. Jedną z wyróżniających się funkcji jest możliwość korzystania z opcji znaczników wykresu w punktach danych, co umożliwia precyzyjną personalizację w celu uzyskania profesjonalnie wyglądających wykresów. Ten artykuł przeprowadzi Cię przez każdy krok potrzebny do osiągnięcia tego celu.

## Wymagania wstępne

Przed kontynuowaniem upewnij się, że:

-  Aspose.Slides dla .NET zainstalowany: Pobierz ze strony[Tutaj](https://releases.aspose.com/slides/net/).
- Podstawowa konfiguracja: plik prezentacji, np. „Test.pptx”, w katalogu roboczym.
- Środowisko programistyczne: Visual Studio lub równoważne, skonfigurowane dla .NET.

## Importowanie wymaganych przestrzeni nazw

Dodaj niezbędne przestrzenie nazw do swojego projektu, aby zapewnić bezproblemowy rozwój:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Krok 1: Utwórz wykres w swojej prezentacji

Zacznij od utworzenia domyślnego wykresu na pierwszym slajdzie prezentacji:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 To dodaje`LineWithMarkers` wykres do slajdu o określonych wymiarach.

## Krok 2: Pobierz indeks arkusza danych wykresu

Domyślny indeks arkusza danych wykresu jest niezbędny do dalszej personalizacji:

```csharp
int defaultWorksheetIndex = 0;
```

## Krok 3: Uzyskaj dostęp do skoroszytu danych wykresu

Aby manipulować danymi wykresu, pobierz skojarzony skoroszyt:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Krok 4: Skonfiguruj serię wykresów i dodaj punkty danych

Wyczyść domyślne serie i dodaj nowe punkty danych dla swoich serii:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Dodaj punkty danych do serii
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Krok 5: Zastosuj wypełnienia obrazkowe do znaczników punktów danych

Niestandardowe obrazy mogą sprawić, że znaczniki danych staną się wizualnie atrakcyjne:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Ustaw niestandardowe obrazy dla znaczników
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Krok 6: Dostosuj rozmiar znacznika

Zmień rozmiar znaczników, aby zwiększyć ich widoczność:

```csharp
series.Marker.Size = 20;
```

## Krok 7: Zapisz zaktualizowaną prezentację

Zapisz dostosowaną prezentację w wybranej lokalizacji:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Wniosek

Aspose.Slides for .NET wyposaża programistów w narzędzia do tworzenia profesjonalnych wykresów z bogatymi opcjami dostosowywania. Wykorzystując opcje znaczników wykresów, możesz znacznie zwiększyć atrakcyjność wizualną i przejrzystość swoich prezentacji. Ten przewodnik krok po kroku zapewnia, że nawet złożone dostosowania są proste do wdrożenia.

## Najczęściej zadawane pytania

### Czy mogę użyć dowolnego formatu obrazu do personalizacji znaczników?
Tak, Aspose.Slides obsługuje różne formaty obrazów, w tym JPEG, PNG i BMP, co pozwala na dostosowywanie znaczników.

### Jak zmienić typ wykresu po jego utworzeniu?
 Aby zmienić typ wykresu, uzyskaj dostęp do`chart.Type` nieruchomość i przypisać inną`ChartType`.

### Czy Aspose.Slides dla .NET jest zgodny ze starszymi wersjami programu PowerPoint?
Tak, obsługuje wsteczną kompatybilność ze starszymi formatami programu PowerPoint, co gwarantuje wszechstronność.

### Czy mogę dynamicznie aktualizować dane na wykresie?
 Oczywiście. Użyj`IChartDataWorkbook` aby programowo aktualizować dane wykresu.

### Gdzie mogę znaleźć więcej materiałów?
 Odkryj[Dokumentacja Aspose.Slides](https://reference.aspose.com/slides/net/)lub dołącz do[fora społecznościowe](https://forum.aspose.com/) o wsparcie.