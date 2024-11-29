---
title: Conversione di XPS in PDF con Aspose.Page per .NET
linktitle: Conversione da XPS a PDF
second_title: API .NET di Aspose.Page
description: Scopri come convertire senza problemi i documenti XPS (XML Paper Specification) in PDF (Portable Document Format) utilizzando la potente libreria Aspose.Page per .NET.
type: docs
weight: 11
url: /it/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Introduzione

In questo tutorial, esploreremo come convertire i documenti XPS (XML Paper Specification) in PDF (Portable Document Format) utilizzando la versatile libreria Aspose.Page per .NET. Questa potente libreria semplifica la conversione dei documenti e offre varie opzioni di personalizzazione, rendendola un'eccellente scelta per gli sviluppatori.

## Prerequisiti

Prima di iniziare, assicurati di avere a disposizione quanto segue:

-  Libreria Aspose.Page per .NET: Scarica e installa la libreria Aspose.Page per .NET da[Documentazione di Aspose.Page](https://reference.aspose.com/page/net/).
  
- Ambiente di sviluppo: configurare un ambiente di sviluppo .NET utilizzando Visual Studio o un altro IDE compatibile.

- Documento XPS: tieni pronto il file XPS che desideri convertire, memorizzato in una directory designata.

## Passaggio 1: importare gli spazi dei nomi richiesti

Iniziamo importando lo spazio dei nomi necessario per accedere alle funzionalità di Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Passaggio 2: inizializzare la directory dei documenti

Definisci il percorso della directory in cui sono archiviati i tuoi documenti:

```csharp
string dataDir = "Your Document Directory";
```

 Assicurati di sostituire`"Your Document Directory"` con il percorso effettivo della directory contenente il documento XPS.

### Passaggio 3: aprire flussi PDF e XPS

Quindi, inizializza i flussi sia per il file XPS di input che per il file PDF di output:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Assicurati di aver impostato il percorso corretto per i tuoi file.

### Passaggio 4: caricare il documento XPS

Ora carica il tuo documento XPS utilizzando la libreria Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Passaggio 5: Configurare le opzioni di salvataggio PDF

Imposta le opzioni di salvataggio per il tuo PDF, inclusi i parametri di compressione e qualità dell'immagine:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Imposta il livello di qualità JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Utilizzare la compressione JPEG per le immagini
    TextCompression = PdfTextCompression.Flate, // Applica la compressione Flate per il testo
    PageNumbers = new int[] { 1, 2, 6 } // Specificare i numeri di pagina da includere
};
```

Sentitevi liberi di adattare questi parametri in base alle vostre esigenze.

### Passaggio 6: creare il dispositivo di rendering PDF

Crea un dispositivo di rendering per il formato PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Passaggio 7: Salvare il documento come PDF

Infine, salva il documento XPS in PDF utilizzando il dispositivo e le opzioni specificati:

```csharp
document.Save(device, options);
```

## Conclusione

Congratulazioni! Hai convertito con successo un documento XPS in PDF utilizzando Aspose.Page per .NET. Questa libreria non solo semplifica la conversione dei documenti, ma offre anche ampie capacità per la gestione di vari formati.

## Domande frequenti

### Posso convertire più file XPS in un unico PDF?

Assolutamente! Puoi scorrere più file XPS e unirli in un unico documento PDF seguendo gli stessi passaggi di conversione.

### Quali altri formati di output supporta Aspose.Page per .NET?

Oltre al PDF, Aspose.Page per .NET supporta una vasta gamma di formati, tra cui TIFF, JPEG e PNG.

### Come posso personalizzare l'aspetto del PDF convertito?

 È possibile regolare i parametri in`PdfSaveOptions` oggetto, come la qualità JPEG e le impostazioni di compressione, per ottenere l'aspetto desiderato.

### Esiste una versione di prova disponibile per Aspose.Page per .NET?

 Sì, puoi provare Aspose.Page per .NET con una versione di prova gratuita disponibile[Qui](https://releases.aspose.com/).

### Dove posso trovare supporto dalla community per Aspose.Page per .NET?

Per discussioni e supporto della comunità, visita il[Forum di Aspose.Page](https://forum.aspose.com/c/page/39).