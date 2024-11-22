---
title: Enregistrer des fichiers PSD sur le disque avec Aspose.PSD pour .NET
linktitle: Enregistrer des images sur le disque avec Aspose.PSD pour .NET
second_title: API .NET Aspose.PSD
description: Découvrez comment enregistrer facilement des images PSD sur un disque en suivant un guide étape par étape. Que vous convertissiez des fichiers PSD en différents formats d'image ou que vous gériez des ressources d'image complexes.
type: docs
weight: 10
url: /fr/net/tutorials/psd/mastering-file-saving-and-exporting/saving-psd-files-to-disk/
---
## Introduction

Dans le monde en constante évolution du développement .NET, Aspose.PSD est une bibliothèque puissante pour gérer efficacement les images PSD. Ce guide vous guidera tout au long du processus d'enregistrement d'images sur disque à l'aide d'Aspose.PSD, que vous soyez un développeur expérimenté ou un nouveau venu dans le codage. 

## Prérequis

Avant de commencer, veuillez vous assurer des points suivants :

### 1. Installer Aspose.PSD pour .NET

 Vous devez avoir Aspose.PSD pour .NET installé dans votre environnement de développement. Téléchargez-le[ici](https://releases.aspose.com/psd/net/).

### 2. Importer les espaces de noms requis

Dans votre projet .NET, incluez les espaces de noms nécessaires en haut de votre code :

```csharp
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## Étape 1 : Définissez votre répertoire de documents

Configurez une variable pour spécifier le répertoire où se trouvent vos documents :

```csharp
// Chemin vers le répertoire des documents
string dataDir = "Your Document Directory";
```

 Assurez-vous de remplacer`"Your Document Directory"` avec le chemin réel.

## Étape 2 : Spécifier les chemins source et de destination

Définissez le fichier PSD source et le chemin de destination de l'image résultante :

```csharp
// ExStart : Sauvegarde sur disque

string sourceFile = dataDir + @"sample.psd";
string destName = dataDir + "result.png";
```

 Ici,`sourceFile` pointe vers le fichier PSD que vous souhaitez traiter, tandis que`destName` est l'endroit où vous souhaitez enregistrer l'image de sortie.

## Étape 3 : charger et enregistrer l’image

Utilisez le code suivant pour charger l'image PSD et l'enregistrer au format PNG :

```csharp
// Charger l'image PSD et remplacer les polices non trouvées
using (Image image = Image.Load(sourceFile))
{
    PsdImage psdImage = (PsdImage)image;
    psdImage.Save(destName, new PngOptions());
}
```

Cet extrait charge le fichier PSD, le convertit au format PNG et l'enregistre à la destination spécifiée. 

## Conclusion

Aspose.PSD pour .NET simplifie les tâches de traitement d'images, ce qui en fait un outil essentiel pour les développeurs. En suivant ce guide, vous avez appris à enregistrer des images sans effort, et il y a encore bien plus à découvrir !

## FAQ

### Aspose.PSD pour .NET peut-il gérer d’autres formats d’image ?

A1 : Absolument ! Aspose.PSD prend en charge différents formats d'image, offrant ainsi une flexibilité dans vos projets.

### Existe-t-il une version d'essai disponible ?

 A2 : Oui, vous pouvez télécharger une version d'essai gratuite[ici](https://releases.aspose.com/).

### Où puis-je trouver du support pour Aspose.PSD pour .NET ?

 A3 : Visitez le[Forum de soutien](https://forum.aspose.com/c/psd/34) pour obtenir de l'aide ou pour poser des questions.

### Comment obtenir un permis temporaire ?

 A4 : Vous pouvez obtenir un permis temporaire[ici](https://purchase.conholdate.com/temporary-license/).

### Où puis-je acheter Aspose.PSD pour .NET ?

 A5 : Acheter Aspose.PSD pour .NET[ici](https://purchase.conholdate.com/buy).