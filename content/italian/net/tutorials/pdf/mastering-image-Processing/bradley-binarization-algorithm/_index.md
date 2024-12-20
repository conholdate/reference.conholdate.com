---
title: Algoritmo di binarizzazione di Bradley
linktitle: Algoritmo di binarizzazione di Bradley
second_title: Riferimento API Aspose.PDF per .NET
description: Scopri come convertire le pagine PDF in immagini TIFF binarie di alta qualità utilizzando l'algoritmo di binarizzazione Bradley in Aspose.PDF per .NET. Questa guida passo passo include un esempio di codice.
type: docs
weight: 30
url: /it/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Introduzione

In questo tutorial, ti guideremo attraverso il processo di conversione di una pagina PDF in un'immagine TIFF utilizzando l'algoritmo di binarizzazione Bradley. Aspose.PDF per .NET semplifica questa attività, consentendoti di automatizzare e semplificare i flussi di lavoro dei tuoi documenti con facilità.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

-  Aspose.PDF per .NET: Scarica la libreria da[Qui](https://releases.aspose.com/pdf/net/).
- Visual Studio (o qualsiasi IDE C#).
- Conoscenza di base di C#.
-  Una licenza valida o una[licenza temporanea](https://purchase.aspose.com/temporary-license/) da Aspose.

## Passaggio 1: imposta il tuo progetto

Per prima cosa, crea un nuovo progetto C# nel tuo IDE e importa gli spazi dei nomi necessari:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Passaggio 2: definire la directory dei documenti

Specificare il percorso della directory in cui si trova il documento PDF, nonché i percorsi di output per le immagini TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Percorso al tuo file PDF
```

In questa directory verranno salvati sia il PDF di origine sia i file TIFF convertiti.

## Passaggio 3: caricare il documento PDF

Apri il documento PDF che vuoi convertire:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Sostituire`PageToTIFF.pdf` con il nome del tuo file PDF.

## Passaggio 4: specificare i percorsi di output

Definire i percorsi di output per i file TIFF generati:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Passaggio 5: imposta la risoluzione dell'immagine

Imposta la risoluzione per le immagini TIFF. Un DPI più alto produrrà una migliore qualità dell'immagine:

```csharp
Resolution resolution = new Resolution(300);
```

## Passaggio 6: configurare le impostazioni TIFF

Configurare le impostazioni per l'immagine TIFF, tra cui compressione e profondità del colore:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Utilizzando 1 bpp (1 bit per pixel) si prepara l'immagine per l'output binario.

## Passaggio 7: creare il dispositivo TIFF

Creare un dispositivo TIFF che gestirà la conversione:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Passaggio 8: Convertire la pagina PDF in TIFF

Converti la prima pagina del PDF in un'immagine TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Passaggio 9: applicare l'algoritmo di binarizzazione di Bradley

Ora, applichiamo l'algoritmo di Bradley per convertire l'immagine TIFF in scala di grigi in un'immagine binaria:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 IL`BinarizeBradley` Il metodo prende due flussi di file (input e output) e un valore di soglia. Regola la soglia come necessario per risultati ottimali.

## Passaggio 10: conferma della conversione riuscita

Infine, verifica che la conversione sia avvenuta correttamente:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Conclusione

Congratulazioni! Hai convertito con successo una pagina PDF in un'immagine TIFF e applicato l'algoritmo di binarizzazione Bradley utilizzando Aspose.PDF per .NET. Questo processo è essenziale per l'archiviazione di documenti, l'OCR e altre applicazioni professionali. Con una risoluzione di alta qualità e una compressione efficiente, le immagini dei tuoi documenti saranno chiare e di dimensioni gestibili.

## Domande frequenti

### Che cos'è l'algoritmo di Bradley?
L'algoritmo di Bradley è una tecnica di binarizzazione che converte le immagini in scala di grigi in immagini binarie determinando una soglia adattiva per ciascun pixel in base all'ambiente circostante.

### Posso convertire più pagine PDF in TIFF utilizzando questo metodo?
 Sì, puoi modificare il`Process` Metodo per scorrere tutte le pagine del documento ai fini della conversione.

### Qual è la risoluzione ottimale per convertire i PDF in TIFF?
In genere, per immagini di alta qualità si consiglia una risoluzione di 300 DPI, ma è possibile modificarla in base alle proprie esigenze specifiche.

### Cosa significa 1 bpp in termini di profondità colore?
bpp (1 bit per pixel) indica che l'immagine sarà in bianco e nero, con ogni pixel completamente nero o completamente bianco.

### L'algoritmo Bradley è adatto per l'OCR?
Sì, l'algoritmo Bradley viene spesso utilizzato nella pre-elaborazione OCR perché migliora il contrasto del testo nei documenti scansionati, migliorando la precisione del riconoscimento.