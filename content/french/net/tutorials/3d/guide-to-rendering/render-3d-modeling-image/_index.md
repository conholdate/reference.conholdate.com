---
title: Rendu d'une image de modélisation 3D avec Aspose.3D pour .NET
linktitle: Rendu d'une image de modèle 3D à partir d'une caméra
second_title: API .NET Aspose.3D
description: Apprenez à créer et personnaliser des modèles 3D primitifs, notamment des boîtes et des cylindres, et à les enregistrer au format FBX sans effort. Que vous soyez un développeur novice ou expérimenté, ce didacticiel étape par étape.
type: docs
weight: 11
url: /fr/net/tutorials/3d/guide-to-rendering/render-3d-modeling-image/
---
## Introduction

Le rendu de modèles 3D en visuels époustouflants est une compétence essentielle dans le développement de logiciels, en particulier lorsque l'on exploite des bibliothèques puissantes comme Aspose.3D pour .NET. Dans cet article, nous vous guiderons tout au long du processus de rendu d'une image de modèle 3D du point de vue d'une caméra. À la fin, vous aurez les connaissances nécessaires pour créer des rendus 3D très détaillés, modifier les angles de caméra et appliquer un éclairage avancé pour un meilleur rendu visuel.

## Prérequis

Avant de commencer, assurez-vous que les conditions préalables suivantes sont en place pour restituer avec succès des images 3D à l'aide d'Aspose.3D pour .NET :

