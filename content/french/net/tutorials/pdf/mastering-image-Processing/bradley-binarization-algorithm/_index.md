---
title: Algorithme de binarisation de Bradley
linktitle: Algorithme de binarisation de Bradley
second_title: Référence de l'API Aspose.PDF pour .NET
description: Découvrez comment convertir des pages PDF en images TIFF binaires de haute qualité à l'aide de l'algorithme de binarisation Bradley dans Aspose.PDF pour .NET. Ce guide étape par étape comprend un exemple de code.
type: docs
weight: 30
url: /fr/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Introduction

Dans ce didacticiel, nous vous guiderons tout au long du processus de conversion d'une page PDF en image TIFF à l'aide de l'algorithme de binarisation Bradley. Aspose.PDF pour .NET simplifie cette tâche, vous permettant d'automatiser et de rationaliser vos flux de travail de documents en toute simplicité.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Aspose.PDF pour .NET : Téléchargez la bibliothèque depuis[ici](https://releases.aspose.com/pdf/net/).
- Visual Studio (ou tout autre IDE C#).
- Connaissances de base de C#.
-  Un permis valide ou un[permis temporaire](https://purchase.aspose.com/temporary-license/) de Aspose.

## Étape 1 : Configurez votre projet

Tout d’abord, créez un nouveau projet C# dans votre IDE et importez les espaces de noms nécessaires :

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Étape 2 : Définir le répertoire des documents

Spécifiez le chemin d'accès au répertoire où se trouve votre document PDF, ainsi que les chemins de sortie des images TIFF :

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Chemin vers votre fichier PDF
```

Ce répertoire stockera à la fois le PDF source et les fichiers TIFF convertis.

## Étape 3 : Charger le document PDF

Ouvrez le document PDF que vous souhaitez convertir :

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Remplacer`PageToTIFF.pdf` avec le nom de votre fichier PDF.

## Étape 4 : Spécifier les chemins de sortie

Définissez les chemins de sortie pour les fichiers TIFF générés :

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Étape 5 : Définir la résolution de l’image

Définissez la résolution des images TIFF. Un DPI plus élevé produira une meilleure qualité d'image :

```csharp
Resolution resolution = new Resolution(300);
```

## Étape 6 : Configurer les paramètres TIFF

Configurez les paramètres de l'image TIFF, y compris la compression et la profondeur de couleur :

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

L'utilisation de 1 bpp (1 bit par pixel) prépare l'image pour la sortie binaire.

## Étape 7 : Créer le périphérique TIFF

Créez un périphérique TIFF qui gérera la conversion :

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Étape 8 : Convertir la page PDF en TIFF

Convertir la première page du PDF en image TIFF :

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Étape 9 : Appliquer l’algorithme de binarisation de Bradley

Appliquez maintenant l’algorithme de Bradley pour convertir l’image TIFF en niveaux de gris en une image binaire :

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 Le`BinarizeBradley` La méthode prend deux flux de fichiers (entrée et sortie) et une valeur de seuil. Ajustez le seuil selon vos besoins pour des résultats optimaux.

## Étape 10 : Confirmer la conversion réussie

Enfin, confirmez que la conversion a réussi :

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Conclusion

Félicitations ! Vous avez converti avec succès une page PDF en image TIFF et appliqué l'algorithme de binarisation Bradley à l'aide d'Aspose.PDF pour .NET. Ce processus est essentiel pour l'archivage de documents, l'OCR et d'autres applications professionnelles. Grâce à une résolution de haute qualité et à une compression efficace, les images de vos documents seront claires et d'une taille gérable.

## FAQ

### Qu'est-ce que l'algorithme de Bradley ?
L'algorithme de Bradley est une technique de binarisation qui convertit les images en niveaux de gris en images binaires en déterminant un seuil adaptatif pour chaque pixel en fonction de son environnement.

### Puis-je convertir plusieurs pages PDF en TIFF en utilisant cette méthode ?
 Oui, vous pouvez modifier le`Process` méthode permettant de parcourir toutes les pages du document pour la conversion.

### Quelle est la résolution optimale pour convertir des PDF en TIFF ?
Une résolution de 300 DPI est généralement recommandée pour les images de haute qualité, mais vous pouvez l'ajuster en fonction de vos besoins spécifiques.

### Que signifie 1bpp en profondeur de couleur ?
1bpp (1 bit par pixel) indique que l'image sera en noir et blanc, chaque pixel étant soit entièrement noir, soit entièrement blanc.

### L'algorithme Bradley est-il adapté à l'OCR ?
Oui, l’algorithme Bradley est souvent utilisé dans le prétraitement OCR car il améliore le contraste du texte dans les documents numérisés, améliorant ainsi la précision de la reconnaissance.