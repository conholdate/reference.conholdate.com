---
title: Crea e firma una nuova riga di firma
linktitle: Crea e firma una nuova riga di firma
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come aggiungere senza problemi una firma digitale ai tuoi documenti Word usando Aspose.Words per .NET. Questo tutorial completo copre tutto, dalla configurazione del tuo ambiente e l'inserimento di una riga di firma al salvataggio e alla verifica dei tuoi documenti firmati.
type: docs
weight: 10
url: /it/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Introduzione

Vuoi aggiungere una firma digitale a un documento Word? Con Aspose.Words per .NET, è più facile di quanto pensi! Questo tutorial ti guiderà attraverso i passaggi per impostare il tuo ambiente, aggiungere una riga di firma e firmare il tuo documento digitalmente. Cominciamo!

## Prerequisiti

Prima di immergerti nel codice, assicurati di avere quanto segue:

1.  Aspose.Words per .NET -[Scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo .NET: Visual Studio è l'ideale per questo compito.
3. Documento da firmare: puoi creare un nuovo documento Word o utilizzarne uno esistente.
4.  File del certificato - A`.pfx` il file è necessario per le firme digitali.
5. Immagine della riga della firma (facoltativa): puoi includere un file immagine per la firma.

## Importa gli spazi dei nomi richiesti

Per utilizzare le funzionalità di Aspose.Words, è necessario importare i seguenti namespace:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Passaggio 1: impostazione della directory dei documenti

Inizia definendo il percorso per la directory dei tuoi documenti. Qui sarà dove salverai e recupererai i tuoi documenti.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Specificare il percorso della directory del documento
```

## Passaggio 2: creazione di un nuovo documento

Ora creiamo un nuovo documento Word. Questo documento servirà come tela per la riga della tua firma.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Fase 3: Inserimento della riga della firma

 Ora, usa il`DocumentBuilder` classe per inserire una riga di firma nel tuo documento:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Passaggio 4: salvataggio del documento

Una volta inserita la riga della firma, salva il documento. Questo è un passaggio cruciale prima di firmare.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Passaggio 5: Configurazione delle opzioni di firma

Imposta le opzioni per il processo di firma. Ciò include la specifica dell'ID della riga della firma e dell'immagine facoltativa da visualizzare con la firma.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Percorso verso la tua immagine
};
```

## Fase 6: Caricamento del certificato

Caricare il file del certificato necessario per firmare il documento:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Modifica il nome del file e la password
```

## Fase 7: Firma del documento

 Infine, firmare il documento utilizzando il`DigitalSignatureUtil` classe. Salva il documento firmato con un nuovo nome per riferimento futuro.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Conclusione

Congratulazioni! Hai creato con successo un documento Word, aggiunto una riga di firma e firmato digitalmente utilizzando Aspose.Words per .NET. Questo potente strumento semplifica l'automazione dei documenti, assicurando che i tuoi contratti e documenti formali siano firmati e autenticati in modo sicuro.

## Domande frequenti

### Posso utilizzare altri formati di immagine per la riga della firma?

Sì, puoi utilizzare vari formati di immagine, tra cui PNG, JPG e BMP.

###  È necessario utilizzare un`.pfx` file for the certificate?

 Sì, un`.pfx` file è un formato standard per l'archiviazione di certificati e chiavi private per firme digitali.

### Posso aggiungere più righe di firma in un singolo documento?

Assolutamente! Puoi inserire più righe di firma ripetendo il passaggio di inserimento quando necessario.

### Cosa succede se non ho un certificato digitale?

Dovrai ottenere un certificato digitale da un'autorità di certificazione attendibile o generarne uno utilizzando strumenti come OpenSSL.

### Come posso verificare la firma digitale nel documento?

È possibile verificare la firma digitale aprendo il documento firmato in Word e controllando i dettagli della firma per confermarne l'autenticità e l'integrità.