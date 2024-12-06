---
title: Rappel d'enregistrement de page dans les documents Word
linktitle: Rappel d'enregistrement de page dans les documents Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment convertir facilement chaque page d'un document Word en images PNG individuelles à l'aide d'Aspose.Words pour .NET. Ce guide fournit des instructions étape par étape, notamment des exemples de code.
type: docs
weight: 10
url: /fr/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Introduction

Avez-vous déjà eu besoin de convertir chaque page d'un document Word en images individuelles ? Que vous cherchiez à créer des vignettes pour un aperçu ou à décomposer un long rapport en visuels digestes, Aspose.Words pour .NET rend cette tâche simple et efficace. Dans ce guide, nous vous expliquerons le processus de configuration d'un rappel d'enregistrement de page pour enregistrer chaque page de votre document sous forme d'image PNG. Commençons !

## Prérequis

Avant de plonger, assurez-vous d'avoir les éléments suivants :

1.  Aspose.Words pour .NET : Téléchargez-le et installez-le depuis[ici](https://releases.aspose.com/words/net/).
2. Visual Studio : n’importe quelle version fonctionnera, mais nous utiliserons Visual Studio 2019 pour ce guide.
3. Connaissances de base en C# : la familiarité avec C# vous aidera à suivre en douceur.

## Étape 1 : Importer les espaces de noms nécessaires

Tout d'abord, nous devons importer les espaces de noms requis. Cela nous permet d'accéder aux classes et méthodes nécessaires sans avoir à saisir l'espace de noms complet à chaque fois.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 2 : définissez votre répertoire de documents

Ensuite, définissez le chemin d'accès à votre répertoire de documents. C'est là que se trouve votre document Word d'entrée et où les images de sortie seront enregistrées.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 3 : Chargez votre document

Chargez maintenant le document que vous souhaitez traiter. Assurez-vous que votre document, nommé « Rendering.docx », se trouve dans le répertoire spécifié.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 4 : Configurer les options d’enregistrement de l’image

Nous allons configurer les options d'enregistrement des images, en spécifiant que nous souhaitons enregistrer les pages sous forme de fichiers PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Ici,`PageSet` définit la plage de pages à enregistrer, et`PageSavingCallback` pointe vers notre classe de rappel personnalisée.

## Étape 5 : implémenter le rappel d'enregistrement de page

Maintenant, nous devons implémenter la classe de rappel qui gère la manière dont chaque page est enregistrée.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Cette classe implémente le`IPageSavingCallback` interface. Dans le`PageSaving` méthode, nous spécifions le modèle de dénomination pour chaque page enregistrée.

## Étape 6 : Enregistrer le document sous forme d'images

Enfin, nous enregistrons le document en utilisant les options configurées.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Conclusion

Félicitations ! Vous avez réussi à configurer un rappel d'enregistrement de page pour enregistrer chaque page d'un document Word sous forme d'image PNG distincte à l'aide d'Aspose.Words pour .NET. Cette technique est incroyablement utile pour diverses applications, de la création d'aperçus de page à la génération d'images de page individuelles pour les rapports.

## FAQ

### Puis-je enregistrer des pages dans des formats autres que PNG ?
 Oui ! Vous pouvez enregistrer des pages dans des formats tels que JPEG, BMP et TIFF en modifiant le`SaveFormat` dans`ImageSaveOptions`.

### Comment puis-je enregistrer uniquement des pages spécifiques ?
 Pour enregistrer des pages spécifiques, ajustez le`PageSet` paramètre dans`ImageSaveOptions` pour inclure uniquement les pages souhaitées.

### Est-il possible de personnaliser la qualité de l'image ?
 Absolument ! Vous pouvez contrôler la qualité de l'image de sortie en définissant des propriétés telles que`ImageSaveOptions.JpegQuality`.

### Comment puis-je gérer efficacement des documents volumineux ?
Pour les documents volumineux, envisagez de traiter les pages par lots pour gérer efficacement l'utilisation de la mémoire.

### Où puis-je trouver plus d'informations sur Aspose.Words pour .NET ?
 Pour des guides et des exemples complets, consultez le[Documentation Aspose.Words](https://reference.aspose.com/words/net/).