---
title: Tieni traccia dei progressi della conversione e-mail con Aspose.Email per .NET
linktitle: Tieni traccia dei progressi della conversione e-mail con Aspose.Email per .NET
second_title: API di elaborazione e-mail Aspose.Email .NET
description: Scopri passo dopo passo come monitorare i progressi della conversione delle email in C# usando Aspose.Email per .NET. Aumenta l'efficienza del tuo progetto con questo tutorial dettagliato.
type: docs
weight: 12
url: /it/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## Introduzione

La gestione efficiente dei documenti di posta elettronica spesso implica il monitoraggio dei progressi della loro conversione. Aspose.Email per .NET fornisce strumenti robusti per raggiungere questo obiettivo, consentendo agli sviluppatori di gestire le operazioni di posta elettronica senza problemi. Questo tutorial si addentra in come è possibile monitorare i progressi della conversione dei documenti di posta elettronica in C#, suddividendo il processo passo dopo passo per una facile comprensione.  

## Prerequisiti  

Prima di immergerci nel tutorial, assicuriamoci che tutto sia impostato:  

1.  Aspose.Email per .NET: Scarica e installa il[Aspose.Email per .NET](https://releases.aspose.com/email/net/) biblioteca.  
2. Ambiente di sviluppo: installare Visual Studio o qualsiasi altro IDE compatibile con .NET.  
3. .NET Framework: assicurarsi che sia installato .NET Framework 4.5 o versione successiva.  
4.  Patente temporanea: valutare l'ottenimento di una[licenza temporanea](https://purchase.aspose.com/temporary-license/) per esplorare tutte le funzionalità di Aspose.Email.  
5.  Esempio di file di posta elettronica: preparare un`.eml` file (ad esempio,`test.eml`) da utilizzare come campione.  

## Importa pacchetti  

Per usare Aspose.Email nel tuo progetto, dovrai importare i namespace richiesti. Aggiungi le seguenti istruzioni using all'inizio del tuo file:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## Passaggio 1: imposta il tuo progetto  

Inizia creando una nuova applicazione console C# in Visual Studio. Questa fungerà da base per l'implementazione del monitoraggio della conversione dei documenti e-mail.  
  
1. Aprire Visual Studio e creare un nuovo progetto di applicazione console.  
2. Installa il pacchetto NuGet Aspose.Email:  
```sh
Install-Package Aspose.Email
```  
3.  Aggiungere il`.eml` file nella directory del progetto.  

## Passaggio 2: caricare il file di posta elettronica  

 Ora, carica il file di posta elettronica in un`MailMessage` oggetto. Questo è il primo passo per lavorare con i dati di posta elettronica.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: Specifica la directory in cui si trova il file di posta elettronica.  
- `MailMessage.Load` : Legge il`.eml` file e lo prepara per ulteriori operazioni.  

## Passaggio 3: inizializzare un flusso di memoria  

 Quindi, crea un`MemoryStream` oggetto per memorizzare temporaneamente i dati e-mail convertiti.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 UN`MemoryStream` viene utilizzato qui per gestire l'output del processo di conversione senza salvare i dati direttamente sul disco.  

## Passaggio 4: definire le opzioni di conversione  

 Impostare il`EmlSaveOptions` con un gestore di avanzamento personalizzato per monitorare l'avanzamento della conversione.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: Specifica il formato di output.  
- `CustomProgressHandler`: Assegna una funzione di gestione personalizzata per monitorare i progressi.  

## Passaggio 5: salva l'e-mail nel flusso di memoria  

Salva il`MailMessage` oggetto utilizzando le opzioni specificate, abilitando la funzionalità di monitoraggio dell'avanzamento.  
 
```csharp
msg.Save(ms, opt);
```
 
Questo passaggio avvia il processo di conversione dell'e-mail e invia aggiornamenti al gestore dell'avanzamento.  

## Fase 6: implementare il gestore dei progressi  

 Definisci il`ShowEmlConversionProgress` Metodo per gestire gli aggiornamenti sullo stato di avanzamento e visualizzarli nella console.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: Fornisce dettagli sul processo di conversione.  
-  Casi di commutazione: Gestisci diverse fasi della conversione:`MimeStructureCreated`, `MimePartSaved` , E`SavedToStream`.  

### Cosa aspettarsi?  
Man mano che la conversione procede, sulla console verranno stampati aggiornamenti dettagliati, come:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## Conclusione  

Monitorare l'avanzamento della conversione di documenti email in C# non è mai stato così facile, grazie ad Aspose.Email per .NET. Seguendo questo tutorial, hai imparato come caricare un file email, impostare un gestore di avanzamento e salvare i dati email monitorando l'intero processo. Questa funzionalità ti assicura di rimanere informato e in controllo durante le operazioni sui documenti email.  

## Domande frequenti  

###  Posso usare questo codice per formati diversi da`.eml`?  
 Sì, modifica il`MailMessageSaveType`per adattarsi ad altri formati come MSG o MHTML.  

### Come posso gestire file di posta elettronica di grandi dimensioni?  
 Considerare l'utilizzo di un`FileStream` invece di un`MemoryStream` per prestazioni migliori con file di grandi dimensioni.  

### Cos'è una licenza temporanea e come posso ottenerla?  
 Una licenza temporanea ti consente di valutare gratuitamente tutte le funzionalità della libreria. Ottienila[Qui](https://purchase.aspose.com/temporary-license/).  

### Posso integrare questo codice in un'applicazione web?  
Sì, il codice è compatibile con le applicazioni web che utilizzano ASP.NET o framework simili.  

### Dove posso trovare risorse aggiuntive?  
 Dai un'occhiata al[documentazione](https://reference.aspose.com/email/net/) o visitare il[forum di supporto](https://forum.aspose.com/c/email/12/) per chiedere aiuto.  