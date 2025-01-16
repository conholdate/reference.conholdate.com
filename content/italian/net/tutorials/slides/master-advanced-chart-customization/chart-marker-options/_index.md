---
title: Opzioni del marcatore grafico sul punto dati in Aspose.Slides .NET
linktitle: Opzioni del marcatore grafico sul punto dati in Aspose.Slides .NET
second_title: API di elaborazione di PowerPoint Aspose.Slides .NET
description: Scopri come migliorare i tuoi grafici PowerPoint con opzioni di marcatori personalizzate usando Aspose.Slides per .NET. Questa guida passo passo copre i prerequisiti, la creazione di grafici, la formattazione dei punti dati e altro ancora.
type: docs
weight: 11
url: /it/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Introduzione

L'integrazione di supporti visivi nelle presentazioni è essenziale per una comunicazione di impatto. Aspose.Slides per .NET fornisce strumenti robusti per creare e personalizzare grafici, consentendo agli sviluppatori di migliorare le loro presentazioni di dati. Una delle caratteristiche più importanti è la possibilità di utilizzare opzioni di marcatura dei grafici sui punti dati, consentendo una personalizzazione precisa per grafici dall'aspetto professionale. Questo articolo ti guiderà attraverso ogni passaggio necessario per raggiungere questo obiettivo.

## Prerequisiti

Prima di procedere, accertarsi di quanto segue:

-  Aspose.Slides per .NET installato: scaricalo da[Qui](https://releases.aspose.com/slides/net/).
- Configurazione di base: un file di presentazione, ad esempio "Test.pptx", nella directory di lavoro.
- Ambiente di sviluppo: Visual Studio o equivalente, configurato per .NET.

## Importazione degli spazi dei nomi richiesti

Aggiungi gli spazi dei nomi necessari al tuo progetto per uno sviluppo senza interruzioni:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Passaggio 1: crea un grafico nella presentazione

Inizia creando un grafico predefinito nella prima diapositiva della presentazione:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Questo aggiunge un`LineWithMarkers` grafico nella diapositiva con le dimensioni specificate.

## Passaggio 2: recuperare l'indice del foglio di lavoro dei dati del grafico

L'indice predefinito del foglio di lavoro dei dati del grafico è essenziale per ulteriori personalizzazioni:

```csharp
int defaultWorksheetIndex = 0;
```

## Passaggio 3: accedere alla cartella di lavoro dei dati del grafico

Per manipolare i dati del grafico, recupera la cartella di lavoro associata:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Passaggio 4: configurare la serie di grafici e aggiungere punti dati

Cancella le serie predefinite e aggiungi nuovi punti dati per le tue serie:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Aggiungere punti dati alla serie
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Passaggio 5: applicare i riempimenti delle immagini ai marcatori dei punti dati

Le immagini personalizzate possono rendere i marcatori di dati visivamente accattivanti:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Imposta immagini personalizzate per i marcatori
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Passaggio 6: personalizza la dimensione del marcatore

Modificare la dimensione dei marcatori per migliorarne la visibilità:

```csharp
series.Marker.Size = 20;
```

## Passaggio 7: Salva la presentazione aggiornata

Salva la presentazione personalizzata nella posizione desiderata:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Conclusione

Aspose.Slides per .NET fornisce agli sviluppatori gli strumenti per creare grafici professionali con ricche opzioni di personalizzazione. Sfruttando le opzioni dei marcatori dei grafici, puoi migliorare significativamente l'aspetto visivo e la chiarezza delle tue presentazioni. Questa guida passo passo assicura che anche le personalizzazioni complesse siano semplici da implementare.

## Domande frequenti

### Posso usare qualsiasi formato immagine per la personalizzazione del pennarello?
Sì, Aspose.Slides supporta vari formati di immagine, tra cui JPEG, PNG e BMP, per la personalizzazione dei marcatori.

### Come posso modificare il tipo di grafico dopo la creazione?
 Per cambiare il tipo di grafico, accedi a`chart.Type` proprietà e assegnarne una diversa`ChartType`.

### Aspose.Slides per .NET è compatibile con le versioni precedenti di PowerPoint?
Sì, supporta la retrocompatibilità con i vecchi formati di PowerPoint, garantendo versatilità.

### Posso aggiornare dinamicamente i dati del grafico?
 Assolutamente. Usa il`IChartDataWorkbook` per aggiornare programmaticamente i dati del grafico.

### Dove posso trovare altre risorse?
 Esplora il[Documentazione di Aspose.Slides](https://reference.aspose.com/slides/net/) unisciti al[forum della comunità](https://forum.aspose.com/) per supporto.