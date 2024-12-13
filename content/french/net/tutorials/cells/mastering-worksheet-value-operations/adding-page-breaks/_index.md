---
title: Ajout de sauts de page dans une feuille de calcul à l'aide d'Aspose.Cells
linktitle: Ajout de sauts de page dans une feuille de calcul à l'aide d'Aspose.Cells
second_title: API de traitement Excel Aspose.Cells .NET
description: Découvrez comment améliorer vos feuilles de calcul Excel en ajoutant efficacement des sauts de page horizontaux et verticaux à l'aide d'Aspose.Cells pour .NET. Ce guide complet vous guide tout au long des étapes de configuration et de codage nécessaires.
type: docs
weight: 10
url: /fr/net/tutorials/cells/mastering-worksheet-value-operations/adding-page-breaks/
---
## Introduction

Dans ce didacticiel, nous vous guiderons dans l'ajout de sauts de page horizontaux et verticaux à vos feuilles de calcul Excel à l'aide d'Aspose.Cells pour .NET. À la fin, vous serez équipé pour mettre en œuvre ces techniques dans vos projets de manière transparente. Commençons !

## Prérequis
Avant de plonger dans le code, assurez-vous d'avoir les éléments suivants prêts :
- Visual Studio : assurez-vous que Visual Studio est installé sur votre système.
-  Aspose.Cells pour .NET : téléchargez et installez la bibliothèque Aspose.Cells. Vous pouvez obtenir une version d'essai gratuite[ici](https://releases.aspose.com/cells/net/).
- .NET Framework : ce didacticiel suppose que vous utilisez .NET Framework ou .NET Core. Le processus peut varier légèrement pour d'autres environnements.
- Connaissances de base en C# : une connaissance de la programmation C# et du concept de sauts de page dans Excel sera utile.

## Paquets d'importation
Pour travailler avec Aspose.Cells, commencez par importer les espaces de noms nécessaires dans votre projet :

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Une fois ces espaces de noms importés, vous pouvez commencer à interagir avec les fichiers Excel et à appliquer des modifications, y compris des sauts de page.

## Étape 1 : Configurez votre classeur
 Créez un nouveau classeur à l'aide de`Workbook` classe, qui sert de base à la manipulation de fichiers Excel.

```csharp
// Définissez le chemin d'accès au répertoire où votre fichier sera enregistré
string dataDir = "Your Document Directory";
// Créer un nouvel objet Classeur
Workbook workbook = new Workbook();
```
Dans ce code :
- `dataDir` spécifie l'emplacement de sauvegarde de votre fichier.
-  Le`Workbook` l'objet est instancié, prêt à être modifié.

## Étape 2 : ajouter un saut de page horizontal
Pour ajouter un saut de page horizontal, qui divise la feuille de calcul en deux parties verticalement, utilisez le code suivant :

```csharp
// Ajouter un saut de page horizontal à la ligne 30
workbook.Worksheets[0].HorizontalPageBreaks.Add("Y30");
```
 Ici,`Worksheets[0]` fait référence à la première feuille du classeur et`HorizontalPageBreaks.Add("Y30")` ajoute un saut à la ligne 30, ce qui fait que le contenu au-dessus apparaît sur une page et que le contenu en dessous commence sur une nouvelle page.

## Étape 3 : ajouter un saut de page vertical
Ensuite, vous pouvez ajouter un saut de page vertical pour séparer le contenu horizontalement entre les colonnes :

```csharp
// Ajouter un saut de page vertical à la colonne Y
workbook.Worksheets[0].VerticalPageBreaks.Add("Y30");
```
 Dans cet exemple,`VerticalPageBreaks.Add("Y30")`crée une rupture après la colonne X, garantissant que le contenu de gauche apparaît sur une page et que le contenu de droite apparaît sur la suivante.

## Étape 4 : Enregistrer le classeur
Enfin, enregistrez le classeur pour conserver les modifications :

```csharp
// Enregistrer le fichier Excel
workbook.Save(dataDir + "AddingPageBreaks_out.xls");
```
Cette ligne enregistre le classeur avec les sauts de page ajoutés dans le chemin spécifié (`AddingPageBreaks_out.xls`).

## Conclusion
L'ajout de sauts de page dans Excel est essentiel pour gérer de grands ensembles de données et préparer des documents pour l'impression. Avec Aspose.Cells pour .NET, vous pouvez automatiser l'insertion de sauts de page horizontaux et verticaux, ce qui rend vos documents plus organisés et plus faciles à lire.

## FAQ

### Comment ajouter plusieurs sauts de page dans Aspose.Cells pour .NET ?
 Vous pouvez ajouter plusieurs sauts de page en appelant le`HorizontalPageBreaks.Add()` ou`VerticalPageBreaks.Add()` méthodes plusieurs fois avec différentes références de cellules.

### Puis-je ajouter des sauts de page à une feuille de calcul spécifique dans un classeur ?
 Oui, spécifiez la feuille de calcul à l'aide du`Worksheets[index]` propriété, où`index` est l'index de base zéro de la feuille de calcul souhaitée.

### Comment supprimer un saut de page dans Aspose.Cells pour .NET ?
Supprimer un saut de page en utilisant`HorizontalPageBreaks.RemoveAt()` ou`VerticalPageBreaks.RemoveAt()` en spécifiant l'index du saut de page que vous souhaitez supprimer.

### Puis-je ajouter automatiquement des sauts de page en fonction de la taille du contenu ?
Aspose.Cells ne fournit pas de fonctionnalité automatique pour cela, mais vous pouvez calculer par programmation où les ruptures doivent se produire en fonction du nombre de lignes/colonnes.

### Puis-je définir des sauts de page en fonction d’une plage spécifique de cellules ?
Oui, vous pouvez spécifier des sauts de page pour n'importe quelle cellule ou plage en fournissant la référence de cellule correspondante, telle que « A1 » ou « B15 ».