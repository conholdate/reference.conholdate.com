---
title: Guida alla firma di PDF con metadati tramite GroupDocs.Signature
linktitle: Guida alla firma di PDF con metadati
second_title: API .NET di GroupDocs.Signature
description: Scopri come rafforzare i tuoi documenti PDF con maggiore sicurezza e tracciabilità firmandoli con metadati usando GroupDocs.Signature per .NET. Questo tutorial completo fornisce una chiara.
type: docs
weight: 11
url: /it/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## Introduzione

In questo tutorial, impareremo come firmare un documento PDF e aggiungere metadati usando GroupDocs.Signature per .NET. L'aggiunta di metadati migliora il documento fornendo informazioni essenziali come autore, data di creazione, ID documento e altro.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1.  GroupDocs.Signature per .NET: Scaricalo da[Qui](https://releases.groupdocs.com/signature/net/).
2. Un documento PDF: tieni pronto un file PDF di esempio da firmare.
3. Conoscenza di base della programmazione C#: è necessaria familiarità con la sintassi C# per comprendere gli esempi di codice.

## Importazione degli spazi dei nomi

Iniziamo importando gli spazi dei nomi richiesti per accedere alle classi e ai metodi necessari:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Passaggio 1: caricare il documento PDF

Specificare il percorso del documento PDF che si desidera firmare:

```csharp
string filePath = "sample.pdf";
```

## Passaggio 2: specificare il percorso del file di output

Definisci dove verrà salvato il PDF firmato con i metadati:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## Passaggio 3: creare un'istanza di firma

 Inizializzare un`Signature` istanza con il percorso al documento PDF:

```csharp
using (Signature signature = new Signature(filePath))
{
    // Il codice correlato alla firma andrà qui
}
```

## Passaggio 4: definire le opzioni dei metadati

 Creare`MetadataSignOptions` e aggiungi i campi dei metadati insieme ai loro valori:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // Valore stringa
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // Valore DateTime
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // Valore intero
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // Doppio valore
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // Valore decimale
    .Add(new PdfMetadataSignature("Total", 123.456F));              // Valore float
```

## Fase 5: Firmare il documento

Firma il documento PDF con le opzioni di metadati specificate e salva il documento firmato:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Conclusione

In questo tutorial, abbiamo spiegato come firmare un documento PDF con metadati usando GroupDocs.Signature per .NET. Seguendo questi passaggi, puoi arricchire facilmente i tuoi file PDF con preziosi metadati, migliorandone la tracciabilità e l'utilità.

## Domande frequenti

### Posso aggiungere campi metadati personalizzati ai miei documenti PDF?

Sì, è possibile aggiungere campi di metadati personalizzati specificando il nome del campo e il valore corrispondente utilizzando GroupDocs.Signature per .NET.

### GroupDocs.Signature per .NET è compatibile con tutte le versioni di .NET Framework?

GroupDocs.Signature per .NET è compatibile con varie versioni di .NET Framework, garantendo flessibilità e facilità di integrazione.

### GroupDocs.Signature supporta la firma di altri formati di documenti oltre al PDF?

Sì, GroupDocs.Signature supporta un'ampia gamma di formati di documenti, tra cui Word, Excel, PowerPoint e altri.

### Posso firmare più documenti contemporaneamente utilizzando GroupDocs.Signature per .NET?

Assolutamente! Puoi firmare più documenti in blocco scorrendo un elenco di file e applicando il processo di firma in modo programmatico.

### È disponibile supporto tecnico per gli utenti di GroupDocs.Signature?

 Sì, GroupDocs fornisce supporto tecnico dedicato tramite i suoi forum. Puoi accedere al forum di supporto[Qui](https://forum.groupdocs.com/c/signature/13).