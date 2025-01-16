---
title: Options de marqueur de graphique sur le point de données dans Aspose.Slides .NET
linktitle: Options de marqueur de graphique sur le point de données dans Aspose.Slides .NET
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Découvrez comment améliorer vos graphiques PowerPoint avec des options de marqueurs personnalisés à l'aide d'Aspose.Slides pour .NET. Ce guide étape par étape couvre les prérequis, la création de graphiques, la mise en forme des points de données, etc.
type: docs
weight: 11
url: /fr/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Introduction

L'intégration d'aides visuelles dans les présentations est essentielle pour une communication efficace. Aspose.Slides pour .NET fournit des outils robustes pour créer et personnaliser des graphiques, permettant aux développeurs d'améliorer leurs présentations de données. L'une des fonctionnalités les plus remarquables est la possibilité d'utiliser des options de marqueur de graphique sur des points de données, ce qui permet une personnalisation précise pour des graphiques d'aspect professionnel. Cet article vous guidera à travers chaque étape nécessaire pour y parvenir.

## Prérequis

Avant de continuer, assurez-vous des points suivants :

-  Aspose.Slides pour .NET installé : téléchargez-le à partir de[ici](https://releases.aspose.com/slides/net/).
- Configuration de base : un fichier de présentation, tel que « Test.pptx », dans votre répertoire de travail.
- Environnement de développement : Visual Studio ou équivalent, configuré pour .NET.

## Importation des espaces de noms requis

Ajoutez les espaces de noms nécessaires à votre projet pour un développement transparent :

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Étape 1 : Créez un graphique dans votre présentation

Commencez par créer un graphique par défaut sur la première diapositive de votre présentation :

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Cela ajoute un`LineWithMarkers` graphique sur votre diapositive avec des dimensions spécifiées.

## Étape 2 : Récupérer l'index de la feuille de calcul des données du graphique

L'index de la feuille de calcul des données du graphique par défaut est essentiel pour une personnalisation ultérieure :

```csharp
int defaultWorksheetIndex = 0;
```

## Étape 3 : Accéder au classeur de données graphiques

Pour manipuler les données d'un graphique, récupérez le classeur associé :

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Étape 4 : Configurer la série de graphiques et ajouter des points de données

Effacez la série par défaut et ajoutez de nouveaux points de données pour votre série :

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Ajouter des points de données à la série
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Étape 5 : Appliquer des remplissages d'image aux marqueurs de points de données

Les images personnalisées peuvent rendre les marqueurs de données visuellement attrayants :

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Définir des images personnalisées pour les marqueurs
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Étape 6 : Personnaliser la taille du marqueur

Modifier la taille des marqueurs pour améliorer la visibilité :

```csharp
series.Marker.Size = 20;
```

## Étape 7 : Enregistrer la présentation mise à jour

Enregistrez la présentation personnalisée à l'emplacement souhaité :

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Conclusion

Aspose.Slides pour .NET fournit aux développeurs des outils pour créer des graphiques professionnels avec de nombreuses options de personnalisation. En exploitant les options de marqueurs de graphique, vous pouvez améliorer considérablement l'attrait visuel et la clarté de vos présentations. Ce guide étape par étape garantit que même les personnalisations complexes sont simples à mettre en œuvre.

## FAQ

### Puis-je utiliser n’importe quel format d’image pour personnaliser les marqueurs ?
Oui, Aspose.Slides prend en charge divers formats d'image, notamment JPEG, PNG et BMP, pour la personnalisation des marqueurs.

### Comment puis-je modifier le type de graphique après la création ?
 Pour modifier le type de graphique, accédez au`chart.Type` propriété et attribuer une autre`ChartType`.

### Aspose.Slides pour .NET est-il compatible avec les anciennes versions de PowerPoint ?
Oui, il prend en charge la compatibilité descendante avec les anciens formats PowerPoint, garantissant ainsi la polyvalence.

### Puis-je mettre à jour dynamiquement les données du graphique ?
 Absolument. Utilisez le`IChartDataWorkbook` pour mettre à jour les données du graphique par programmation.

### Où puis-je trouver plus de ressources ?
 Explorez le[Documentation Aspose.Slides](https://reference.aspose.com/slides/net/)ou rejoignez le[forums communautaires](https://forum.aspose.com/) pour le soutien.