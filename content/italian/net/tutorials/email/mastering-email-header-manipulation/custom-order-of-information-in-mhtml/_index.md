---
title: Ordine personalizzato delle informazioni in MHTML con Aspose.Email
linktitle: Ordine personalizzato delle informazioni in MHTML con Aspose.Email
second_title: API di elaborazione e-mail Aspose.Email .NET
description: Scopri come definire l'ordine personalizzato delle informazioni in MHTML utilizzando Aspose.Email per .NET in questo tutorial passo dopo passo.
type: docs
weight: 14
url: /it/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## Introduzione

La creazione di formati di posta elettronica avanzati può migliorare notevolmente la comunicazione, in particolare quando si esportano e-mail in formati di file diversi come MHTML. Aspose.Email per .NET fornisce agli sviluppatori un potente toolkit per la manipolazione delle e-mail, che include la definizione di un ordine personalizzato per la visualizzazione delle informazioni durante l'esportazione in MHTML. In questa guida, analizzeremo i passaggi necessari per raggiungere questo obiettivo, rendendolo facile da seguire sia che tu sia uno sviluppatore esperto o che tu stia appena iniziando. Quindi, iniziamo subito!

## Prerequisiti

Prima di addentrarti nella definizione dell'ordine personalizzato delle informazioni in MHTML, ci sono alcuni prerequisiti che devi verificare:

1. Ambiente di sviluppo .NET: assicurati di avere un ambiente di sviluppo .NET configurato. Puoi usare Visual Studio, Visual Studio Code o qualsiasi altro IDE compatibile.

2.  Libreria Aspose.Email: è necessario che sia installata la libreria Aspose.Email per .NET. È possibile scaricare l'ultima versione da[Pagina delle release di Aspose](https://releases.aspose.com/email/net/).

3. Nozioni di base di C#: la familiarità con la programmazione C# ti aiuterà a comprendere meglio il codice.

4.  Esempio di file e-mail: avrai bisogno di un campione`.eml` file (ad esempio,`Attachments.eml`) a scopo di test.

Una volta soddisfatti questi prerequisiti, sei pronto per seguire il tutorial!

## Importa pacchetti

Per iniziare con il tuo codice, dovrai importare i namespace necessari dalla libreria Aspose.Email. Questo è essenziale per accedere a tutte le classi e i metodi necessari per manipolare i file email.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

Includili all'inizio del tuo file C#. Ora sei pronto per immergerti nella codifica!

Ora che hai impostato tutto, suddividiamo il tutorial in passaggi gestibili.

## Passaggio 1: imposta la directory dei dati

La prima cosa da fare è stabilire una directory in cui verranno archiviati i file di posta elettronica. Potrebbe essere qualsiasi percorso sulla tua macchina locale.

```csharp
string dataDir = "Your Data Directory";
```

 Sostituire`"Your Data Directory"` con il percorso effettivo in cui ti trovi`.eml` il file si trova. Ad esempio, se il tuo file si trova in`C:\Emails`, scriveresti:

```csharp
string dataDir = @"C:\Emails\";
```

## Passaggio 2: carica il messaggio e-mail

Successivamente, è necessario caricare il`.eml` file in un`MailMessage` oggetto. Ciò consente di manipolare il contenuto e i metadati dell'email.

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

Assicurati che il nome del file corrisponda a quello che hai nella directory specificata. Se il tuo file ha un nome diverso, aggiorna il nome del file di conseguenza.

## Passaggio 3: imposta le opzioni di salvataggio MHTML

Una volta caricata la tua email, è il momento di definire come vuoi salvarla come MHTML. Puoi iniziare con le opzioni predefinite.

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

Questa riga inizializza le opzioni di salvataggio MHTML, preparando il terreno per la successiva personalizzazione delle intestazioni.

## Passaggio 4: Salva MHTML con ordine predefinito

Salviamo l'email come MHTML usando l'ordine predefinito. Questo ti dà una base di riferimento con cui fare un confronto dopo la personalizzazione.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

 Esegui questa riga e controlla la directory specificata. Ora dovresti vedere un nuovo file MHTML denominato`CustomOrderOfInformationInMHTML_1.mhtml`Aprilo per vedere come vengono visualizzate le informazioni per impostazione predefinita.

## Passaggio 5: personalizzare l'ordine dell'intestazione

Ora arriva la parte divertente! Puoi specificare quali intestazioni includere nell'output MHTML e in quale ordine. Inizieremo con alcune intestazioni comuni.

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

Aggiungendo queste intestazioni, stai comunicando ad Aspose come desideri che venga visualizzata l'email.

## Passaggio 6: Salva MHTML con ordine personalizzato

Dopo aver personalizzato le intestazioni, è necessario salvare nuovamente l'e-mail come MHTML per vedere come il nuovo ordine influisce sull'output.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

 Esegui questo codice, quindi apri`CustomOrderOfInformationInMHTML_2.mhtml`Confrontalo con il primo per vedere come sono cambiate le informazioni in base all'ordine dell'intestazione.

## Passaggio 7: Cancella e aggiungi un nuovo ordine di intestazione

E se volessi un ordine completamente diverso? Puoi ricominciare da capo cancellando le impostazioni dell'intestazione esistenti.

```csharp
opt.RenderingHeaders.Clear();
```

Ora è il momento di definire un nuovo ordine per le intestazioni. Ad esempio, se vuoi dare priorità agli allegati e ai destinatari delle copie:

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## Passaggio 8: Salva MHTML con nuovo ordine personalizzato

Infine, salva l'email un'ultima volta con le nuove impostazioni dell'intestazione.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

 Dopo aver eseguito questa riga, apri`CustomOrderOfInformationInMHTML_3.mhtml` controlla come vengono presentate le informazioni in base alla tua nuova personalizzazione.

## Conclusione

Ed ecco fatto: una guida semplice per definire un ordine personalizzato di informazioni in MHTML usando Aspose.Email per .NET. Seguendo questi passaggi, puoi controllare come le tue email sono rappresentate in formato MHTML, assicurandoti che le informazioni più importanti siano presentate in un modo che si adatti alle tue esigenze. 

## Domande frequenti

### Che cos'è MHTML?
MHTML sta per "MIME HTML", un formato di archivio di pagine web che combina HTML e altre risorse come le immagini.

### Posso usare Aspose.Email gratuitamente?
 Sì, Aspose fornisce una versione di prova gratuita per gli sviluppatori da esplorare. Puoi trovarla[Qui](https://releases.aspose.com/).

### Cosa succede se riscontro problemi utilizzando Aspose.Email?
 Puoi ottenere supporto dalla comunità tramite[Forum di Aspose](https://forum.aspose.com/c/email/12/).

### È disponibile una licenza temporanea per Aspose.Email?
 Sì, puoi richiedere una licenza temporanea[Qui](https://purchase.aspose.com/temporary-license/).

### Dove posso acquistare Aspose.Email?
 Puoi acquistare la biblioteca qui[collegamento](https://purchase.aspose.com/buy).