-  Bibliothèque Aspose.3D pour .NET : Tout d'abord, téléchargez la bibliothèque Aspose.3D pour .NET. Vous pouvez l'installer à l'aide de NuGet ou la télécharger directement depuis le[Page de sortie d'Aspose](https://releases.aspose.com/3d/net/).
- Un modèle 3D : Préparez votre modèle 3D dans un format compatible, tel que OBJ, FBX ou 3DS. Pour ce tutoriel, nous utiliserons un`Aspose3D.obj` déposer.
- Environnement de développement .NET : assurez-vous de disposer d'un environnement de développement .NET opérationnel. Ce didacticiel suppose que vous utilisez Visual Studio ou un IDE similaire.

## Importer les espaces de noms nécessaires

La première étape de la configuration de votre projet consiste à inclure les espaces de noms nécessaires pour Aspose.3D. Cela permettra à votre code d'accéder à la fonctionnalité Aspose.3D qui vous aidera à charger le modèle, à configurer la caméra, l'éclairage et à restituer la scène.

```csharp
using System;
using System.IO;
using System.Collections;
using Aspose.ThreeD;
using Aspose.ThreeD.Animation;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
using Aspose.ThreeD.Utilities;
using System.Drawing;
using System.Drawing.Imaging;
```

## Étape 1 : Charger la scène 3D

La première action de tout flux de travail de rendu 3D consiste à charger la scène, qui comprend le modèle, la caméra, l'éclairage et tout autre élément requis pour restituer l'image. Voici comment charger votre modèle 3D dans la scène :

```csharp
Scene scene = new Scene();
var path = "YourModelPath/Aspose3D.obj";  // Spécifiez ici le chemin de votre modèle
scene.Open(path);
```

## Étape 2 : Configurer la caméra

Le réglage de la caméra appropriée est essentiel pour capturer la scène sous l'angle souhaité. Dans cette étape, nous allons créer une caméra de perspective, définir ses plans proche et lointain pour la profondeur et positionner la caméra dans la scène pour capturer correctement le modèle.

```csharp
Camera cam = new Camera(ProjectionType.Perspective);
cam.NearPlane = 1;
cam.FarPlane = 500;
scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(170, 16, 130);  // Positionner la caméra
cam.LookAt = new Vector3(28, 0, -30);  // Régler le point de mise au point de l'appareil photo
```

## Étape 3 : ajouter de l’éclairage à la scène

L'éclairage joue un rôle essentiel dans l'amélioration de l'apparence du modèle 3D. Aspose.3D vous permet d'ajouter différents types de lumières telles que des lumières ponctuelles, des lumières directionnelles et des projecteurs pour éclairer la scène. Dans cette étape, nous allons ajouter une combinaison de ces lumières pour rendre le modèle plus réaliste.

```csharp
scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Point,
    ConstantAttenuation = 0.3,
    Color = new Vector3(Color.White)
}).Transform.Translation = new Vector3(30, 10, 10);

scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Directional,
    ConstantAttenuation = 0.3,
    Direction = new Vector3(-0.3, -0.4, 0.3),
    Color = new Vector3(Color.White)
});

scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Spot,
    CastShadows = true,
    LookAt = new Vector3(28, 10, -30),
    Color = new Vector3(Color.White)
}).Transform.Translation = new Vector3(40, 10, 50);
```

## Étape 4 : Spécifier les options de rendu de l’image

Maintenant que nous avons notre scène avec le modèle, la caméra et les lumières, il est temps de spécifier les options de rendu. Ces options vous permettent de personnaliser la couleur d'arrière-plan, d'activer les ombres et de définir les répertoires de texture pour un effet plus réaliste.

```csharp
ImageRenderOptions opt = new ImageRenderOptions();
opt.BackgroundColor = Color.AliceBlue;  // Définir la couleur d'arrière-plan
opt.AssetDirectories.Add("YourDocumentDirectory" + "textures");  // Définir le répertoire de texture
opt.EnableShadows = true;  //Activer les ombres pour la profondeur
```

## Étape 5 : Rendre la scène

Une fois tout configuré, la dernière étape consiste à générer le rendu du modèle 3D dans un fichier image. Vous pouvez spécifier la taille et le format de l'image, et Aspose.3D se chargera du reste.

```csharp
scene.Render(cam, "YourOutputDirectory/Render3DModelImageFromCamera.png", new Size(1024, 1024), ImageFormat.Png, opt);
```

Cela rendra l'image du modèle 3D dans le répertoire de sortie spécifié au format PNG.

## Conclusion

Félicitations ! Vous savez maintenant comment générer un rendu d'image de modèle 3D à partir d'une perspective de caméra à l'aide d'Aspose.3D pour .NET. En suivant les étapes ci-dessus, vous pouvez tester différents modèles, positions de caméra et configurations d'éclairage pour créer des visualisations 3D plus dynamiques et visuellement plus attrayantes. Aspose.3D vous offre la flexibilité nécessaire pour personnaliser vos rendus 3D en fonction des besoins de votre projet.

## FAQ

### Puis-je utiliser Aspose.3D pour .NET avec d’autres outils de modélisation 3D ?

Oui, Aspose.3D prend en charge divers formats de modèles 3D tels que OBJ, FBX et 3DS, ce qui le rend compatible avec les outils de modélisation populaires tels que Blender, 3ds Max et Maya.

### Comment puis-je résoudre les problèmes de rendu ?

Pour le dépannage, vérifiez le[Forum Aspose.3D](https://forum.aspose.com/c/3d/18) pour des solutions aux problèmes de rendu courants. Vous pouvez également vous référer à la documentation pour des conseils détaillés.

### Existe-t-il un essai gratuit disponible ?

 Oui, Aspose propose un[essai gratuit](https://releases.aspose.com/) pour vous permettre d'explorer toutes les fonctionnalités d'Aspose.3D et d'évaluer ses capacités avant de procéder à un achat.

### Où puis-je trouver une documentation complète ?

 Vous pouvez trouver une documentation détaillée pour Aspose.3D pour .NET sur le[page de documentation](https://reference.aspose.com/3d/net/), qui fournit une couverture approfondie des fonctionnalités et des fonctionnalités de la bibliothèque.

### Comment acheter Aspose.3D pour .NET ?

 Pour acheter Aspose.3D pour .NET, visitez le[page d'achat](https://purchase.conholdate.com/buy), où vous pouvez choisir une licence adaptée à vos besoins.