---
title: Création d'un rectangle rempli
linktitle: Création d'un rectangle rempli
second_title: Référence de l'API Aspose.PDF pour .NET
description: Découvrez la puissance de la manipulation PDF avec Aspose.PDF pour .NET dans ce didacticiel étape par étape. Apprenez à créer par programmation des documents PDF visuellement attrayants en dessinant des rectangles remplis.
type: docs
weight: 50
url: /fr/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Introduction

Avez-vous déjà souhaité créer des PDF visuellement époustouflants par programmation ? Si tel est le cas, vous êtes au bon endroit ! Dans ce tutoriel, nous allons explorer Aspose.PDF pour .NET, une bibliothèque puissante qui simplifie la manipulation des documents PDF. Aujourd'hui, nous allons nous concentrer sur la création d'un rectangle rempli dans un fichier PDF. Que vous soyez un développeur chevronné ou que vous débutiez, ce guide vous guidera à travers chaque étape de manière conviviale et engageante. Alors, prenez votre casquette de codeur et commençons !

## Prérequis

Avant de plonger dans le code, assurez-vous de disposer des éléments suivants :

1. Visual Studio : installez Visual Studio sur votre machine, car c'est un excellent IDE pour le développement .NET.
2. Aspose.PDF pour .NET : téléchargez et installez la bibliothèque Aspose.PDF depuis[ici](https://releases.aspose.com/pdf/net/).
3. Connaissances de base de C# : la familiarité avec la programmation C# vous aidera à mieux comprendre les extraits de code.

## Étape 1 : Créer un nouveau projet

1. Ouvrez Visual Studio et créez un nouveau projet d’application console.
2. Nommez votre projet de manière appropriée.

## Étape 2 : Ajouter une référence Aspose.PDF

1. Faites un clic droit sur votre projet dans l’Explorateur de solutions.
2. Sélectionnez Gérer les packages NuGet.
3. Recherchez Aspose.PDF et installez la dernière version.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Maintenant que nous avons tout configuré, plongeons dans le code !

## Étape 3 : Configurez votre répertoire de documents

Spécifiez le chemin où votre PDF sera enregistré :

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel sur votre machine où vous souhaitez enregistrer le PDF.

## Étape 4 : Créer une instance de document

Initialiser un nouveau document PDF :

```csharp
//Créer une instance de document
Document doc = new Document();
```

## Étape 5 : Ajouter une page au document

Chaque PDF nécessite au moins une page. Ajoutons-en une :

```csharp
// Ajouter une page à la collection de pages du fichier PDF
Page page = doc.Pages.Add();
```

## Étape 6 : Créer une instance de graphique

 UN`Graph` l'instance agit comme une toile pour dessiner des formes :

```csharp
// Créer une instance de graphique
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Étape 7 : ajouter le graphique à la page

Attachez le graphique à la page :

```csharp
// Ajouter un objet graphique à la collection de paragraphes de l'instance de page
page.Paragraphs.Add(graph);
```

## Étape 8 : Créer une instance de rectangle

Définissez la position et la taille du rectangle :

```csharp
// Créer une instance de Rectangle
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Étape 9 : Spécifier la couleur de remplissage

Choisissez une couleur pour votre rectangle. Pour cet exemple, nous utiliserons le rouge :

```csharp
// Spécifier la couleur de remplissage pour l'objet graphique
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Étape 10 : Ajouter le rectangle au graphique

Ajoutez le rectangle au graphique :

```csharp
// Ajouter un objet rectangle à la collection de formes de l'objet graphique
graph.Shapes.Add(rect);
```

## Étape 11 : Enregistrer le document PDF

Enfin, enregistrez votre document dans le répertoire spécifié :

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Enregistrer le fichier PDF
doc.Save(dataDir);
```

## Étape 12 : Message de confirmation

Imprimez un message de confirmation pour indiquer la réussite :

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Conclusion

Félicitations ! Vous avez réussi à créer un rectangle rempli dans un document PDF à l'aide d'Aspose.PDF pour .NET. Cette puissante bibliothèque ouvre un monde de possibilités pour la manipulation de PDF, vous permettant de générer des documents époustouflants par programmation. Que vous créiez des rapports, des factures ou tout autre type de PDF, Aspose.PDF est là pour vous.

## FAQ

### Qu'est-ce qu'Aspose.PDF pour .NET ?
Aspose.PDF pour .NET est une bibliothèque qui permet aux développeurs de créer, manipuler et convertir des documents PDF par programmation.

### Puis-je utiliser Aspose.PDF gratuitement ?
 Oui, Aspose propose une version d'essai gratuite que vous pouvez utiliser pour explorer les fonctionnalités de la bibliothèque. Vous pouvez la télécharger[ici](https://releases.aspose.com/).

### Existe-t-il un moyen d’obtenir de l’aide pour Aspose.PDF ?
 Absolument ! Vous pouvez obtenir de l'aide via le forum Aspose[ici](https://forum.aspose.com/c/pdf/10).

### Comment puis-je acheter Aspose.PDF ?
 Vous pouvez acheter Aspose.PDF en visitant la page d'achat[ici](https://purchase.aspose.com/buy).

### Quels types de formes puis-je créer avec Aspose.PDF ?
Vous pouvez créer diverses formes, notamment des rectangles, des cercles, des lignes, etc., à l'aide de la bibliothèque Aspose.PDF.