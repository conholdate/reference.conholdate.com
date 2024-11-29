---
title: Appliquer le seuillage Bradley dans Aspose.PSD pour .NET
linktitle: Appliquer le seuil Bradley
second_title: API .NET Aspose.PSD
description: Apprenez étape par étape comment charger des fichiers PSD, appliquer des techniques de seuillage et enregistrer vos résultats dans différents formats, améliorant ainsi vos tâches de segmentation d'images pour diverses applications.
type: docs
weight: 15
url: /fr/net/tutorials/psd/guide-image-processing/apply-bradley-thresholding/
---
## Introduction

Bienvenue dans notre tutoriel sur l'application de la technique du seuil Bradley à l'aide d'Aspose.PSD pour .NET. Cette puissante bibliothèque permet une manipulation transparente des fichiers Photoshop dans les applications .NET. Le seuil Bradley est une méthode efficace de binarisation des images, qui permet de distinguer les objets de leur arrière-plan.

## Prérequis

Avant de vous lancer dans le processus, assurez-vous de disposer des prérequis suivants :

-  Bibliothèque Aspose.PSD pour .NET : téléchargez et installez la dernière version à partir du[documentation](https://reference.aspose.com/psd/net/).
- Répertoire de documents : créez un répertoire de travail pour stocker votre fichier PSD source et l’image binarisée de sortie.

## Importer les espaces de noms nécessaires

Commencez votre projet en important les espaces de noms pertinents pour accéder aux fonctionnalités d'Aspose.PSD :

```csharp
// Importer les espaces de noms Aspose.PSD
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## Étape 1 : Chargez votre image source

Définissez le chemin d'accès à votre répertoire de documents ainsi que le fichier PSD source et le nom du fichier de sortie :

```csharp
// Spécifiez le chemin d'accès à votre répertoire de documents
string dataDir = "Your Document Directory";

string sourceFile = Path.Combine(dataDir, "sample.psd");
string outputFile = Path.Combine(dataDir, "binarized_out.png");
```

## Étape 2 : Appliquer le seuil Bradley

Ensuite, chargez l'image PSD, choisissez votre valeur de seuil, appliquez le seuillage Bradely, puis enregistrez les résultats :

```csharp
// Charger l'image PSD
using (PsdImage image = (PsdImage)Image.Load(sourceFile))
{
    // Définissez la valeur seuil (expérimentez cette valeur si nécessaire)
    double threshold = 0.15;

    // Binariser l'image en utilisant la méthode Bradley
    image.BinarizeBradley(threshold);

    // Enregistrer l'image binarisée au format PNG
    image.Save(outputFile, new PngOptions());
}
```

## Conclusion

Félicitations ! Vous avez implémenté avec succès la technique du seuil Bradley à l'aide d'Aspose.PSD pour .NET. Cette méthode peut grandement améliorer la segmentation d'images pour diverses applications, de l'analyse de documents à la conception graphique.

## FAQ

### Puis-je appliquer le seuil Bradley à n’importe quel type d’image ?

Absolument ! Le seuillage Bradley est polyvalent et peut être appliqué à la plupart des types d'images pour améliorer la segmentation.

### Où puis-je trouver plus d'informations sur Aspose.PSD ?

 Pour une documentation et des ressources détaillées, visitez le[Documentation d'Aspose.PSD](https://reference.aspose.com/psd/net/).

### Existe-t-il une version d'essai disponible ?

 Oui ! Vous pouvez tester Aspose.PSD pour .NET avec une version d'essai gratuite[ici](https://releases.aspose.com/).

### Comment puis-je obtenir de l'aide pour Aspose.PSD ?

 Pour le soutien et les discussions de la communauté, consultez le[Forum Aspose.PSD](https://forum.aspose.com/c/psd/34).

### Comment puis-je acheter une licence pour Aspose.PSD ?

 Vous pouvez acheter une licence directement[ici](https://purchase.conholdate.com/buy).