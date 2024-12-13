---
title: Implementare intestazione e piè di pagina con Aspose.Cells per .NET
linktitle: Implementare intestazione e piè di pagina con Aspose.Cells per .NET
second_title: API di elaborazione Excel .NET Aspose.Cells
description: Scopri come migliorare i tuoi documenti Excel personalizzando a livello di programmazione intestazioni e piè di pagina tramite Aspose.Cells per .NET. Questa guida completa ti accompagna in ogni passaggio, dall'impostazione della cartella di lavoro all'inserimento dinamico del nome del foglio di lavoro.
type: docs
weight: 22
url: /it/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## Introduzione

Le intestazioni e i piè di pagina sono elementi essenziali nei fogli di calcolo Excel, poiché forniscono informazioni contestuali critiche come nomi di file, date e numeri di pagina. Sia che tu stia automatizzando report o generando file dinamici, Aspose.Cells per .NET semplifica il processo di personalizzazione di intestazioni e piè di pagina a livello di programmazione. Questa guida offre un approccio passo dopo passo per migliorare i tuoi file Excel con intestazioni e piè di pagina raffinati e professionali.

## Prerequisiti

Prima di immergerti, assicurati di avere quanto segue:

1.  Aspose.Cells per .NET: scaricalo e installalo da[Qui](https://releases.aspose.com/cells/net/).
2. Configurazione IDE: utilizzare Visual Studio o l'IDE preferito con il framework .NET.
3.  Licenza: inizia con una prova gratuita, ma considera di ottenere una licenza completa o temporanea per una funzionalità completa. Puoi[ottenere una licenza temporanea](https://purchase.aspose.com/temporary-license/).

## Importazione dei pacchetti richiesti

Inizia importando gli spazi dei nomi necessari nel tuo progetto:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Questo ti darà accesso alle classi e ai metodi necessari per lavorare con intestazioni, piè di pagina e altre funzionalità di Excel in Aspose.Cells.

## Passaggio 1: creare una cartella di lavoro e accedere alle impostazioni della pagina

Inizia creando una nuova cartella di lavoro e accedendo all'impostazione di pagina del foglio di lavoro. Qui è dove modificherai le impostazioni di intestazione e piè di pagina.

```csharp
// Definisci il percorso in cui salvare il tuo documento
string dataDir = "Your Document Directory";

// Crea un'istanza di un oggetto Workbook
Workbook excel = new Workbook();
```

 Qui, un`Workbook` L'oggetto rappresenta il file Excel. L'`PageSetup` proprietà del foglio di lavoro ti consentirà di personalizzare intestazioni e piè di pagina.

## Passaggio 2: accedere alle proprietà del foglio di lavoro e di PageSetup

 Ogni foglio di lavoro in Aspose.Cells ha un`PageSetup` proprietà che governa le caratteristiche del layout, tra cui intestazioni e piè di pagina. Ottieni il`PageSetup` oggetto per il tuo foglio di lavoro:

```csharp
// Ottenere il riferimento al PageSetup del primo foglio di lavoro
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Ora,`pageSetup` contiene le impostazioni necessarie per personalizzare intestazioni e piè di pagina.

## Passaggio 3: imposta la sezione sinistra dell'intestazione

Le intestazioni sono composte da tre sezioni: sinistra, centro e destra. Iniziamo impostando la sezione sinistra per visualizzare il nome del foglio di lavoro.

```csharp
// Imposta il nome del foglio di lavoro nella sezione sinistra dell'intestazione
pageSetup.SetHeader(0, "&A");
```

 Utilizzando`&A`visualizza dinamicamente il nome del foglio di lavoro, il che è particolarmente utile per le cartelle di lavoro con più fogli.

## Passaggio 4: aggiungere data e ora al centro dell'intestazione

Successivamente, aggiungi la data e l'ora correnti nella sezione centrale dell'intestazione, applicando un font personalizzato per lo stile.

```csharp
// Imposta data e ora nella sezione centrale dell'intestazione con carattere in grassetto
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

In questa riga:
- `&D` inserisce la data corrente.
- `&T` inserisce l'ora corrente.
- `"Times New Roman,Bold"` applica il carattere Times New Roman in grassetto.

## Passaggio 5: visualizzare il nome del file nella sezione destra dell'intestazione

Per completare l'intestazione, visualizza il nome del file sul lato destro con una dimensione del carattere specificata.

```csharp
// Visualizza il nome del file nella sezione destra dell'intestazione con dimensione del carattere personalizzata
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Qui,`&F` rappresenta il nome del file e`&12` imposta la dimensione del carattere a 12.

## Passaggio 6: aggiungere testo personalizzato alla sezione del piè di pagina sinistro

Ora impostiamo la sezione del piè di pagina sinistro con testo personalizzato e uno stile di carattere specifico.

```csharp
// Aggiungi testo personalizzato con stile di carattere alla sezione sinistra del piè di pagina
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

In questo esempio, il testo`123` è formattato con il font "Courier New" in dimensione 14, mentre il resto mantiene il font predefinito del piè di pagina.

## Passaggio 7: inserire il numero di pagina al centro del piè di pagina

L'inserimento dei numeri di pagina nel piè di pagina aiuta i lettori a tenere traccia dei documenti composti da più pagine.

```csharp
// Inserire il numero di pagina nella sezione centrale del piè di pagina
pageSetup.SetFooter(1, "&P");
```

 IL`&P` il codice aggiunge il numero di pagina corrente alla sezione centrale del piè di pagina.

## Passaggio 8: mostra il conteggio totale delle pagine nella sezione del piè di pagina destro

Completa il piè di pagina visualizzando il numero totale di pagine nella sezione giusta.

```csharp
// Visualizza il conteggio totale delle pagine nella sezione destra del piè di pagina
pageSetup.SetFooter(2, "&N");
```

 IL`&N` il codice fornisce il conteggio totale delle pagine, informando i lettori della lunghezza del documento.

## Passaggio 9: Salvare la cartella di lavoro

Infine, salva la cartella di lavoro per generare un file Excel con intestazioni e piè di pagina personalizzati.

```csharp
// Salva la cartella di lavoro
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Questa riga salva il file con le tue personalizzazioni al loro posto.

## Conclusione

La personalizzazione di intestazioni e piè di pagina nei fogli di lavoro Excel aumenta la professionalità dei tuoi documenti. Con Aspose.Cells per .NET, puoi facilmente controllare questi elementi, dalla visualizzazione dei nomi dei fogli di lavoro all'inserimento di testo personalizzato, date, orari e numeri di pagina dinamici. Ora che hai imparato i passaggi, puoi migliorare i tuoi progetti di automazione Excel.

## Domande frequenti

### Posso usare font diversi per sezioni diverse di intestazioni e piè di pagina?
Sì, Aspose.Cells consente di specificare font univoci per ogni sezione dell'intestazione e del piè di pagina.

### Come faccio a rimuovere intestazioni e piè di pagina?
 Cancella intestazioni e piè di pagina impostando il loro testo su una stringa vuota utilizzando`SetHeader` O`SetFooter`.

### Posso inserire immagini nelle intestazioni o nei piè di pagina con Aspose.Cells per .NET?
Attualmente, Aspose.Cells supporta principalmente il testo nelle intestazioni e nei piè di pagina. Le immagini potrebbero richiedere metodi alternativi, come l'inserimento diretto nel foglio di lavoro.

### Aspose.Cells supporta dati dinamici nelle intestazioni e nei piè di pagina?  
 Sì, puoi utilizzare vari codici dinamici (come`&D`per data o`&P` per numero di pagina) per aggiungere contenuti dinamici.

### Come posso regolare l'altezza dell'intestazione o del piè di pagina?  
 Aspose.Cells fornisce opzioni all'interno di`PageSetup` classe per regolare i margini dell'intestazione e del piè di pagina, offrendoti il controllo sulla spaziatura.