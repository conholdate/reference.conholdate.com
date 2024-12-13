---
title: Dodawanie warstwy do pliku geobazy przy użyciu Aspose.GIS dla .NET
linktitle: Dodaj warstwę do pliku geobazy danych
second_title: Aspose.GIS .NET API
description: Dowiedz się, jak dodać nową warstwę do File Geodatabase (GDB) przy użyciu Aspose.GIS dla .NET. Ten kompleksowy przewodnik obejmuje wymagania wstępne, importy przestrzeni nazw i szczegółowe kroki tworzenia i walidacji warstw w zestawach danych GIS.
type: docs
weight: 16
url: /pl/net/tutorials/gis/mastering-layer-management/add-layer-to-file-geo-database/
---
## Wstęp

Technologia Geographic Information System (GIS) odgrywa kluczową rolę w nowoczesnej analizie i wizualizacji danych. Aspose.GIS dla .NET to wyjątkowa biblioteka umożliwiająca deweloperom wydajne manipulowanie danymi geograficznymi. Ten szczegółowy przewodnik opisuje, jak dodać nową warstwę do zestawu danych File Geodatabase (GDB) przy użyciu Aspose.GIS dla .NET. Wykonaj te kompleksowe kroki, aby płynnie zintegrować warstwy i zwiększyć możliwości GIS.

## Wymagania wstępne dodawania warstw do pliku GDB

Zanim przejdziemy dalej, upewnij się, że posiadasz następujące rzeczy:

1. Biblioteka Aspose.GIS dla .NET  
    Pobierz i zainstaluj bibliotekę z[Strona Aspose.GIS dla .NET](https://reference.aspose.com/gis/net/).

2. Zestaw danych Geobazy Plików (GDB)  
   Upewnij się, że posiadasz istniejący zestaw danych GDB dla tej operacji.

3. Środowisko programistyczne  
   Zainstaluj i skonfiguruj preferowane środowisko IDE z obsługą .NET (np. Visual Studio).

4. Licencja tymczasowa (opcjonalnie)  
    Aby uzyskać pełną ocenę funkcji, poproś o[licencja tymczasowa](https://purchase.conholdate.com/temporary-license/).

5. Katalog danych  
   Przygotuj katalog do zarządzania zbiorami danych wejściowych i wyjściowych.

## Importowanie wymaganych przestrzeni nazw

Przed kodowaniem uwzględnij niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności Aspose.GIS. Dodaj następujący fragment kodu na początku swojego projektu:

```csharp
using Aspose.Gis;
using Aspose.Gis.Geometries;
using Aspose.Gis.SpatialReferencing;
using System;
```

## Krok 1: Duplikuj zbiór danych GDB

Aby zachować integralność oryginalnego zestawu danych, utwórz duplikat. Użyj następującego kodu, aby skopiować zestaw danych do nowej lokalizacji:

```csharp
string dataDir = "C:\\GISData\\"; // Katalog zawierający Twoje zestawy danych
string originalPath = dataDir + "ExistingDataset.gdb";
string newDatasetPath = dataDir + "ModifiedDataset.gdb";

// Funkcja duplikowania katalogu
RunExamples.CopyDirectory(originalPath, newDatasetPath);
```

## Krok 2: Otwórz zbiór danych i sprawdź możliwość tworzenia

Aspose.GIS pozwala deweloperom otwierać zestawy danych i sprawdzać, czy można dodawać nowe warstwy. Użyj następującego fragmentu kodu, aby potwierdzić możliwości tworzenia zestawu danych:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    Console.WriteLine($"Can Create Layers: {dataset.CanCreateLayers}"); // Powinien zwrócić wartość True
}
```

## Krok 3: Utwórz nową warstwę w zestawie danych

Dodanie warstwy wymaga zdefiniowania jej układu odniesienia przestrzennego i atrybutów. Oto jak utworzyć i wypełnić warstwę przykładowymi danymi:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    // Utwórz nową warstwę z układem odniesienia przestrzennego WGS 84
    using (var layer = dataset.CreateLayer("NewLayer", SpatialReferenceSystem.Wgs84))
    {
        // Dodaj schemat atrybutów
        layer.Attributes.Add(new FeatureAttribute("LocationName", AttributeDataType.String));

        // Utwórz i dodaj funkcję
        var feature = layer.ConstructFeature();
        feature.SetValue("LocationName", "Sample Point");
        feature.Geometry = new Point(34.0522, -118.2437); // Długość i szerokość geograficzna
        layer.Add(feature);
    }
}
```

## Krok 4: Otwórz i sprawdź poprawność nowej warstwy

Po utworzeniu warstwy sprawdź jej zawartość, aby zapewnić dokładność. Użyj następującego fragmentu kodu:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    using (var layer = dataset.OpenLayer("NewLayer"))
    {
        Console.WriteLine($"Feature Count: {layer.Count}");
        Console.WriteLine($"Attribute Value: {layer[0].GetValue<string>("LocationName")}");
    }
}
```

## Wniosek

Dodanie warstwy do zestawu danych File Geodatabase za pomocą Aspose.GIS dla .NET to prosty proces, jeśli wykonasz poniższe kroki. Od duplikowania zestawów danych po tworzenie i sprawdzanie poprawności warstw, biblioteka zapewnia solidne narzędzia do zarządzania danymi GIS. Opanowując te techniki, możesz ulepszyć swoje przepływy pracy GIS i osiągnąć skuteczną manipulację danymi geograficznymi.

## Najczęściej zadawane pytania

### Do czego służy Aspose.GIS dla .NET?
Aspose.GIS dla platformy .NET to biblioteka przeznaczona do przetwarzania i manipulowania danymi geograficznymi, obsługująca różne formaty plików, w tym Shapefiles, GDB i inne.

### Czy mogę dodać wiele warstw w jednej operacji?
Tak, Aspose.GIS umożliwia tworzenie i zarządzanie wieloma warstwami w obrębie zestawu danych.

### Jakie układy odniesienia przestrzennego są obsługiwane?
Biblioteka obsługuje liczne układy odniesienia przestrzennego, w tym WGS 84, NAD 83 i niestandardowe układy współrzędnych.

### Gdzie mogę znaleźć wsparcie?
 Odwiedź[Forum Aspose.GIS](https://forum.aspose.com/c/gis/33) do dyskusji i wsparcia społeczności.

### Czy jest dostępna bezpłatna wersja próbna?
 Tak,[bezpłatny okres próbny](https://releases.aspose.com/) jest dostępny do testowania funkcji biblioteki.