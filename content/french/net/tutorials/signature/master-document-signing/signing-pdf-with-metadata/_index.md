---
title: Guide de signature de fichiers PDF avec métadonnées à l'aide de GroupDocs.Signature
linktitle: Guide pour la signature de PDF avec des métadonnées
second_title: API .NET de GroupDocs.Signature
description: Découvrez comment renforcer la sécurité et la traçabilité de vos documents PDF en les signant avec des métadonnées à l'aide de GroupDocs.Signature pour .NET. Ce didacticiel complet fournit une approche claire.
type: docs
weight: 11
url: /fr/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## Introduction

Dans ce didacticiel, nous allons apprendre à signer un document PDF et à ajouter des métadonnées à l'aide de GroupDocs.Signature pour .NET. L'ajout de métadonnées améliore le document en fournissant des informations essentielles telles que la paternité, la date de création, l'ID du document, etc.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  GroupDocs.Signature pour .NET : Téléchargez-le depuis[ici](https://releases.groupdocs.com/signature/net/).
2. Un document PDF : Préparez un exemple de fichier PDF pour la signature.
3. Connaissances de base de la programmation C# : une familiarité avec la syntaxe C# est nécessaire pour comprendre les exemples de code.

## Importer des espaces de noms

Commencez par importer les espaces de noms requis pour accéder aux classes et méthodes nécessaires :

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Étape 1 : Charger le document PDF

Spécifiez le chemin du document PDF que vous souhaitez signer :

```csharp
string filePath = "sample.pdf";
```

## Étape 2 : Spécifier le chemin du fichier de sortie

Définissez où le PDF signé avec les métadonnées sera enregistré :

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## Étape 3 : Créer une instance de signature

 Initialiser un`Signature` instance avec le chemin vers le document PDF :

```csharp
using (Signature signature = new Signature(filePath))
{
    // Le code relatif à la signature sera placé ici
}
```

## Étape 4 : Définir les options de métadonnées

 Créer`MetadataSignOptions` et ajoutez les champs de métadonnées avec leurs valeurs :

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // Valeur de chaîne
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // Valeur DateHeure
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // Valeur entière
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // Valeur double
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // Valeur décimale
    .Add(new PdfMetadataSignature("Total", 123.456F));              // Valeur flottante
```

## Étape 5 : Signer le document

Signez le document PDF avec les options de métadonnées spécifiées et enregistrez le document signé :

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Conclusion

Dans ce tutoriel, nous avons expliqué comment signer un document PDF avec des métadonnées à l'aide de GroupDocs.Signature pour .NET. En suivant ces étapes, vous pouvez facilement enrichir vos fichiers PDF avec des métadonnées précieuses, améliorant ainsi leur traçabilité et leur utilité.

## FAQ

### Puis-je ajouter des champs de métadonnées personnalisés à mes documents PDF ?

Oui, vous pouvez ajouter des champs de métadonnées personnalisés en spécifiant le nom du champ et sa valeur correspondante à l’aide de GroupDocs.Signature pour .NET.

### GroupDocs.Signature pour .NET est-il compatible avec toutes les versions du .NET Framework ?

GroupDocs.Signature pour .NET est compatible avec différentes versions du .NET Framework, garantissant flexibilité et facilité d'intégration.

### GroupDocs.Signature prend-il en charge la signature d’autres formats de documents en dehors du PDF ?

Oui, GroupDocs.Signature prend en charge une large gamme de formats de documents, notamment Word, Excel, PowerPoint, etc.

### Puis-je signer plusieurs documents en masse à l’aide de GroupDocs.Signature pour .NET ?

Absolument ! Vous pouvez signer plusieurs documents en masse en parcourant une liste de fichiers et en appliquant le processus de signature par programmation.

### Le support technique est-il disponible pour les utilisateurs de GroupDocs.Signature ?

Oui, GroupDocs fournit un support technique dédié via ses forums. Vous pouvez accéder au forum d'assistance[ici](https://forum.groupdocs.com/c/signature/13).