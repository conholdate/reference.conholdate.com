---
title: Creazione di un rettangolo riempito
linktitle: Creazione di un rettangolo riempito
second_title: Riferimento API Aspose.PDF per .NET
description: Sblocca la potenza della manipolazione PDF con Aspose.PDF per .NET in questo tutorial passo dopo passo. Scopri come creare a livello di programmazione documenti PDF visivamente accattivanti disegnando rettangoli pieni.
type: docs
weight: 50
url: /it/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Introduzione

Hai mai desiderato creare PDF visivamente sbalorditivi tramite programmazione? Se sì, sei nel posto giusto! In questo tutorial, esploreremo Aspose.PDF per .NET, una potente libreria che semplifica la manipolazione dei documenti PDF. Oggi, ci concentreremo sulla creazione di un rettangolo riempito all'interno di un file PDF. Che tu sia uno sviluppatore esperto o alle prime armi, questa guida ti guiderà attraverso ogni passaggio in modo amichevole e coinvolgente. Quindi, prendi il tuo cappello da programmatore e iniziamo!

## Prerequisiti

Prima di immergerci nel codice, assicurati di avere quanto segue:

1. Visual Studio: installa Visual Studio sul tuo computer, poiché è un IDE eccellente per lo sviluppo .NET.
2. Aspose.PDF per .NET: Scarica e installa la libreria Aspose.PDF da[Qui](https://releases.aspose.com/pdf/net/).
3. Conoscenza di base di C#: la familiarità con la programmazione C# ti aiuterà a comprendere meglio i frammenti di codice.

## Passaggio 1: creare un nuovo progetto

1. Aprire Visual Studio e creare un nuovo progetto di applicazione console.
2. Assegna un nome appropriato al tuo progetto.

## Passaggio 2: aggiungere il riferimento Aspose.PDF

1. Fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.
2. Selezionare Gestisci pacchetti NuGet.
3. Cerca Aspose.PDF e installa la versione più recente.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Ora che abbiamo impostato tutto, tuffiamoci nel codice!

## Passaggio 3: imposta la directory dei documenti

Specifica il percorso in cui verrà salvato il tuo PDF:

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo sul tuo computer in cui desideri salvare il PDF.

## Passaggio 4: creare un'istanza di documento

Inizializza un nuovo documento PDF:

```csharp
// Crea istanza del documento
Document doc = new Document();
```

## Passaggio 5: aggiungere una pagina al documento

Ogni PDF ha bisogno di almeno una pagina. Aggiungiamone una:

```csharp
// Aggiungi pagina alla raccolta di pagine del file PDF
Page page = doc.Pages.Add();
```

## Passaggio 6: creare un'istanza del grafico

 UN`Graph` l'istanza funge da tela per disegnare forme:

```csharp
// Crea istanza del grafico
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Passaggio 7: aggiungere il grafico alla pagina

Allega il grafico alla pagina:

```csharp
// Aggiungere l'oggetto grafico alla raccolta di paragrafi dell'istanza di pagina
page.Paragraphs.Add(graph);
```

## Passaggio 8: creare un'istanza rettangolare

Definisci la posizione e la dimensione del rettangolo:

```csharp
// Crea istanza Rectangle
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Passaggio 9: specificare il colore di riempimento

Scegli un colore per il tuo rettangolo. Per questo esempio, useremo il rosso:

```csharp
// Specificare il colore di riempimento per l'oggetto grafico
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Passaggio 10: aggiungere il rettangolo al grafico

Aggiungi il rettangolo al grafico:

```csharp
// Aggiungi oggetto rettangolo alla raccolta di forme dell'oggetto Graph
graph.Shapes.Add(rect);
```

## Passaggio 11: Salvare il documento PDF

Infine, salva il documento nella directory specificata:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Salva file PDF
doc.Save(dataDir);
```

## Passaggio 12: messaggio di conferma

Stampa un messaggio di conferma per indicare il successo:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Conclusione

Congratulazioni! Hai creato con successo un rettangolo riempito in un documento PDF usando Aspose.PDF per .NET. Questa potente libreria apre un mondo di possibilità per la manipolazione di PDF, consentendoti di generare documenti sbalorditivi a livello di programmazione. Che tu stia creando report, fatture o qualsiasi altro tipo di PDF, Aspose.PDF ti copre.

## Domande frequenti

### Che cos'è Aspose.PDF per .NET?
Aspose.PDF per .NET è una libreria che consente agli sviluppatori di creare, manipolare e convertire documenti PDF a livello di programmazione.

### Posso usare Aspose.PDF gratuitamente?
 Sì, Aspose offre una versione di prova gratuita che puoi usare per esplorare le funzionalità della libreria. Puoi scaricarla[Qui](https://releases.aspose.com/).

### Esiste un modo per ottenere supporto per Aspose.PDF?
 Assolutamente! Puoi ottenere supporto tramite il forum Aspose[Qui](https://forum.aspose.com/c/pdf/10).

### Come posso acquistare Aspose.PDF?
 Puoi acquistare Aspose.PDF visitando la pagina di acquisto[Qui](https://purchase.aspose.com/buy).

### Quali tipi di forme posso creare con Aspose.PDF?
Utilizzando la libreria Aspose.PDF è possibile creare varie forme, tra cui rettangoli, cerchi, linee e altro ancora.