---
title: Créer des formes de groupe dans PowerPoint avec Aspose.Slides pour .NET
linktitle: Créer des formes de groupe dans PowerPoint avec Aspose.Slides pour .NET
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Découvrez comment créer et gérer des formes de groupe à l'aide d'Aspose.Slides pour .NET. Ce guide complet fournit des instructions claires, étape par étape.
type: docs
weight: 11
url: /fr/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Introduction

L'amélioration de l'attrait visuel et de l'organisation de vos présentations PowerPoint peut avoir un impact significatif sur l'engagement de votre public. Une méthode efficace pour y parvenir consiste à utiliser des formes de groupe. Dans ce didacticiel, nous allons découvrir comment exploiter Aspose.Slides pour .NET pour créer et manipuler des formes de groupe dans vos présentations.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des éléments suivants :

-  Aspose.Slides pour .NET : téléchargez et installez la dernière version de la bibliothèque Aspose.Slides à partir du[Site Web d'Aspose](https://releases.aspose.com/slides/net/).
- Environnement de développement : configurez un IDE compatible .NET, tel que Visual Studio, pour travailler sur votre projet.
- Connaissances de base de C# : Familiarisez-vous avec les concepts fondamentaux de C#.


## Importer les espaces de noms nécessaires

Dans votre projet C#, commencez par inclure les espaces de noms suivants :

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Étape 1 : instancier la classe de présentation

 Créer une instance de`Presentation`classe dans laquelle vous travaillerez sur vos diapositives. Précisez le répertoire où sont stockés vos documents :

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // Les étapes pour créer et manipuler des formes se dérouleront ici
}
```

## Étape 2 : Accéder à la première diapositive

Récupérez la première diapositive de votre présentation nouvellement créée :

```csharp
ISlide slide = pres.Slides[0];
```

## Étape 3 : Accéder à la collection de formes

Obtenez la collection de formes sur la diapositive :

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Étape 4 : Ajouter une forme de groupe

Il est maintenant temps d’ajouter une forme de groupe à la diapositive :

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Étape 5 : ajouter des formes à l’intérieur du groupe

Vous pouvez remplir la forme de groupe avec des formes individuelles, telles que des rectangles :

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Forme 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Forme 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Forme 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Forme 4
```

## Étape 6 : Définir le cadre pour la forme du groupe

La définition d’un cadre pour la forme du groupe lui donne une limite définie :

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Étape 7 : Enregistrer la présentation

Enfin, enregistrez votre présentation modifiée dans le répertoire spécifié :

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Conclusion

Félicitations ! Vous avez réussi à créer des formes de groupe dans vos présentations PowerPoint à l'aide d'Aspose.Slides pour .NET. En organisant les formes de cette manière, vous pouvez améliorer considérablement la présentation visuelle et la clarté de votre contenu, ce qui rend vos présentations plus percutantes.

## FAQ

### Aspose.Slides est-il compatible avec la dernière version de .NET ?

 Oui, Aspose.Slides est régulièrement mis à jour pour assurer la compatibilité avec les dernières versions de .NET. Vérifiez le[documentation](https://reference.aspose.com/slides/net/) pour les derniers détails de compatibilité.

### Puis-je essayer Aspose.Slides avant d'acheter ?

 Absolument ! Vous pouvez télécharger une version d'essai gratuite[ici](https://releases.aspose.com/).

### Où puis-je trouver de l'aide pour les requêtes liées à Aspose.Slides ?

 Visitez Aspose.Slides[forum](https://forum.aspose.com/c/slides/11) pour le soutien et les discussions de la communauté.

### Comment obtenir une licence temporaire pour Aspose.Slides ?

 Vous pouvez demander une licence temporaire[ici](https://purchase.aspose.com/temporary-license/).

### Où puis-je acheter une licence complète pour Aspose.Slides ?

 Vous pouvez acheter une licence auprès du[page d'achat](https://purchase.aspose.com/buy).