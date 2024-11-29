---
title: Padroneggiare la manipolazione dei file DGN con Aspose.CAD in .NET
linktitle: Padroneggiare la manipolazione dei file DGN
second_title: Aspose.CAD .NET - Formato file CAD e BIM
description: Scopri come caricare file DGN, scorrere i loro elementi, gestire entità 2D e 3D ed esportarle come immagini raster, sfruttando al contempo le potenti funzionalità della libreria Aspose.CAD.
type: docs
weight: 18
url: /it/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Introduzione

Sei uno sviluppatore .NET desideroso di integrare file DGN nelle tue applicazioni? Aspose.CAD per .NET offre una potente libreria progettata specificamente per lavorare con formati di file DGN. In questo tutorial, esploreremo come gestire in modo efficiente i file DGN, inclusi gli elementi supportati e come manipolarli nei tuoi progetti .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere la seguente configurazione:

- Conoscenza di base della programmazione .NET: sarà utile avere familiarità con C# o VB.NET.
- Visual Studio: installato sul computer per lo sviluppo del progetto.
-  Libreria Aspose.CAD per .NET: scaricala da[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Passaggio 1: importare gli spazi dei nomi necessari

Per sfruttare le funzionalità di Aspose.CAD, inizia importando gli spazi dei nomi richiesti nel tuo progetto.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Passaggio 2: carica il file DGN

 Inizia caricando un file DGN esistente nella tua applicazione. Questo viene fatto istanziando un`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Procedi con la tua logica qui
}
```

## Passaggio 3: scorrere gli elementi DGN

Una volta caricato il file DGN, puoi scorrere i suoi elementi. Aspose.CAD fornisce una varietà di tipi di elementi DGN per la tua manipolazione.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Elaborare ogni elemento
}
```

## Passaggio 4: Gestire entità 2D e 3D

È possibile distinguere tra elementi DGN 2D e 3D. Di seguito è riportato come gestirli in modo efficiente:

### Gestire entità 2D

È possibile gestire le entità 2D precedentemente supportate con un blocco switch-case.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Aggiungi qui la tua logica di elaborazione
        break;
}
```

### Gestire entità 3D

Allo stesso modo, gestisci le entità 3D come segue:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Aggiungi qui la tua logica di elaborazione
        break;
}
```

## Passaggio 5: esportare il file DGN

Dopo aver manipolato gli elementi DGN, potresti voler esportare il file come immagine raster. Ciò può essere facilmente ottenuto con Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Definisci il tuo percorso di output
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Conclusione

In questo tutorial, abbiamo imparato come usare Aspose.CAD per .NET per gestire in modo efficace i file DGN. Seguendo i passaggi descritti, puoi gestire senza sforzo sia gli elementi DGN 2D che 3D ed esportarli come immagini raster. Questa potente libreria consente un'integrazione senza soluzione di continuità dell'elaborazione DGN nelle tue applicazioni .NET, migliorando le capacità del tuo progetto.

## Domande frequenti

### Dove posso trovare la documentazione per Aspose.CAD per .NET?

 La documentazione completa è disponibile[Qui](https://reference.aspose.com/cad/net/).

### Come posso scaricare Aspose.CAD per .NET?

 Puoi scaricare l'ultima versione della libreria[Qui](https://releases.aspose.com/cad/net/).

### È disponibile una prova gratuita di Aspose.CAD per .NET?

 Sì, è disponibile una prova gratuita[Qui](https://releases.aspose.com/).

### Come posso ottenere licenze temporanee per Aspose.CAD per .NET?

 Puoi richiedere licenze temporanee[Qui](https://purchase.conholdate.com/temporary-license/).

### Hai bisogno di aiuto o hai domande?

Per supporto o per porre domande, visita la community Aspose.CAD[forum di supporto](https://forum.aspose.com/c/cad/19).