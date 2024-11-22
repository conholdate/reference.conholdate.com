---
title: Renderizza una vista panoramica di una scena 3D usando Aspose.3D per .NET
linktitle: Renderizza una vista panoramica di una scena 3D
second_title: API .NET di Aspose.3D
description: Scopri come realizzare un'incredibile vista panoramica di una scena 3D nelle tue applicazioni .NET usando Aspose.3D. Segui la nostra guida passo passo per il rendering immersivo della scena.
type: docs
weight: 13
url: /it/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Introduzione

Creare scene 3D panoramiche e immersive è un punto di svolta per gli sviluppatori che vogliono migliorare le proprie applicazioni con effetti visivi sbalorditivi. Che tu stia lavorando su un motore di gioco, una visualizzazione architettonica o esperienze web immersive, il rendering di scene 3D come panorami consente agli utenti di sperimentare una vista dinamica da tutte le angolazioni. Aspose.3D per .NET è lo strumento perfetto per integrare perfettamente questa funzionalità nei tuoi progetti .NET. Questa guida completa ti guiderà attraverso il processo di rendering di un panorama da una scena 3D utilizzando Aspose.3D per .NET.

## Prerequisiti

Prima di immergerti nel processo di rendering, assicurati di avere a disposizione quanto segue:

-  Aspose.3D per .NET: per iniziare, è necessario installare Aspose.3D, che fornisce tutti gli strumenti necessari per la gestione delle risorse 3D e il rendering.[Scarica Aspose.3D per .NET](https://releases.aspose.com/3d/net/) per iniziare.
- Ambiente di sviluppo .NET: è richiesto un ambiente di sviluppo .NET completamente configurato. Assicurati di avere Visual Studio o qualsiasi altro IDE compatibile.
- Esempio di file di scena 3D: puoi utilizzare qualsiasi scena 3D in formati come`.glb`, `.fbx` , O`.obj`Per questo tutorial, useremo un semplice file "VirtualCity.glb".

Una volta soddisfatti questi prerequisiti, possiamo passare alla configurazione della scena.

## Importa gli spazi dei nomi necessari

Per lavorare con Aspose.3D, dovremo importare diversi namespace nel nostro progetto. Questi namespace consentono di manipolare in modo efficiente oggetti 3D, impostazioni della telecamera e opzioni di rendering.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Questi namespace sono essenziali per caricare la scena 3D, configurare la telecamera, l'illuminazione e impostare le texture di rendering che formano la vista panoramica.

## Passaggio 1: carica la scena 3D nella tua applicazione

 Il primo passo è caricare la scena 3D nella tua applicazione. Questo può essere fatto usando`Scene` classe fornita da Aspose.3D. Sostituisci`"VirtualCity.glb"` con il percorso al file della scena 3D.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 IL`Scene` L'oggetto carica la scena 3D nella memoria, consentendo di interagire con essa e di applicare tecniche di rendering.

## Fase 2: Impostare la telecamera e le luci

Per assicurarti che la tua scena 3D venga catturata correttamente, dovrai impostare una telecamera e un'illuminazione appropriata. La telecamera ti consente di controllare la prospettiva della scena, mentre le luci aiutano a illuminare gli oggetti.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Impostazione della telecamera: i piani vicino e lontano della telecamera sono impostati per definire l'intervallo visibile nella scena 3D.
- Impostazione delle luci: vengono aggiunte due luci, una puntiforme e un'altra con un colore specifico, per aggiungere profondità e realismo alla scena.

## Passaggio 3: impostare il motore di rendering e definire i target di rendering

Ora che la scena, la telecamera e le luci sono impostate, il passo successivo è creare il renderer e definire i render target. Il renderer è responsabile della generazione delle immagini 3D e i render target definiscono dove verrà archiviato l'output finale.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Texture di rendering cubo: viene utilizzata per il rendering di una mappa cubo per la vista panoramica. Definiamo qui una texture 512x512.
- Texture di rendering finale: questa è la texture che conterrà la vista panoramica equrettangolare finale.

## Passaggio 4: configurare la viewport e rendere la scena

Dopo aver creato le texture di rendering, dobbiamo configurare la viewport, che definisce la regione della scena 3D che verrà catturata dalla telecamera.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Questo codice imposta la finestra per la mappa del cubo e rende la scena in`rt` rendere la texture.

## Passaggio 5: applicare la post-elaborazione per la proiezione equrettangolare

A questo punto, dobbiamo applicare la post-elaborazione per convertire la mappa del cubo in una vista panoramica equirettangolare. Questa trasformazione assicura che l'immagine finale sarà un panorama appropriato.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Proiezione equirettangolare: questo effetto di post-elaborazione prende la mappa del cubo e la trasforma in una proiezione panoramica equirettangolare, fornendo una vista fluida a 360 gradi.

## Passaggio 6: Salvare il panorama renderizzato

Una volta completati il rendering e la post-elaborazione, l'ultimo passaggio consiste nel salvare il panorama finale in un file immagine, ad esempio un PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

In questo modo l'immagine panoramica viene salvata nella directory specificata, consentendo di integrarla nella propria applicazione o di visualizzarla su un sito web.

## Conclusione

Il rendering di viste panoramiche di scene 3D non è mai stato così facile con Aspose.3D per .NET. Seguendo i passaggi descritti sopra, puoi caricare facilmente una scena 3D, configurare la telecamera e le luci, eseguire il rendering della scena e applicare effetti di post-elaborazione per generare immagini panoramiche immersive. Aspose.3D per .NET fornisce la potenza e la flessibilità per dare vita alle tue visualizzazioni 3D e integrarle senza soluzione di continuità nelle tue applicazioni.

## Domande frequenti

### Posso usare la mia scena 3D per il rendering dei panorami?
Assolutamente. Sostituisci semplicemente il percorso del file della scena campione con la posizione della tua scena 3D personalizzata.

### Sono disponibili ulteriori effetti di post-elaborazione?
Sì, Aspose.3D offre una gamma di effetti di post-elaborazione, come profondità di campo, bloom e altro ancora, che possono essere applicati per migliorare le immagini renderizzate.

### Come posso ottimizzare le prestazioni di rendering?
Le prestazioni di rendering possono essere ottimizzate regolando parametri quali la dimensione e la risoluzione della texture di rendering, nonché modificando i piani vicini e lontani della telecamera.

### Posso integrarlo in un'applicazione web?
Sì, Aspose.3D per .NET può essere integrato nelle applicazioni web .NET per il rendering dinamico di panorami 3D.

### Esiste un forum della community per il supporto di Aspose.3D?
 Sì, puoi visitare il[Forum di Aspose.3D](https://forum.aspose.com/c/3d/18) per supporto e discussioni nella comunità.