---
title: Ajout d'une nouvelle signature numérique au fichier Excel signé
linktitle: Ajout d'une nouvelle signature numérique au fichier Excel signé
second_title: API de traitement Excel Aspose.Cells .NET
description: Découvrez comment ajouter une nouvelle signature numérique à un fichier Excel signé existant à l'aide d'Aspose.Cells pour .NET. Ce guide complet couvre toutes les conditions préalables, les instructions étape par étape et un exemple de code.
type: docs
weight: 12
url: /fr/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Introduction

Dans le paysage numérique actuel, garantir l'authenticité et l'intégrité des documents est plus crucial que jamais. Les signatures numériques offrent un moyen fiable de vérifier qu'un document n'a pas été modifié et qu'il provient d'une source légitime. Si vous travaillez avec des fichiers Excel dans .NET et que vous devez ajouter une nouvelle signature numérique à un fichier déjà signé, ce guide est fait pour vous ! Nous vous expliquerons le processus d'ajout d'une signature numérique à un fichier Excel signé existant à l'aide d'Aspose.Cells pour .NET.

## Prérequis

Avant de nous lancer dans la mise en œuvre, assurez-vous de disposer des éléments suivants :

1.  Aspose.Cells pour .NET : téléchargez et installez Aspose.Cells à partir du[page de sortie](https://releases.aspose.com/cells/net/).
2. .NET Framework : assurez-vous que .NET Framework est configuré sur votre machine et que vous êtes familiarisé avec les concepts de base de la programmation .NET.
3. Certificat numérique : obtenez un certificat numérique valide au format .pfx. Pour effectuer des tests, vous pouvez créer un certificat auto-signé.
4. Environnement de développement : utilisez un IDE comme Visual Studio pour écrire et exécuter votre code C#.
5. Exemple de fichier Excel : disposez d’un fichier Excel existant qui est déjà signé numériquement, qui sera la cible pour l’ajout d’une nouvelle signature.

Avec ces prérequis en place, passons au code !

## Importer les packages nécessaires

En haut de votre fichier C#, incluez les espaces de noms suivants pour accéder aux classes et méthodes requises :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Étape 1 : Définissez vos répertoires

Spécifiez les répertoires de vos fichiers sources et où enregistrer le fichier de sortie :

```csharp
// Répertoire des sources
string sourceDir = "Your Document Directory"; // Remplacez par votre répertoire actuel
// Répertoire de sortie
string outputDir = "Your Document Directory"; // Remplacez par votre répertoire actuel
```

## Étape 2 : charger le classeur signé existant

Chargez le classeur Excel déjà signé :

```csharp
// Charger le classeur qui est déjà signé numériquement
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Étape 3 : Créer une collection de signatures numériques

Créez une collection pour gérer vos signatures numériques :

```csharp
//Créer la collection de signatures numériques
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Étape 4 : chargez votre certificat

Chargez votre certificat numérique, qui sera utilisé pour créer la nouvelle signature :

```csharp
// Fichier de certificat et son mot de passe
string certFileName = sourceDir + "AsposeDemo.pfx"; // Votre fichier de certificat
string password = "aspose"; // Votre mot de passe de certificat

// Créer un nouveau certificat
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Étape 5 : Créer une nouvelle signature numérique

Créez maintenant une nouvelle signature numérique et ajoutez-la à votre collection :

```csharp
// Créez une nouvelle signature numérique et ajoutez-la à la collection
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Étape 6 : ajouter la collection Signature au classeur

Ajoutez la collection de signatures numériques au classeur :

```csharp
// Ajouter une collection de signatures numériques au classeur
workbook.AddDigitalSignature(dsCollection);
```

## Étape 7 : Enregistrer le classeur

Enregistrez le classeur avec la nouvelle signature numérique incluse :

```csharp
// Enregistrer le classeur
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Étape 8 : Confirmer le succès

Fournir un retour d'information en cas d'exécution réussie :

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Conclusion

Félicitations ! Vous avez ajouté avec succès une nouvelle signature numérique à un fichier Excel déjà signé à l'aide d'Aspose.Cells pour .NET. Ce processus améliore la sécurité de vos documents et garantit leur authenticité et leur intégrité.

## FAQ

### Qu'est-ce qu'une signature numérique ?

Une signature numérique est un schéma mathématique qui vérifie l’authenticité et l’intégrité des messages ou documents numériques, garantissant qu’ils n’ont pas été modifiés et confirmant l’identité du signataire.

### Ai-je besoin d’un certificat spécial pour créer une signature numérique ?

Oui, un certificat numérique émis par une autorité de certification (CA) de confiance est requis pour créer une signature numérique valide.

### Puis-je utiliser un certificat auto-signé pour les tests ?

Absolument ! Vous pouvez utiliser un certificat auto-signé à des fins de développement et de test, mais pour la production, il est conseillé d'utiliser un certificat d'une autorité de certification de confiance.

### Que se passe-t-il si j'essaie d'ajouter une signature à un document non signé ?

Si vous essayez d'ajouter une signature numérique à un document qui n'est pas déjà signé, cela fonctionnera sans problème, mais la signature d'origine ne sera pas présente.

### Où puis-je trouver plus d'informations sur Aspose.Cells ?

 Pour des guides détaillés et des références API, consultez le[Documentation d'Aspose.Cells](https://reference.aspose.com/cells/net/).