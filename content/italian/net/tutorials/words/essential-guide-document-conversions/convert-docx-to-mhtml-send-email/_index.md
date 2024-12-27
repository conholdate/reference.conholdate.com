---
title: Converti DOCX in MHTML e invia e-mail utilizzando Aspose.Words per .NET
linktitle: Converti DOCX in MHTML e invia e-mail utilizzando Aspose.Words per .NET
second_title: API di elaborazione dei documenti Aspose.Words
description: Questa guida completa fornisce un tutorial dettagliato sulla conversione di documenti DOCX in formato MHTML e sul loro invio tramite e-mail utilizzando le librerie Aspose.Words e Aspose.Email in .NET.
type: docs
weight: 10
url: /it/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Introduzione

Nel panorama digitale odierno, convertire documenti tra formati e inviarli via email è un'attività comune. Questa guida ti guiderà nella conversione di un file DOCX in formato MHTML e nell'invio via email utilizzando le potenti librerie Aspose.Words e Aspose.Email per .NET. Analizzeremo ogni passaggio in modo chiaro, assicurandoti di poter seguire con facilità. Cominciamo!

## Prerequisiti

Prima di immergerti nel processo, assicurati di aver impostato quanto segue:

1.  Aspose.Words per .NET: Scarica e installa la libreria da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email per .NET: Scarica e installa questa libreria da[Pagina delle release di Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: assicurati che .NET Framework sia installato sul tuo computer.
4. Server SMTP: per inviare e-mail è necessario avere accesso a un server SMTP.

## Importazione degli spazi dei nomi necessari

Per utilizzare Aspose.Words e Aspose.Email nel tuo progetto, devi importare i namespace richiesti. Aggiungi le seguenti direttive using in cima al tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Passaggio 1: caricare il documento DOCX

 Inizia caricando il documento DOCX che desideri convertire. Utilizza il`Document` classe da Aspose.Words per ottenere questo risultato.

```csharp
// Specificare il percorso della directory del documento.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Passaggio 2: salvare il documento come MHTML

 Successivamente, converti il documento caricato in formato MHTML. Questo viene fatto utilizzando`Save` metodo del`Document` classe.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Reimposta la posizione del flusso all'inizio per la lettura.
    stream.Position = 0;
}
```

## Passaggio 3: creare un messaggio e-mail

Ora, crea un messaggio email dal flusso MHTML usando Aspose.Email. Utilizzerai`MailMessage` classe per questo scopo.

```csharp
// Carica il flusso MHTML in un messaggio di posta elettronica MIME Aspose.Email.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Passaggio 4: Invia l'e-mail

 Infine, invia l'email utilizzando un client SMTP. Configura il client SMTP con i dettagli del tuo server e utilizza`Send` metodo per inviare il messaggio.

```csharp
// Configurare e inviare il messaggio utilizzando Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Conclusione

Congratulazioni! Hai convertito con successo un documento DOCX in MHTML e lo hai inviato via email usando Aspose.Words e Aspose.Email per .NET. Questo processo prevede il caricamento del documento, la sua conversione in MHTML, la creazione di un messaggio email e l'invio tramite un client SMTP. Con questi passaggi, puoi automatizzare la conversione e l'invio di documenti via email senza problemi nelle tue applicazioni.

## Domande frequenti

### Posso usare questo metodo per convertire altri formati di documenti?
Assolutamente! Aspose.Words supporta un'ampia gamma di formati, consentendoti di convertire DOC, DOCX, RTF e altro in MHTML.

### Come posso aggiungere allegati all'email?
 Puoi aggiungere facilmente allegati utilizzando`Attachments` proprietà del`MailMessage` classe.

### Aspose.Words è compatibile con .NET Core?
Sì, Aspose.Words è compatibile con .NET Core, il che lo rende adatto all'uso nelle applicazioni .NET Core.

### Ho bisogno di una licenza per Aspose.Words e Aspose.Email?
 Sì, entrambe le librerie richiedono una licenza. Puoi ottenere una licenza temporanea per scopi di valutazione da[Pagina di acquisto Aspose](https://purchase.conholdate.com/temporary-license/).

### Dove posso trovare ulteriore documentazione?
 Per una documentazione dettagliata, consulta Aspose.Words[Qui](https://reference.aspose.com/words/net/) e Aspose.Email[Qui](https://reference.aspose.com/email/net/).