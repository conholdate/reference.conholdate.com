---
title: Ajouter des signatures de texte aux documents à l'aide de GroupDocs.Signature
linktitle: Ajouter des signatures de texte aux documents
second_title: API .NET de GroupDocs.Signature
description: Découvrez comment signer des documents avec du texte à l'aide de GroupDocs.Signature pour .NET. Guide étape par étape pour ajouter des signatures de texte par programmation.
type: docs
weight: 17
url: /fr/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Introduction

Dans le paysage numérique actuel, la signature électronique de documents est devenue essentielle pour rationaliser les flux de travail et économiser des ressources. GroupDocs.Signature pour .NET fournit une solution puissante pour ajouter par programmation des signatures de texte à divers formats de documents. Ce didacticiel vous guidera à travers les étapes à suivre pour signer un document avec du texte à l'aide de GroupDocs.Signature pour .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1. GroupDocs.Signature pour .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.groupdocs.com/signature/net/).
2. Environnement de développement : configurez votre environnement de développement .NET.
3. Document : Préparez le document que vous souhaitez signer (par exemple, PDF, Word).

## Importer les espaces de noms nécessaires

Commencez par importer les espaces de noms requis dans votre projet .NET :

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Étape 1 : Charger le document

Commencez par charger le document que vous souhaitez signer :

```csharp
string filePath = "sample.pdf"; // Chemin vers votre document
string fileName = Path.GetFileName(filePath);
```

## Étape 2 : définir le chemin du fichier de sortie

Ensuite, définissez le chemin du fichier de sortie où le document signé sera enregistré :

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Étape 3 : Créer des options de signature

Configurez les options de votre signature textuelle, notamment le contenu, la position, la taille, la couleur et le style de police :

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // Position X
    Top = 200, // Position Y
    Width = 100, // Largeur de la signature
    Height = 30, // Hauteur de la signature
    ForeColor = Color.Red, // Couleur du texte
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Paramètres de police
};
```

## Étape 4 : Signer le document

Enfin, utilisez GroupDocs.Signature pour appliquer la signature du texte et enregistrer le document signé :

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Signer le document
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Conclusion

Dans ce didacticiel, nous avons montré comment ajouter par programmation une signature de texte à un document à l'aide de GroupDocs.Signature pour .NET. En suivant ces étapes, vous pouvez améliorer efficacement la sécurité et l'authenticité de vos documents.

## FAQ

### Puis-je personnaliser l’apparence de la signature textuelle ?
Oui, vous pouvez personnaliser divers attributs tels que la couleur, la police, la taille et la position de la signature de texte en fonction de vos besoins.

### GroupDocs.Signature est-il compatible avec plusieurs formats de documents ?
Absolument ! GroupDocs.Signature prend en charge une large gamme de formats, notamment PDF, Word, Excel, PowerPoint, etc.

### Puis-je ajouter plusieurs signatures de texte à un seul document ?
Oui, vous pouvez ajouter plusieurs signatures de texte, chacune avec ses propres options de personnalisation.

### GroupDocs.Signature garantit-il l’intégrité du document après la signature ?
Oui, la bibliothèque utilise des algorithmes cryptographiques robustes pour garantir l’intégrité des documents et empêcher toute falsification après la signature.

### Existe-t-il une version d'essai disponible pour tester avant l'achat ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/) pour explorer les fonctionnalités avant de faire un achat.