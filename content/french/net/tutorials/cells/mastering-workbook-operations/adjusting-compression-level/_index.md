---
title: Réglage du niveau de compression dans le classeur
linktitle: Réglage du niveau de compression dans le classeur
second_title: API de traitement Excel Aspose.Cells .NET
description: Découvrez comment gérer efficacement des fichiers Excel volumineux en ajustant les niveaux de compression à l'aide d'Aspose.Cells pour .NET. Ce guide étape par étape couvre tout, de la configuration des répertoires à la mesure des temps de compression, vous aidant à optimiser la taille des fichiers et à améliorer les performances.
type: docs
weight: 14
url: /fr/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Introduction

La gestion de fichiers Excel volumineux peut être un défi, notamment en termes d'efficacité de stockage et de transfert. Heureusement, la compression de fichiers peut réduire considérablement la taille de ces fichiers, ce qui les rend plus faciles à gérer. Si vous utilisez Aspose.Cells pour .NET, vous avez la possibilité d'ajuster facilement le niveau de compression de vos classeurs. Ce guide vous guidera tout au long du processus, étape par étape, en fournissant des explications claires sur chaque partie du code.

## Prérequis

Avant de plonger dans le code, assurez-vous de disposer des prérequis suivants :

1. Connaissances de base de C# : la familiarité avec la programmation C# vous aidera à mieux comprendre les extraits de code.
2.  Bibliothèque Aspose.Cells : Téléchargez et installez la bibliothèque Aspose.Cells depuis[ici](https://releases.aspose.com/cells/net/).
3. Visual Studio : un environnement de développement comme Visual Studio est nécessaire pour exécuter le code.
4. .NET Framework : assurez-vous que votre projet est configuré avec une version compatible du .NET Framework.

## Importer les packages nécessaires

Pour commencer, vous devez importer les packages nécessaires dans votre projet C#. Ajoutez les lignes suivantes en haut de votre fichier de code :

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Ces packages sont essentiels pour travailler avec des fichiers Excel à l'aide de la bibliothèque Aspose.Cells.`Aspose.Cells` L'espace de noms contient toutes les classes nécessaires pour manipuler les fichiers Excel, tandis que`Aspose.Cells.Xlsb` fournit des options pour enregistrer des fichiers au format XLSB.

## Étape 1 : définir les répertoires source et de sortie

Tout d’abord, configurez les répertoires dans lesquels se trouvent vos fichiers sources et où vous souhaitez enregistrer les fichiers de sortie :

```csharp
// Définir les répertoires source et de sortie
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Assurez-vous de remplacer`"Your Document Directory\\"` avec les chemins réels vers vos répertoires. Cela garantit que votre programme peut localiser les fichiers avec lesquels il doit travailler.

## Étape 2 : charger le classeur

Ensuite, chargez le classeur que vous souhaitez compresser :

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Ici, nous créons une nouvelle instance du`Workbook` classez et chargez un fichier Excel existant. Assurez-vous que le nom du fichier correspond à celui de votre répertoire source.

## Étape 3 : Configurer les options d’enregistrement

Maintenant, configurez les options d’enregistrement de votre classeur :

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 Le`XlsbSaveOptions`La classe vous permet de spécifier diverses options lors de l'enregistrement de votre classeur au format XLSB, y compris les niveaux de compression.

## Étape 4 : Mesurer le temps de compression pour le niveau 1

Commencez par le premier niveau de compression et mesurez le temps nécessaire pour enregistrer le classeur :

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Cet extrait définit le type de compression sur Niveau 1, enregistre le classeur et mesure le temps écoulé.

## Étape 5 : Mesurer le temps de compression pour le niveau 6

Ensuite, testez les performances avec la compression de niveau 6 :

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Cette étape est similaire à la précédente, mais avec un niveau de compression plus élevé.

## Étape 6 : Mesurer le temps de compression pour le niveau 9

Enfin, évaluez les performances avec le niveau de compression le plus élevé :

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Cette étape définit le niveau de compression sur le niveau 9, où vous verrez probablement la réduction la plus significative de la taille du fichier, même si le traitement peut prendre plus de temps.

## Étape 7 : Résultat final

Une fois tous les niveaux de compression terminés, affichez un message indiquant que le processus s'est terminé avec succès :

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Cette simple ligne confirme que votre programme s'est exécuté sans problème.

## Conclusion

Le réglage du niveau de compression de vos classeurs à l'aide d'Aspose.Cells pour .NET est un processus simple qui peut conduire à des améliorations significatives de la taille et des performances des fichiers. En suivant les étapes décrites dans ce guide, vous pouvez implémenter efficacement la compression dans vos applications, améliorant ainsi vos capacités de gestion de fichiers Excel.

## FAQ

### Qu'est-ce qu'Aspose.Cells ?  
Aspose.Cells est une bibliothèque puissante pour .NET qui permet aux développeurs de créer, manipuler et convertir des fichiers Excel sans avoir besoin de Microsoft Excel.

### Comment installer Aspose.Cells ?  
 Vous pouvez télécharger et installer Aspose.Cells à partir du[Site Web d'Aspose](https://releases.aspose.com/cells/net/).

### Quels niveaux de compression sont disponibles ?  
Aspose.Cells prend en charge plusieurs niveaux de compression allant du niveau 1 (compression la plus faible) au niveau 9 (compression la plus élevée).

### Puis-je tester Aspose.Cells gratuitement ?  
 Oui ! Vous pouvez obtenir un essai gratuit d'Aspose.Cells[ici](https://releases.aspose.com/).

### Où puis-je trouver du support pour Aspose.Cells ?  
 Pour toute question ou assistance, visitez le forum d'assistance Aspose[ici](https://forum.aspose.com/c/cells/9).