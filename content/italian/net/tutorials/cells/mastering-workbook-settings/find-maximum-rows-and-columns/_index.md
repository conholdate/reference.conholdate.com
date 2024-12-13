---
title: Trova il numero massimo di righe e colonne nei formati XLS e XLSX
linktitle: Trova il numero massimo di righe e colonne nei formati XLS e XLSX
second_title: API di elaborazione Excel .NET Aspose.Cells
description: Scopri come gestire in modo efficiente grandi set di dati in Excel utilizzando la libreria Aspose.Cells per .NET. Questa guida fornisce un approccio passo dopo passo per identificare il numero massimo di righe e colonne supportate dai formati di file XLS e XLSX.
type: docs
weight: 11
url: /it/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Introduzione

Gestire grandi set di dati in Excel può essere impegnativo, soprattutto per quanto riguarda i limiti di vari formati di file. Questo tutorial ti guiderà nell'uso della libreria Aspose.Cells per .NET per determinare il numero massimo di righe e colonne supportate dai formati XLS (Excel 97-2003) e XLSX (Excel 2007 e successivi). Alla fine, sarai in grado di gestire in modo efficiente le attività correlate a Excel.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. [Quadro .NET](https://dotnet.microsoft.com/en-us/download) O[.NET Core](https://dotnet.microsoft.com/en-us/download) installato sul tuo sistema.
2. [Aspose.Cells per .NET](https://releases.aspose.com/cells/net/) libreria scaricata e referenziata nel tuo progetto (puoi anche installarla tramite[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## Importazione dei pacchetti richiesti

Aggiungere le seguenti istruzioni using all'inizio del file C# per importare i pacchetti necessari dalla libreria Aspose.Cells:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Passaggio 1: numero massimo di righe e colonne per il formato XLS

Cominciamo col trovare il numero massimo di righe e colonne supportate dal formato XLS.

```csharp
// Stampa un messaggio sul formato XLS.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Creare una cartella di lavoro in formato XLS.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Recupera il numero massimo di righe e colonne.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Visualizza i risultati.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Stampa un messaggio per indicare che stiamo lavorando con il formato XLS.
2.  Crea un`Workbook` istanza per il formato XLS utilizzando`FileFormatType.Excel97To2003`.
3.  Ottieni il numero massimo di righe e colonne con`wb.Settings.MaxRow` E`wb.Settings.MaxColumn`, aggiungendo 1 poiché sono basati su zero.
4. Invia alla console il numero massimo di righe e colonne.

## Passaggio 2: numero massimo di righe e colonne per il formato XLSX

Ora esploreremo il numero massimo di righe e colonne supportate dal formato XLSX.

```csharp
// Stampa un messaggio sul formato XLSX.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Creare una cartella di lavoro in formato XLSX.
wb = new Workbook(FileFormatType.Xlsx);

// Recupera il numero massimo di righe e colonne.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Visualizza i risultati.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Stampa un messaggio che indica che stiamo lavorando con il formato XLSX.
2.  Crea un`Workbook` istanza per il formato XLSX utilizzando`FileFormatType.Xlsx`.
3. Recupera e visualizza il numero massimo di righe e colonne come prima.

## Passaggio 3: visualizzazione di un messaggio di successo

Dopo aver eseguito i passaggi, indichiamo il successo.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Conclusione

In questo tutorial, hai imparato come usare la libreria Aspose.Cells per .NET per trovare il numero massimo di righe e colonne supportate dai formati di file XLS e XLSX. Comprendere questi limiti è essenziale per una gestione efficace dei dati Excel, assicurando che i tuoi set di dati siano allineati con le capacità di formato.

## Domande frequenti

### Qual è il numero massimo di righe supportate dal formato XLS?
Il numero massimo di righe supportato dal formato XLS è 65.536.

### Qual è il numero massimo di colonne supportate dal formato XLS?
Il numero massimo di colonne supportato dal formato XLS è 256.

### Qual è il numero massimo di righe supportate dal formato XLSX?
Il numero massimo di righe supportato dal formato XLSX è 1.048.576.

### Qual è il numero massimo di colonne supportate dal formato XLSX?
Il numero massimo di colonne supportato dal formato XLSX è 16.384.

### Posso utilizzare la libreria Aspose.Cells per .NET con altri formati di file Excel?
 Sì, Aspose.Cells per .NET supporta vari formati di file, tra cui XLS, XLSX, ODS e altri. Controlla il[documentazione](https://reference.aspose.com/cells/net/) per maggiori dettagli sulle funzionalità e caratteristiche supportate.