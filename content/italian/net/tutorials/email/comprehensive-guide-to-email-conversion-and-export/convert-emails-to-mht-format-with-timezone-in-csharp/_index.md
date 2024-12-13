---
title: Convertire le email in formato MHT con fuso orario in C#
linktitle: Convertire le email in formato MHT con fuso orario in C#
second_title: API di elaborazione e-mail Aspose.Email .NET
description: Questa guida dettagliata fornisce istruzioni chiare su come convertire i messaggi di posta elettronica nel formato MHT, gestendo con precisione le informazioni sul fuso orario mediante la libreria Aspose.Email per .NET.
type: docs
weight: 12
url: /it/net/tutorials/email/comprehensive-guide-to-email-conversion-and-export/convert-emails-to-mht-format-with-timezone-in-csharp/
---
## Introduzione

Convertire i messaggi di posta elettronica in vari formati è un'attività comune nelle applicazioni software, specialmente in scenari in cui i dati di ora e fuso orario sono cruciali. Questa guida ti guiderà attraverso il processo di conversione delle e-mail in formato MHT, assicurandoti che le informazioni sul fuso orario siano accuratamente conservate.

## Impostazione dell'ambiente di sviluppo

Per iniziare, assicurati di disporre di un ambiente di sviluppo adatto:

1. Installa Visual Studio: assicurati di avere una versione compatibile di Visual Studio installata sul tuo computer.
2. Crea un nuovo progetto C#: avvia Visual Studio e crea un nuovo progetto C# per la tua applicazione di conversione e-mail.

## Installazione di Aspose.Email per .NET

Aspose.Email per .NET è una potente libreria che semplifica le attività di elaborazione delle email. Segui questi passaggi per installarla:

1. Apri il tuo progetto in Visual Studio.
2. Passare a Strumenti > Gestore pacchetti NuGet > Gestisci pacchetti NuGet per la soluzione.
3. Cerca Aspose.Email e installa il pacchetto.
```csharp
// Aggiungere le istruzioni di utilizzo necessarie
using Aspose.Email;
```
## Caricamento e analisi dei messaggi di posta elettronica

Successivamente, dovrai caricare e analizzare il messaggio email che desideri convertire. Utilizza il seguente frammento di codice:

```csharp
// Carica il messaggio di posta elettronica
var message = MailMessage.Load("path/to/your/email.eml");

// Accedi alle proprietà del messaggio
var subject = message.Subject;
var sender = message.From.Address;
// ... altre proprietà secondo necessità
```

## Gestione delle informazioni sul fuso orario

Gestire accuratamente le informazioni sul fuso orario è fondamentale. Il seguente frammento di codice mostra come estrarre e gestire i dati sul fuso orario da un messaggio di posta elettronica:

```csharp
var timezone = message.TimezoneOffset;
var timezoneId = Timezone.GetIdFromOffset(timezone);
var timezoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timezoneId);
// Ora puoi usare timezoneInfo per gestire le conversioni di fuso orario
```

## Conversione di e-mail in formato MHT

Ora eseguiamo la conversione del core nel formato MHT utilizzando Aspose.Email:

```csharp
// Imposta le opzioni di salvataggio MHT
var mhtOptions = MhtSaveOptions.DefaultMhtml;

// Crea un flusso di memoria per l'output MHT
using var mhtStream = new MemoryStream();
message.Save(mhtStream, mhtOptions);
```

## Salvataggio del file MHT

Una volta convertito il messaggio di posta elettronica nel formato MHT, è il momento di salvarlo come file:

```csharp
// Salvare il flusso MHT in un file
using var fileStream = new FileStream("output.mht", FileMode.Create);
mhtStream.Seek(0, SeekOrigin.Begin);
mhtStream.CopyTo(fileStream);
```

## Conclusione

In questa guida, hai imparato come convertire i messaggi email in formato MHT gestendo in modo efficace le informazioni sul fuso orario tramite Aspose.Email per .NET. Seguendo questi passaggi ed esplorando ulteriori opzioni di personalizzazione, puoi integrare senza problemi la funzionalità di conversione email nelle tue applicazioni.

## Domande frequenti

### Come gestire gli allegati durante la conversione delle email?

 Per gestire gli allegati, utilizzare`Attachments` proprietà del`MailMessage` classe. Scorrere gli allegati e salvarli quando necessario durante il processo di conversione.

### Posso convertire le email in altri formati utilizzando Aspose.Email per .NET?

Assolutamente! Aspose.Email per .NET supporta vari formati, tra cui MSG, EML, PST e altri. Puoi adattare gli esempi di codice forniti per adattarli al formato di output desiderato.

### Le informazioni sul fuso orario vengono conservate nel formato MHT?

 Sì, le informazioni sul fuso orario vengono conservate durante il processo di conversione. Gestire gli offset del fuso orario e utilizzare l'appropriato`TimeZoneInfo`metodi, è possibile garantire una rappresentazione accurata del fuso orario nel file MHT.

### Dove posso trovare ulteriore documentazione e aggiornamenti su Aspose.Email per .NET?

 Per informazioni complete e aggiornamenti, fare riferimento alla documentazione:[Riferimento API Aspose.Email per .NET](https://reference.aspose.com/email/net/)

### Come posso scaricare l'ultima versione di Aspose.Email per .NET?

 Puoi scaricare l'ultima versione dalla pagina delle release:[Scarica Aspose.Email per .NET](https://releases.aspose.com/email/net/)