---
title: Cambiare l'orientamento della pagina PDF
linktitle: Cambiare l'orientamento della pagina PDF
second_title: Riferimento API Aspose.PDF per .NET
description: Scopri come regolare facilmente l'orientamento della pagina dei file PDF utilizzando Aspose.PDF per .NET. Questa guida passo passo fornisce istruzioni chiare su come caricare, ruotare e salvare i tuoi documenti.
type: docs
weight: 10
url: /it/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Introduzione

Ti è mai capitato di imbatterti in un file PDF in cui l'orientamento della pagina è completamente sbagliato? Che si tratti di un documento scansionato in modo errato o di uno che necessita semplicemente di un layout diverso, modificare l'orientamento può fare un mondo di differenza. Fortunatamente, Aspose.PDF per .NET offre un modo potente e intuitivo per manipolare i file PDF, inclusa la modifica dell'orientamento delle pagine. In questa guida, ti guideremo passo dopo passo nel processo, sia che tu voglia passare da verticale a orizzontale o viceversa.

## Prerequisiti

Prima di entrare nei dettagli, assicurati di avere a disposizione quanto segue:

-  Aspose.PDF per .NET: assicurati di avere installata la libreria Aspose.PDF. Se non l'hai ancora fatto, puoi[scaricalo qui](https://releases.aspose.com/pdf/net/).
- Un ambiente di sviluppo .NET: puoi utilizzare Visual Studio, JetBrains Rider o qualsiasi altro IDE tu preferisca per lo sviluppo .NET.
- Conoscenza di base di C#: la familiarità con C# ti aiuterà a seguire più facilmente il programma.
- Un file PDF: tieni pronto un file PDF di esempio per il test. Puoi crearne uno o scaricarne uno online.

 Se stai appena iniziando, prendi in considerazione di provare Aspose.PDF con un[licenza temporanea gratuita](https://purchase.aspose.com/temporary-license/) prima di decidere di[acquista la versione completa](https://purchase.aspose.com/buy).

## Importazione degli spazi dei nomi

Per manipolare le pagine PDF, dovrai prima importare i namespace necessari nel tuo progetto C#. Aggiungi le seguenti righe all'inizio del tuo file di codice:

```csharp
using System.IO;
using Aspose.Pdf;
```

Ora che abbiamo impostato tutto, cominciamo!

## Passaggio 1: caricare il documento PDF

 Il primo passo è caricare il file PDF che vuoi modificare. Usa il`Document` classe dallo spazio dei nomi Aspose.PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Assicurati di sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo del file PDF.

## Passaggio 2: scorrere ogni pagina

Successivamente, faremo un ciclo su ogni pagina del documento PDF. Questo ci consente di applicare la modifica dell'orientamento a tutte le pagine:

```csharp
foreach (Page page in doc.Pages)
{
    // Manipola ogni pagina
}
```

## Passaggio 3: accedi al MediaBox della pagina

 Ogni pagina PDF ha un`MediaBox` che ne definisce i confini. Dobbiamo accedervi per controllare l'orientamento corrente e apportare modifiche:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 IL`MediaBox` fornisce le dimensioni della pagina, tra cui larghezza e altezza.

## Passaggio 4: scambia larghezza e altezza

Per cambiare l'orientamento della pagina, scambieremo i valori di larghezza e altezza. Questa regolazione cambierà le dimensioni della pagina:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Qui calcoliamo le nuove dimensioni e riposizioniamo l'angolo inferiore sinistro (`LLY`) di conseguenza.

## Passaggio 5: Aggiorna MediaBox e CropBox

 Ora che abbiamo le nuove dimensioni, applicheremo queste modifiche al`MediaBox` E`CropBox` per garantire che la pagina venga visualizzata correttamente:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Passaggio 6: ruota la pagina

Per finalizzare il cambio di orientamento, ruoteremo la pagina. Con Aspose.PDF è semplice:

```csharp
page.Rotate = Rotation.on90; // Ruota di 90 gradi
```

Questa linea capovolge effettivamente la pagina nell'orientamento desiderato.

## Passaggio 7: Salvare il PDF di output

Dopo aver modificato l'orientamento di tutte le pagine, salva il documento aggiornato in un nuovo file:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Assicuratevi di specificare un nuovo nome file per evitare di sovrascrivere il documento originale.

## Conclusione

Ed ecco fatto! Cambiare l'orientamento della pagina di un file PDF usando Aspose.PDF per .NET è un processo semplice. Caricando il documento, scorrendo le pagine, aggiornando MediaBox e salvando il file, puoi facilmente adattare il layout alle tue esigenze. Che tu stia correggendo un documento scansionato male o formattando le pagine per una presentazione, questa guida dovrebbe aiutarti a svolgere il lavoro in modo efficiente.

## Domande frequenti

### Posso ruotare pagine specifiche invece di tutte le pagine del PDF?  
Sì, puoi modificare il ciclo in modo che punti a pagine specifiche in base al loro indice, anziché scorrere tutte le pagine.

### Che cosa è il`MediaBox`?  
 IL`MediaBox` definisce la dimensione e la forma della pagina in un file PDF, determinando dove verrà posizionato il contenuto.

### Aspose.PDF per .NET funziona con altri formati di file?  
Sì, Aspose.PDF può gestire vari formati di file, tra cui HTML, XML, XPS e altri.

### Esiste una versione gratuita di Aspose.PDF per .NET?  
 Sì, puoi iniziare con un[prova gratuita](https://releases.aspose.com/) o richiedi un[licenza temporanea](https://purchase.aspose.com/temporary-license/).

### Posso annullare le modifiche una volta salvate?  
Una volta salvato il documento, le modifiche sono permanenti. È consigliabile lavorare su una copia o conservare un backup del file originale.