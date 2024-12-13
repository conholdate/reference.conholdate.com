---
title: Copiare i dati all'interno della cartella di lavoro di Excel utilizzando Aspose.Cells per .NET
linktitle: Copiare i dati all'interno della cartella di lavoro di Excel utilizzando Aspose.Cells per .NET
second_title: API di elaborazione Excel .NET Aspose.Cells
description: Scopri come copiare in modo efficiente i dati all'interno di una cartella di lavoro Excel utilizzando Aspose.Cells per .NET. Segui questa guida passo passo per duplicare facilmente fogli, trasferire dati e gestire file Excel con facilità.
type: docs
weight: 12
url: /it/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Introduzione

In questa guida dettagliata, mostreremo come copiare dati all'interno della stessa cartella di lavoro usando Aspose.Cells per .NET. Seguendo le istruzioni passo passo descritte di seguito, imparerai come duplicare i fogli a livello di programmazione, preservandone il contenuto e la formattazione.

## Prerequisiti per la copia dei dati in Excel con Aspose.Cells

Prima di immergerci nel processo di codifica, assicuriamoci di avere tutto a posto:

1. Libreria Aspose.Cells per .NET: è necessario che la libreria Aspose.Cells per .NET sia installata. È possibile scaricare l'ultima versione da[Pagina di download di Aspose.Cells per .NET](https://releases.aspose.com/cells/net/).
2. Ambiente di sviluppo: per scrivere ed eseguire il codice è necessario un IDE compatibile con .NET, come Visual Studio.
3.  Licenza Aspose: puoi usare una prova gratuita o una licenza acquistata. Per maggiori informazioni, visita[Qui](https://purchase.aspose.com/temporary-license/).

Una volta impostati i prerequisiti, sei pronto per iniziare a lavorare con la libreria.

## Importazione dei pacchetti richiesti

Per iniziare, dovrai importare i namespace rilevanti da Aspose.Cells. Questo ti consente di lavorare con file Excel usando le classi e i metodi forniti da Aspose.Cells.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Questi namespace ti daranno accesso a`Workbook` classe (per lavorare con file Excel) e`WorksheetCollection` (per accedere a più fogli all'interno di una cartella di lavoro).

## Passaggio 1: inizializzare i percorsi dei file per la cartella di lavoro

Per mantenere il tuo codice organizzato, è essenziale definire i percorsi dei file in cui si trova la tua cartella di lavoro e dove intendi salvare il file modificato. Ecco come puoi specificare i percorsi:

```csharp
// Definire il percorso della directory in cui si trova il file Excel.
string dataDir = "Your Directory Path";

// Definire il percorso completo della cartella di lavoro di input.
string inputPath = dataDir + "book1.xls";
```

 Sostituire`"Your Directory Path"` con il percorso effettivo alla directory contenente la cartella di lavoro. Questo aiuta a garantire che il codice sia flessibile e che tu possa gestire i percorsi in modo efficace.

## Passaggio 2: aprire la cartella di lavoro per accedere ai dati

 Ora che i percorsi dei file sono impostati, il passaggio successivo consiste nel caricare la cartella di lavoro di Excel in un`Workbook` oggetto. Ciò consente di accedere al suo contenuto per la manipolazione.

```csharp
// Caricare il file Excel nell'oggetto Workbook.
Workbook wb = new Workbook(inputPath);
```

 Con questa riga hai caricato con successo`book1.xls` dentro il`wb` oggetto, rendendo accessibili i suoi dati.

## Passaggio 3: accedi alla raccolta di fogli di lavoro

 Una volta caricata la cartella di lavoro, puoi accedere ai fogli in essa contenuti. Aspose.Cells fornisce`Worksheets`raccolta, che consente di interagire con ciascun foglio di lavoro nella cartella di lavoro.

```csharp
// Recupera la raccolta dei fogli di lavoro dalla cartella di lavoro.
WorksheetCollection sheets = wb.Worksheets;
```

 IL`sheets` l'oggetto ora ti dà accesso a tutti i fogli di lavoro all'interno`book1.xls`e puoi eseguire diverse operazioni su di essi, tra cui copiare dati da un foglio all'altro.

## Passaggio 4: Copiare i dati da un foglio all'altro

 Per copiare i dati da un foglio di lavoro a un altro all'interno della stessa cartella di lavoro, Aspose.Cells offre un metodo di facile utilizzo chiamato`AddCopy`Questo metodo crea un duplicato del foglio di lavoro specificato e lo aggiunge alla cartella di lavoro.

```csharp
// Copia i dati da "Sheet1" a un nuovo foglio all'interno della cartella di lavoro.
sheets.AddCopy("Sheet1");
```

 In questo esempio, stiamo copiando i dati da "Sheet1" a un nuovo foglio. Il`AddCopy` Il metodo duplicherà l'intero foglio, conservandone tutti i contenuti, comprese formule, formattazione e valori.

## Passaggio 5: salvare la cartella di lavoro modificata

 Dopo aver copiato i dati, puoi salvare la cartella di lavoro modificata con un nuovo nome o posizione. Questo viene fatto chiamando il comando`Save`metodo sul`Workbook` oggetto.

```csharp
//Salvare la cartella di lavoro modificata con un nuovo nome.
wb.Save(dataDir + "book1_copy.xls");
```

 Questo salverà la cartella di lavoro con il foglio copiato come`book1_copy.xls` nella directory specificata. Puoi modificare il nome del file e il percorso in base alle tue esigenze.

## Conclusione

Copiare dati all'interno di una cartella di lavoro Excel usando Aspose.Cells per .NET è un compito facile e questa guida fornisce i passaggi necessari per farlo in modo efficiente. Che tu stia duplicando interi fogli o intervalli di dati specifici, Aspose.Cells offre un'API robusta e flessibile che rende l'automazione di Excel semplice ed efficace.

## Domande frequenti

### Posso copiare più fogli contemporaneamente?

Aspose.Cells non supporta la copia di più fogli in una singola chiamata. Tuttavia, puoi scorrere i fogli che vuoi copiare e copiarli individualmente.

### Come posso rinominare il foglio copiato?

Dopo aver copiato il foglio, puoi rinominarlo come segue:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells è compatibile con .NET Core?

Sì, Aspose.Cells è completamente compatibile con gli ambienti .NET Framework e .NET Core.

### In che modo Aspose.Cells gestisce la formattazione durante la copia?

 IL`AddCopy`metodo conserva tutto il contenuto e la formattazione durante la copia dei fogli, garantendo che i dati copiati siano identici all'originale.

### Posso copiare un foglio in una cartella di lavoro diversa?

 Sì, puoi copiare un foglio in una cartella di lavoro diversa utilizzando`Copy` metodo con un riferimento alla cartella di lavoro di destinazione.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```