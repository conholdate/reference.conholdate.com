---
title: Extraire l'audio des hyperliens dans PowerPoint à l'aide d'Aspose.Slides
linktitle: Extraire l'audio des hyperliens
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Découvrez comment extraire l'audio des hyperliens dans les présentations PowerPoint avec Aspose.Slides pour .NET. Ce guide étape par étape fournit des instructions claires.
type: docs
weight: 12
url: /fr/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## Introduction

Dans les présentations multimédias, l'audio améliore considérablement l'impact de vos diapositives. Si vous avez déjà rencontré une présentation PowerPoint avec des liens hypertexte audio et que vous vous êtes demandé comment extraire cet audio pour d'autres utilisations, vous êtes au bon endroit. Ce guide vous guidera tout au long du processus d'extraction de l'audio à partir des liens hypertexte dans une présentation PowerPoint à l'aide de la bibliothèque Aspose.Slides pour .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

### Bibliothèque Aspose.Slides pour .NET

 Assurez-vous que la bibliothèque Aspose.Slides pour .NET est installée. Si vous ne l'avez pas encore fait, vous pouvez la télécharger à partir du[Documentation Aspose.Slides pour .NET](https://reference.aspose.com/slides/net/).

### Présentation PowerPoint avec hyperliens audio

Vous aurez besoin d'une présentation PowerPoint (PPTX) contenant des hyperliens avec l'audio associé. Cette présentation sera votre source pour l'extraction audio.

## Importation des espaces de noms requis

Pour utiliser efficacement Aspose.Slides pour .NET, vous devez importer les espaces de noms suivants dans votre projet C# :

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Maintenant que tout est en place, décomposons le processus d’extraction en étapes simples.

## Étape 1 : Définir le répertoire des documents

 Commencez par spécifier le répertoire dans lequel se trouve votre présentation PowerPoint. Remplacez`"Your Document Directory"` avec le chemin réel.

```csharp
string dataDir = "Your Document Directory";
```

## Étape 2 : Charger la présentation PowerPoint

 Ensuite, chargez la présentation PowerPoint (PPTX) qui contient le lien hypertexte audio. Remplacer`"HyperlinkSound.pptx"` avec le nom de votre fichier de présentation réel.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Passez à l’étape suivante.
}
```

## Étape 3 : Accéder au lien hypertexte sonore

Récupérez l'hyperlien de la première forme de la première diapositive. Si cet hyperlien est associé à un son, nous pouvons procéder à son extraction.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Passez à l’étape suivante.
}
```

## Étape 4 : Extraire l'audio du lien hypertexte

Si l'hyperlien contient du son, nous pouvons l'extraire sous forme de tableau d'octets et l'enregistrer sous forme de fichier multimédia.

```csharp
// Extraire le son du lien hypertexte sous forme de tableau d'octets
byte[] audioData = link.Sound.BinaryData;

// Spécifiez le chemin où vous souhaitez enregistrer l'audio extrait
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Enregistrez l'audio extrait dans un fichier multimédia
File.WriteAllBytes(outMediaPath, audioData);
```

Félicitations ! Vous avez réussi à extraire l'audio d'un lien hypertexte dans une présentation PowerPoint à l'aide d'Aspose.Slides pour .NET. Vous pouvez désormais utiliser cet audio dans vos projets multimédias.

## Conclusion

Aspose.Slides pour .NET offre un moyen puissant et convivial d'extraire l'audio des hyperliens dans les présentations PowerPoint. Grâce aux étapes décrites dans ce guide, vous pouvez facilement réutiliser le contenu audio de vos présentations pour améliorer vos projets.

## FAQ

### Aspose.Slides pour .NET est-elle une bibliothèque gratuite ?
 Non, Aspose.Slides pour .NET est une bibliothèque commerciale, mais vous pouvez télécharger une version d'essai gratuite pour explorer ses fonctionnalités à partir de[ici](https://releases.aspose.com/).

### Puis-je extraire l'audio d'anciens formats PowerPoint comme PPT ?
Oui, Aspose.Slides pour .NET prend en charge les formats PPTX et PPT pour l'extraction audio.

### Existe-t-il un forum communautaire pour le support d'Aspose.Slides ?
 Absolument ! Vous pouvez obtenir de l'aide et partager vos expériences dans le[Forum communautaire Aspose.Slides](https://forum.aspose.com/).

### Puis-je acheter une licence temporaire pour Aspose.Slides pour un projet à court terme ?
Oui, vous pouvez obtenir une licence temporaire pour vos besoins de projet à court terme en visitant[ce lien](https://purchase.aspose.com/temporary-license/).

### Existe-t-il d’autres formats audio pris en charge pour l’extraction en dehors de MPG ?
Oui, Aspose.Slides pour .NET permet l'extraction dans divers formats audio. Vous pouvez convertir l'audio dans votre format préféré après l'extraction.