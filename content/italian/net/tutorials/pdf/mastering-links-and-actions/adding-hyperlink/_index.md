---
title: Aggiunta di collegamento ipertestuale nel file PDF
linktitle: Aggiunta di collegamento ipertestuale nel file PDF
second_title: Riferimento API Aspose.PDF per .NET
description: Scopri come elevare la funzionalità dei tuoi documenti PDF aggiungendo collegamenti ipertestuali interattivi tramite Aspose.PDF per .NET. Questa guida completa fornisce un tutorial passo dopo passo.
type: docs
weight: 10
url: /it/net/tutorials/pdf/mastering-links-and-actions/adding-hyperlink/
---
## Introduzione

Migliorare l'interattività e la navigabilità dei documenti PDF può migliorare significativamente l'esperienza utente. Che tu stia creando fatture con link a portali di pagamento o report che indirizzano i lettori a risorse online, aggiungere collegamenti ipertestuali è un modo potente per rendere i tuoi PDF più intuitivi. In questa guida, ti guideremo attraverso il processo di aggiunta di collegamenti ipertestuali ai file PDF utilizzando la libreria Aspose.PDF per .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. .NET Framework: una versione compatibile di .NET Framework installata sul computer.
2.  Aspose.PDF per la libreria .NET: Scarica la libreria da[Sito web di Aspose](https://releases.aspose.com/pdf/net/).
3. Conoscenza di base del linguaggio C#: la familiarità con la programmazione C# ti aiuterà a seguire il corso senza problemi.
4. Ambiente di sviluppo: un IDE come Visual Studio configurato per la codifica e il test.

Una volta soddisfatti questi prerequisiti, sei pronto per iniziare!

## Passaggio 1: imposta la directory dei documenti

Inizia definendo la directory in cui verranno archiviati i tuoi file PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Sostituire`YOUR_DOCUMENT_DIRECTORY` con il percorso effettivo in cui desideri salvare i tuoi PDF.

## Passaggio 2: aprire il documento PDF esistente

 Per modificare un PDF esistente, utilizzare`Document`classe dalla libreria Aspose.PDF:

```csharp
Document document = new Document(dataDir + "AddHyperlink.pdf");
```

 Assicurati che il file`"AddHyperlink.pdf"` esiste nella directory specificata.

## Passaggio 3: accedi alla pagina PDF

Seleziona la pagina in cui vuoi aggiungere l'hyperlink. Ad esempio, per aggiungerlo alla prima pagina:

```csharp
Page page = document.Pages[1]; // L'indice delle pagine inizia da 1
```

## Passaggio 4: creare l'annotazione del collegamento

Definisci l'area cliccabile per l'hyperlink utilizzando un rettangolo:

```csharp
LinkAnnotation link = new LinkAnnotation(page, new Aspose.Pdf.Rectangle(100, 100, 300, 300));
```

 Regola le coordinate del rettangolo`(100, 100)` A`(300, 300)` per soddisfare le tue esigenze di progettazione.

## Passaggio 5: Configurare il bordo del collegamento

Puoi personalizzare il bordo del collegamento; qui lo renderemo invisibile:

```csharp
Border border = new Border(link) { Width = 0 };
link.Border = border;
```

## Passaggio 6: specificare l'azione del collegamento ipertestuale

Imposta l'azione per l'hyperlink. In questo esempio, creeremo un collegamento al sito web Aspose:

```csharp
link.Action = new GoToURIAction("http://(Italiano)
```

## Passaggio 7: aggiungere l'annotazione del collegamento alla pagina

Aggiungere l'hyperlink alla raccolta di annotazioni della pagina:

```csharp
page.Annotations.Add(link);
```

## Passaggio 8: creare un'annotazione di testo libero

L'aggiunta di un'annotazione di testo aiuta a fornire un contesto per l'hyperlink:

```csharp
FreeTextAnnotation textAnnotation = new FreeTextAnnotation(
    document.Pages[1], 
    new Aspose.Pdf.Rectangle(100, 100, 300, 300), 
    new DefaultAppearance(FontRepository.FindFont("TimesNewRoman"), 10, Color.Blue)
)
{
    Contents = "Link to Aspose website",
    Border = border
};

document.Pages[1].Annotations.Add(textAnnotation);
```

## Passaggio 9: Salvare il documento

Infine, salva il PDF aggiornato con l'hyperlink:

```csharp
dataDir = dataDir + "AddHyperlink_out.pdf";
document.Save(dataDir);
```

## Conclusione

Aggiungere collegamenti ipertestuali ai tuoi documenti PDF usando Aspose.PDF per .NET non solo ne aumenta la professionalità, ma migliora anche il coinvolgimento degli utenti. Con i passaggi descritti in questa guida, puoi facilmente aggiungere collegamenti ipertestuali a qualsiasi PDF che crei o modifichi.

## Domande frequenti

### Posso modificare lo stile del collegamento ipertestuale?  
Sì, puoi personalizzare l'aspetto del collegamento ipertestuale, inclusi i caratteri, i colori e gli stili dei bordi.

### Cosa succede se voglio creare un collegamento a una pagina interna?  
 Utilizzo`GoToAction` invece di`GoToURIAction` per creare collegamenti a pagine diverse all'interno dello stesso PDF.

### Aspose.PDF supporta altri formati di file?  
Sì, Aspose.PDF supporta un'ampia gamma di formati di file per la manipolazione e la conversione.

### Come posso ottenere una licenza temporanea per lo sviluppo?  
 È possibile ottenere una licenza temporanea visitando[questo collegamento](https://purchase.aspose.com/temporary-license/).

### Dove posso trovare altri tutorial su Aspose.PDF?  
 Esplora altri tutorial in[Documentazione Aspose](https://reference.aspose.com/pdf/net/).