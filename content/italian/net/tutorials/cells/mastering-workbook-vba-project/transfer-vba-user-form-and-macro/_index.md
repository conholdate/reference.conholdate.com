---
title: Trasferisci moduli utente VBA e macro tra cartelle di lavoro Excel
linktitle: Trasferisci moduli utente VBA e macro tra cartelle di lavoro Excel
second_title: API di elaborazione Excel .NET Aspose.Cells
description: Sblocca la potenza dell'automazione di Excel con questa guida completa sul trasferimento di moduli utente VBA e macro tra cartelle di lavoro utilizzando Aspose.Cells per .NET. Perfetto sia per principianti che per sviluppatori esperti.
type: docs
weight: 11
url: /it/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Introduzione

Benvenuti alla guida definitiva per migliorare la vostra esperienza Excel usando macro VBA e moduli utente! In questo tutorial, esploreremo come trasferire un VBA Macro UserForm Designer da una cartella di lavoro a un'altra usando la potente libreria Aspose.Cells per .NET. Che siate sviluppatori esperti o alle prime armi, questa guida passo passo vi fornirà le conoscenze per gestire i file Excel a livello di programmazione. Pronti a tuffarvi? Cominciamo!

## Prerequisiti
Prima di passare alla codifica, assicuriamoci di avere tutto ciò di cui hai bisogno:

1. Ambiente di sviluppo C#: un ambiente di lavoro per lo sviluppo C#, con Visual Studio altamente consigliato.
2.  Aspose.Cells per la libreria .NET: assicurati di integrare la libreria Aspose.Cells nel tuo progetto. Puoi facilmente[scaricalo qui](https://releases.aspose.com/cells/net/).
3. Conoscenza di base di VBA e macro di Excel: la familiarità con VBA e con il funzionamento delle macro di Excel migliorerà la comprensione di questo tutorial.
4. Un file Excel con un modulo utente: crea o ottieni una cartella di lavoro Excel contenente un modulo utente (preferibilmente con macro abilitate, come`.xlsm` file).

## Importazione dei pacchetti richiesti
Per utilizzare le funzionalità fornite da Aspose.Cells, includi i seguenti namespace all'inizio del tuo file C#:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Questi namespace ti daranno accesso ai potenti strumenti incorporati nella libreria Aspose.Cells.

## Passaggio 1: definire le directory di origine e di output
Per prima cosa, stabilisci le posizioni dei tuoi file:

```csharp
// Definire le directory di origine e di output
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Sostituisci i percorsi segnaposto con le directory effettive in cui sono archiviati i tuoi file.

## Passaggio 2: creare una cartella di lavoro di destinazione vuota
Successivamente, crea una nuova cartella di lavoro in cui copierai il modulo utente e le macro:

```csharp
// Crea una cartella di lavoro di destinazione vuota
Workbook target = new Workbook();
```

In questo modo viene inizializzata una cartella di lavoro vuota, che fungerà da base per il trasferimento dei dati successivo.

## Passaggio 3: carica la cartella di lavoro del modello
Carica la cartella di lavoro contenente il tuo modulo utente e le macro:

```csharp
// Caricare il file Excel contenente il modulo utente di VBA-Macro Designer
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Regolare`"sampleDesignerForm.xlsm"` al nome del tuo file effettivo.

## Passaggio 4: Copiare i fogli di lavoro nella cartella di lavoro di destinazione
Ora, copiamo i fogli di lavoro dal modello alla cartella di lavoro di destinazione:

```csharp
// Copia tutti i fogli di lavoro modello nella cartella di lavoro di destinazione
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Aggiungere un messaggio nella cella A2 del foglio di lavoro di destinazione
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Questo codice esegue un ciclo su ogni foglio di lavoro nel modello e lo copia nella cartella di lavoro di destinazione, garantendo che tutti i dati vengano trasferiti senza problemi.

## Passaggio 5: Copiare le macro VBA dal modello
Successivamente, copieremo le macro VBA, inclusi i moduli UserForm Designer, nella nuova cartella di lavoro:

```csharp
// Copiare il modulo utente di VBA-Macro Designer dal modello alla destinazione
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Copia il codice del modulo ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Copia il codice e i dati di altri moduli
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Ottieni lo spazio di archiviazione del progettista del modulo utente
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Aggiungere l'archiviazione del progettista al progetto VBA di destinazione
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Questo codice garantisce che non solo il codice ma anche il design del modulo utente venga copiato, preservando la funzionalità delle macro.

## Passaggio 6: salvare la cartella di lavoro di destinazione
Dopo aver completato il processo di copia, salva la nuova cartella di lavoro:

```csharp
// Salvare la cartella di lavoro di destinazione
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Modifica il nome del file di output come necessario. Questo passaggio crea la tua cartella di lavoro personalizzata piena di macro e moduli utente.

## Passaggio 7: conferma il successo
Infine, visualizza un messaggio di successo sulla console:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Questa semplice frase ti rassicura che il tuo processo è andato liscio: una conferma essenziale del tuo duro lavoro!

## Conclusione
Congratulazioni! Hai imparato con successo come copiare un VBA Macro User Form Designer da una cartella di lavoro a un'altra usando Aspose.Cells per .NET. Anche se all'inizio può sembrare scoraggiante, la pratica ti renderà esperto nelle manipolazioni delle cartelle di lavoro. Ricorda, la codifica riguarda la sperimentazione, quindi non esitare a esplorare diverse funzionalità nei tuoi file Excel. Se hai domande o hai bisogno di assistenza, i forum e la documentazione di Aspose sono eccellenti risorse di supporto.

## Domande frequenti

### Quali versioni di Excel supporta Aspose.Cells?
Aspose.Cells supporta vari formati Excel, tra cui XLSX, XLSM, CSV e altri.

### Posso usare Aspose.Cells gratuitamente?
 Sì! Puoi iniziare con una prova gratuita per valutare la libreria:[Prova gratuita](https://releases.aspose.com/).

### Ho bisogno di Visual Studio per eseguire questo codice?
Sebbene Visual Studio sia consigliato per le sue funzionalità intuitive, qualsiasi IDE C# che supporti lo sviluppo .NET sarà sufficiente.

### Dove posso trovare altri esempi e documentazione?
 Puoi esplorare il[Documentazione di Aspose.Cells](https://reference.aspose.com/cells/net/) per ulteriori esempi e spiegazioni approfondite.

### Come posso risolvere i problemi durante l'utilizzo di Aspose.Cells?
 Dovresti visitare il[Forum di supporto Aspose](https://forum.aspose.com/c/cells/9) per ricevere aiuto dalla comunità e dal personale di supporto di Aspose.