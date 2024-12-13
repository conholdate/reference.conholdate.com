---
title: Gérer la visibilité des signets dans les documents Word
linktitle: Gérer la visibilité des signets dans les documents Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment contrôler de manière experte la visibilité du contenu des documents Word à l'aide d'Aspose.Words pour .NET. Ce guide étape par étape.
type: docs
weight: 10
url: /fr/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Introduction

Êtes-vous prêt à améliorer vos compétences en manipulation de documents avec Aspose.Words pour .NET ? Que vous soyez un développeur chevronné automatisant des tâches documentaires ou un individu curieux explorant le contrôle programmatique des fichiers Word, ce guide est fait pour vous. Aujourd'hui, nous allons découvrir comment afficher et masquer du contenu en fonction des signets dans un document Word. Commençons !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1. Visual Studio : toute version compatible avec .NET.
2. Aspose.Words pour .NET : Téléchargez-le[ici](https://releases.aspose.com/words/net/).
3. Connaissances de base en C# : une connaissance de l'écriture de programmes C# simples suffira.
4. Un exemple de document Word : préparez un document Word (par exemple, « Bookmarks.docx ») contenant des signets pour ce didacticiel.

### Créer un nouveau projet

1. Ouvrez Visual Studio et créez un nouveau projet d'application console (.NET Core). Nommez-le quelque chose comme « BookmarkVisibilityManager ».

### Installer Aspose.Words pour .NET

Ajoutez Aspose.Words à votre projet via le gestionnaire de packages NuGet :

1. Accédez à Outils > Gestionnaire de packages NuGet > Gérer les packages NuGet pour la solution.
2. Recherchez « Aspose.Words ».
3. Installer le paquet.

Une fois votre projet configuré, procédons au chargement du document.

## Importation d'espaces de noms

Commencez par importer les espaces de noms essentiels. Ceux-ci fournissent les classes et les méthodes nécessaires à la manipulation de documents Word avec Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Étape 1 : Chargement du document

Pour manipuler le document Word, nous devons d'abord le charger. Voici comment procéder :

```csharp
// Définissez le chemin d'accès à votre répertoire de documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Cet extrait définit le chemin d'accès à votre répertoire de documents et charge le document dans un`Document` objet.

## Étape 2 : Afficher/masquer le contenu ajouté aux favoris

 Créons maintenant une méthode pour basculer la visibilité du contenu en fonction des signets. Nous appellerons cette méthode`ShowHideBookmarkedContent`.

Voici l'implémentation de la méthode :

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Récupération des signets :`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` récupère le signet spécifié.
- Traversée de nœuds : nous parcourons les nœuds dans le signet.
-  Basculement de visibilité : pour chaque`Run` nœud (représentant un segment de texte), nous définissons son`Hidden` propriété basée sur la`isHidden` paramètre.

## Étape 3 : Application de la méthode

Maintenant que notre méthode est prête, utilisons-la pour afficher ou masquer le contenu d'un signet spécifique :

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Masque le contenu dans « MyBookmark1 »
```

Cette ligne masquera le contenu associé au signet nommé « MyBookmark1 ».

## Étape 4 : enregistrement du document

Une fois vos modifications effectuées, n'oubliez pas d'enregistrer le document modifié :

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Cela enregistre le document avec les paramètres de visibilité mis à jour.

## Conclusion

Félicitations ! Vous avez appris avec succès à afficher et à masquer le contenu marqué d'un signet dans un document Word à l'aide d'Aspose.Words pour .NET. Cette puissante bibliothèque simplifie la manipulation des documents, ce qui la rend idéale pour automatiser les rapports, créer des modèles ou expérimenter avec des fichiers Word. Bon codage !

## FAQ

### Puis-je activer plusieurs signets à la fois ?
 Oui, appelez simplement le`ShowHideBookmarkedContent` méthode pour chaque signet que vous souhaitez activer/désactiver.

### Le masquage du contenu affecte-t-il la structure du document ?
Non, masquer du contenu affecte uniquement sa visibilité ; le contenu reste intact dans le document.

### Puis-je utiliser cette méthode pour d’autres types de contenu ?
Cette méthode est spécialement conçue pour les exécutions de texte. Pour les autres types de contenu, vous devrez adapter la logique de parcours des nœuds en conséquence.

### Aspose.Words pour .NET est-il gratuit ?
 Aspose.Words propose un essai gratuit[ici](https://releases.aspose.com/) , mais une licence complète est requise pour une utilisation en production. Vous pouvez l'acheter[ici](https://purchase.aspose.com/buy).

### Comment puis-je obtenir de l'aide si je rencontre des problèmes ?
 Pour obtenir de l'aide, visitez le forum de la communauté Aspose[ici](https://forum.aspose.com/c/words/8).