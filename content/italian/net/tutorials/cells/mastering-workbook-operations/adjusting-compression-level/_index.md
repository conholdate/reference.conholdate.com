---
title: Regolazione del livello di compressione nella cartella di lavoro
linktitle: Regolazione del livello di compressione nella cartella di lavoro
second_title: API di elaborazione Excel .NET Aspose.Cells
description: Scopri come gestire in modo efficiente file Excel di grandi dimensioni regolando i livelli di compressione tramite Aspose.Cells per .NET. Questa guida passo passo copre tutto, dall'impostazione delle directory alla misurazione dei tempi di compressione, aiutandoti a ottimizzare le dimensioni dei file e a migliorare le prestazioni.
type: docs
weight: 14
url: /it/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Introduzione

Gestire file Excel di grandi dimensioni può essere una sfida, soprattutto quando si tratta di efficienza di archiviazione e trasferimento. Fortunatamente, la compressione dei file può ridurre significativamente le dimensioni di questi file, rendendoli più facili da gestire. Se utilizzi Aspose.Cells per .NET, hai la possibilità di regolare facilmente il livello di compressione delle tue cartelle di lavoro. Questa guida ti guiderà passo dopo passo nel processo, fornendo spiegazioni chiare di ogni parte del codice.

## Prerequisiti

Prima di immergerci nel codice, assicurati di disporre dei seguenti prerequisiti:

1. Conoscenza di base di C#: la familiarità con la programmazione C# ti aiuterà a comprendere meglio i frammenti di codice.
2.  Libreria Aspose.Cells: Scarica e installa la libreria Aspose.Cells da[Qui](https://releases.aspose.com/cells/net/).
3. Visual Studio: per eseguire il codice è necessario un ambiente di sviluppo come Visual Studio.
4. .NET Framework: assicurati che il tuo progetto sia configurato con una versione compatibile di .NET Framework.

## Importazione dei pacchetti necessari

Per iniziare, devi importare i pacchetti necessari nel tuo progetto C#. Aggiungi le seguenti righe all'inizio del tuo file di codice:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Questi pacchetti sono essenziali per lavorare con file Excel utilizzando la libreria Aspose.Cells.`Aspose.Cells` lo spazio dei nomi contiene tutte le classi necessarie per manipolare i file Excel, mentre`Aspose.Cells.Xlsb` fornisce opzioni per salvare i file nel formato XLSB.

## Passaggio 1: definire le directory di origine e di output

Per prima cosa, imposta le directory in cui si trovano i file sorgente e in cui desideri salvare i file di output:

```csharp
// Definire le directory di origine e di output
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Assicurati di sostituire`"Your Document Directory\\"` con i percorsi effettivi delle tue directory. Questo assicura che il tuo programma possa individuare i file con cui deve lavorare.

## Passaggio 2: caricare la cartella di lavoro

Quindi, carica la cartella di lavoro che vuoi comprimere:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Qui creiamo una nuova istanza di`Workbook` class e carica un file Excel esistente. Assicurati che il nome del file corrisponda a quello nella directory di origine.

## Passaggio 3: imposta le opzioni di salvataggio

Ora, configura le opzioni di salvataggio per la tua cartella di lavoro:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 IL`XlsbSaveOptions`La classe consente di specificare varie opzioni quando si salva la cartella di lavoro nel formato XLSB, inclusi i livelli di compressione.

## Fase 4: Misurare il tempo di compressione per il livello 1

Inizia con il primo livello di compressione e misura il tempo necessario per salvare la cartella di lavoro:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Questo frammento imposta il tipo di compressione su Livello 1, salva la cartella di lavoro e misura il tempo trascorso.

## Fase 5: Misurare il tempo di compressione per il livello 6

Successivamente, testa le prestazioni con la compressione di livello 6:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Questo passaggio è simile al precedente, ma con un livello di compressione più elevato.

## Fase 6: Misurare il tempo di compressione per il livello 9

Infine, valuta le prestazioni con il livello di compressione più elevato:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Questo passaggio imposta il livello di compressione al livello 9, dove probabilmente si noterà la riduzione più significativa delle dimensioni del file, anche se l'elaborazione potrebbe richiedere più tempo.

## Fase 7: Output finale

Dopo aver completato tutti i livelli di compressione, viene visualizzato un messaggio che indica che il processo è stato completato correttamente:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Questa semplice riga conferma che il programma è stato eseguito senza problemi.

## Conclusione

Regolare il livello di compressione delle cartelle di lavoro utilizzando Aspose.Cells per .NET è un processo semplice che può portare a miglioramenti significativi nelle dimensioni e nelle prestazioni dei file. Seguendo i passaggi descritti in questa guida, puoi implementare in modo efficiente la compressione nelle tue applicazioni, migliorando le tue capacità di gestione dei file Excel.

## Domande frequenti

### Che cos'è Aspose.Cells?  
Aspose.Cells è una potente libreria per .NET che consente agli sviluppatori di creare, manipolare e convertire file Excel senza dover utilizzare Microsoft Excel.

### Come faccio a installare Aspose.Cells?  
 Puoi scaricare e installare Aspose.Cells da[Sito web di Aspose](https://releases.aspose.com/cells/net/).

### Quali livelli di compressione sono disponibili?  
Aspose.Cells supporta più livelli di compressione, dal Livello 1 (compressione più bassa) al Livello 9 (compressione più alta).

### Posso provare Aspose.Cells gratuitamente?  
 Sì! Puoi ottenere una prova gratuita di Aspose.Cells[Qui](https://releases.aspose.com/).

### Dove posso trovare supporto per Aspose.Cells?  
 Per qualsiasi domanda o supporto, visita il forum di supporto di Aspose[Qui](https://forum.aspose.com/c/cells/9).