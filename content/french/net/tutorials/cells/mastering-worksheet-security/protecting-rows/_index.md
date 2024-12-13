---
title: Protection des lignes dans une feuille de calcul à l'aide d'Aspose.Cells
linktitle: Protection des lignes dans une feuille de calcul à l'aide d'Aspose.Cells
second_title: API de traitement Excel Aspose.Cells .NET
description: Découvrez comment sécuriser les informations sensibles dans vos feuilles de calcul Excel en protégeant des lignes spécifiques à l'aide d'Aspose.Cells pour .NET. Ce didacticiel complet couvre tout, de la configuration de votre environnement.
type: docs
weight: 18
url: /fr/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Introduction

Travailler avec des fichiers Excel par programmation nécessite souvent non seulement la manipulation des données, mais également leur protection. La protection de lignes spécifiques dans une feuille de calcul peut être cruciale pour protéger les informations sensibles ou empêcher les modifications accidentelles. Dans ce didacticiel, nous verrons comment protéger les lignes d'une feuille de calcul Excel à l'aide d'Aspose.Cells pour .NET. Nous vous guiderons à travers les étapes nécessaires, de la configuration de votre environnement à la mise en œuvre simple des fonctionnalités de protection des lignes.

## Prérequis
Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Cells pour .NET : téléchargez-le et installez-le à partir du[Page de téléchargement des cellules Aspose](https://releases.aspose.com/cells/net/).
2. Visual Studio ou tout autre IDE .NET : vous avez besoin d'un environnement de développement. Visual Studio est recommandé, mais tout IDE compatible .NET fera l'affaire.
3. Connaissances de base en C# : la familiarité avec la programmation C# vous aidera à suivre et à modifier l'exemple de code selon vos besoins.
4.  Documentation de l'API Aspose.Cells : consultez la[Documentation d'Aspose.Cells pour .NET](https://reference.aspose.com/cells/net/) pour un aperçu de la structure et des méthodes de la classe.

Une fois les prérequis prêts, nous pouvons procéder à la mise en œuvre.

## Importer les packages nécessaires
Commencez par importer les packages requis dans votre projet C#. Ces bibliothèques sont essentielles pour interagir avec les fichiers Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## Étape 1 : Créer un nouveau classeur et une nouvelle feuille de calcul
Avant d’appliquer des paramètres de protection, créez un nouveau classeur et sélectionnez la feuille de calcul avec laquelle vous souhaitez travailler.

```csharp
// Définissez le chemin vers le répertoire des documents.
string dataDir = "Your Document Directory";
// Créez le répertoire s'il n'existe pas.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Créez un nouveau classeur et sélectionnez la première feuille de calcul.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Étape 2 : définir les objets Style et StyleFlag
Définissez les objets de style et d'indicateur de style, qui vous permettront de modifier les propriétés des cellules, comme les verrouiller ou les déverrouiller.

```csharp
// Définissez les objets de style et d'indicateur de style.
Style style;
StyleFlag flag;
```

## Étape 3 : déverrouiller toutes les colonnes de la feuille de calcul
Par défaut, toutes les cellules d'une feuille de calcul Excel sont verrouillées. Pour protéger uniquement des lignes spécifiques, déverrouillez d'abord toutes les colonnes.

```csharp
// Parcourez toutes les colonnes et déverrouillez-les.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Étape 4 : Verrouiller des lignes spécifiques
Maintenant, verrouillez les lignes que vous souhaitez protéger. Dans cet exemple, nous allons verrouiller la première ligne.

```csharp
// Verrouillez la première rangée.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Vous pouvez répéter cette étape pour toutes les lignes supplémentaires que vous souhaitez verrouiller.

## Étape 5 : Protégez la feuille
Une fois les lignes nécessaires verrouillées, il est temps de protéger la feuille de calcul. Cela empêchera toute modification des lignes verrouillées à moins que la protection ne soit supprimée.

```csharp
// Protégez la feuille.
sheet.Protect(ProtectionType.All);
```

## Étape 6 : Enregistrer le classeur
Enfin, enregistrez le classeur avec les modifications appliquées. Vous pouvez choisir parmi différents formats, tels qu'Excel 97-2003 ou des versions plus récentes.

```csharp
// Enregistrez le fichier Excel.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Conclusion
Félicitations ! Vous avez appris avec succès à protéger les lignes d'une feuille de calcul Excel à l'aide d'Aspose.Cells pour .NET. En suivant ces étapes, vous pouvez déverrouiller ou verrouiller des lignes ou des colonnes selon vos besoins et appliquer une protection pour maintenir l'intégrité de vos données.

## FAQ
### Comment puis-je protéger plusieurs lignes à la fois ?
Vous pouvez parcourir plusieurs indices de ligne et appliquer le style de verrouillage à chacun d'eux individuellement.

### Puis-je définir un mot de passe pour la protection des feuilles ?
 Oui, vous pouvez transmettre un mot de passe au`sheet.Protect()` méthode pour renforcer la protection par mot de passe.

### Puis-je déverrouiller des cellules spécifiques au lieu de colonnes entières ?
Oui, vous pouvez déverrouiller des cellules individuelles en modifiant leurs propriétés de style au lieu de déverrouiller des colonnes entières.

### Que se passe-t-il si j’essaie de modifier une ligne protégée ?
Lorsqu'une ligne est protégée, Excel empêche toute modification des cellules verrouillées, sauf si la feuille n'est pas protégée.

### Puis-je protéger des plages spécifiques dans une ligne ?
 Oui ! Vous pouvez verrouiller des plages individuelles dans une rangée en définissant le`IsLocked` propriété pour des cellules spécifiques dans cette plage.