---
title: Estrarre il testo evidenziato dai PDF utilizzando Aspose.PDF per .NET
linktitle: Estrarre il testo evidenziato dai PDF utilizzando Aspose.PDF per .NET
second_title: Riferimento API Aspose.PDF per .NET
description: Sblocca il potenziale dei tuoi documenti PDF imparando come estrarre il testo evidenziato con Aspose.PDF per .NET. Questa guida completa ti accompagna in ogni passaggio, dalla configurazione all'implementazione.
type: docs
weight: 60
url: /it/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## Introduzione

Quando si lavora con file PDF, l'estrazione del testo evidenziato può essere essenziale per l'analisi dei dati, la revisione dei contenuti o l'organizzazione delle note. Se si utilizza Aspose.PDF per .NET, si è fortunati. Questo tutorial fornisce istruzioni chiare e dettagliate su come estrarre in modo efficiente il testo evidenziato da un documento PDF.

## Prerequisiti

Prima di iniziare, assicurati di avere a disposizione quanto segue:

-  Aspose.PDF per la libreria .NET: Scarica la libreria da[pagina di rilascio](https://releases.aspose.com/pdf/net/).
- Ambiente di sviluppo: un ambiente di lavoro come Visual Studio.
- Conoscenza di base di C#: è necessaria familiarità con C# e con la programmazione orientata agli oggetti.
-  Licenza Aspose: sebbene sia possibile iniziare con una prova gratuita,[licenza temporanea](https://purchase.aspose.com/temporary-license/) o una licenza completa da[Qui](https://purchase.aspose.com/buy) fornirà un accesso illimitato.

## Importa gli spazi dei nomi necessari

Inizia importando gli spazi dei nomi richiesti nel tuo progetto C#:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Questi namespace forniscono l'accesso alle classi e ai metodi necessari per gestire i documenti PDF e le annotazioni.

## Passaggio 1: imposta la directory del progetto

Specifica la directory in cui si trova il tuo file PDF:

```csharp
// Percorso alla directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Assicurati di sostituire il percorso con la directory effettiva del tuo file PDF.

## Passaggio 2: caricare il documento PDF

Carica il documento PDF con il seguente codice:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Assicurarsi che il file specificato esista nella directory indicata.

## Passaggio 3: accedere alle annotazioni sulla pagina

Per accedere alle annotazioni, scorrere le annotazioni sulla pagina desiderata (in questo caso, la prima pagina):

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 Questo codice filtra per`TextMarkupAnnotation` tipi, che rappresentano i punti salienti.

## Passaggio 4: estrai il testo evidenziato

Ora estraiamo e visualizziamo il testo dalle annotazioni evidenziate:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

In questo modo vengono recuperati tutti i frammenti di testo contrassegnati associati all'evidenziazione e vengono visualizzati sulla console.

## Conclusione

Estrarre testo evidenziato da un PDF usando Aspose.PDF per .NET è semplice e può migliorare significativamente il processo di gestione dei documenti. Seguendo i passaggi descritti sopra, puoi raccogliere in modo efficiente testo evidenziato per varie applicazioni, come la preparazione di report o l'analisi dei dati.

## Domande frequenti

### Posso estrarre altri tipi di annotazioni?
 Sì, basta regolare il`if` condizione per includere diversi tipi di annotazione come`TextAnnotation` O`StampAnnotation`.

### Come posso estrarre il testo evidenziato da tutte le pagine PDF?
È possibile scorrere tutte le pagine utilizzando:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### È necessaria una licenza per Aspose.PDF per .NET?
 È disponibile una prova gratuita, ma considera un[licenza temporanea](https://purchase.aspose.com/temporary-license/) oppure una licenza completa per un accesso completo.

### Posso salvare il testo estratto in un file?
Assolutamente! Puoi modificare il codice per scrivere il testo estratto in un file di testo.

### Aspose.PDF supporta altre piattaforme?
Sì, Aspose.PDF supporta anche Java e altre piattaforme, offrendo funzionalità simili.