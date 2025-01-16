---
title: Trouver le nombre maximal de lignes et de colonnes dans les formats XLS et XLSX
linktitle: Trouver le nombre maximal de lignes et de colonnes dans les formats XLS et XLSX
second_title: API de traitement Excel Aspose.Cells .NET
description: Découvrez comment gérer efficacement de grands ensembles de données dans Excel en utilisant la bibliothèque Aspose.Cells pour .NET. Ce guide fournit une approche étape par étape pour identifier le nombre maximal de lignes et de colonnes prises en charge par les formats de fichier XLS et XLSX.
type: docs
weight: 11
url: /fr/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Introduction

La gestion de grands ensembles de données dans Excel peut être difficile, notamment en raison des limites des différents formats de fichiers. Ce didacticiel vous guidera dans l'utilisation de la bibliothèque Aspose.Cells pour .NET pour déterminer le nombre maximal de lignes et de colonnes prises en charge par les formats XLS (Excel 97-2003) et XLSX (Excel 2007 et versions ultérieures). À la fin, vous serez en mesure de gérer efficacement les tâches liées à Excel.

## Prérequis

Avant de commencer, assurez-vous d'avoir les éléments suivants :

1. [Cadre .NET](https://dotnet.microsoft.com/en-us/download) ou[.NET Core](https://dotnet.microsoft.com/en-us/download) installé sur votre système.
2. [Aspose.Cells pour .NET](https://releases.aspose.com/cells/net/) bibliothèque téléchargée et référencée dans votre projet (vous pouvez également l'installer via[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## Importation des packages requis

Ajoutez les instructions using suivantes en haut de votre fichier C# pour importer les packages nécessaires à partir de la bibliothèque Aspose.Cells :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Étape 1 : Nombre maximal de lignes et de colonnes pour le format XLS

Commençons par trouver le nombre maximal de lignes et de colonnes prises en charge par le format XLS.

```csharp
// Imprimer un message sur le format XLS.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Créer un classeur au format XLS.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Récupérer le maximum de lignes et de colonnes.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Afficher les résultats.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Imprimez un message pour indiquer que nous travaillons avec le format XLS.
2.  Créer un`Workbook` instance pour le format XLS en utilisant`FileFormatType.Excel97To2003`.
3.  Obtenez le maximum de lignes et de colonnes avec`wb.Settings.MaxRow` et`wb.Settings.MaxColumn`, en ajoutant 1 car ceux-ci sont basés sur zéro.
4. Affichez le nombre maximal de lignes et de colonnes sur la console.

## Étape 2 : Nombre maximal de lignes et de colonnes pour le format XLSX

Ensuite, nous explorerons le nombre maximal de lignes et de colonnes prises en charge par le format XLSX.

```csharp
// Imprimer un message sur le format XLSX.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Créer un classeur au format XLSX.
wb = new Workbook(FileFormatType.Xlsx);

// Récupérer le maximum de lignes et de colonnes.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Afficher les résultats.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Imprimez un message indiquant que nous travaillons avec le format XLSX.
2.  Créer un`Workbook` instance pour le format XLSX en utilisant`FileFormatType.Xlsx`.
3. Récupérez et affichez le maximum de lignes et de colonnes comme précédemment.

## Étape 3 : Affichage d'un message de réussite

Après avoir exécuté les étapes, indiquons le succès.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Conclusion

Dans ce didacticiel, vous avez appris à utiliser la bibliothèque Aspose.Cells pour .NET pour rechercher le nombre maximal de lignes et de colonnes prises en charge par les formats de fichier XLS et XLSX. Il est essentiel de comprendre ces limites pour une gestion efficace des données Excel, afin de garantir que vos ensembles de données s'alignent sur les capacités de format.

## FAQ

### Quel est le nombre maximal de lignes pris en charge par le format XLS ?
Le nombre maximal de lignes prises en charge par le format XLS est de 65 536.

### Quel est le nombre maximal de colonnes prises en charge par le format XLS ?
Le nombre maximal de colonnes prises en charge par le format XLS est de 256.

### Quel est le nombre maximal de lignes pris en charge par le format XLSX ?
Le nombre maximal de lignes prises en charge par le format XLSX est de 1 048 576.

### Quel est le nombre maximal de colonnes prises en charge par le format XLSX ?
Le nombre maximal de colonnes prises en charge par le format XLSX est de 16 384.

### Puis-je utiliser la bibliothèque Aspose.Cells pour .NET avec d’autres formats de fichiers Excel ?
 Oui, Aspose.Cells pour .NET prend en charge divers formats de fichiers, notamment XLS, XLSX, ODS, etc. Vérifiez le[documentation](https://reference.aspose.com/cells/net/) pour plus de détails sur les fonctionnalités prises en charge.