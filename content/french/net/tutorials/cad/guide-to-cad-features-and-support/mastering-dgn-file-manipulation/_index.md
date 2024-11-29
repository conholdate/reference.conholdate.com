---
title: Maîtriser la manipulation des fichiers DGN avec Aspose.CAD dans .NET
linktitle: Maîtriser la manipulation des fichiers DGN
second_title: Aspose.CAD .NET - Format de fichier CAO et BIM
description: Découvrez comment charger des fichiers DGN, parcourir leurs éléments, gérer les entités 2D et 3D et les exporter sous forme d'images raster, tout en exploitant les puissantes fonctionnalités de la bibliothèque Aspose.CAD.
type: docs
weight: 18
url: /fr/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Introduction

Vous êtes un développeur .NET désireux d'intégrer des fichiers DGN dans vos applications ? Aspose.CAD pour .NET propose une bibliothèque puissante conçue spécifiquement pour travailler avec les formats de fichiers DGN. Dans ce didacticiel, nous découvrirons comment gérer efficacement les fichiers DGN, y compris les éléments pris en charge et comment les manipuler dans vos projets .NET.

## Prérequis

Avant de commencer, assurez-vous d’avoir la configuration suivante :

- Connaissances de base de la programmation .NET : une familiarité avec C# ou VB.NET sera bénéfique.
- Visual Studio : installé sur votre machine pour le développement de projets.
-  Bibliothèque Aspose.CAD pour .NET : Téléchargez-la depuis[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Étape 1 : Importer les espaces de noms nécessaires

Pour exploiter les fonctionnalités d'Aspose.CAD, commencez par importer les espaces de noms requis dans votre projet.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Étape 2 : chargez votre fichier DGN

 Commencez par charger un fichier DGN existant dans votre application. Cela se fait en instanciant un`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Poursuivez votre logique ici
}
```

## Étape 3 : parcourir les éléments DGN

Une fois le fichier DGN chargé, vous pouvez parcourir ses éléments. Aspose.CAD fournit une variété de types d'éléments DGN pour votre manipulation.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Traiter chaque élément
}
```

## Étape 4 : gérer les entités 2D et 3D

Vous pouvez faire la différence entre les éléments DGN 2D et 3D. Voici comment les gérer efficacement :

### Gérer les entités 2D

Vous pouvez gérer les entités 2D précédemment prises en charge avec un bloc switch-case.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Ajoutez votre logique de traitement ici
        break;
}
```

### Gérer les entités 3D

De même, gérez les entités 3D comme suit :

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Ajoutez votre logique de traitement ici
        break;
}
```

## Étape 5 : Exporter le fichier DGN

Après avoir manipulé les éléments DGN, vous souhaiterez peut-être exporter le fichier sous forme d'image raster. Cela peut être facilement réalisé avec Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Définissez votre chemin de sortie
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Conclusion

Dans ce didacticiel, nous avons appris à utiliser Aspose.CAD pour .NET pour gérer efficacement les fichiers DGN. En suivant les étapes décrites, vous pouvez facilement gérer les éléments DGN 2D et 3D et les exporter sous forme d'images raster. Cette puissante bibliothèque permet une intégration transparente du traitement DGN dans vos applications .NET, améliorant ainsi les capacités de votre projet.

## FAQ

### Où puis-je trouver la documentation d'Aspose.CAD pour .NET ?

 La documentation complète est disponible[ici](https://reference.aspose.com/cad/net/).

### Comment télécharger Aspose.CAD pour .NET ?

 Vous pouvez télécharger la dernière version de la bibliothèque[ici](https://releases.aspose.com/cad/net/).

### Existe-t-il un essai gratuit disponible pour Aspose.CAD pour .NET ?

 Oui, un essai gratuit est accessible[ici](https://releases.aspose.com/).

### Comment puis-je obtenir des licences temporaires pour Aspose.CAD pour .NET ?

 Vous pouvez demander des licences temporaires[ici](https://purchase.conholdate.com/temporary-license/).

### Besoin d'aide ou avez des questions ?

Pour obtenir de l'aide ou poser des questions, visitez la communauté Aspose.CAD[Forum de soutien](https://forum.aspose.com/c/cad/19).