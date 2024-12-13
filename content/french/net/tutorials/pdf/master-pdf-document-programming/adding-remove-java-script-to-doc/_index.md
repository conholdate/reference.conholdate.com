---
title: Ajout et suppression de Javascript au document PDF
linktitle: Ajout et suppression de Javascript au document PDF
second_title: Référence de l'API Aspose.PDF pour .NET
description: Ce guide complet vous montre comment ajouter des comportements personnalisés, effectuer des calculs ou des validations de manière dynamique et intégrer d'autres applications logicielles.
type: docs
weight: 30
url: /fr/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## Introduction

Dans ce guide complet, nous allons nous plonger dans le monde d'Aspose.PDF pour .NET et exploiter tout son potentiel pour ajouter des fonctionnalités JavaScript personnalisées à vos documents PDF. Cette fonctionnalité puissante vous permet d'intégrer des éléments dynamiques, d'améliorer l'expérience utilisateur et de rationaliser les flux de travail.

## Prérequis

Pour suivre, vous aurez besoin de :

1. Aspose.PDF pour .NET installé dans votre projet (téléchargement depuis[Page de téléchargement d'Aspose.PDF pour .NET](https://releases.aspose.com/pdf/net/))
2. Une licence valide pour utiliser la bibliothèque
3. AC# IDE ou éditeur de texte

## Paquets d'importation

Pour commencer, importez les espaces de noms nécessaires dans votre projet :

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## Étape 1 : Initialiser un nouveau document PDF

Créez un nouveau document PDF et ajoutez-le à votre toile :

```csharp
Document doc = new Document();
doc.Pages.Add();
```

C'est ici que vous commencerez à créer votre PDF riche en JavaScript.

## Étape 2 : ajouter du JavaScript au PDF

 Insérez des fonctions JavaScript dans votre document à l'aide de la`doc.JavaScript` collection. Voici un exemple :

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## Étape 3 : Enregistrer le PDF avec JavaScript

Enregistrez votre document mis à jour sur le disque :

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

Vous pouvez désormais accéder et modifier le code JavaScript dans un PDF existant.

## Étape 4 : charger et afficher JavaScript dans le PDF existant

 Chargez un fichier PDF contenant du JavaScript et accédez à ses clés à l'aide de la`Keys` propriété:

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## Étape 5 : Afficher les fonctions JavaScript

Parcourez les clés JavaScript et imprimez leur code correspondant sur la console :

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

Cela montre comment vous pouvez vérifier quelles fonctions JavaScript sont actuellement présentes.

## Étape 6 : Supprimer JavaScript du PDF

Recherchez la fonction JavaScript souhaitée en utilisant son nom et supprimez-la :

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

Vérifiez que la fonction a été supprimée avec succès en réimprimant les fonctions restantes.

## Conclusion

Dans ce guide complet, vous avez découvert comment exploiter la puissance de la fonctionnalité JavaScript personnalisable d'Aspose.PDF pour .NET. Grâce à cette fonctionnalité, vous pouvez créer des PDF dynamiques, améliorer l'expérience utilisateur et rationaliser les flux de travail. En maîtrisant ces étapes et en explorant plus en détail les capacités de la bibliothèque, vous serez sur la bonne voie pour débloquer de nouvelles possibilités dans vos applications.

## FAQ

### Puis-je ajouter plusieurs fonctions JavaScript à un seul PDF ?
 Oui ! Vous pouvez ajouter autant de fonctions JavaScript que nécessaire en utilisant le`doc.JavaScript` collection.

### Que se passe-t-il si j’essaie de supprimer une fonction JavaScript inexistante ?
 Si la fonction n'existe pas, la`Remove`La méthode ne génèrera pas d'erreur, mais ne supprimera rien non plus. Pour gérer les fonctions inexistantes, vous pouvez ajouter une gestion des erreurs supplémentaire ou modifier le code pour les ignorer.

### Est-il possible d'exécuter JavaScript dès l'ouverture du PDF ?
Oui ! Vous pouvez configurer JavaScript pour qu'il s'exécute sur des déclencheurs spécifiques, comme l'ouverture du document ou le clic sur un bouton.

### Puis-je modifier le JavaScript après l'avoir ajouté au PDF ?
Oui, vous pouvez charger un PDF existant, accéder à son JavaScript, modifier le code et enregistrer à nouveau le document.

### La suppression de JavaScript affecte-t-elle le reste du contenu PDF ?
Non, la suppression de JavaScript n'affecte que le script. Le contenu du PDF reste inchangé.