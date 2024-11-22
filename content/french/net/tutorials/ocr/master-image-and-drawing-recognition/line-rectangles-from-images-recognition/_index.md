---
title: Extraction de rectangles de lignes à partir de la reconnaissance d'images
linktitle: Extraction de rectangles de lignes à partir de la reconnaissance d'images
second_title: API Aspose.OCR .NET
description: Découvrez comment implémenter la reconnaissance optique de caractères (OCR) dans vos applications .NET à l'aide d'Aspose.OCR. Ce guide complet vous guide tout au long du processus d'extraction de rectangles pour les lignes reconnues.
type: docs
weight: 10
url: /fr/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Introduction

Bienvenue dans le monde d'Aspose.OCR pour .NET, un outil impressionnant conçu pour intégrer la reconnaissance optique de caractères (OCR) dans vos applications .NET. Que vous soyez un développeur expérimenté ou un nouveau venu curieux, ce guide vous guidera à travers les étapes à suivre pour obtenir des rectangles représentant des lignes à partir de texte reconnu dans des images.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

- Connaissances de base du développement C# et .NET.
- Un environnement de développement intégré (IDE) comme Visual Studio.
-  La bibliothèque Aspose.OCR pour .NET est installée. Vous pouvez la télécharger[ici](https://releases.aspose.com/ocr/net/).
- Un exemple d'image contenant du texte à reconnaître.

## Espaces de noms requis

Pour commencer, vous devrez ajouter les espaces de noms nécessaires à votre projet. Incluez ces lignes en haut de votre fichier C# :

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Suivez ces étapes pour récupérer les rectangles des lignes dans une image OCR.

## Étape 1 : Configurez votre répertoire de documents

Spécifiez le répertoire où se trouve votre fichier image :

```csharp
// Définissez le chemin d’accès à votre répertoire de documents
string dataDir = "Your Document Directory";
```

 Assurez-vous de remplacer`"Your Document Directory"` avec le chemin réel.

## Étape 2 : Initialiser Aspose.OCR

 Créer une instance de`AsposeOcr` classe pour accéder à ses fonctionnalités :

```csharp
// Initialiser l'API Aspose.OCR
AsposeOcr api = new AsposeOcr();
```

## Étape 3 : Spécifier le chemin d’accès à l’image

Définissez le chemin complet vers le fichier image que vous souhaitez traiter :

```csharp
// Spécifiez le chemin complet vers l'image
string fullPath = dataDir + "sample.png";
```

## Étape 4 : Reconnaître l'image et obtenir des rectangles pour les lignes

 Maintenant, vous pouvez utiliser le`GetRectangles` méthode pour extraire les rectangles des lignes de texte reconnues :

```csharp
// Récupérer les rectangles pour les lignes dans l'image spécifiée
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## Étape 5 : Afficher les résultats

Enfin, imprimez les coordonnées de chaque rectangle de ligne détecté sur la console :

```csharp
// Afficher les coordonnées des rectangles détectés
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Conclusion

Félicitations ! Vous avez réussi à récupérer des rectangles pour les lignes d'une image OCR à l'aide d'Aspose.OCR pour .NET. Cette technologie ouvre de nombreuses possibilités d'extraction et de traitement de texte dans vos applications.

## FAQ

### Puis-je utiliser Aspose.OCR pour .NET avec n’importe quel type d’image ?

Oui, Aspose.OCR prend en charge différents formats d'image, offrant ainsi une flexibilité pour vos applications OCR.

### Quel est le taux de précision de la reconnaissance OCR ?

Aspose.OCR utilise des algorithmes avancés pour obtenir une grande précision dans la reconnaissance de texte, adaptée à divers scénarios.

### Une version d'essai est-elle disponible ?

 Oui, vous pouvez explorer les fonctionnalités d'Aspose.OCR pour .NET en téléchargeant le[essai gratuit](https://releases.aspose.com/).

### Où puis-je trouver une documentation détaillée ?

 Une documentation complète peut être trouvée[ici](https://reference.aspose.com/ocr/net/), offrant des informations et des lignes directrices détaillées.

### Vous avez besoin d’aide supplémentaire ou vous avez des questions ?

 Rejoignez la discussion sur le[Forum Aspose.OCR](https://forum.aspose.com/c/ocr/16) pour le soutien de la communauté.