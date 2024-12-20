---
title: Modifier l'orientation de la page PDF
linktitle: Modifier l'orientation de la page PDF
second_title: Référence de l'API Aspose.PDF pour .NET
description: Découvrez comment ajuster facilement l'orientation des pages des fichiers PDF à l'aide d'Aspose.PDF pour .NET. Ce guide étape par étape fournit des instructions claires sur le chargement, la rotation et l'enregistrement de vos documents.
type: docs
weight: 10
url: /fr/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Introduction

Avez-vous déjà rencontré un fichier PDF dont l'orientation des pages était complètement erronée ? Qu'il s'agisse d'un document mal numérisé ou d'un document nécessitant simplement une mise en page différente, le réglage de l'orientation peut faire toute la différence. Heureusement, Aspose.PDF pour .NET offre un moyen puissant et convivial de manipuler les fichiers PDF, notamment de modifier l'orientation des pages. Dans ce guide, nous vous guiderons pas à pas tout au long du processus, que vous souhaitiez passer du mode portrait au mode paysage ou vice versa.

## Prérequis

Avant de plonger dans les détails, assurez-vous que les éléments suivants sont en place :

-  Aspose.PDF pour .NET : assurez-vous que la bibliothèque Aspose.PDF est installée. Si vous ne l'avez pas encore fait, vous pouvez[téléchargez-le ici](https://releases.aspose.com/pdf/net/).
- Un environnement de développement .NET : vous pouvez utiliser Visual Studio, JetBrains Rider ou tout autre IDE de votre choix pour le développement .NET.
- Connaissances de base de C# : la familiarité avec C# vous aidera à suivre plus facilement.
- Un fichier PDF : préparez un exemple de fichier PDF pour le tester. Vous pouvez en créer un ou télécharger un exemple en ligne.

 Si vous débutez, pensez à essayer Aspose.PDF avec un[permis temporaire gratuit](https://purchase.aspose.com/temporary-license/) avant de décider de[acheter la version complète](https://purchase.aspose.com/buy).

## Importer des espaces de noms

Pour manipuler des pages PDF, vous devez d'abord importer les espaces de noms nécessaires dans votre projet C#. Ajoutez les lignes suivantes en haut de votre fichier de code :

```csharp
using System.IO;
using Aspose.Pdf;
```

Maintenant que nous avons tout mis en place, commençons !

## Étape 1 : Charger le document PDF

 La première étape consiste à charger le fichier PDF que vous souhaitez modifier. Utilisez le`Document` classe de l'espace de noms Aspose.PDF :

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Assurez-vous de remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre fichier PDF.

## Étape 2 : Parcourir chaque page

Ensuite, nous allons parcourir chaque page du document PDF. Cela nous permet d'appliquer le changement d'orientation à toutes les pages :

```csharp
foreach (Page page in doc.Pages)
{
    // Manipuler chaque page
}
```

## Étape 3 : Accéder à la MediaBox de la page

 Chaque page PDF a une`MediaBox` qui définit ses limites. Nous devons y accéder pour vérifier l'orientation actuelle et effectuer des ajustements :

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 Le`MediaBox` fournit les dimensions de la page, y compris la largeur et la hauteur.

## Étape 4 : échangez la largeur et la hauteur

Pour modifier l'orientation de la page, nous allons échanger les valeurs de largeur et de hauteur. Ce réglage modifiera les dimensions de la page :

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Ici, nous calculons les nouvelles dimensions et repositionnons le coin inférieur gauche (`LLY`) par conséquent.

## Étape 5 : mettre à jour la MediaBox et la CropBox

 Maintenant que nous avons les nouvelles dimensions, nous allons appliquer ces modifications à la`MediaBox` et`CropBox` pour garantir que la page s'affiche correctement :

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Étape 6 : Faire pivoter la page

Pour finaliser le changement d'orientation, nous allons faire pivoter la page. C'est simple avec Aspose.PDF :

```csharp
page.Rotate = Rotation.on90; // Faire pivoter de 90 degrés
```

Cette ligne retourne efficacement la page dans l’orientation souhaitée.

## Étape 7 : Enregistrer le PDF de sortie

Après avoir modifié l'orientation de toutes les pages, enregistrez le document mis à jour dans un nouveau fichier :

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Assurez-vous de fournir un nouveau nom de fichier pour éviter d'écraser le document d'origine.

## Conclusion

Et voilà ! Changer l'orientation de page d'un fichier PDF à l'aide d'Aspose.PDF pour .NET est un processus simple. En chargeant le document, en parcourant les pages, en mettant à jour la MediaBox et en enregistrant le fichier, vous pouvez facilement ajuster la mise en page pour répondre à vos besoins. Que vous corrigiez un document mal numérisé ou que vous mettiez en forme des pages pour une présentation, ce guide devrait vous aider à faire le travail efficacement.

## FAQ

### Puis-je faire pivoter des pages spécifiques au lieu de toutes les pages du PDF ?  
Oui, vous pouvez modifier la boucle pour cibler des pages spécifiques par leur index au lieu de parcourir toutes les pages.

### Qu'est-ce que le`MediaBox`?  
 Le`MediaBox` définit la taille et la forme de la page dans un fichier PDF, déterminant où le contenu est placé.

### Aspose.PDF pour .NET fonctionne-t-il avec d’autres formats de fichiers ?  
Oui, Aspose.PDF peut gérer différents formats de fichiers, notamment HTML, XML, XPS, etc.

### Existe-t-il une version gratuite d'Aspose.PDF pour .NET ?  
 Oui, vous pouvez commencer avec un[essai gratuit](https://releases.aspose.com/) ou demander un[permis temporaire](https://purchase.aspose.com/temporary-license/).

### Puis-je annuler les modifications une fois enregistrées ?  
Une fois le document enregistré, les modifications sont permanentes. Il est conseillé de travailler sur une copie ou de conserver une sauvegarde du fichier d'origine.