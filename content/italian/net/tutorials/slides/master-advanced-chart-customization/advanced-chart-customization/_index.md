---
title: Personalizzazione avanzata dei grafici con Aspose.Slides per .NET
linktitle: Personalizzazione avanzata dei grafici con Aspose.Slides per .NET
second_title: API di elaborazione di PowerPoint Aspose.Slides .NET
description: Sblocca il pieno potenziale di Aspose.Slides per .NET padroneggiando tecniche avanzate di personalizzazione dei grafici. Questa guida passo passo copre tutto, dalla creazione di grafici di base ai dettagli complessi come linee della griglia, titoli degli assi e colori personalizzati.
type: docs
weight: 10
url: /it/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Introduzione

Creare grafici visivamente accattivanti e informativi è fondamentale per una presentazione efficace dei dati. Aspose.Slides per .NET offre potenti strumenti per la personalizzazione dei grafici, consentendoti di adattare ogni aspetto dei tuoi grafici. In questo tutorial, esploreremo tecniche avanzate per la personalizzazione dei grafici utilizzando Aspose.Slides per .NET.

## Prerequisiti

Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:

1.  Libreria Aspose.Slides per .NET: Scarica e installa la libreria Aspose.Slides da[Qui](https://releases.aspose.com/slides/net/).
2. Ambiente di sviluppo .NET: configura un ambiente di sviluppo .NET, come Visual Studio.
3. Conoscenza di base di C#: la familiarità con la programmazione C# sarà utile poiché scriveremo codice C#.

Ora scomponiamo il processo di personalizzazione avanzata del grafico in passaggi chiari.

## Passaggio 1: creare una nuova presentazione

Inizia creando una nuova presentazione in cui inserire il tuo grafico.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "Your Document Directory";

// Creare la directory se non esiste.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Crea un'istanza della presentazione
Presentation pres = new Presentation();
```

## Passaggio 2: accedi alla prima diapositiva

Successivamente, accedi alla prima diapositiva in cui desideri aggiungere il grafico.

```csharp
// Accedi alla prima diapositiva
ISlide slide = pres.Slides[0];
```

## Passaggio 3: aggiungere un grafico di esempio

Ora aggiungiamo alla diapositiva un grafico a linee con dei marcatori.

```csharp
// Aggiungi un grafico di esempio
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Passaggio 4: imposta il titolo del grafico

Impostare un titolo per il grafico fornisce un contesto essenziale.

```csharp
// Imposta il titolo del grafico
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

## Passaggio 5: personalizzare le linee principali della griglia

È possibile migliorare le linee della griglia per l'asse dei valori per una migliore leggibilità.

```csharp
// Personalizza le linee principali della griglia per l'asse dei valori
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Passaggio 6: personalizzare le linee della griglia secondaria

Allo stesso modo, personalizzare le linee della griglia secondaria per l'asse dei valori.

```csharp
// Personalizza le linee della griglia secondaria per l'asse dei valori
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Passaggio 7: definire il formato numerico dell'asse dei valori

È possibile formattare i numeri visualizzati sull'asse dei valori.

```csharp
// Imposta il formato del numero dell'asse dei valori
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Passaggio 8: impostare i valori massimo e minimo

Definisci i valori massimo e minimo per il grafico.

```csharp
// Imposta i valori massimi e minimi del grafico
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Passaggio 9: personalizzare le proprietà del testo dell'asse dei valori

Migliorando le proprietà del testo dell'asse dei valori si migliora la leggibilità.

```csharp
// Personalizza le proprietà del testo dell'asse dei valori
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Passaggio 10: aggiungere il titolo dell'asse del valore

Aggiungere un titolo all'asse dei valori può chiarire cosa rappresentano i dati.

```csharp
// Imposta il titolo dell'asse dei valori
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

## Passaggio 11: personalizzare le linee principali della griglia per l'asse delle categorie

Ora miglioriamo le linee principali della griglia per l'asse delle categorie.

```csharp
// Personalizza le linee principali della griglia per l'asse Categoria
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Passaggio 12: personalizzare le linee della griglia secondaria per l'asse delle categorie

Allo stesso modo, personalizzare le linee della griglia secondaria per l'asse delle categorie.

```csharp
// Personalizza le linee della griglia secondaria per l'asse Categoria
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Passaggio 13: personalizzare le proprietà del testo dell'asse delle categorie

Migliora lo stile del carattere e l'aspetto delle etichette degli assi delle categorie.

```csharp
// Personalizza le proprietà del testo dell'asse delle categorie
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Passaggio 14: aggiungere il titolo dell'asse delle categorie

Se necessario, puoi anche aggiungere un titolo per l'asse delle categorie.

```csharp
// Imposta titolo asse categoria
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

## Fase 15: Ulteriori personalizzazioni

Migliora ulteriormente il tuo grafico con personalizzazioni aggiuntive, come legende, colori delle pareti e impostazioni dell'area del grafico.

```csharp
// Ulteriori personalizzazioni (facoltative)

// Personalizza le proprietà del testo delle leggende
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Mostra le legende del grafico senza sovrapporre il grafico
chart.Legend.Overlay = true;

// Impostazione del colore della parete posteriore del grafico
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Imposta il colore del pavimento del grafico
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Imposta il colore dell'area del grafico
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Salva la presentazione
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Conclusione

In questa guida completa, abbiamo trattato tecniche avanzate di personalizzazione dei grafici utilizzando Aspose.Slides per .NET. Hai imparato come creare una presentazione, aggiungere un grafico, perfezionarne l'aspetto e personalizzare vari elementi del grafico, come linee della griglia, etichette degli assi e legende. 

## Domande frequenti

### Quali versioni di .NET sono supportate da Aspose.Slides per .NET?
Aspose.Slides per .NET supporta varie versioni di .NET, tra cui .NET Framework e .NET Core. Fare riferimento alla documentazione per un elenco completo delle versioni supportate.

### Posso creare grafici da fonti dati come file Excel?
Sì, Aspose.Slides consente di creare grafici da fonti di dati esterne come fogli di calcolo Excel. Consulta la documentazione per esempi dettagliati.

### Come posso aggiungere etichette dati personalizzate alle mie serie di grafici?
 Per aggiungere etichette dati personalizzate, accedi a`DataLabels` proprietà della serie e personalizzare le etichette come necessario. Puoi trovare esempi di codice nella documentazione.

### È possibile esportare il grafico in formati diversi, come PDF o immagini?
Assolutamente! Aspose.Slides ti consente di esportare le tue presentazioni con grafici in vari formati, inclusi PDF e formati immagine.

### Dove posso trovare altri tutorial ed esempi per Aspose.Slides per .NET?
 Visita Aspose.Slides[sito web](https://reference.aspose.com/slides/net/) per tutorial approfonditi, esempi di codice e documentazione.