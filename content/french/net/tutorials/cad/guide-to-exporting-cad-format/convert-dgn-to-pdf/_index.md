---
title: Convertir DGN en PDF dans Aspose.CAD pour .NET
linktitle: Convertir DGN en PDF dans Aspose.CAD pour .NET
second_title: Aspose.CAD .NET - Format de fichier CAO et BIM
description: Découvrez comment convertir sans effort des fichiers DGN en PDF à l'aide de la puissante bibliothèque Aspose.CAD pour .NET. Ce guide étape par étape est conçu pour les développeurs de tous niveaux.
type: docs
weight: 12
url: /fr/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Introduction

Naviguer dans le monde des fichiers CAO peut être difficile, mais avec Aspose.CAD pour .NET, les développeurs peuvent facilement manipuler et convertir différents formats CAO. L'un des besoins courants est la conversion de fichiers DGN en PDF, que nous explorerons étape par étape dans ce didacticiel.

## Prérequis

Pour suivre, assurez-vous d'avoir les éléments suivants :

- Maîtrise de base de C# et du framework .NET.
-  Bibliothèque Aspose.CAD pour .NET installée. Vous pouvez la télécharger[ici](https://releases.aspose.com/cad/net/).
- Un exemple de fichier DGN (par exemple, Nikon_D90_Camera.dgn). 

## Étape 1 : Importer les espaces de noms requis

Commencez par importer les espaces de noms pertinents dans votre projet C# :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Étape 2 : charger le fichier DGN

Spécifiez le répertoire de votre fichier DGN et chargez-le à l'aide du code suivant :

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Un traitement supplémentaire aura lieu ici...
}
```

## Étape 3 : Configurer les options de rastérisation

Ensuite, configurez les options de rastérisation pour définir comment votre DGN sera rendu dans le PDF :

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Ajustez la largeur selon vos besoins
    PageHeight = 300, // Ajustez la hauteur selon vos besoins
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Étape 4 : Créer des options PDF

Définissez les options PDF en intégrant les paramètres de rastérisation configurés précédemment :

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Étape 5 : Enregistrer le fichier DGN au format PDF

Enfin, enregistrez le fichier DGN au format PDF en utilisant les options que vous avez configurées :

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Conclusion

Félicitations ! Vous avez converti avec succès un fichier DGN en PDF à l'aide d'Aspose.CAD pour .NET. Ce didacticiel simple vous a guidé dans le chargement du fichier DGN, la définition des options de rastérisation et l'enregistrement de la sortie au format PDF.

## FAQ

### Ai-je besoin de connaissances préalables en CAO pour utiliser Aspose.CAD ?  
Absolument ! Aspose.CAD est conçu pour simplifier les tâches de CAO complexes, en les rendant accessibles à tous les développeurs, quelles que soient leurs connaissances en CAO.

### Où puis-je trouver plus de ressources et de documentation pour Aspose.CAD ?  
 Vous pouvez explorer des guides et des exemples complets dans le[Documentation d'Aspose.CAD](https://reference.aspose.com/cad/net/).

### Existe-t-il un essai gratuit disponible pour Aspose.CAD ?  
 Oui, un essai gratuit peut être obtenu[ici](https://releases.aspose.com/).

### Comment puis-je obtenir une licence temporaire pour Aspose.CAD ?  
 Vous pouvez demander des licences temporaires[ici](https://purchase.conholdate.com/temporary-license/).

### Besoin d'aide ou avez des questions ?  
Rejoignez la conversation dans le[Forum Aspose.CAD](https://forum.aspose.com/c/cad/19) pour le soutien et les demandes de renseignements de la communauté.