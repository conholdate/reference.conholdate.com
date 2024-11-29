---
title: Ajout d'un composant de case à cocher au document PDF
linktitle: Ajout d'un composant de case à cocher au document PDF
second_title: API .NET GroupDocs.Annotation
description: Découvrez comment enrichir vos documents PDF en ajoutant des composants de case à cocher interactifs à l'aide du SDK GroupDocs.Annotation pour .NET. Ce didacticiel complet fournit un guide clair étape par étape.
type: docs
weight: 11
url: /fr/net/tutorials/annotation/guide-to-document-components/adding-checkbox-component/
---
## Introduction

Dans ce didacticiel, nous vous expliquerons le processus d'ajout d'un composant Checkbox à un document PDF à l'aide du SDK GroupDocs.Annotation pour .NET. Cette fonctionnalité vous permet d'améliorer vos documents PDF avec des éléments interactifs, les rendant ainsi plus attrayants pour les utilisateurs.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  GroupDocs.Annotation pour .NET SDK : téléchargez-le à partir de[ici](https://releases.groupdocs.com/annotation/net/).
2. Environnement de développement : configurez un environnement de développement .NET sur votre machine.

## Étape 1 : Importer les espaces de noms requis

Tout d’abord, incluez les espaces de noms nécessaires dans votre projet :

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Étape 2 : définir le chemin de sortie

Spécifiez où le document PDF modifié sera enregistré :

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Étape 3 : Initialiser l'annotateur

 Créer une instance de`Annotator` classe avec le chemin vers votre document PDF d'entrée :

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

## Étape 4 : créer le composant de case à cocher

Maintenant, créons et personnalisons le composant Checkbox :

```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100), // Définir la position et la taille
    PenColor = 65535, // Définissez la couleur (dans ce cas, le jaune)
    Style = BoxStyle.Star, // Choisissez un style pour la case à cocher
    Replies = new List<Reply>
    {
        new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
        new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
    }
};
```

## Étape 5 : ajouter la case à cocher au document

Ajoutez le composant de case à cocher créé au PDF :

```csharp
annotator.Add(checkBox);
```

## Étape 6 : Enregistrer le document modifié

Enregistrez le document PDF mis à jour avec la case à cocher incluse :

```csharp
annotator.Save("result.pdf");
```

## Étape 7 : Afficher le chemin de sortie

Enfin, informez l'utilisateur où le document modifié est enregistré :

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

Dans ce didacticiel, nous avons ajouté avec succès un composant Checkbox à un document PDF à l'aide de GroupDocs.Annotation pour .NET. Cette fonctionnalité vous permet de créer des PDF interactifs qui peuvent améliorer l'expérience et l'engagement des utilisateurs.

## FAQ

### Puis-je personnaliser l’apparence de la case à cocher ?

Absolument ! Vous pouvez modifier diverses propriétés telles que la couleur, le style et la taille pour répondre à vos besoins spécifiques.

### GroupDocs.Annotation pour .NET est-il adapté à une utilisation commerciale ?

Oui, GroupDocs.Annotation pour .NET fournit des licences commerciales pour les entreprises.

### Puis-je essayer GroupDocs.Annotation pour .NET avant d'acheter ?

 Oui, un essai gratuit est disponible. Vous pouvez y accéder[ici](https://releases.groupdocs.com/).

### Où puis-je trouver de l'aide pour GroupDocs.Annotation pour .NET ?

 Du soutien et des ressources supplémentaires sont disponibles sur le[Forum GroupDocs](https://forum.groupdocs.com/c/annotation/10).

### Ai-je besoin d’une licence temporaire à des fins de test ?

 Vous pouvez obtenir une licence temporaire pour les tests auprès de[ici](https://purchase.groupdocs.com/temporary-license/).