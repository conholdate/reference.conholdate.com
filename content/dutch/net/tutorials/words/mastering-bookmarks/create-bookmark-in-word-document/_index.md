---
title: Maak een bladwijzer in een Word-document met Aspose.Words voor .NET
linktitle: Maak een bladwijzer in een Word-document met Aspose.Words voor .NET
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u uw Word-documenten kunt verbeteren door bladwijzers te maken en beheren met Aspose.Words voor .NET. Deze stapsgewijze zelfstudiegids.
type: docs
weight: 10
url: /nl/net/tutorials/words/mastering-bookmarks/create-bookmark-in-word-document/
---
## Invoering

Navigeren door grote documenten kan een uitdaging zijn, maar bladwijzers maken het een fluitje van een cent! Deze tutorial begeleidt u bij het maken van bladwijzers in een Word-document met Aspose.Words voor .NET. U leert stap voor stap hoe u uw document instelt, bladwijzers toevoegt en het opslaat als PDF. Laten we beginnen!

## Vereisten

Zorg ervoor dat u het volgende bij de hand hebt voordat u aan de slag gaat:

1.  Aspose.Words voor .NET-bibliotheek: Download en installeer het vanaf[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Gebruik Visual Studio of een .NET-compatibele IDE.
3. Basiskennis van C#: Kennis van C#-programmeerconcepten is nuttig.

## Naamruimten importeren

Importeer eerst de benodigde naamruimten om met Aspose.Words te kunnen werken:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Het document en DocumentBuilder instellen

 Maak een nieuw document en initialiseer de`DocumentBuilder`, waarmee u inhoud en bladwijzers kunt toevoegen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Maak de hoofdbladwijzer

Om een bladwijzer te maken, moet u het begin- en eindpunt opgeven. Zo maakt u een bladwijzer met de naam "Mijn bladwijzer":

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside the main bookmark.");
```
- `StartBookmark`: Markeert het begin van de bladwijzer.
- `Writeln`: Voegt tekst toe aan de bladwijzer.

## Stap 3: Een geneste bladwijzer maken

U kunt bladwijzers nesten voor een betere organisatie. Hier leest u hoe u "Nested Bookmark" toevoegt in "My Bookmark":

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside the nested bookmark.");
builder.EndBookmark("Nested Bookmark");
```
- Met nesten kunt u een hiërarchische structuur creëren. 
- `EndBookmark`: Sluit de huidige bladwijzer.

## Stap 4: Tekst toevoegen buiten de geneste bladwijzer

Nadat u de geneste bladwijzer hebt gemaakt, kunt u doorgaan met het toevoegen van inhoud binnen de hoofdbladwijzer:

```csharp
builder.Writeln("Text after the nested bookmark.");
builder.EndBookmark("My Bookmark");
```
Hiermee wordt gegarandeerd dat de hoofdbladwijzer zowel de geneste bladwijzer als eventuele aanvullende tekst bevat.

## Stap 5: PDF-opslagopties configureren

Om bladwijzers in de PDF op te nemen, configureert u de opslagopties:

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```
- `PdfSaveOptions`: Definieert hoe het document als PDF wordt opgeslagen.
- `BookmarksOutlineLevels`: Hiermee stelt u de hiërarchie van bladwijzers in de PDF in.

## Stap 6: Sla het document op

Sla het document ten slotte op als PDF:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```
 De`Save` Met deze methode wordt het document opgeslagen in de opgegeven indeling en op de opgegeven locatie, inclusief bladwijzers.

## Conclusie

Bladwijzers maken in een Word-document met Aspose.Words voor .NET is eenvoudig en verbetert de documentnavigatie. Of u nu rapporten, eBooks genereert of uitgebreide documenten beheert, bladwijzers zijn van onschatbare waarde. Volg deze tutorial en u hebt in een mum van tijd een goed georganiseerde, gebladerde PDF!

## Veelgestelde vragen

### Kan ik meerdere bladwijzers op verschillende niveaus maken?
Ja! U kunt meerdere bladwijzers maken en hun hiërarchie definiëren wanneer u ze opslaat als PDF.

### Hoe kan ik de tekst van een bladwijzer bijwerken?
 Gebruik`DocumentBuilder.MoveToBookmark` om naar de bladwijzer te navigeren en de tekst bij te werken.

### Is het mogelijk om een bladwijzer te verwijderen?
 Absoluut! Gebruik de`Bookmarks.Remove` methode door de naam van de bladwijzer op te geven.

### Kan ik bladwijzers maken in andere formaten dan PDF?
Ja, Aspose.Words ondersteunt bladwijzers in formaten zoals DOCX, HTML en EPUB.

### Hoe kan ik ervoor zorgen dat de bladwijzers correct in de PDF worden weergegeven?
 Definiëren`BookmarksOutlineLevels` goed in`PdfSaveOptions` om ervoor te zorgen dat de bladwijzers in het PDF-overzicht worden opgenomen.