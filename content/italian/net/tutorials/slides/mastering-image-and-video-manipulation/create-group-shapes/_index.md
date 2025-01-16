---
title: Crea forme di gruppo in PowerPoint con Aspose.Slides per .NET
linktitle: Crea forme di gruppo in PowerPoint con Aspose.Slides per .NET
second_title: API di elaborazione di PowerPoint Aspose.Slides .NET
description: Scopri come creare e gestire forme di gruppo usando Aspose.Slides per .NET. Questa guida completa fornisce istruzioni chiare e dettagliate.
type: docs
weight: 11
url: /it/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Introduzione

Migliorare l'aspetto visivo e l'organizzazione delle tue presentazioni PowerPoint può avere un impatto significativo sul coinvolgimento del tuo pubblico. Un metodo efficace per raggiungere questo obiettivo è tramite forme di gruppo. In questo tutorial, esploreremo come sfruttare Aspose.Slides per .NET per creare e manipolare forme di gruppo nelle tue presentazioni.

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di avere quanto segue:

-  Aspose.Slides per .NET: Scarica e installa l'ultima versione della libreria Aspose.Slides da[Sito web di Aspose](https://releases.aspose.com/slides/net/).
- Ambiente di sviluppo: configura un IDE compatibile con .NET, come Visual Studio, per lavorare sul tuo progetto.
- Conoscenze di base del linguaggio C#: familiarizzare con i concetti fondamentali del linguaggio C#.


## Importa gli spazi dei nomi necessari

Nel tuo progetto C#, inizia includendo i seguenti namespace:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Passaggio 1: istanziare la classe di presentazione

 Crea un'istanza di`Presentation`classe in cui lavorerai sulle tue slide. Specifica la directory in cui sono archiviati i tuoi documenti:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // I passaggi per creare e manipolare le forme andranno qui
}
```

## Passaggio 2: accedi alla prima diapositiva

Recupera la prima diapositiva della presentazione appena creata:

```csharp
ISlide slide = pres.Slides[0];
```

## Passaggio 3: accedi alla raccolta di forme

Ottieni la raccolta di forme nella diapositiva:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Passaggio 4: aggiungere una forma di gruppo

Adesso è il momento di aggiungere una forma di gruppo alla diapositiva:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Passaggio 5: aggiungere forme all'interno del gruppo

È possibile popolare la forma del gruppo con forme individuali, come rettangoli:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Forma 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Forma 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Forma 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Forma 4
```

## Passaggio 6: definire la cornice per la forma del gruppo

Impostando una cornice per la forma del gruppo si ottiene un confine definito:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Passaggio 7: Salva la presentazione

Infine, salva la presentazione modificata nella directory specificata:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Conclusione

Congratulazioni! Hai creato con successo forme di gruppo nelle tue presentazioni PowerPoint usando Aspose.Slides per .NET. Organizzando le forme in questo modo, puoi migliorare notevolmente il layout visivo e la chiarezza del tuo contenuto, rendendo le tue presentazioni più incisive.

## Domande frequenti

### Aspose.Slides è compatibile con l'ultima versione di .NET?

 Sì, Aspose.Slides viene aggiornato regolarmente per la compatibilità con le ultime versioni di .NET. Controlla il[documentazione](https://reference.aspose.com/slides/net/) per i dettagli più recenti sulla compatibilità.

### Posso provare Aspose.Slides prima di acquistarlo?

 Assolutamente! Puoi scaricare una versione di prova gratuita[Qui](https://releases.aspose.com/).

### Dove posso trovare supporto per le query relative ad Aspose.Slides?

 Visita Aspose.Slides[foro](https://forum.aspose.com/c/slides/11) per il supporto e le discussioni della comunità.

### Come posso ottenere una licenza temporanea per Aspose.Slides?

 Puoi richiedere una licenza temporanea[Qui](https://purchase.aspose.com/temporary-license/).

### Dove posso acquistare una licenza completa per Aspose.Slides?

 Puoi acquistare una licenza da[pagina di acquisto](https://purchase.aspose.com/buy).