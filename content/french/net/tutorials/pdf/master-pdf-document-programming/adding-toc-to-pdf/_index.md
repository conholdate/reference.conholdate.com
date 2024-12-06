---
title: Ajout d'une table des matières à un document PDF
linktitle: Ajout d'une table des matières à un document PDF
second_title: Référence de l'API Aspose.PDF pour .NET
description: Ce didacticiel montre comment ajouter une table des matières (TOC) à un document PDF à l'aide d'Aspose.Pdf pour .NET.
type: docs
weight: 40
url: /fr/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Introduction

La création d'une table des matières (TOC) dans un document PDF peut grandement améliorer sa navigation et son accessibilité. Dans ce guide, nous allons vous montrer comment ajouter une table des matières à un fichier PDF à l'aide d'Aspose.Pdf pour .NET.

## Prérequis

Avant de commencer, assurez-vous d'avoir les éléments suivants :

1.   Aspose.PDF pour .NET : Téléchargez et installez la dernière version à partir de[ici](https://releases.aspose.com/pdf/net/).
2.  Environnement de développement : configurez un environnement de développement .NET comme Visual Studio.
3.   Licence : Demandez une licence temporaire si nécessaire ; veuillez visiter[Page de licence Aspose.Pdf](https://asposepdf.com/developers) pour plus d'informations.

Importer les bibliothèques nécessaires

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Étape 1 : Charger le document PDF

Chargez votre fichier PDF existant à l'endroit où vous souhaitez ajouter la table des matières. Spécifiez le chemin d'accès au répertoire de votre document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Étape 2 : insérer une nouvelle page pour la table des matières

Insérer une nouvelle page au début du document PDF. Cette page servira de table des matières (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Étape 3 : Créer un objet d'information TOC

Créez un objet qui représentera les informations de la table des matières. Ajoutez un titre et un lien vers celui-ci pour une meilleure navigation.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Étape 4 : Définir les éléments de la table des matières

Définissez les éléments (ou titres) qui seront affichés dans la table des matières. Ces éléments peuvent aider les lecteurs à naviguer vers des sections spécifiques du document.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Étape 5 : Créer des titres de table des matières

Créez des titres pour les deux premiers éléments de la table des matières. Ces titres seront liés à leurs pages respectives.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Étape 6 : Enregistrer le PDF avec la table des matières

Enfin, enregistrez le fichier PDF mis à jour.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Message de confirmation

Afficher un message de confirmation pour informer l'utilisateur que le processus est terminé.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Conclusion

Avec Aspose.PDF pour .NET, ajouter une table des matières à un PDF est non seulement facile mais également personnalisable. Que vous ayez besoin de créer des liens de navigation simples ou des structures complexes, cet outil est fait pour vous. Ainsi, la prochaine fois que vous travaillerez sur un long PDF, n'oubliez pas d'ajouter une table des matières pour une touche professionnelle.

## FAQ

### Puis-je personnaliser l'apparence de la table des matières dans Aspose.PDF ?

Oui, vous pouvez entièrement personnaliser l'apparence de la table des matières, y compris le style de police, la taille et l'alignement.

### Comment ajouter des sous-titres à la table des matières ?

 Vous pouvez ajouter des sous-titres en ajustant le`Heading` niveau (par exemple,`Heading(2)`).

### Est-il possible de mettre à jour automatiquement la table des matières si le document change ?

Non, la table des matières ne se mettra pas à jour automatiquement. Vous devrez la recréer si la structure du document change.

### Puis-je lier des entrées de table des matières à des documents externes ?

Oui, vous pouvez utiliser des hyperliens pour lier des entrées de table des matières à des PDF ou des URL externes.

### Aspose.PDF prend-il en charge les tables des matières à plusieurs niveaux ?

Oui, Aspose.PDF prend en charge les tables des matières à plusieurs niveaux pour les documents complexes avec des sous-sections.
