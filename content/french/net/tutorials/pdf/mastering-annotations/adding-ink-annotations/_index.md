---
title: Ajout d'annotations à l'encre avec Aspose.PDF pour .NET
linktitle: Ajout d'annotations à l'encre avec Aspose.PDF pour .NET
second_title: Référence de l'API Aspose.PDF pour .NET
description: Découvrez comment rendre vos documents PDF plus interactifs et attrayants en ajoutant des annotations manuscrites à l'aide d'Aspose.PDF pour .NET. Ce guide complet vous guide tout au long du processus.
type: docs
weight: 20
url: /fr/net/tutorials/pdf/mastering-annotations/adding-ink-annotations/
---
## Introduction

Bienvenue dans le monde passionnant de la manipulation de PDF avec Aspose.PDF pour .NET ! Que vous souhaitiez améliorer des documents pour un usage professionnel, des projets personnels ou tout autre usage intermédiaire, vous êtes au bon endroit. Dans ce guide, nous allons explorer une fonctionnalité pratique d'Aspose.PDF : l'ajout d'annotations manuscrites à vos fichiers PDF. Cette fonctionnalité est parfaite pour incorporer des notes manuscrites ou des signatures, rendant ainsi vos documents plus interactifs et attrayants.

## Prérequis

Avant de passer au code, assurons-nous que tout est configuré :

1. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur. Aspose.PDF fonctionne parfaitement avec différentes versions, y compris .NET Core.
2.  Bibliothèque Aspose.PDF : Téléchargez et référencez la bibliothèque Aspose.PDF pour .NET dans votre projet. Vous pouvez récupérer la dernière version à partir du[lien de téléchargement](https://releases.aspose.com/pdf/net/).
3. Éditeur de code : bien que vous puissiez utiliser n’importe quel éditeur de code, Visual Studio est fortement recommandé pour son interface conviviale avec les applications .NET.
4. Connaissances de base en C# : la familiarité avec C# vous aidera à parcourir les exemples de codage en douceur.
5. Configuration de l'environnement de développement : assurez-vous que votre IDE est configuré pour les projets .NET et que vous avez correctement référencé la bibliothèque Aspose.PDF.

Une fois ces conditions préalables remplies, vous êtes prêt à commencer à ajouter des annotations manuscrites à vos PDF !

## Importer les packages nécessaires

Avant de nous plonger dans le codage, importons les packages requis. En haut de votre fichier C#, ajoutez les instructions using suivantes :

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
using System.Collections.Generic;
```

Ces instructions donneront accès à toutes les classes et méthodes nécessaires pour travailler avec les annotations PDF.

Décomposons le processus d’ajout d’une annotation manuscrite à votre document PDF en étapes claires.

## Étape 1 : Configurer le document et le répertoire

Tout d’abord, établissez le document et le chemin d’accès pour enregistrer le fichier de sortie :

```csharp
string dataDir = "YOUR DATA DIRECTORY";
Document doc = new Document();
```

 Ici,`dataDir` pointe vers le répertoire où votre PDF résultant sera enregistré, et nous instancions un nouveau`Document` objet à éditer.

## Étape 2 : ajouter une page à votre document

Ensuite, ajoutez une page à votre document nouvellement créé :

```csharp
Page pdfPage = doc.Pages.Add();
```

Chaque PDF nécessite au moins une page, cette étape est donc essentielle.

## Étape 3 : Définir le rectangle de dessin

Maintenant, définissez où sur la page vous placerez votre annotation à l'encre :

```csharp
System.Drawing.Rectangle drect = new System.Drawing.Rectangle
{
    Height = (int)pdfPage.Rect.Height,
    Width = (int)pdfPage.Rect.Width,
    X = 0,
    Y = 0
};
Aspose.Pdf.Rectangle arect = Aspose.Pdf.Rectangle.FromRect(drect);
```

 Ce code crée un`Rectangle` objet qui spécifie la zone sur la page pour votre annotation à l'encre, s'adaptant à la page entière.

## Étape 4 : Préparez les points d'encre

Ensuite, définissez les points qui constitueront votre annotation à l’encre :

```csharp
IList<Point[]> inkList = new List<Point[]>();
Aspose.Pdf.Point[] arrpt = new Aspose.Pdf.Point[3];
inkList.Add(arrpt);
arrpt[0] = new Aspose.Pdf.Point(100, 800);
arrpt[1] = new Aspose.Pdf.Point(200, 800);
arrpt[2] = new Aspose.Pdf.Point(200, 700);
```

Ce bloc crée une liste de tableaux de points, où chaque tableau représente un ensemble de points pour votre trait d'encre. Ici, nous définissons trois points formant un triangle, mais n'hésitez pas à ajuster les coordonnées pour les adapter à votre conception.

## Étape 5 : Créer l'annotation à l'encre

Avec vos points définis, créez l’annotation à l’encre :

```csharp
InkAnnotation ia = new InkAnnotation(pdfPage, arect, inkList)
{
    Title = "Your Title",
    Color = Aspose.Pdf.Color.LightBlue,
    CapStyle = CapStyle.Rounded
};
```

 Nous instancions le`InkAnnotation` objet, en passant par la page, le rectangle et les points d'encre. Personnalisez les propriétés comme`Title`, `Color` , et`CapStyle` pour répondre à vos besoins !

## Étape 6 : Définir la bordure et l’opacité

Pour que votre annotation se démarque, stylisons-la :

```csharp
Border border = new Border(ia)
{
    Width = 25
};
ia.Border = border;
ia.Opacity = 0.5;
```

Ce code ajoute une bordure avec une largeur spécifique et définit l'opacité de l'annotation pour la rendre semi-transparente.

## Étape 7 : ajouter l'annotation à la page

Maintenant, ajoutez votre annotation à la page PDF :

```csharp
pdfPage.Annotations.Add(ia);
```

Cette ligne ajoute l'annotation d'encre à la collection d'annotations de la page.

## Étape 8 : Enregistrer le document

Enfin, enregistrez votre document modifié :

```csharp
dataDir = dataDir + "AddInkAnnotation_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nInk annotation added successfully.\nFile saved at " + dataDir);
```

 Ici, nous modifions`dataDir` pour inclure le nom du fichier de sortie et enregistrer le document. Un message de confirmation vous avertira que tout s'est bien passé.

## Conclusion

Félicitations ! Vous avez ajouté avec succès une annotation manuscrite à votre document PDF à l'aide d'Aspose.PDF pour .NET. Cette fonctionnalité simple mais puissante peut améliorer vos documents et les rendre interactifs. Que vous ajoutiez des signatures, des notes ou des gribouillages, les annotations manuscrites offrent un moyen unique d'enrichir votre contenu.

## FAQ

### Qu'est-ce qu'Aspose.PDF ?
Aspose.PDF est une bibliothèque permettant de créer, de manipuler et de convertir des documents PDF dans des applications .NET.

### Puis-je utiliser Aspose.PDF gratuitement ?
Oui ! Aspose propose une version d'essai gratuite pour évaluer ses produits. Vous pouvez la télécharger[ici](https://releases.aspose.com/).

### Est-il possible d'ajouter plusieurs annotations à l'encre ?
 Absolument ! Vous pouvez créer plusieurs`InkAnnotation` objets et les ajouter à la page de votre document.

### Où puis-je trouver plus d’exemples ?
 Découvrez le[documentation](https://reference.aspose.com/pdf/net/) pour des tutoriels détaillés et des exemples.

### Que dois-je faire si j’ai besoin d’aide ?
 Si vous rencontrez des problèmes, vous pouvez demander de l'aide sur le[Forum de soutien](https://forum.aspose.com/c/pdf/10).