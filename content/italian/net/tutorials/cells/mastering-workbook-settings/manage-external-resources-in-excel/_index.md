---
title: Gestire le risorse esterne in Excel con Aspose.Cells per .NET
linktitle: Gestire le risorse esterne in Excel con Aspose.Cells per .NET
second_title: API di elaborazione Excel .NET Aspose.Cells
description: Scopri come controllare senza problemi le risorse esterne nelle cartelle di lavoro di Excel utilizzando Aspose.Cells per .NET. Questa guida completa ti accompagna in ogni passaggio, dall'implementazione di un provider di flussi personalizzato al rendering dei fogli di lavoro.
type: docs
weight: 10
url: /it/net/tutorials/cells/mastering-workbook-settings/manage-external-resources-in-excel/
---
## Introduzione

Quando si lavora con i dati in Excel, la gestione fluida delle risorse esterne può migliorare notevolmente la funzionalità della tua applicazione. Se stai cercando di controllare immagini e altri elementi esterni nelle cartelle di lavoro di Excel utilizzando Aspose.Cells per .NET, sei nel posto giusto! Questa guida ti guiderà passo dopo passo nel processo, consentendoti di implementare una soluzione personalizzata per gestire queste risorse senza sforzo.

## Prerequisiti

Prima di addentrarci negli aspetti della codifica, assicurati di aver impostato quanto segue:

1. Visual Studio: un IDE per scrivere e testare le tue applicazioni .NET. Visual Studio è consigliato per il suo ampio supporto e l'interfaccia intuitiva.
2.  Aspose.Cells per .NET: Scarica la libreria da[Pagina di rilascio di Aspose Cells](https://releases.aspose.com/cells/net/).
3. Conoscenza di base di C#: la familiarità con i concetti di C# e .NET ti aiuterà a comprendere meglio l'implementazione.
4. Imposta il tuo progetto: assicurati che il tuo progetto faccia riferimento alla libreria Aspose.Cells, che puoi aggiungere tramite NuGet Package Manager in Visual Studio.
5. File di esempio: tenere pronto un file Excel di esempio contenente risorse esterne (ad esempio immagini collegate) a scopo dimostrativo.

Una volta soddisfatti tutti questi prerequisiti, possiamo iniziare a gestire le risorse esterne con Aspose.Cells.

## Importa pacchetti
Per iniziare a programmare, dovrai importare i pacchetti necessari nel tuo file C#. Ecco cosa ti serve:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

## Passaggio 1: definire le directory

Per prima cosa, specifica le directory di origine e di output in cui sono archiviati i file e dove desideri che vengano salvati i file di output.

```csharp
// Definire la directory di origine
static string sourceDir = @"C:\Path\To\Your\Documents\"; // Personalizza il percorso
// Definire la directory di output
static string outputDir = @"C:\Path\To\Your\Output\";
```

Assicuratevi di sostituire i percorsi con le directory effettive presenti sul vostro computer.

### Passaggio 2: implementare l'interfaccia IStreamProvider

 Successivamente, crea una classe personalizzata che implementa il`IStreamProvider` interfaccia. Questa classe gestirà il modo in cui si accede alle risorse esterne come le immagini.

```csharp
class CustomStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        // Pulisci le risorse se necessario
        options.Stream?.Close();
    }

    public void InitStream(StreamProviderOptions options)
    {
        // Aprire il flusso di file per la risorsa esterna
        options.Stream = new FileStream(Path.Combine(sourceDir, "image.png"), FileMode.Open, FileAccess.Read);
    }
}
```

 Nel`InitStream` metodo, apriamo il file che funge da risorsa esterna e lo assegniamo al`Stream` proprietà.

### Passaggio 3: caricare il file Excel

Carichiamo ora la cartella di lavoro di Excel che include la risorsa esterna.

```csharp
public static void Execute()
{
    // Carica il file Excel
    Workbook workbook = new Workbook(Path.Combine(sourceDir, "sample.xlsx"));
    
    // Assegna il provider di streaming personalizzato
    workbook.Settings.StreamProvider = new CustomStreamProvider();
```

Questo frammento carica il file Excel e assegna il provider di flusso personalizzato per la gestione delle risorse esterne.

### Passaggio 4: accedi al foglio di lavoro

Dopo aver caricato la cartella di lavoro, accedi facilmente al foglio di lavoro desiderato.

```csharp
    // Accedi al primo foglio di lavoro
    Worksheet worksheet = workbook.Worksheets[0];
```

È possibile accedere a qualsiasi foglio di lavoro specificandone l'indice.

### Passaggio 5: configurare le opzioni di immagine e stampa

Definisci l'aspetto desiderato dell'immagine di output configurando le opzioni di immagine o di stampa.

```csharp
    // Specificare le opzioni di immagine o stampa
    ImageOrPrintOptions options = new ImageOrPrintOptions
    {
        OnePagePerSheet = true,
        ImageType = Drawing.ImageType.Png
    };
```

Scegliendo PNG si ottiene un output nitido e chiaro.

### Passaggio 6: Trasforma il foglio di lavoro in un'immagine

Adesso arriva la parte emozionante: trasformare il foglio di lavoro in un file immagine!

```csharp
    // Crea un rendering del foglio e converti il foglio di lavoro in un'immagine
    SheetRender sheetRender = new SheetRender(worksheet, options);
    sheetRender.ToImage(0, Path.Combine(outputDir, "output.png"));
    
    Console.WriteLine("Excel sheet rendered successfully to an image!");
}
```

Questo codice converte l'intero foglio di lavoro in un'immagine PNG, che verrà salvata nella directory di output specificata.

## Conclusione

Congratulazioni! Ora hai imparato come controllare le risorse esterne nei file Excel usando Aspose.Cells per .NET. Questa funzionalità non solo migliora le capacità della tua applicazione, ma semplifica anche il modo in cui gestisci set di dati e presentazioni. Seguendo i passaggi descritti sopra, puoi adattare questa soluzione per adattarla ai requisiti unici del tuo progetto.

## Domande frequenti

### Che cos'è Aspose.Cells?
Aspose.Cells è una libreria solida progettata per consentire agli sviluppatori .NET di creare, manipolare e gestire file Excel senza dover usare Microsoft Excel.

### Come posso scaricare Aspose.Cells per .NET?
 Puoi scaricarlo da[Sito web di Aspose](https://releases.aspose.com/cells/net/).

### È disponibile una prova gratuita?
 Sì! Aspose offre una prova gratuita di Aspose.Cells, disponibile sul loro[pagina di rilascio](https://releases.aspose.com/cells/net/).

### Quali tipi di file supporta Aspose.Cells?
Aspose.Cells supporta vari formati Excel, tra cui XLS, XLSX, CSV e altri.

### Dove posso trovare supporto per Aspose.Cells?
 Visita il[Forum di Aspose](https://forum.aspose.com/c/cells/9) per assistenza e supporto alla comunità.