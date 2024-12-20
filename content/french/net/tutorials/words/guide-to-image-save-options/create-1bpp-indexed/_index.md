---
title: Créer 1Bpp indexé
linktitle: Créer 1Bpp indexé
second_title: API de traitement de documents Aspose.Words
description: Ce guide fournit des instructions étape par étape et un exemple de code pour vous aider à créer efficacement des images indexées 1Bpp à des fins d'archivage, d'impression ou d'économie d'espace.
type: docs
weight: 10
url: /fr/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Introduction

Avez-vous déjà eu besoin de convertir un document Word en une image en noir et blanc ? Que ce soit pour l'archivage numérique, l'impression ou simplement pour économiser de l'espace, la conversion de vos documents en une image indexée de 1 Bpp peut s'avérer extrêmement utile. Dans ce guide, nous allons vous présenter une méthode simple pour y parvenir à l'aide d'Aspose.Words pour .NET. Commençons !

## Prérequis

Avant de plonger dans le code, assurez-vous de disposer des éléments suivants :

-  Aspose.Words pour .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.aspose.com/words/net/).
- Environnement de développement .NET : bien que Visual Studio soit un choix populaire, tout IDE prenant en charge .NET fonctionnera.
- Connaissances de base de C# : une connaissance de C# sera utile, mais nous garderons les choses simples.
- Exemple de document Word : préparez un document pour la conversion.

## Étape 1 : Importer les espaces de noms nécessaires

Pour utiliser Aspose.Words, vous devez importer les espaces de noms pertinents. Cela est essentiel pour accéder aux classes et méthodes nécessaires à la manipulation des documents.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 2 : Configurez votre répertoire de documents

Spécifiez le chemin d’accès au répertoire où votre document Word est stocké et où vous souhaitez enregistrer l’image convertie.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Étape 3 : Charger le document Word

Chargez votre document Word dans un`Aspose.Words.Document` objet. Cet objet vous permet de manipuler le document par programmation.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 4 : Configurer les options d’enregistrement de l’image

 Ensuite, configurez le`ImageSaveOptions` pour définir comment le document sera enregistré en tant qu'image. Nous allons le configurer pour qu'il soit enregistré au format PNG avec un mode couleur indexé de 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Convertir uniquement la première page
    ImageColorMode = ImageColorMode.BlackAndWhite, // Mettre en noir et blanc
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Utiliser le format indexé 1Bpp
};
```

- SaveFormat.Png : spécifie que le format de sortie sera PNG.
- PageSet(1) : indique que seule la première page du document sera convertie.
- ImageColorMode.BlackAndWhite : garantit que l'image est en noir et blanc.
- ImagePixelFormat.Format1bppIndexed : définit le format de pixel sur 1 Bpp indexé, en optimisant l'espace.

## Étape 5 : Enregistrer le document en tant qu’image

 Enfin, utilisez le`Save` méthode de la`Document` objet pour enregistrer l'image convertie.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Conclusion

Félicitations ! Vous avez converti avec succès un document Word en une image indexée de 1 Bpp à l'aide d'Aspose.Words pour .NET. Cette méthode est non seulement efficace, mais vous aide également à créer des images à contraste élevé adaptées à diverses applications. N'hésitez pas à intégrer cette fonctionnalité dans vos projets. Bon codage !

## FAQ

### Qu'est-ce qu'une image indexée 1Bpp ?
Une image indexée 1Bpp (1 bit par pixel) est un format d'image en noir et blanc où chaque pixel est représenté par un seul bit, soit 0, soit 1. Ce format est très efficace en termes d'espace, ce qui le rend idéal pour l'archivage.

### Puis-je convertir plusieurs pages d’un document Word à la fois ?
 Oui ! Modifiez simplement le`PageSet` propriété dans le`ImageSaveOptions` pour inclure plusieurs pages ou le configurer pour convertir l'intégralité du document.

### Ai-je besoin d'une licence pour utiliser Aspose.Words pour .NET ?
 Oui, une licence est requise pour bénéficier de toutes les fonctionnalités. Vous pouvez obtenir une[licence temporaire ici](https://purchase.aspose.com/temporary-license/).

### Vers quels autres formats d’image puis-je convertir mon document Word ?
 Aspose.Words prend en charge différents formats, notamment JPEG, BMP et TIFF. Il suffit de modifier le`SaveFormat` dans le`ImageSaveOptions`au format souhaité.

### Où puis-je trouver plus de documentation sur Aspose.Words pour .NET ?
 Pour une documentation complète, visitez le[Page de documentation d'Aspose.Words pour .NET](https://reference.aspose.com/words/net/).