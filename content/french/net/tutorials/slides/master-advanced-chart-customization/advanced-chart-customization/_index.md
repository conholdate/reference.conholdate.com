---
title: Personnalisation avancée des graphiques avec Aspose.Slides pour .NET
linktitle: Personnalisation avancée des graphiques avec Aspose.Slides pour .NET
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Exploitez tout le potentiel d'Aspose.Slides pour .NET en maîtrisant les techniques avancées de personnalisation des graphiques. Ce guide étape par étape couvre tout, de la création de graphiques de base aux détails complexes tels que les lignes de grille, les titres d'axe et les couleurs personnalisées.
type: docs
weight: 10
url: /fr/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Introduction

La création de graphiques visuellement attrayants et informatifs est essentielle pour une présentation efficace des données. Aspose.Slides pour .NET propose des outils puissants pour la personnalisation des graphiques, vous permettant de personnaliser chaque aspect de vos graphiques. Dans ce didacticiel, nous allons explorer des techniques avancées de personnalisation des graphiques à l'aide d'Aspose.Slides pour .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des prérequis suivants :

1.  Bibliothèque Aspose.Slides pour .NET : téléchargez et installez la bibliothèque Aspose.Slides à partir de[ici](https://releases.aspose.com/slides/net/).
2. Environnement de développement .NET : configurez un environnement de développement .NET, tel que Visual Studio.
3. Connaissances de base de C# : une familiarité avec la programmation C# sera bénéfique, car nous écrirons du code C#.

Maintenant, décomposons le processus de personnalisation avancée des graphiques en étapes claires.

## Étape 1 : Créer une nouvelle présentation

Commencez par créer une nouvelle présentation pour contenir votre graphique.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "Your Document Directory";

// Créer un répertoire s'il n'existe pas.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Instancier la présentation
Presentation pres = new Presentation();
```

## Étape 2 : Accéder à la première diapositive

Ensuite, accédez à la première diapositive où vous souhaitez ajouter le graphique.

```csharp
// Accéder à la première diapositive
ISlide slide = pres.Slides[0];
```

## Étape 3 : ajouter un exemple de graphique

Maintenant, ajoutons un graphique linéaire avec des marqueurs à la diapositive.

```csharp
// Ajouter un exemple de graphique
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Étape 4 : définir le titre du graphique

Définir un titre pour votre graphique fournit un contexte essentiel.

```csharp
// Définir le titre du graphique
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Étape 5 : Personnaliser les principales lignes de la grille

Vous pouvez améliorer les lignes de la grille de l’axe des valeurs pour une meilleure lisibilité.

```csharp
// Personnaliser les principales lignes de la grille pour l'axe des valeurs
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Étape 6 : Personnaliser les lignes mineures de la grille

De même, personnalisez les lignes de grille mineures pour l’axe des valeurs.

```csharp
// Personnaliser les lignes de grille mineures pour l'axe des valeurs
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Étape 7 : Définir le format numérique de l'axe des valeurs

Vous pouvez formater les nombres affichés sur l’axe des valeurs.

```csharp
// Format du numéro de l'axe de valeur définie
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Étape 8 : définir les valeurs maximales et minimales

Définissez les valeurs maximales et minimales du graphique.

```csharp
// Définir les valeurs maximales et minimales du graphique
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Étape 9 : Personnaliser les propriétés du texte de l'axe des valeurs

L’amélioration des propriétés de texte de l’axe des valeurs améliore la lisibilité.

```csharp
// Personnaliser les propriétés du texte de l'axe des valeurs
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Étape 10 : Ajouter un titre à l'axe de valeur

L’ajout d’un titre à l’axe des valeurs peut clarifier ce que représentent les données.

```csharp
// Définir le titre de l'axe des valeurs
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Étape 11 : Personnaliser les lignes principales de la grille pour l'axe des catégories

Maintenant, améliorons les principales lignes de la grille pour l’axe des catégories.

```csharp
// Personnaliser les lignes principales de la grille pour l'axe des catégories
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Étape 12 : Personnaliser les lignes de grille secondaires pour l'axe des catégories

De même, personnalisez les lignes de grille mineures pour l’axe des catégories.

```csharp
// Personnaliser les lignes de grille mineures pour l'axe des catégories
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Étape 13 : Personnaliser les propriétés du texte de l'axe des catégories

Améliorer le style de police et l’apparence des étiquettes des axes de catégorie.

```csharp
// Personnaliser les propriétés du texte de l'axe des catégories
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Étape 14 : Ajouter un titre d'axe de catégorie

Si nécessaire, vous pouvez également ajouter un titre pour l’axe des catégories.

```csharp
// Définir le titre de l'axe des catégories
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Étape 15 : Personnalisations supplémentaires

Améliorez davantage votre graphique avec des personnalisations supplémentaires, telles que des légendes, des couleurs de murs et des paramètres de zone de tracé.

```csharp
// Personnalisations supplémentaires (en option)

// Personnaliser les propriétés du texte des légendes
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Afficher les légendes des graphiques sans chevauchement des graphiques
chart.Legend.Overlay = true;

// Tableau de réglage de la couleur du mur arrière
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Définir la couleur du sol du graphique
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Définir la couleur de la zone de tracé
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Enregistrer la présentation
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Conclusion

Dans ce guide complet, nous avons abordé les techniques avancées de personnalisation des graphiques à l'aide d'Aspose.Slides pour .NET. Vous avez appris à créer une présentation, à ajouter un graphique, à affiner son apparence et à personnaliser divers éléments de graphique tels que les lignes de quadrillage, les étiquettes d'axe et les légendes. 

## FAQ

### Quelles versions de .NET sont prises en charge par Aspose.Slides pour .NET ?
Aspose.Slides pour .NET prend en charge plusieurs versions de .NET, notamment .NET Framework et .NET Core. Reportez-vous à la documentation pour obtenir la liste complète des versions prises en charge.

### Puis-je créer des graphiques à partir de sources de données telles que des fichiers Excel ?
Oui, Aspose.Slides vous permet de créer des graphiques à partir de sources de données externes telles que des feuilles de calcul Excel. Consultez la documentation pour des exemples détaillés.

### Comment puis-je ajouter des étiquettes de données personnalisées à ma série de graphiques ?
 Pour ajouter des étiquettes de données personnalisées, accédez au`DataLabels` propriété de la série et ajustez les étiquettes selon vos besoins. Vous pouvez trouver des exemples de code dans la documentation.

### Est-il possible d'exporter le graphique vers différents formats, tels que PDF ou images ?
Absolument ! Aspose.Slides vous permet d'exporter vos présentations avec des graphiques vers différents formats, notamment PDF et image.

### Où puis-je trouver plus de tutoriels et d'exemples pour Aspose.Slides pour .NET ?
 Visitez Aspose.Slides[site web](https://reference.aspose.com/slides/net/) pour des tutoriels complets, des exemples de code et de la documentation.