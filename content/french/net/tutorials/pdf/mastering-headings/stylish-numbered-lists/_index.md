---
title: Listes numérotées élégantes avec Aspose.PDF pour .NET
linktitle: Listes numérotées élégantes avec Aspose.PDF pour .NET
second_title: Référence de l'API Aspose.PDF pour .NET
description: Découvrez comment créer de belles listes numérotées dans vos documents PDF avec Aspose.PDF pour .NET. Ce guide vous guide tout au long du processus d'application de différents styles de numérotation, comme les chiffres romains.
type: docs
weight: 10
url: /fr/net/programming-with-headings/stylish-numbered-lists/
---
## Introduction

Avez-vous déjà eu besoin de créer des listes numérotées bien structurées dans vos documents PDF ? Qu'il s'agisse de documents juridiques, de rapports ou de présentations, des styles de numérotation efficaces sont essentiels pour organiser votre contenu. Avec Aspose.PDF pour .NET, vous pouvez facilement appliquer différents styles de numérotation à vos titres PDF, ce qui permet d'obtenir des documents soignés et professionnels.

## Prérequis

Avant de passer au codage, assurez-vous d'avoir les éléments suivants prêts :

1.  Aspose.PDF pour .NET : Téléchargez la dernière version à partir de[ici](https://releases.aspose.com/pdf/net/).
2. Environnement de développement : vous aurez besoin de Visual Studio ou de tout IDE compatible .NET.
3. .NET Framework : assurez-vous que .NET Framework 4.0 ou supérieur est installé.
4.  Licence : Vous pouvez utiliser une licence temporaire à partir de[ici](https://purchase.aspose.com/temporary-license/) ou explorez le[essai gratuit](https://releases.aspose.com/) options.

## Importation des packages requis

Commencez par importer les espaces de noms nécessaires dans votre projet :

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Étape 1 : Configuration du document

Commençons par créer un nouveau document PDF et configurer sa mise en page, y compris la taille de la page et les marges.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Définir les dimensions et les marges de la page
pdfDoc.PageInfo.Width = 612.0; // 8,5 pouces
pdfDoc.PageInfo.Height = 792.0; // 11 pouces
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // Marges de 1 pouce
```

Cette configuration donne à votre document un format lettre standard avec des marges d'un pouce sur tous les côtés.

## Étape 2 : Ajout d'une page au PDF

Ensuite, nous ajouterons une page vierge au document PDF, où nous appliquerons plus tard les styles de numérotation.

```csharp
// Ajouter une nouvelle page au document PDF
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // Utiliser les mêmes paramètres que le document
```

## Étape 3 : Créer une boîte flottante

Une FloatingBox vous permet de positionner le contenu indépendamment du flux de la page, vous donnant ainsi un meilleur contrôle sur votre mise en page.

```csharp
//Créer une FloatingBox pour le contenu structuré
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Étape 4 : Ajout de titres avec des chiffres romains

Maintenant, ajoutons notre premier titre avec une numérotation en chiffres romains minuscules.

```csharp
// Créer le premier titre avec des chiffres romains
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Étape 5 : Ajout d'un deuxième titre avec un numéro de départ personnalisé

Ensuite, nous allons ajouter un deuxième titre, à partir du chiffre romain 13.

```csharp
// Créez un deuxième titre commençant par le chiffre romain 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Étape 6 : Ajout d'un titre avec numérotation alphabétique

Pour varier, ajoutons un troisième titre utilisant une numérotation alphabétique en minuscules.

```csharp
// Créer un titre avec une numérotation alphabétique
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Étape 7 : Enregistrer le PDF

Enfin, enregistrons le fichier PDF dans le répertoire souhaité.

```csharp
// Enregistrer le document PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Conclusion

Félicitations ! Vous avez appliqué avec succès différents styles de numérotation (chiffres romains et alphabétiques) aux titres d'un fichier PDF à l'aide d'Aspose.PDF pour .NET. La flexibilité d'Aspose.PDF vous permet de contrôler la mise en page, les styles de numérotation et le positionnement du contenu, ce qui vous permet de créer des documents PDF bien organisés et professionnels.

## FAQ

### Puis-je appliquer différents styles de numérotation au même document PDF ?  
Oui, vous pouvez mélanger différents styles de numérotation, tels que les chiffres romains, les chiffres arabes et la numérotation alphabétique dans le même document.

### Comment puis-je personnaliser le numéro de départ des titres ?  
 Vous pouvez définir le numéro de départ de n'importe quel titre à l'aide de la`StartNumber` propriété.

### Existe-t-il un moyen de réinitialiser la séquence de numérotation ?  
 Oui, vous pouvez réinitialiser la numérotation en ajustant le`StartNumber` propriété pour chaque rubrique.

### Puis-je appliquer un style gras ou italique aux titres en plus de la numérotation ?  
 Absolument ! Vous pouvez personnaliser les styles de titre en modifiant des propriétés telles que la police, la taille, le gras et l'italique à l'aide de l'`TextState` objet.

### Comment obtenir une licence temporaire pour Aspose.PDF ?  
 Vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.aspose.com/temporary-license/)pour tester Aspose.PDF sans restrictions.