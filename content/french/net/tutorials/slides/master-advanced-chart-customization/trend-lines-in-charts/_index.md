---
title: Lignes de tendance dans les graphiques avec Aspose.Slides pour .NET
linktitle: Lignes de tendance dans les graphiques avec Aspose.Slides pour .NET
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Découvrez comment ajouter et personnaliser des lignes de tendance dans les graphiques à l'aide d'Aspose.Slides pour .NET. Ce guide complet couvre les lignes de tendance exponentielles, linéaires, logarithmiques, polynomiales et à moyenne mobile pour améliorer la visualisation de vos données.
type: docs
weight: 12
url: /fr/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Introduction  

L'ajout de lignes de tendance aux graphiques est une technique essentielle pour analyser les tendances des données et prévoir les valeurs futures. Avec Aspose.Slides pour .NET, vous pouvez facilement ajouter et personnaliser des lignes de tendance à vos graphiques de présentation, améliorant ainsi la visualisation de vos données. Ce guide fournit une procédure détaillée pour ajouter des lignes de tendance à différents types de graphiques dans une présentation PowerPoint à l'aide d'Aspose.Slides pour .NET.  

## Prérequis  

Avant de nous lancer dans l’implémentation, assurez-vous de disposer de la configuration suivante :  

1.  Aspose.Slides pour .NET : téléchargez et installez la bibliothèque à partir du[page de téléchargement](https://releases.aspose.com/slides/net/).  
2. Environnement de développement : utilisez un IDE comme Visual Studio pour le codage.  
3. Connaissances de base en C# : une connaissance de la programmation C# est requise pour suivre ce tutoriel.  

## Importation des espaces de noms requis  

Pour commencer, importez les espaces de noms essentiels dans votre projet :  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Étape 1 : Configuration de la présentation  

Commencez par initialiser une présentation vide. Elle servira de conteneur pour votre graphique.  

```csharp
string dataDir = "Your/Documents/Directory";

// Assurez-vous que le répertoire existe
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Créer une nouvelle présentation
Presentation presentation = new Presentation();
```

## Étape 2 : Ajouter un graphique à une diapositive  

Maintenant, ajoutez une diapositive et incluez un graphique à colonnes groupées pour visualiser vos données.  

```csharp
// Ajouter une diapositive vierge
ISlide slide = presentation.Slides[0];

// Ajouter un graphique à colonnes groupées
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Étape 3 : Remplissage des données du graphique  

Remplissez le graphique avec des exemples de données.  

```csharp
// Accéder au classeur de données de graphique par défaut
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Mettre à jour les valeurs par défaut des catégories et des séries
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Étape 4 : Ajout de lignes de tendance  

### Ligne de tendance exponentielle  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Ligne de tendance linéaire  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Ligne de tendance logarithmique  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Ligne de tendance moyenne mobile  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Ligne de tendance polynomiale  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Ligne de tendance de puissance  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Étape 5 : Enregistrer la présentation  

Enfin, enregistrez la présentation avec toutes les lignes de tendance ajoutées à votre graphique.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Conclusion  

Avec Aspose.Slides pour .NET, ajouter des lignes de tendance à vos graphiques devient une tâche simple. Cette fonctionnalité vous permet de présenter efficacement les tendances des données et d'ajouter des touches professionnelles à vos présentations. Suivez les étapes ci-dessus pour intégrer différents types de lignes de tendance et améliorer la visualisation de vos données.  

## FAQ  

### Puis-je personnaliser l’apparence des lignes de tendance ?  
 Oui, vous pouvez personnaliser la couleur, l'épaisseur et le style des lignes de tendance à l'aide du`Format.Line` propriété.  

### Existe-t-il un support pour d’autres types de graphiques ?  
Oui, Aspose.Slides pour .NET prend en charge différents types de graphiques, notamment les graphiques à barres, à secteurs et en courbes.  

### Comment afficher les équations et les valeurs R au carré ?  
 Activer`DisplayEquation` et`DisplayRSquaredValue` propriétés d'une ligne de tendance pour afficher ces valeurs sur le graphique.  

### Puis-je utiliser Aspose.Slides pour .NET avec d’autres langages ?  
Oui, la bibliothèque est compatible avec tous les langages pris en charge par .NET, y compris VB.NET et F#.  

### Où puis-je trouver de la documentation supplémentaire ?  
 Visitez le[Aspose.Slides pour la documentation .NET](https://reference.aspose.com/slides/net/) pour plus d'informations.