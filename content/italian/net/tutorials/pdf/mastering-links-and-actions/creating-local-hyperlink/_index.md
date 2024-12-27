---
title: Creazione di un collegamento ipertestuale locale nel file PDF
linktitle: Creazione di un collegamento ipertestuale locale nel file PDF
second_title: Riferimento API Aspose.PDF per .NET
description: Scopri come migliorare la navigazione nei tuoi documenti PDF creando collegamenti ipertestuali locali usando Aspose.PDF per .NET. Questo tutorial passo dopo passo ti guida attraverso l'intero processo.
type: docs
weight: 40
url: /it/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Introduzione

In questa guida, ti guideremo attraverso il processo di creazione di collegamenti ipertestuali locali in un file PDF utilizzando Aspose.PDF per .NET. Analizzeremo ogni passaggio in modo chiaro, assicurandoti che anche se sei alle prime armi con la manipolazione di PDF, sarai in grado di seguire senza sforzo.

## Prerequisiti

Prima di immergerti nel codice, assicurati di avere quanto segue:

1.  Visual Studio: scaricalo da[Sito web di Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.PDF per .NET: Scarica la libreria tramite[Sito web di Aspose](https://releases.aspose.com/pdf/net/)Questa libreria fornisce un ricco set di funzionalità per la manipolazione dei PDF.
3. Conoscenza di base di C#: la familiarità con la programmazione C# sarà utile, ma non preoccuparti: spiegheremo il codice riga per riga.
4. .NET Framework: assicurati di avere .NET Framework installato sul tuo computer. Controlla i requisiti su Aspose.PDF[documentazione](https://reference.aspose.com/pdf/net/).

Con questi prerequisiti, sei pronto per imparare a creare collegamenti ipertestuali locali nei tuoi documenti PDF!

## Importazione dei pacchetti richiesti

Ora che hai impostato tutto, è il momento di importare i pacchetti necessari nel tuo progetto C#.

### Apri il tuo progetto

Apri il tuo progetto .NET esistente o creane uno nuovo in Visual Studio. Se stai iniziando da zero, seleziona "Crea un nuovo progetto" dalla schermata di avvio.

### Aggiungi riferimento a Aspose.PDF

 Fai clic con il pulsante destro del mouse su "Dependencies" nella cartella del progetto in Solution Explorer. Seleziona "Manage NuGet Packages", cerca`Aspose.PDF`, e installa l'ultima versione disponibile. Questo ti fornirà tutti gli strumenti di cui hai bisogno per creare e manipolare i PDF.

### Importazione degli spazi dei nomi

Nella parte superiore del file .cs, aggiungi le seguenti direttive using:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Queste direttive consentono di accedere alle funzionalità della libreria senza problemi.

Scomponiamo il processo di creazione di collegamenti ipertestuali locali in semplici passaggi.

## Passaggio 1: impostare l'istanza del documento

 Crea una nuova istanza di`Document` classe, che rappresenta il file PDF con cui lavorerai.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Imposta la directory dei tuoi documenti
Document doc = new Document(); // Crea istanza del documento
```

 Sostituire`"YOUR_DOCUMENT_DIRECTORY"` con il percorso effettivo sul tuo sistema in cui verrà salvato il PDF.

## Passaggio 2: aggiungere una pagina al documento

Successivamente, aggiungi una pagina al tuo documento PDF.

```csharp
Page page = doc.Pages.Add(); // Aggiungi una nuova pagina
```

Questa riga aggiunge una nuova pagina al documento, in cui verranno inseriti tutti i tuoi contenuti.

## Passaggio 3: creare un frammento di testo

Ora creiamo un pezzo di testo che fungerà da collegamento cliccabile.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Crea un frammento di testo
```

 Questo`TextFragment` visualizzerà il testo su cui gli utenti potranno cliccare.

## Passaggio 4: creare un collegamento ipertestuale locale

Ora, crea un collegamento ipertestuale locale che punti alla pagina 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Crea un collegamento ipertestuale locale
link.TargetPageNumber = 7; // Imposta la pagina di destinazione per il collegamento
text.Hyperlink = link; // Imposta l'hyperlink per il frammento di testo
```

 IL`LocalHyperlink` La classe consente di specificare il numero di pagina di destinazione per il collegamento ipertestuale.

## Passaggio 5: aggiungere il frammento di testo alla pagina

Aggiungi il testo cliccabile alla pagina che hai creato.

```csharp
page.Paragraphs.Add(text); // Aggiungi il frammento di testo alla pagina
```

Questa riga aggiunge il testo alla raccolta di paragrafi della pagina.

## Passaggio 6: creare un altro frammento di testo (facoltativo)

Aggiungiamo un altro collegamento ipertestuale per tornare alla pagina 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Crea un nuovo frammento di testo
textBack.IsInNewPage = true; // Indica che dovrebbe essere su una nuova pagina
```

## Passaggio 7: impostare il secondo collegamento ipertestuale locale

Crea un altro collegamento ipertestuale locale per la pagina 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Crea un altro collegamento ipertestuale locale
linkBack.TargetPageNumber = 1; // Imposta la pagina di destinazione per il secondo collegamento ipertestuale
textBack.Hyperlink = linkBack; // Imposta l'hyperlink per il secondo frammento di testo
```

## Passaggio 8: aggiungere il secondo frammento di testo alla nuova pagina

Aggiungere il secondo frammento di testo alla sua pagina.

```csharp
Page newPage = doc.Pages.Add(); // Aggiungi una nuova pagina per il secondo collegamento
newPage.Paragraphs.Add(textBack); // Aggiungi il frammento di testo alla nuova pagina
```

## Passaggio 9: Salvare il documento

Infine, salva il documento.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Specificare il nome del file di output
doc.Save(dataDir); // Salva il documento aggiornato
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Questa riga combina il percorso della directory con il nome del file e il`Save()` metodo salva il documento.

## Conclusione

Creare collegamenti ipertestuali locali nei file PDF usando Aspose.PDF per .NET è una funzionalità pratica che migliora la navigazione e l'esperienza utente. Ora hai le conoscenze per guidare i tuoi lettori direttamente alle informazioni di cui hanno bisogno, rendendo i tuoi PDF più interattivi e intuitivi.

## Domande frequenti

### Che cos'è Aspose.PDF per .NET?
Aspose.PDF per .NET è una libreria che consente agli sviluppatori di creare, manipolare e convertire documenti PDF a livello di programmazione utilizzando il framework .NET.

### Posso creare collegamenti ipertestuali a pagine web esterne?
Sì, Aspose.PDF supporta anche la creazione di collegamenti ipertestuali a URL esterni oltre ai collegamenti ipertestuali locali all'interno del PDF.

### Esiste una prova gratuita per Aspose.PDF?
 Assolutamente! Puoi accedere alla prova gratuita da[Sito web di Aspose](https://releases.aspose.com/).

### Quali linguaggi di programmazione supporta Aspose?
Aspose offre librerie per vari linguaggi di programmazione, tra cui Java, C++e Python, tra gli altri.

### Come posso ottenere supporto per i prodotti Aspose?
 Puoi cercare supporto tramite[Forum di Aspose](https://forum.aspose.com/c/pdf/10).