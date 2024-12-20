---
title: Crea 1Bpp indicizzato
linktitle: Crea 1Bpp indicizzato
second_title: API di elaborazione dei documenti Aspose.Words
description: Questa guida fornisce istruzioni dettagliate e codice di esempio per aiutarti a creare in modo efficiente immagini indicizzate 1Bpp per scopi di archiviazione, stampa o risparmio di spazio.
type: docs
weight: 10
url: /it/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Introduzione

Hai mai avuto bisogno di convertire un documento Word in un'immagine in bianco e nero? Che si tratti di archiviazione digitale, stampa o semplicemente di risparmiare spazio, convertire i tuoi documenti in un'immagine indicizzata 1Bpp può essere incredibilmente utile. In questa guida, ti mostreremo un metodo semplice per ottenere questo risultato utilizzando Aspose.Words per .NET. Cominciamo!

## Prerequisiti

Prima di immergerti nel codice, assicurati di avere quanto segue:

-  Aspose.Words per .NET: Scarica e installa la libreria da[Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo .NET: sebbene Visual Studio sia una scelta popolare, funzionerà qualsiasi IDE che supporti .NET.
- Conoscenza di base del linguaggio C#: la familiarità con il linguaggio C# sarà utile, ma semplificheremo le cose.
- Esempio di documento Word: prepara un documento per la conversione.

## Passaggio 1: importare gli spazi dei nomi necessari

Per usare Aspose.Words, devi importare i namespace rilevanti. Questo è essenziale per accedere alle classi e ai metodi richiesti per la manipolazione dei documenti.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 2: imposta la directory dei documenti

Specificare il percorso della directory in cui è archiviato il documento Word e dove si desidera salvare l'immagine convertita.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Passaggio 3: caricare il documento Word

Carica il tuo documento Word in un`Aspose.Words.Document` oggetto. Questo oggetto consente di manipolare il documento a livello di programmazione.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 4: configurare le opzioni di salvataggio dell'immagine

 Quindi, imposta il`ImageSaveOptions` per definire come il documento verrà salvato come immagine. Lo configureremo per salvare in formato PNG con modalità colore indicizzato 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Converti solo la prima pagina
    ImageColorMode = ImageColorMode.BlackAndWhite, // Impostato su bianco e nero
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Utilizzare il formato indicizzato 1Bpp
};
```

- SaveFormat.Png: specifica che il formato di output sarà PNG.
- PageSet(1): indica che verrà convertita solo la prima pagina del documento.
- ImageColorMode.BlackAndWhite: assicura che l'immagine sia in bianco e nero.
- ImagePixelFormat.Format1bppIndexed: imposta il formato pixel su indicizzato a 1 Bpp, ottimizzando lo spazio.

## Passaggio 5: salvare il documento come immagine

 Infine, utilizzare il`Save` metodo del`Document` oggetto per salvare l'immagine convertita.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Conclusione

Congratulazioni! Hai convertito con successo un documento Word in un'immagine indicizzata 1Bpp usando Aspose.Words per .NET. Questo metodo non è solo efficiente, ma ti aiuta anche a creare immagini ad alto contrasto adatte a varie applicazioni. Sentiti libero di integrare questa funzionalità nei tuoi progetti. Buona codifica!

## Domande frequenti

### Cos'è un'immagine indicizzata 1Bpp?
Un'immagine indicizzata a 1 Bpp (1 bit per pixel) è un formato di immagine in bianco e nero in cui ogni pixel è rappresentato da un singolo bit, 0 o 1. Questo formato è altamente efficiente in termini di spazio, il che lo rende ideale per l'archiviazione.

### Posso convertire più pagine di un documento Word contemporaneamente?
 Sì! Basta modificare il`PageSet` proprietà nella`ImageSaveOptions` per includere più pagine o impostarlo per convertire l'intero documento.

### Ho bisogno di una licenza per utilizzare Aspose.Words per .NET?
 Sì, è richiesta una licenza per la piena funzionalità. Puoi ottenere una[licenza temporanea qui](https://purchase.aspose.com/temporary-license/).

### In quali altri formati immagine posso convertire il mio documento Word?
 Aspose.Words supporta vari formati, tra cui JPEG, BMP e TIFF. Basta cambiare il`SaveFormat` nel`ImageSaveOptions`nel formato desiderato.

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?
 Per una documentazione completa, visitare il[Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).