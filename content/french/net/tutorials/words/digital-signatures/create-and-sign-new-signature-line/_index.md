---
title: Créer et signer une nouvelle ligne de signature
linktitle: Créer et signer une nouvelle ligne de signature
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment ajouter facilement une signature numérique à vos documents Word à l'aide d'Aspose.Words pour .NET. Ce didacticiel complet couvre toutes les étapes, de la configuration de votre environnement à l'insertion d'une ligne de signature, en passant par l'enregistrement et la vérification de vos documents signés.
type: docs
weight: 10
url: /fr/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Introduction

Vous souhaitez ajouter une signature numérique à un document Word ? Avec Aspose.Words pour .NET, c'est plus facile que vous ne le pensez ! Ce tutoriel vous guidera à travers les étapes de configuration de votre environnement, d'ajout d'une ligne de signature et de signature numérique de votre document. C'est parti !

## Prérequis

Avant de plonger dans le code, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET -[Téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement .NET - Visual Studio est idéal pour cette tâche.
3. Document à signer - Vous pouvez créer un nouveau document Word ou utiliser un document existant.
4.  Fichier de certificat - A`.pfx` le fichier est nécessaire pour les signatures numériques.
5. Image de la ligne de signature (facultatif) - Vous pouvez inclure un fichier image pour la signature.

## Importer les espaces de noms requis

Pour utiliser les fonctionnalités d'Aspose.Words, vous devez importer les espaces de noms suivants :

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Étape 1 : Configuration du répertoire de documents

Commencez par définir le chemin d'accès à votre répertoire de documents. C'est là que vous enregistrerez et récupérerez vos documents.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Spécifiez le chemin du répertoire de votre document
```

## Étape 2 : Créer un nouveau document

Ensuite, créons un nouveau document Word. Ce document servira de canevas pour votre ligne de signature.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 3 : Insertion de la ligne de signature

 Maintenant, utilisez le`DocumentBuilder` classe pour insérer une ligne de signature dans votre document :

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Étape 4 : enregistrement du document

Une fois la ligne de signature insérée, enregistrez le document. Il s'agit d'une étape cruciale avant de signer.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Étape 5 : Configuration des options de signature

Configurez les options du processus de signature. Cela inclut la spécification de l'ID de la ligne de signature et de l'image facultative à afficher avec la signature.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Chemin vers votre image
};
```

## Étape 6 : chargement du certificat

Chargez le fichier de certificat requis pour signer le document :

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Ajuster le nom du fichier et le mot de passe
```

## Étape 7 : Signature du document

 Enfin, signez le document en utilisant le`DigitalSignatureUtil` classe. Enregistrez le document signé sous un nouveau nom pour référence ultérieure.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Conclusion

Félicitations ! Vous avez créé avec succès un document Word, ajouté une ligne de signature et l'avez signé numériquement à l'aide d'Aspose.Words pour .NET. Cet outil puissant simplifie l'automatisation des documents, garantissant que vos contrats et documents officiels sont signés et authentifiés en toute sécurité.

## FAQ

### Puis-je utiliser d’autres formats d’image pour la ligne de signature ?

Oui, vous pouvez utiliser différents formats d’image, notamment PNG, JPG et BMP.

###  Est-il nécessaire d'utiliser un`.pfx` file for the certificate?

 Oui, un`.pfx` Le fichier est un format standard pour stocker des certificats et des clés privées pour les signatures numériques.

### Puis-je ajouter plusieurs lignes de signature dans un seul document ?

Absolument ! Vous pouvez insérer plusieurs lignes de signature en répétant l'étape d'insertion selon vos besoins.

### Que faire si je n’ai pas de certificat numérique ?

Vous devrez obtenir un certificat numérique auprès d'une autorité de certification de confiance ou en générer un à l'aide d'outils tels qu'OpenSSL.

### Comment vérifier la signature numérique dans le document ?

Vous pouvez vérifier la signature numérique en ouvrant le document signé dans Word et en vérifiant les détails de la signature pour confirmer son authenticité et son intégrité.