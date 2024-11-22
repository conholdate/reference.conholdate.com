---
title: Maîtriser les effets d'après-animation avec Aspose.Slides pour .NET
linktitle: Maîtriser les effets d'après-animation avec Aspose.Slides pour .NET
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Libérez tout le potentiel de vos présentations en maîtrisant les effets d'après-animation avec Aspose.Slides pour .NET. Ce guide étape par étape vous fournit l'essentiel.
type: docs
weight: 11
url: /fr/net/tutorials/slides/master-slide-animation-control/control-after-animation-effects/
---
## Introduction

Les animations dynamiques peuvent améliorer considérablement vos présentations, les rendant plus attrayantes et visuellement plus attrayantes. Avec Aspose.Slides pour .NET, vous pouvez facilement contrôler les effets post-animation, ce qui vous permet de créer des expériences interactives pour votre public. Ce didacticiel vous guidera étape par étape dans le processus de manipulation de ces effets dans vos diapositives.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

- Connaissances de base de la programmation C# et .NET.
-  La bibliothèque Aspose.Slides pour .NET est installée. Téléchargez-la[ici](https://releases.aspose.com/slides/net/).
- Un environnement de développement intégré (IDE) comme Visual Studio.

## Importer des espaces de noms

Pour accéder aux fonctionnalités Aspose.Slides nécessaires, incluez les espaces de noms suivants dans votre code :

```csharp
using System.Drawing;
using System.IO;
using Aspose.Slides.Animation;
using Aspose.Slides.SlideShow;
using Aspose.Slides.Export;
```

## Étape 1 : Configurer le répertoire de documents

Commencez par vérifier que le répertoire de vos documents existe. Si ce n'est pas le cas, créez-le :

```csharp
string dataDir = "Your Document Directory";
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## Étape 2 : définir le chemin du fichier de sortie

Spécifiez le chemin du fichier de sortie pour votre présentation modifiée :

```csharp
string outPath = Path.Combine(dataDir, "AnimationAfterEffect-out.pptx");
```

## Étape 3 : Charger la présentation

 Chargez votre présentation existante à l'aide de la`Presentation` classe:

```csharp
using (Presentation pres = new Presentation(dataDir + "AnimationAfterEffect.pptx"))
```

## Étape 4 : Modifier les effets d'animation sur la diapositive 1

Clonez la première diapositive et définissez son effet post-animation sur « Masquer au prochain clic de souris » :

```csharp
ISlide slide1 = pres.Slides.AddClone(pres.Slides[0]);
ISequence seq = slide1.Timeline.MainSequence;
foreach (IEffect effect in seq)
    effect.AfterAnimationType = AfterAnimationType.HideOnNextMouseClick;
```

## Étape 5 : Modifier les effets d'animation sur la diapositive 2

Clonez à nouveau la première diapositive, en changeant l'effet d'après-animation en « Couleur » avec une teinte verte :

```csharp
ISlide slide2 = pres.Slides.AddClone(pres.Slides[0]);
seq = slide2.Timeline.MainSequence;
foreach (IEffect effect in seq)
{
    effect.AfterAnimationType = AfterAnimationType.Color;
    effect.AfterAnimationColor.Color = Color.Green;
}
```

## Étape 6 : Modifier les effets After Animation sur la diapositive 3

Pour la troisième diapositive, définissez l’effet après animation sur « Masquer après l’animation » :

```csharp
ISlide slide3 = pres.Slides.AddClone(pres.Slides[0]);
seq = slide3.Timeline.MainSequence;
foreach (IEffect effect in seq)
    effect.AfterAnimationType = AfterAnimationType.HideAfterAnimation;
```

## Étape 7 : Enregistrer la présentation modifiée

Enfin, enregistrez votre présentation modifiée :

```csharp
pres.Save(outPath, SaveFormat.Pptx);
```

## Conclusion

Félicitations ! Vous avez appris avec succès à contrôler les effets d'après-animation sur les diapositives à l'aide d'Aspose.Slides pour .NET. N'hésitez pas à expérimenter différents effets pour créer des présentations dynamiques et attrayantes qui captiveront votre public.

## FAQ

### Puis-je appliquer différents effets post-animation à des éléments individuels dans une diapositive ?

Oui, vous pouvez personnaliser les effets post-animation pour des éléments individuels en les parcourant et en ajustant leurs propriétés en conséquence.

### Aspose.Slides est-il compatible avec les dernières versions de .NET ?

Absolument ! Aspose.Slides est régulièrement mis à jour pour assurer la compatibilité avec les dernières versions du framework .NET.

### Comment puis-je ajouter des animations personnalisées aux diapositives à l’aide d’Aspose.Slides ?

 Pour des informations détaillées sur l'ajout d'animations personnalisées, reportez-vous à la[Documentation Aspose.Slides](https://reference.aspose.com/slides/net/).

### Quels formats de fichiers Aspose.Slides prend-il en charge pour l’enregistrement des présentations ?

Aspose.Slides prend en charge divers formats, notamment PPTX, PPT, PDF, etc. Consultez la documentation pour obtenir une liste complète.

### Où puis-je obtenir de l'aide ou poser des questions concernant Aspose.Slides ?

 Pour obtenir du soutien et interagir avec la communauté, visitez le[Forum Aspose.Slides](https://forum.aspose.com/c/slides/11).