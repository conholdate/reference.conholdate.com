---
title: Aggiungere Java Script al file PDF
linktitle: Aggiungi file PDF Java Script
second_title: Riferimento API Aspose.PDF per .NET
description: Questo documento fornisce una guida completa su come aggiungere elementi interattivi, come avvisi pop-up o funzioni di stampa automatica, ai documenti PDF utilizzando Aspose.PDF per .NET.
type: docs
weight: 10
url: /it/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## Introduzione
Questo documento fornisce una guida completa per aggiungere elementi interattivi come avvisi pop-up o funzioni di stampa automatica ai documenti PDF utilizzando Aspose.PDF per .NET. Sfruttando le capacità di questa libreria, puoi creare PDF dinamici e coinvolgenti che soddisfano le varie esigenze degli utenti.

## Prerequisiti
 Prima di procedere, assicurati di aver scaricato l'ultima versione di Aspose.PDF per .NET da[Rilasci di Aspose](https://releases.aspose.com/pdf/net/) oppure ottenuto una prova gratuita tramite il loro sito web:[releases.aspose.com](http://releases.aspose.com).

Dovresti anche avere una conoscenza di base di C# e avere familiarità con l'ambiente di sviluppo che stai utilizzando. Inoltre, se hai bisogno di evitare limitazioni durante il tuo processo di sviluppo, prendi in considerazione l'acquisto di una licenza temporanea da Aspose.

## Importazione dei pacchetti necessari
Per iniziare a scrivere il codice, importare gli spazi dei nomi richiesti dalla libreria Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Passaggio 1: caricamento di un PDF esistente
Carica un documento PDF esistente a cui desideri aggiungere elementi interattivi:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo del file PDF.

## Passaggio 2: aggiunta di JavaScript a livello di documento

 Per applicare uno script che si attiva all'apertura del documento, creare un'istanza di`JavascriptAction` oggetto:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Passaggio 3: aggiunta di JavaScript a livello di pagina

 Per attivare azioni specifiche in base all'apertura o alla chiusura delle pagine, creare un'istanza di`JavascriptAction` oggetto per ogni pagina:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Passaggio 4: salvataggio del documento PDF

Per salvare il documento PDF modificato, specificare il percorso del file di output:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Conclusione
Seguendo questa guida e utilizzando Aspose.PDF per .NET, puoi migliorare efficacemente i tuoi PDF con elementi interattivi. Questa libreria offre una soluzione completa per creare documenti dinamici e coinvolgenti che soddisfano le varie esigenze degli utenti.

## Domande frequenti

### Posso aggiungere più azioni JavaScript a pagine diverse di un PDF?
Sì, puoi assegnare diverse azioni JavaScript a singole pagine o all'intero documento.

### È possibile rimuovere JavaScript da un PDF dopo averlo aggiunto?
 Sì, puoi rimuovere o modificare le azioni JavaScript esistenti cancellando il`Actions` proprietà del documento o della pagina.

### Quali tipi di funzioni JavaScript posso utilizzare in un PDF?
È possibile utilizzare qualsiasi codice JavaScript supportato dal motore JavaScript di Adobe Acrobat, ad esempio per la stampa, gli avvisi e la manipolazione dei moduli.

### JavaScript funziona in tutti i visualizzatori PDF?
La maggior parte delle azioni JavaScript funzionerà nei visualizzatori PDF che supportano PDF interattivi, come Adobe Acrobat. Tuttavia, alcuni lettori PDF di base potrebbero non supportare JavaScript.