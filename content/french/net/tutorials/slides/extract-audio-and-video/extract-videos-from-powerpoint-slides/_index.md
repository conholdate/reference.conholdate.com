---
title: Extraire des vidéos à partir de diapositives PowerPoint avec Aspose.Slides
linktitle: Extraire des vidéos à partir de diapositives PowerPoint
second_title: API de traitement PowerPoint Aspose.Slides .NET
description: Découvrez comment extraire facilement des fichiers vidéo intégrés à partir de présentations PowerPoint à l'aide d'Aspose.Slides pour .NET. Ce guide complet étape par étape couvre tout, de la configuration de votre environnement à l'enregistrement des vidéos extraites.
type: docs
weight: 14
url: /fr/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## Introduction

Aspose.Slides pour .NET est une bibliothèque puissante qui permet aux développeurs d'interagir avec des présentations PowerPoint par programmation. Dans ce guide, nous vous expliquerons le processus d'extraction de vidéos intégrées dans des diapositives PowerPoint à l'aide d'Aspose.Slides pour .NET. 

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Aspose.Slides pour .NET : obtenez et installez la bibliothèque à partir du[Site Web d'Aspose](https://purchase.aspose.com/buy).
-  Présentation PowerPoint : Préparez un fichier PowerPoint (par exemple,`Video.pptx`) avec la vidéo que vous souhaitez extraire.

## Espaces de noms nécessaires

Pour travailler avec Aspose.Slides pour .NET, vous devez importer les espaces de noms appropriés. Incluez les éléments suivants dans votre code :

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Étape 1 : Spécifier le répertoire du document

Tout d’abord, définissez le chemin d’accès à votre présentation PowerPoint :

```csharp
string dataDir = "Your Document Directory";
```

 Remplacer`"Your Document Directory"` avec le chemin réel vers le répertoire contenant votre fichier PowerPoint.

## Étape 2 : Charger la présentation

 Chargez la présentation PowerPoint dans un`Presentation` objet:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 Ceci initialise le`Presentation` objet avec votre fichier PowerPoint spécifié.

## Étape 3 : parcourir les diapositives et les formes

Ensuite, parcourez chaque diapositive de la présentation et vérifiez les images vidéo :

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Procéder à l'extraction de la vidéo
        }
    }
}
```

## Étape 4 : Extraire les données vidéo

Une fois que vous avez trouvé une image vidéo, extrayez ses propriétés et ses données binaires :

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Stocker la forme sous forme d'image vidéo
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Obtenir l'extension de fichier
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Étape 5 : Enregistrez la vidéo

Enfin, écrivez les données vidéo extraites dans un fichier :

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

Ce code crée un nouveau fichier dans votre répertoire spécifié et y écrit les données vidéo.

## Conclusion

Avec Aspose.Slides pour .NET, l'extraction de vidéos à partir de diapositives PowerPoint est un processus simple. En suivant ce guide, vous pouvez facilement gérer le contenu multimédia dans vos applications .NET, enrichissant ainsi l'expérience utilisateur et les fonctionnalités.

## FAQ

### Qu'est-ce qu'Aspose.Slides pour .NET ?
Aspose.Slides pour .NET est une bibliothèque conçue pour fonctionner avec des présentations PowerPoint, permettant aux utilisateurs de créer, modifier et manipuler des fichiers de présentation par programmation.

### Où puis-je trouver la documentation d'Aspose.Slides pour .NET ?
 Vous pouvez accéder à la documentation complète[ici](https://reference.aspose.com/slides/net/).

### Aspose.Slides pour .NET est-il disponible pour un essai gratuit ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ce lien](https://releases.aspose.com/).

### Comment puis-je obtenir une licence temporaire pour Aspose.Slides pour .NET ?
 Les demandes de licences temporaires peuvent être faites[ici](https://purchase.aspose.com/temporary-license/).

### Où puis-je obtenir de l'aide pour Aspose.Slides pour .NET ?
 Une assistance est disponible via le[Forum Aspose.Slides](https://forum.aspose.com/).