---
title: Linee di tendenza nei grafici con Aspose.Slides per .NET
linktitle: Linee di tendenza nei grafici con Aspose.Slides per .NET
second_title: API di elaborazione di PowerPoint Aspose.Slides .NET
description: Scopri come aggiungere e personalizzare le linee di tendenza nei grafici usando Aspose.Slides per .NET. Questa guida completa copre le linee di tendenza esponenziali, lineari, logaritmiche, polinomiali e di media mobile per migliorare la visualizzazione dei tuoi dati.
type: docs
weight: 12
url: /it/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Introduzione  

Aggiungere linee di tendenza ai grafici è una tecnica fondamentale per analizzare le tendenze dei dati e prevedere i valori futuri. Con Aspose.Slides per .NET, puoi aggiungere e personalizzare senza problemi le linee di tendenza ai grafici della tua presentazione, migliorando la visualizzazione dei tuoi dati. Questa guida fornisce una procedura dettagliata per aggiungere linee di tendenza a vari tipi di grafici in una presentazione PowerPoint utilizzando Aspose.Slides per .NET.  

## Prerequisiti  

Prima di addentrarci nell'implementazione, assicurati di avere la seguente configurazione:  

1.  Aspose.Slides per .NET: Scarica e installa la libreria da[pagina di download](https://releases.aspose.com/slides/net/).  
2. Ambiente di sviluppo: utilizzare un IDE come Visual Studio per la codifica.  
3. Conoscenze di base del linguaggio C#: per seguire questo tutorial è richiesta familiarità con la programmazione C#.  

## Importazione degli spazi dei nomi richiesti  

Per iniziare, importa gli spazi dei nomi essenziali nel tuo progetto:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Fase 1: Impostazione della presentazione  

Per prima cosa, inizializza una presentazione vuota. Questa servirà da contenitore per il tuo grafico.  

```csharp
string dataDir = "Your/Documents/Directory";

// Assicurarsi che la directory esista
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Crea una nuova presentazione
Presentation presentation = new Presentation();
```

## Passaggio 2: aggiunta di un grafico a una diapositiva  

Ora aggiungi una diapositiva e includi un grafico a colonne raggruppate per visualizzare i tuoi dati.  

```csharp
// Aggiungi una diapositiva vuota
ISlide slide = presentation.Slides[0];

// Aggiungere un grafico a colonne raggruppate
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Passaggio 3: Popolamento dei dati del grafico  

Compilare il grafico con dati campione.  

```csharp
// Accedi alla cartella di lavoro dei dati del grafico predefinito
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Aggiornare le categorie predefinite e i valori delle serie
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Fase 4: aggiunta di linee di tendenza  

### Linea di tendenza esponenziale  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Linea di tendenza lineare  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Linea di tendenza logaritmica  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Linea di tendenza della media mobile  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Linea di tendenza polinomiale  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Linea di tendenza della potenza  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Passaggio 5: salvataggio della presentazione  

Infine, salva la presentazione con tutte le linee di tendenza aggiunte al grafico.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Conclusione  

Utilizzando Aspose.Slides per .NET, aggiungere linee di tendenza ai grafici diventa un compito semplice. Questa funzionalità consente di presentare le tendenze dei dati in modo efficace e di aggiungere tocchi professionali alle presentazioni. Seguire i passaggi sopra per incorporare vari tipi di linee di tendenza e migliorare la visualizzazione dei dati.  

## Domande frequenti  

### Posso personalizzare l'aspetto delle linee di tendenza?  
 Sì, puoi personalizzare il colore, lo spessore e lo stile delle linee di tendenza utilizzando`Format.Line` proprietà.  

### Sono supportati altri tipi di grafici?  
Sì, Aspose.Slides per .NET supporta vari tipi di grafici, tra cui grafici a barre, a torta e a linee.  

### Come posso visualizzare le equazioni e i valori R-quadrato?  
 Abilitare`DisplayEquation` E`DisplayRSquaredValue` proprietà di una linea di tendenza per visualizzare questi valori sul grafico.  

### Posso usare Aspose.Slides per .NET con altri linguaggi?  
Sì, la libreria è compatibile con tutti i linguaggi supportati da .NET, inclusi VB.NET e F#.  

### Dove posso trovare ulteriore documentazione?  
 Visita il[Documentazione Aspose.Slides per .NET](https://reference.aspose.com/slides/net/) per ulteriori informazioni.