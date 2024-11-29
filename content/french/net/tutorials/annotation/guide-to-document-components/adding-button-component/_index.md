---
title: Ajout de composants de bouton avec GroupDocs.Annotation pour .NET
linktitle: Ajout de composants de bouton
second_title: API .NET GroupDocs.Annotation
description: Découvrez comment améliorer vos documents PDF en ajoutant des composants de bouton interactifs à l'aide de GroupDocs.Annotation pour .NET. Ce didacticiel étape par étape.
type: docs
weight: 10
url: /fr/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## Introduction

Dans ce didacticiel, nous vous expliquerons le processus simple d'ajout d'un composant de bouton à un document PDF à l'aide de la bibliothèque GroupDocs.Annotation pour .NET. À la fin de ce guide, vous serez en mesure d'améliorer vos documents PDF avec des fonctionnalités interactives.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  GroupDocs.Annotation pour .NET : téléchargez et installez la bibliothèque GroupDocs.Annotation pour .NET à partir de[ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : Configurez un environnement de développement approprié avec le framework .NET installé.

## Étape 1 : Importer les espaces de noms nécessaires

Commencez par importer les espaces de noms requis dans votre projet :

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Étape 2 : Initialiser le chemin de sortie

Définissez le chemin de sortie où le PDF modifié sera enregistré :

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Étape 3 : ajouter un composant de bouton

Maintenant, créons et ajoutons le composant Bouton à votre PDF :

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // Position et taille du bouton
        PenColor = 65535,                       // Couleur de bordure du bouton
        Style = BorderStyle.Dashed,             // Style de bordure
        BorderWidth = 0,                        // Largeur de la bordure
        BorderColor = 0,                        // Couleur de la bordure
        AlternateName = "Name",                 //Nom alternatif pour le bouton
        PartialName = "Partial Name",           // Nom partiel du bouton
        NormalCaption = "Caption",               // Texte affiché sur le bouton
        ButtonColor = 16761035,                 // Couleur d'arrière-plan du bouton
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // Ajoutez le bouton à l'annotateur
    annotator.Save("result.pdf"); // Enregistrer le PDF modifié
}
```

## Étape 4 : Afficher le chemin de sortie

Enfin, informez l'utilisateur où le fichier de sortie est enregistré :

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Félicitations ! Vous avez ajouté avec succès un composant Bouton à un document PDF à l'aide de GroupDocs.Annotation pour .NET.

## Conclusion

Dans ce didacticiel, nous avons montré comment intégrer des composants Button dans des documents PDF avec GroupDocs.Annotation pour .NET. En suivant ces étapes, vous pouvez améliorer considérablement l'interactivité de vos documents PDF.

## FAQ

### Puis-je personnaliser l'apparence du bouton ?

Absolument ! Vous pouvez modifier diverses propriétés telles que la taille, la couleur et le style pour répondre à vos besoins.

### GroupDocs.Annotation pour .NET est-il compatible avec toutes les versions PDF ?

Oui, GroupDocs.Annotation pour .NET prend en charge une large gamme de versions PDF, garantissant ainsi la compatibilité avec la plupart des documents.

### Puis-je ajouter plusieurs composants de bouton à un seul document PDF ?

Oui, vous pouvez ajouter autant de composants de bouton que nécessaire à un document PDF.

### GroupDocs.Annotation pour .NET prend-il en charge d’autres formats de fichiers ?

Oui, il prend en charge divers formats de documents, notamment DOCX, PPTX et XLSX, en plus du PDF.

### Existe-t-il une version d’essai disponible à des fins de test ?

 Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Annotation pour .NET à partir de[ici](https://releases.groupdocs.com/).
