---
title: Ajout d'une image dans un fichier PDF
linktitle: Ajout d'une image dans un fichier PDF
second_title: Référence de l'API Aspose.PDF pour .NET
description: Découvrez comment ajouter des images par programmation à des fichiers PDF avec Aspose.PDF pour .NET. Ce didacticiel complet couvre chaque étape, de la configuration de votre environnement au rendu des images sur des pages spécifiques.
type: docs
weight: 10
url: /fr/net/tutorials/pdf/mastering-image-Processing/adding-image/
---
## Introduction

Avez-vous déjà eu besoin d'insérer une image dans un fichier PDF par programmation ? Que vous développiez un système de génération de documents ou que vous ajoutiez des éléments de marque, Aspose.PDF pour .NET simplifie cette tâche. Dans ce didacticiel, nous vous expliquerons les étapes à suivre pour ajouter une image à un fichier PDF.

## Prérequis

Avant de commencer à coder, assurez-vous de disposer des éléments suivants :

-  Bibliothèque Aspose.PDF pour .NET : téléchargez et installez la dernière version à partir de[Téléchargements Aspose](https://releases.aspose.com/pdf/net/).
- Environnement de développement .NET : vous pouvez utiliser Visual Studio ou n’importe quel IDE de votre choix.
- Connaissances de base de C# : une connaissance de la programmation C# et des principes orientés objet est utile.
- Exemples de fichiers : un fichier PDF et une image (par exemple, un logo) à insérer.

## Étape 1 : Configurez votre environnement de développement

Commencez par créer un nouveau projet C# dans votre IDE. Importez les espaces de noms nécessaires pour travailler avec Aspose.PDF :

```csharp
using System.IO;
using Aspose.Pdf;
using System;
```

Ces espaces de noms vous permettront de manipuler des documents PDF et de gérer efficacement les flux de fichiers.

## Étape 2 : Ouvrir le document PDF

 Localisez votre fichier PDF et ouvrez-le à l'aide du`Document` classe:

```csharp
// Spécifiez le chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Ouvrir le document PDF
Document pdfDocument = new Document(dataDir + "AddImage.pdf");
```

 Assurez-vous de remplacer`YOUR DOCUMENT DIRECTORY` avec le chemin réel où votre PDF est stocké.

## Étape 3 : Définir les coordonnées de l’image

Définissez les coordonnées où l'image sera placée dans le PDF :

```csharp
// Définir les coordonnées de l'image
int lowerLeftX = 100;
int lowerLeftY = 100;
int upperRightX = 200;
int upperRightY = 200;
```

Ces coordonnées déterminent la position et la taille de l'image sur la page.

## Étape 4 : Sélectionner la page pour l'insertion de l'image

Choisissez la page du PDF sur laquelle vous souhaitez ajouter l'image. N'oubliez pas qu'Aspose.PDF utilise une indexation à base unique pour les pages :

```csharp
// Obtenez la première page du PDF
Page page = pdfDocument.Pages[1];
```

## Étape 5 : charger l’image dans un flux

Chargez l'image que vous souhaitez insérer dans un flux :

```csharp
// Charger l'image dans un flux
using (FileStream imageStream = new FileStream(dataDir + "aspose-logo.jpg", FileMode.Open))
{
    // Ajouter une image aux ressources de la page
    page.Resources.Images.Add(imageStream);
}
```

Assurez-vous que le chemin du fichier image est correct.

## Étape 6 : Enregistrer l’état actuel des graphiques

Avant de placer l'image, enregistrez l'état graphique actuel :

```csharp
// Enregistrer l'état graphique actuel
page.Contents.Add(new Aspose.Pdf.Operators.GSave());
```

## Étape 7 : Définir le placement de l'image avec un rectangle et une matrice

 Créer un`Rectangle` pour le placement de l'image et un`Matrix` pour la mise à l'échelle :

```csharp
// Créer des objets rectangulaires et matriciels
Aspose.Pdf.Rectangle rectangle = new Aspose.Pdf.Rectangle(lowerLeftX, lowerLeftY, upperRightX, upperRightY);
Matrix matrix = new Matrix(new double[] { rectangle.URX - rectangle.LLX, 0, 0, rectangle.URY - rectangle.LLY, rectangle.LLX, rectangle.LLY });
```

## Étape 8 : Appliquer la transformation de la matrice

 Utilisez le`ConcatenateMatrix` opérateur pour positionner correctement l'image :

```csharp
// Appliquer la transformation matricielle
page.Contents.Add(new Aspose.Pdf.Operators.ConcatenateMatrix(matrix));
```

## Étape 9 : Afficher l'image sur la page PDF

 Rendre l'image en utilisant le`Do` opérateur:

```csharp
XImage ximage = page.Resources.Images[page.Resources.Images.Count];
// Dessine l'image sur la page
page.Contents.Add(new Aspose.Pdf.Operators.Do(ximage.Name));
```

## Étape 10 : Restaurer l’état graphique

Après avoir rendu l'image, restaurez l'état graphique :

```csharp
// Restaurer l'état graphique
page.Contents.Add(new Aspose.Pdf.Operators.GRestore());
```

## Étape 11 : Enregistrer le document PDF mis à jour

Enfin, enregistrez le PDF modifié :

```csharp
dataDir = dataDir + "AddImage_out.pdf";
// Enregistrer le document mis à jour
pdfDocument.Save(dataDir);
```

## Conclusion

L'insertion d'une image dans un PDF à l'aide d'Aspose.PDF pour .NET est un processus simple lorsqu'il est décomposé en étapes claires. Cette méthode vous permet de personnaliser vos PDF avec des logos, des filigranes ou d'autres images de manière transparente.

## FAQ

### Puis-je ajouter plusieurs images sur une seule page ?
Oui, vous pouvez répéter les étapes pour chaque image que vous souhaitez insérer.

### Comment contrôler la taille de l'image insérée ?
La taille est déterminée par les coordonnées du rectangle que vous définissez.

### Puis-je insérer d’autres types de fichiers comme PNG ou GIF ?
Oui, Aspose.PDF prend en charge divers formats d'image, notamment PNG, GIF, BMP et JPEG.

### Est-il possible d'ajouter des images de manière dynamique ?
Absolument ! Vous pouvez charger dynamiquement des images en fournissant le chemin du fichier ou en utilisant des flux.

### Puis-je ajouter des images en masse à plusieurs pages ?
Oui, vous pouvez parcourir les pages d’un document et ajouter des images en utilisant la même approche.