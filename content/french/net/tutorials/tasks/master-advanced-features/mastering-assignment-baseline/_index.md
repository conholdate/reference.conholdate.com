---
title: Maîtriser les bases de référence des tâches avec Aspose.Tasks pour .NET
linktitle: Gestion de la base de référence des tâches dans Aspose.Tasks
second_title: API .NET Aspose.Tasks
description: Découvrez comment gérer efficacement les lignes de base des affectations à l'aide d'Aspose.Tasks pour .NET. Ce guide étape par étape couvre le chargement de projets, la définition de lignes de base, la récupération de données, la comparaison de lignes de base et bien plus encore pour optimiser les flux de travail de gestion de projet.
type: docs
weight: 14
url: /fr/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## Introduction

Une gestion de projet efficace repose sur un suivi et une gestion précis des bases de référence des affectations. Avec Aspose.Tasks pour .NET, vous bénéficiez d'une boîte à outils robuste pour rationaliser la gestion des bases de référence des affectations afin de mieux comprendre le projet. Dans cet article, nous vous expliquons le processus de gestion des bases de référence des affectations, en veillant à ce que vos projets restent sur la bonne voie.

## Prérequis

Avant de vous lancer dans la mise en œuvre, assurez-vous de disposer des éléments suivants :

- Expertise en programmation : Connaissance de base de C#.
- Environnement de développement : Visual Studio installé et configuré.
-  Bibliothèque Aspose.Tasks pour .NET : téléchargez-la à partir de[Versions d'Aspose.Tasks](https://releases.aspose.com/tasks/net/).
- Fichier Projet : Accès à un fichier projet au format MPP.

## Importer les espaces de noms requis

Pour utiliser la fonctionnalité d'Aspose.Tasks, incluez les espaces de noms suivants dans votre fichier de projet :

```csharp
using Aspose.Tasks;
using System;
```

## Étape 1 : charger un projet et définir des lignes de base

Le chargement d'un projet et la définition d'une ligne de base sont essentiels à la gestion des lignes de base des affectations. Le code suivant montre comment charger un projet et établir sa ligne de base.

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// Définir la base de référence du projet
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## Étape 2 : Récupérer les données de base de l'affectation

Vous pouvez extraire des informations de base détaillées pour chaque affectation de ressources. Voici comment procéder :

```csharp
foreach (var assignment in project.ResourceAssignments)
{
    foreach (var baseline in assignment.Baselines)
    {
        Console.WriteLine("Baseline Start: " + baseline.Start);
        Console.WriteLine("Baseline Finish: " + baseline.Finish);
        Console.WriteLine("Baseline Cost: " + baseline.Cost);
        Console.WriteLine("Baseline Work: " + baseline.Work);
    }
}
```

## Étape 3 : comparer les valeurs de référence entre les missions

Aspose.Tasks vous permet de comparer par programmation les lignes de base pour évaluer les différences entre les affectations de ressources.

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## Étape 4 : modifier les détails de la ligne de base par programmation

Vous pouvez modifier par programmation les données de base pour répondre aux besoins évolutifs du projet :

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // Ajustement du coût de base
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // Ajout d'heures de travail

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## Conclusion

La gestion efficace des bases de référence des tâches est essentielle pour maintenir le contrôle sur les calendriers et les budgets des projets. Aspose.Tasks pour .NET vous fournit les outils nécessaires pour gérer les bases de référence avec précision, permettant ainsi une prise de décision basée sur les données.

## FAQ

### Aspose.Tasks peut-il gérer plusieurs lignes de base pour un seul projet ?  
Oui, Aspose.Tasks prend en charge plusieurs lignes de base, offrant une flexibilité dans le suivi de différentes versions de projet.

### Aspose.Tasks est-il compatible avec les fichiers de projet non MPP ?  
Absolument. Aspose.Tasks prend en charge des formats tels que XML, MPX, etc.

### Puis-je automatiser les mises à jour de base ?  
Oui, l'API permet des modifications de base dynamiques et automatisées par programmation.

### Aspose.Tasks fournit-il des données de base échelonnées dans le temps ?  
Oui, des données de base détaillées et échelonnées dans le temps peuvent être récupérées et analysées.

### Où puis-je accéder au support et à la documentation ?  
 Visite[Documentation sur Aspose.Tasks](https://reference.aspose.com/words/net/) ou rejoignez le[Forum d'assistance Aspose](https://forum.aspose.com/c/words/8) pour obtenir de l'aide. 