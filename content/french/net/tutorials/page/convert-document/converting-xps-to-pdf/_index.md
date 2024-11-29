---
title: Conversion de XPS en PDF avec Aspose.Page pour .NET
linktitle: Conversion de XPS en PDF
second_title: API .NET d'Aspose.Page
description: Découvrez comment convertir de manière transparente des documents XPS (XML Paper Specification) en PDF (Portable Document Format) à l'aide de la puissante bibliothèque Aspose.Page pour .NET.
type: docs
weight: 11
url: /fr/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Introduction

Dans ce didacticiel, nous allons découvrir comment convertir des documents XPS (XML Paper Specification) en PDF (Portable Document Format) à l'aide de la bibliothèque polyvalente Aspose.Page pour .NET. Cette puissante bibliothèque simplifie la conversion des documents et offre diverses options de personnalisation, ce qui en fait un excellent choix pour les développeurs.

## Prérequis

Avant de commencer, assurez-vous que les éléments suivants sont en place :

-  Bibliothèque Aspose.Page pour .NET : téléchargez et installez la bibliothèque Aspose.Page pour .NET à partir du[Documentation d'Aspose.Page](https://reference.aspose.com/page/net/).
  
- Environnement de développement : configurez un environnement de développement .NET à l’aide de Visual Studio ou d’un autre IDE compatible.

- Document XPS : Préparez le fichier XPS que vous souhaitez convertir, stocké dans un répertoire désigné.

## Étape 1 : Importer les espaces de noms requis

Commencez par importer l'espace de noms nécessaire pour accéder aux fonctionnalités d'Aspose.Page :

```csharp
using Aspose.Page.XPS;
```

## Étape 2 : Initialiser le répertoire de documents

Définissez le chemin du répertoire où sont stockés vos documents :

```csharp
string dataDir = "Your Document Directory";
```

 Assurez-vous de remplacer`"Your Document Directory"` avec le chemin réel vers le répertoire contenant votre document XPS.

### Étape 3 : ouvrir les flux PDF et XPS

Ensuite, initialisez les flux pour le fichier XPS d’entrée et le fichier PDF de sortie :

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Assurez-vous d'avoir défini le chemin correct pour vos fichiers.

### Étape 4 : charger le document XPS

Maintenant, chargez votre document XPS en utilisant la bibliothèque Aspose.Page :

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Étape 5 : Configurer les options d’enregistrement PDF

Configurez les options d'enregistrement de votre PDF, y compris la qualité de l'image et les paramètres de compression :

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Définir le niveau de qualité JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Utiliser la compression JPEG pour les images
    TextCompression = PdfTextCompression.Flate, // Appliquer la compression Flate pour le texte
    PageNumbers = new int[] { 1, 2, 6 } // Spécifiez les numéros de page à inclure
};
```

N'hésitez pas à ajuster ces paramètres selon vos besoins.

### Étape 6 : Créer le périphérique de rendu PDF

Créer un périphérique de rendu pour le format PDF :

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Étape 7 : Enregistrer le document au format PDF

Enfin, enregistrez le document XPS au format PDF à l’aide du périphérique et des options spécifiés :

```csharp
document.Save(device, options);
```

## Conclusion

Félicitations ! Vous avez converti avec succès un document XPS en PDF à l'aide d'Aspose.Page pour .NET. Cette bibliothèque simplifie non seulement la conversion de documents, mais offre également des fonctionnalités étendues pour gérer divers formats.

## FAQ

### Puis-je convertir plusieurs fichiers XPS en un seul PDF ?

Absolument ! Vous pouvez parcourir plusieurs fichiers XPS et les fusionner en un seul document PDF en suivant les mêmes étapes de conversion.

### Quels autres formats de sortie Aspose.Page pour .NET prend-il en charge ?

Outre le format PDF, Aspose.Page pour .NET prend en charge une gamme de formats, notamment TIFF, JPEG et PNG.

### Comment puis-je personnaliser l'apparence du PDF converti ?

 Vous pouvez ajuster les paramètres dans le`PdfSaveOptions` objet, tels que les paramètres de qualité et de compression JPEG, pour obtenir l'apparence souhaitée.

### Existe-t-il une version d'essai disponible pour Aspose.Page pour .NET ?

 Oui, vous pouvez essayer Aspose.Page pour .NET avec un essai gratuit disponible[ici](https://releases.aspose.com/).

### Où puis-je trouver du support communautaire pour Aspose.Page pour .NET ?

Pour des discussions et un soutien communautaires, visitez le[Forum Aspose.Page](https://forum.aspose.com/c/page/39).