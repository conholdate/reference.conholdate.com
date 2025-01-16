---
title: Zaawansowana personalizacja wykresów z Aspose.Slides dla .NET
linktitle: Zaawansowana personalizacja wykresów z Aspose.Slides dla .NET
second_title: Aspose.Slides .NET API przetwarzania programu PowerPoint
description: Odkryj pełny potencjał Aspose.Slides dla .NET, opanowując zaawansowane techniki dostosowywania wykresów. Ten przewodnik krok po kroku obejmuje wszystko, od podstawowego tworzenia wykresów po skomplikowane szczegóły, takie jak linie siatki, tytuły osi i niestandardowe kolory.
type: docs
weight: 10
url: /pl/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Wstęp

Tworzenie atrakcyjnych wizualnie i informacyjnych wykresów jest kluczowe dla skutecznej prezentacji danych. Aspose.Slides for .NET oferuje potężne narzędzia do dostosowywania wykresów, umożliwiając dostosowanie każdego aspektu wykresów. W tym samouczku przyjrzymy się zaawansowanym technikom dostosowywania wykresów przy użyciu Aspose.Slides for .NET.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełniasz następujące wymagania wstępne:

1.  Biblioteka Aspose.Slides dla platformy .NET: Pobierz i zainstaluj bibliotekę Aspose.Slides ze strony[Tutaj](https://releases.aspose.com/slides/net/).
2. Środowisko programistyczne .NET: skonfiguruj środowisko programistyczne .NET, np. Visual Studio.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# będzie przydatna, ponieważ będziemy pisać kod w tym języku.

Teraz omówimy zaawansowany proces dostosowywania wykresu w prostych krokach.

## Krok 1: Utwórz nową prezentację

Zacznij od utworzenia nowej prezentacji, w której będziesz mógł umieścić wykres.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "Your Document Directory";

// Utwórz katalog, jeśli nie istnieje.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Utwórz prezentację
Presentation pres = new Presentation();
```

## Krok 2: Dostęp do pierwszego slajdu

Następnie przejdź do pierwszego slajdu, do którego chcesz dodać wykres.

```csharp
// Uzyskaj dostęp do pierwszego slajdu
ISlide slide = pres.Slides[0];
```

## Krok 3: Dodaj przykładowy wykres

Teraz dodajmy do slajdu wykres liniowy ze znacznikami.

```csharp
// Dodaj przykładowy wykres
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Krok 4: Ustaw tytuł wykresu

Nadanie wykresowi tytułu zapewnia niezbędny kontekst.

```csharp
// Ustaw tytuł wykresu
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

## Krok 5: Dostosuj główne linie siatki

Możesz udoskonalić linie siatki dla osi wartości, aby zwiększyć czytelność.

```csharp
// Dostosuj główne linie siatki dla osi wartości
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Krok 6: Dostosuj linie siatki pomocniczej

W podobny sposób dostosuj pomocnicze linie siatki dla osi wartości.

```csharp
// Dostosuj mniejsze linie siatki dla osi wartości
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Krok 7: Zdefiniuj format liczbowy osi wartości

Można formatować liczby wyświetlane na osi wartości.

```csharp
// Ustaw format numeru osi wartości
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Krok 8: Ustaw wartości maksymalne i minimalne

Zdefiniuj wartości maksymalne i minimalne dla wykresu.

```csharp
// Ustaw maksymalne i minimalne wartości wykresu
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Krok 9: Dostosuj właściwości tekstu osi wartości

Ulepszenie właściwości tekstowych osi wartości poprawia czytelność.

```csharp
// Dostosuj właściwości tekstu osi wartości
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Krok 10: Dodaj tytuł osi wartości

Dodanie tytułu do osi wartości może wyjaśnić, co przedstawiają dane.

```csharp
// Ustaw tytuł osi wartości
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

## Krok 11: Dostosuj główne linie siatki dla osi kategorii

Teraz udoskonalimy główne linie siatki dla osi kategorii.

```csharp
// Dostosuj główne linie siatki dla osi kategorii
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Krok 12: Dostosuj linie siatki pomocniczej dla osi kategorii

W podobny sposób dostosuj pomocnicze linie siatki dla osi kategorii.

```csharp
// Dostosuj linie siatki pomocniczej dla osi kategorii
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Krok 13: Dostosuj właściwości tekstu osi kategorii

Poprawiono styl czcionki i wygląd etykiet osi kategorii.

```csharp
// Dostosuj właściwości tekstu osi kategorii
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Krok 14: Dodaj tytuł osi kategorii

W razie potrzeby można również dodać tytuł dla osi kategorii.

```csharp
// Ustaw tytuł osi kategorii
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

## Krok 15: Dodatkowe dostosowania

Ulepsz swój wykres, dodając dodatkowe dostosowania, takie jak legendy, kolory ścian i ustawienia obszaru wykresu.

```csharp
// Dodatkowe dostosowania (opcjonalne)

// Dostosuj właściwości tekstu legend
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Pokaż legendy wykresu bez nakładania się wykresu
chart.Legend.Overlay = true;

// Ustawianie koloru tylnej ściany wykresu
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Ustaw kolor podłogi wykresu
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Ustaw kolor obszaru wykresu
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Zapisz prezentację
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Wniosek

W tym kompleksowym przewodniku omówiliśmy zaawansowane techniki dostosowywania wykresów przy użyciu Aspose.Slides dla .NET. Dowiedziałeś się, jak utworzyć prezentację, dodać wykres, udoskonalić jego wygląd i dostosować różne elementy wykresu, takie jak linie siatki, etykiety osi i legendy. 

## Najczęściej zadawane pytania

### Jakie wersje platformy .NET są obsługiwane przez Aspose.Slides dla platformy .NET?
Aspose.Slides for .NET obsługuje różne wersje .NET, w tym .NET Framework i .NET Core. Zapoznaj się z dokumentacją, aby uzyskać pełną listę obsługiwanych wersji.

### Czy mogę tworzyć wykresy na podstawie źródeł danych, np. plików Excel?
Tak, Aspose.Slides pozwala tworzyć wykresy z zewnętrznych źródeł danych, takich jak arkusze kalkulacyjne Excel. Zapoznaj się z dokumentacją, aby uzyskać szczegółowe przykłady.

### Jak mogę dodać niestandardowe etykiety danych do serii wykresów?
 Aby dodać niestandardowe etykiety danych, uzyskaj dostęp do`DataLabels` właściwość serii i dostosuj etykiety według potrzeb. Przykłady kodu znajdziesz w dokumentacji.

### Czy można wyeksportować wykres do innych formatów, np. PDF lub obrazów?
Oczywiście! Aspose.Slides umożliwia eksportowanie prezentacji z wykresami do różnych formatów, w tym PDF i obrazów.

### Gdzie mogę znaleźć więcej samouczków i przykładów dla Aspose.Slides dla .NET?
 Odwiedź Aspose.Slides[strona internetowa](https://reference.aspose.com/slides/net/) aby uzyskać dostęp do obszernych samouczków, przykładów kodu i dokumentacji.