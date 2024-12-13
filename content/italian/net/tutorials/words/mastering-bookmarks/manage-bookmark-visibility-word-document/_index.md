---
title: Gestire la visibilità dei segnalibri nei documenti di Word
linktitle: Gestire la visibilità dei segnalibri nei documenti di Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come controllare in modo esperto la visibilità del contenuto nei documenti Word utilizzando Aspose.Words per .NET. Questa guida passo passo.
type: docs
weight: 10
url: /it/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Introduzione

Siete pronti a migliorare le vostre capacità di manipolazione dei documenti con Aspose.Words per .NET? Che siate uno sviluppatore esperto che automatizza le attività sui documenti o un individuo curioso che esplora il controllo programmatico sui file Word, questa guida è fatta su misura per voi. Oggi approfondiremo come mostrare e nascondere il contenuto in base ai segnalibri in un documento Word. Cominciamo!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. Visual Studio: qualsiasi versione compatibile con .NET.
2. Aspose.Words per .NET: Scaricalo[Qui](https://releases.aspose.com/words/net/).
3. Conoscenza di base del linguaggio C#: è sufficiente avere familiarità con la scrittura di semplici programmi in C#.
4. Un esempio di documento Word: preparare un documento Word (ad esempio, "Bookmarks.docx") contenente i segnalibri per questa esercitazione.

### Crea un nuovo progetto

1. Apri Visual Studio e crea un nuovo progetto Console App (.NET Core). Chiamalo qualcosa come "BookmarkVisibilityManager".

### Installa Aspose.Words per .NET

Aggiungi Aspose.Words al tuo progetto tramite NuGet Package Manager:

1. Passare a Strumenti > Gestore pacchetti NuGet > Gestisci pacchetti NuGet per la soluzione.
2. Cerca "Aspose.Words".
3. Installa il pacchetto.

Una volta impostato il progetto, procediamo a caricare il documento.

## Importazione di namespace

Inizia importando i namespace essenziali. Questi forniscono le classi e i metodi necessari per manipolare i documenti Word con Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Fase 1: Caricamento del documento

Per manipolare il documento Word, dobbiamo prima caricarlo. Ecco come fare:

```csharp
// Definisci il percorso della directory dei tuoi documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Questo frammento imposta il percorso alla directory del documento e carica il documento in un`Document` oggetto.

## Passaggio 2: Mostra/Nascondi il contenuto aggiunto ai segnalibri

 Ora, creiamo un metodo per alternare la visibilità del contenuto in base ai segnalibri. Chiameremo questo metodo`ShowHideBookmarkedContent`.

Ecco l'implementazione del metodo:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Recupero segnalibro:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` recupera il segnalibro specificato.
- Attraversamento dei nodi: eseguiamo un'iterazione sui nodi all'interno del segnalibro.
-  Attiva/disattiva visibilità: per ogni`Run` nodo (che rappresenta un segmento di testo), impostiamo il suo`Hidden` proprietà basata sulla`isHidden` parametro.

## Fase 3: applicazione del metodo

Ora che abbiamo pronto il nostro metodo, utilizziamolo per mostrare o nascondere il contenuto all'interno di un segnalibro specifico:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Nasconde il contenuto all'interno di "MyBookmark1"
```

Questa riga nasconderà il contenuto associato al segnalibro denominato "MyBookmark1".

## Passaggio 4: salvataggio del documento

Dopo aver apportato le modifiche, non dimenticare di salvare il documento modificato:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

In questo modo il documento viene salvato con le impostazioni di visibilità aggiornate.

## Conclusione

Congratulazioni! Hai imparato con successo come mostrare e nascondere il contenuto con segnalibro in un documento Word usando Aspose.Words per .NET. Questa potente libreria semplifica la manipolazione dei documenti, rendendola ideale per automatizzare report, creare modelli o sperimentare con file Word. Buona codifica!

## Domande frequenti

### Posso attivare/disattivare più segnalibri contemporaneamente?
 Sì, basta chiamare il`ShowHideBookmarkedContent` metodo per ogni segnalibro che vuoi attivare/disattivare.

### Nascondere il contenuto influisce sulla struttura del documento?
No, nascondere un contenuto ne compromette solo la visibilità; il contenuto rimane intatto all'interno del documento.

### Posso usare questo metodo per altri tipi di contenuti?
Questo metodo è specificamente progettato per le esecuzioni di testo. Per altri tipi di contenuto, dovrai adattare la logica di attraversamento del nodo di conseguenza.

### Aspose.Words per .NET è gratuito?
 Aspose.Words offre una prova gratuita[Qui](https://releases.aspose.com/) , ma è richiesta una licenza completa per l'uso in produzione. Puoi acquistarla[Qui](https://purchase.aspose.com/buy).

### Come posso ottenere supporto se riscontro problemi?
 Per supporto, visita il forum della community Aspose[Qui](https://forum.aspose.com/c/words/8).