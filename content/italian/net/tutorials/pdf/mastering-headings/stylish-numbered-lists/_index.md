---
title: Elenchi numerati eleganti utilizzando Aspose.PDF per .NET
linktitle: Elenchi numerati eleganti utilizzando Aspose.PDF per .NET
second_title: Riferimento API Aspose.PDF per .NET
description: Scopri come creare elenchi numerati in modo splendido nei tuoi documenti PDF con Aspose.PDF per .NET. Questa guida ti accompagna attraverso il processo di applicazione di vari stili di numerazione, come i numeri romani.
type: docs
weight: 10
url: /it/net/programming-with-headings/stylish-numbered-lists/
---
## Introduzione

Hai mai avuto bisogno di creare elenchi ben strutturati e numerati nei tuoi documenti PDF? Che si tratti di documenti legali, report o presentazioni, stili di numerazione efficaci sono essenziali per organizzare i tuoi contenuti. Con Aspose.PDF per .NET, puoi facilmente applicare vari stili di numerazione alle intestazioni dei tuoi PDF, ottenendo documenti raffinati e professionali.

## Prerequisiti

Prima di passare alla codifica, assicurati di avere pronto quanto segue:

1.  Aspose.PDF per .NET: Scarica l'ultima versione da[Qui](https://releases.aspose.com/pdf/net/).
2. Ambiente di sviluppo: avrai bisogno di Visual Studio o di qualsiasi IDE compatibile con .NET.
3. .NET Framework: assicurati di aver installato .NET Framework 4.0 o versione successiva.
4.  Licenza: puoi utilizzare una licenza temporanea da[Qui](https://purchase.aspose.com/temporary-license/) o esplora il[prova gratuita](https://releases.aspose.com/) opzioni.

## Importazione dei pacchetti richiesti

Inizia importando gli spazi dei nomi necessari nel tuo progetto:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Fase 1: Impostazione del documento

Iniziamo creando un nuovo documento PDF e configurandone il layout, comprese le dimensioni della pagina e i margini.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Imposta le dimensioni e i margini della pagina
pdfDoc.PageInfo.Width = 612.0; // 8,5 pollici
pdfDoc.PageInfo.Height = 792.0; // 11 pollici
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // Margini di 1 pollice
```

Con questa impostazione il documento avrà un formato lettera standard con margini di un pollice su tutti i lati.

## Passaggio 2: aggiunta di una pagina al PDF

Successivamente aggiungeremo una pagina vuota al documento PDF, dove in seguito applicheremo gli stili di numerazione.

```csharp
// Aggiungere una nuova pagina al documento PDF
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // Utilizzare le stesse impostazioni del documento
```

## Passaggio 3: creazione di una casella mobile

Un FloatingBox consente di posizionare il contenuto indipendentemente dal flusso della pagina, offrendo un maggiore controllo sul layout.

```csharp
//Crea un FloatingBox per contenuti strutturati
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Fase 4: Aggiunta di titoli con numeri romani

Aggiungiamo ora la nostra prima intestazione con la numerazione in numeri romani minuscoli.

```csharp
// Crea il primo titolo con i numeri romani
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Passaggio 5: aggiunta di una seconda intestazione con numero iniziale personalizzato

Ora aggiungeremo una seconda intestazione, partendo dal numero romano 13.

```csharp
// Crea una seconda intestazione a partire dal numero romano 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Passaggio 6: aggiunta di un'intestazione con numerazione alfabetica

Per variare, aggiungiamo una terza intestazione utilizzando la numerazione alfabetica in minuscolo.

```csharp
// Crea un titolo con numerazione alfabetica
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Passaggio 7: salvataggio del PDF

Infine, salviamo il file PDF nella directory desiderata.

```csharp
// Salva il documento PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Conclusione

Congratulazioni! Hai applicato con successo vari stili di numerazione, numeri romani e alfabetici, alle intestazioni in un file PDF utilizzando Aspose.PDF per .NET. La flessibilità di Aspose.PDF ti consente di controllare il layout di pagina, gli stili di numerazione e il posizionamento del contenuto, consentendoti di creare documenti PDF ben organizzati e professionali.

## Domande frequenti

### Posso applicare stili numerici diversi allo stesso documento PDF?  
Sì, è possibile combinare diversi stili di numerazione, come numeri romani, numeri arabi e numerazione alfabetica, all'interno dello stesso documento.

### Come posso personalizzare il numero iniziale per le intestazioni?  
 È possibile impostare il numero iniziale per qualsiasi intestazione utilizzando`StartNumber` proprietà.

### C'è un modo per reimpostare la sequenza di numerazione?  
 Sì, puoi reimpostare la numerazione regolando il`StartNumber` proprietà per ogni intestazione.

### Posso applicare lo stile grassetto o corsivo ai titoli oltre alla numerazione?  
 Assolutamente! Puoi personalizzare gli stili di intestazione modificando proprietà come font, dimensione, grassetto e corsivo utilizzando`TextState` oggetto.

### Come posso ottenere una licenza temporanea per Aspose.PDF?  
 È possibile ottenere una licenza temporanea da[Qui](https://purchase.aspose.com/temporary-license/)per testare Aspose.PDF senza restrizioni.