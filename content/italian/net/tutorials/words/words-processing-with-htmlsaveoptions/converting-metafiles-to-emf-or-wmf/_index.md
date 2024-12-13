---
title: Conversione di metafile in Emf o Wmf
linktitle: Conversione di metafile in Emf o Wmf
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come convertire senza problemi le immagini SVG nei formati EMF o WMF nei documenti Word utilizzando Aspose.Words per .NET. Guida dettagliata con esempi di codice per risultati accurati e compatibili.
type: docs
weight: 10
url: /it/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-emf-or-wmf/
---
## Introduzione

Gestire e convertire in modo efficiente i formati delle immagini è una parte fondamentale della creazione di documenti Word professionali. In questa guida, approfondiamo l'uso di Aspose.Words per .NET per convertire le immagini SVG in formati EMF (Enhanced Metafile) o WMF (Windows Metafile) per un'integrazione senza soluzione di continuità. Questo tutorial fornisce istruzioni chiare e dettagliate per aiutare gli sviluppatori a implementare la conversione con facilità.

## Prerequisiti per la conversione da SVG a EMF o WMF

Per garantire un'esperienza di sviluppo fluida, verificare che siano soddisfatti i seguenti prerequisiti:

-  Aspose.Words per .NET: Ottieni l'ultima versione da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: verifica l'installazione di .NET Framework (o .NET Core/5/6 a seconda dell'ambiente).
- Ambiente di sviluppo: si consiglia Visual Studio per le sue funzionalità affidabili.
- Competenza in C#: è essenziale avere familiarità con la programmazione C#.

## Importazione degli spazi dei nomi richiesti

Nel tuo progetto, importa gli spazi dei nomi necessari per accedere alle funzionalità di Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: definire la directory dei documenti

Imposta un percorso di directory in cui verranno archiviati i tuoi documenti Word. Ciò è essenziale per gestire efficacemente i file di output.

```csharp
string dataDir = @"C:\MyDocuments\";
```

 Sostituire`@"C:\MyDocuments\"` con il percorso desiderato.

## Passaggio 2: preparare la stringa HTML contenente SVG

Componi una stringa HTML che incorpora il tuo contenuto SVG. Ciò consente ad Aspose.Words di eseguire il rendering e l'elaborazione dell'SVG.

```csharp
string htmlContent = 
    @"<html>
        <body>
            <svg xmlns='http://www.w3.org/2000/svg' width='300' height='100' viewBox='0 0 300 100'>
                <rect x='10' y='10' width='280' height='80' fill='blue' stroke='black' stroke-width='2'/>
                <text x='20' y='60' fill='white' font-size='20'>Aspose SVG Example</text>
            </svg>
        </body>
    </html>";
```

## Passaggio 3: configurare le opzioni di caricamento HTML

 Per garantire la corretta gestione della conversione SVG, configurare`HtmlLoadOptions` con`ConvertSvgToEmf`.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    ConvertSvgToEmf = true
};
```

## Passaggio 4: caricare l'HTML in un documento Word

 Utilizzare le opzioni di carico configurate per creare un`Document` oggetto dalla stringa HTML.

```csharp
using (MemoryStream htmlStream = new MemoryStream(Encoding.UTF8.GetBytes(htmlContent)))
{
    Document document = new Document(htmlStream, loadOptions);
}
```

## Passaggio 5: configurare le opzioni di salvataggio per EMF/WMF

 Personalizza le opzioni di salvataggio per definire il formato metafile desiderato. Qui, scegliamo`HtmlMetafileFormat.Emf`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Emf
};
```

## Passaggio 6: Salvare il documento

Salvare il documento utilizzando le opzioni di salvataggio specificate.

```csharp
document.Save(dataDir + "ConvertedDocument.emf", saveOptions);
```

Il file risultante conterrà il contenuto SVG convertito nel formato EMF.

## Conclusione

Questo tutorial ha dimostrato come convertire le immagini SVG in formati EMF o WMF usando Aspose.Words per .NET. Seguendo questi passaggi, puoi migliorare la compatibilità e la fedeltà visiva dei tuoi documenti Word. Che tu stia automatizzando la creazione di documenti o preparando report di alta qualità, questo metodo assicura risultati impeccabili.

## Domande frequenti

### Posso usare questo metodo per elaborare in batch più SVG?
Sì, è possibile scorrere più file HTML contenenti SVG, applicando lo stesso processo in un ciclo.

### Qual è la differenza tra EMF e WMF?
EMF è una versione migliorata di WMF, che offre un supporto migliore per grafici complessi e dimensioni di dati maggiori.

### Aspose.Words è compatibile con .NET Core?
Sì, Aspose.Words per .NET supporta .NET Core e .NET 5/6, rendendolo adatto alle moderne applicazioni multipiattaforma.

### Posso mantenere il formato SVG originale nell'output?
No, questo metodo converte specificamente SVG in EMF/WMF. Tuttavia, puoi mantenere l'SVG originale incorporandolo direttamente nel documento senza conversione.

### Dove posso scaricare una versione di prova gratuita di Aspose.Words?
 Puoi scaricare una versione di prova gratuita da[Pagina delle release di Aspose](https://releases.aspose.com/).