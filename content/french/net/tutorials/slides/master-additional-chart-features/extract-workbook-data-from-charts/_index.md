---
title: Extraire les données du classeur à partir des graphiques avec Aspose.Slides pour .NET
linktitle: Extraire les données du classeur à partir des graphiques avec Aspose.Slides pour .NET
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Libérez le potentiel de vos présentations PowerPoint en apprenant à récupérer les données d'un classeur à partir de graphiques à l'aide d'Aspose.Slides pour .NET. Ce didacticiel étape par étape vous guide tout au long du processus, facilitant ainsi l'extraction et l'utilisation efficaces des données des graphiques.
type: docs
weight: 12
url: /fr/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## Introduction

Travailler avec des présentations PowerPoint peut s'avérer difficile, notamment lors de l'extraction de données précieuses à partir de graphiques intégrés. Heureusement, Aspose.Slides pour .NET fournit une solution robuste qui simplifie ce processus. Dans ce didacticiel, nous vous guiderons étape par étape sur la façon de récupérer un classeur à partir d'un graphique dans une présentation PowerPoint.

## Prérequis

Avant de passer au code, assurez-vous d'avoir les éléments suivants prêts :

### Aspose.Slides pour .NET

Vous devez avoir installé Aspose.Slides pour .NET dans votre environnement de développement. Si vous ne l'avez pas encore fait, vous pouvez le télécharger à partir du site Web :

[Télécharger Aspose.Slides pour .NET](https://releases.aspose.com/slides/net/)

### Présentation PowerPoint

Ayez votre fichier de présentation PowerPoint à portée de main, en particulier celui qui contient un graphique avec les données associées que vous souhaitez récupérer.

## Étape 1 : Importer les espaces de noms nécessaires

Pour travailler efficacement avec Aspose.Slides, vous devez d'abord importer les espaces de noms requis :

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Étape 2 : Définir le répertoire des documents

Spécifiez le répertoire où se trouve votre fichier de présentation :

```csharp
string dataDir = "Your Document Directory"; // Ajustez ce chemin selon vos besoins
```

## Étape 3 : Charger la présentation

Vous pouvez charger la présentation PowerPoint tout en activant la récupération du classeur à partir du cache du graphique. Voici comment procéder :

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // Accéder et travailler avec les données du graphique
    // Votre code ira ici
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 Dans cette étape, le`LoadOptions` L'objet vous permet d'activer la récupération du classeur à l'aide de l'`RecoverWorkbookFromChartCache` propriété.

## Étape 4 : Récupérer le graphique et accéder à son classeur

Il est maintenant temps d'explorer le graphique et de récupérer les données associées :

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // Ajustez l'index selon vos besoins
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// Vous pouvez désormais travailler avec les données du classeur selon vos besoins
```

En accédant à la première forme de la première diapositive (qui devrait être un graphique), vous obtenez le classeur de données du graphique et pouvez manipuler ou extraire les données selon vos besoins.

## Conclusion

Dans ce didacticiel, nous avons montré comment récupérer efficacement un classeur à partir d'un graphique dans une présentation PowerPoint à l'aide d'Aspose.Slides pour .NET. En suivant ces étapes, vous pouvez facilement extraire et utiliser les données du graphique pour vos besoins analytiques.

## FAQ

### Qu'est-ce qu'Aspose.Slides pour .NET ?

Aspose.Slides pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, manipuler et convertir des présentations Microsoft PowerPoint par programmation.

### Puis-je essayer Aspose.Slides pour .NET avant d'acheter ?

 Oui ! Aspose propose une version d'essai gratuite d'Aspose.Slides pour .NET. Vous pouvez évaluer ses capacités avant de procéder à un achat.[Obtenez l'essai gratuit ici](https://releases.aspose.com/).

### Où puis-je trouver la documentation d'Aspose.Slides pour .NET ?

 Vous pouvez accéder à la documentation complète d'Aspose.Slides pour .NET[ici](https://reference.aspose.com/slides/net/), qui comprend des exemples et des références API.

### Comment acheter une licence pour Aspose.Slides pour .NET ?

 Pour acheter une licence, visitez le site Web d'Aspose et utilisez le lien suivant :[Acheter Aspose.Slides pour .NET](https://purchase.aspose.com/buy).