---
title: Extraire le texte en surbrillance des fichiers PDF à l'aide d'Aspose.PDF pour .NET
linktitle: Extraire le texte en surbrillance des fichiers PDF à l'aide d'Aspose.PDF pour .NET
second_title: Référence de l'API Aspose.PDF pour .NET
description: Libérez le potentiel de vos documents PDF en apprenant à extraire le texte mis en surbrillance avec Aspose.PDF pour .NET. Ce guide complet vous guide à travers chaque étape, de la configuration à la mise en œuvre.
type: docs
weight: 60
url: /fr/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## Introduction

Lorsque vous travaillez avec des fichiers PDF, l'extraction du texte mis en surbrillance peut être essentielle pour l'analyse des données, la révision du contenu ou l'organisation des notes. Si vous utilisez Aspose.PDF pour .NET, vous avez de la chance. Ce didacticiel fournit des instructions claires, étape par étape, sur la manière d'extraire efficacement le texte mis en surbrillance d'un document PDF.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Bibliothèque Aspose.PDF pour .NET : téléchargez la bibliothèque à partir du[page de sortie](https://releases.aspose.com/pdf/net/).
- Environnement de développement : un environnement de travail comme Visual Studio.
- Connaissances de base de C# : Une familiarité avec C# et la programmation orientée objet est nécessaire.
-  Licence Aspose : Bien que vous puissiez commencer avec un essai gratuit, un[permis temporaire](https://purchase.aspose.com/temporary-license/) ou une licence complète de[ici](https://purchase.aspose.com/buy) fournira un accès illimité.

## Importer les espaces de noms nécessaires

Commencez par importer les espaces de noms requis dans votre projet C# :

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Ces espaces de noms donnent accès aux classes et méthodes nécessaires à la gestion des documents et des annotations PDF.

## Étape 1 : Configurez votre répertoire de projet

Spécifiez le répertoire où se trouve votre fichier PDF :

```csharp
// Chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Assurez-vous de remplacer le chemin par le répertoire réel de votre fichier PDF.

## Étape 2 : Charger le document PDF

Chargez le document PDF avec le code suivant :

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Assurez-vous que le fichier spécifié existe dans le répertoire donné.

## Étape 3 : Accéder aux annotations sur la page

Pour accéder aux annotations, parcourez les annotations sur la page souhaitée (dans ce cas, la première page) :

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 Ce code filtre pour`TextMarkupAnnotation` types, qui représentent les points forts.

## Étape 4 : Extraire le texte en surbrillance

Maintenant, extrayez et affichez le texte des annotations en surbrillance :

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

Cela récupère tous les fragments de texte marqués associés à la surbrillance et les imprime sur la console.

## Conclusion

L'extraction de texte surligné d'un PDF à l'aide d'Aspose.PDF pour .NET est simple et peut améliorer considérablement votre processus de gestion de documents. En suivant les étapes décrites ci-dessus, vous pouvez collecter efficacement le texte surligné pour diverses applications, telles que la préparation de rapports ou l'analyse de données.

## FAQ

### Puis-je extraire d’autres types d’annotations ?
 Oui, ajustez simplement le`if` condition d'inclure différents types d'annotations comme`TextAnnotation` ou`StampAnnotation`.

### Comment puis-je extraire le texte en surbrillance de toutes les pages PDF ?
Vous pouvez parcourir toutes les pages en utilisant :
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Une licence est-elle nécessaire pour Aspose.PDF pour .NET ?
 Un essai gratuit est disponible, mais envisagez un[permis temporaire](https://purchase.aspose.com/temporary-license/) ou une licence complète pour un accès complet.

### Puis-je enregistrer le texte extrait dans un fichier ?
Absolument ! Vous pouvez modifier le code pour écrire le texte extrait dans un fichier texte.

### Aspose.PDF prend-il en charge d’autres plates-formes ?
Oui, Aspose.PDF prend également en charge Java et d'autres plates-formes, offrant des fonctionnalités similaires.