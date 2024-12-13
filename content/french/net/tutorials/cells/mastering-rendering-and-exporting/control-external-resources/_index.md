---
title: Contrôler les ressources externes avec Aspose.Cells pour .NET
linktitle: Contrôler les ressources externes avec Aspose.Cells pour .NET
second_title: API de traitement Excel Aspose.Cells .NET
description: Exploitez tout le potentiel de vos conversions Excel en PDF avec Aspose.Cells pour .NET. Dans ce guide complet, découvrez comment gérer les ressources externes, telles que les images, pour garantir que vos PDF reflètent exactement vos exigences de mise en forme.
type: docs
weight: 12
url: /fr/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Introduction

Dans le paysage numérique actuel, la conversion de feuilles de calcul Excel en documents PDF est une tâche courante et essentielle. Que vous prépariez des rapports, des données financières ou des supports de présentation, il est essentiel de vous assurer que vos PDF reflètent le format souhaité. Aspose.Cells pour .NET fournit une bibliothèque puissante qui vous permet de contrôler ce processus de conversion en détail, en particulier lorsque vous traitez des ressources externes telles que des images. Dans ce guide, nous découvrirons comment gérer efficacement les ressources externes pendant le processus de conversion d'Excel en PDF à l'aide d'Aspose.Cells. Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants à disposition :

1. Visual Studio ou tout autre IDE compatible .NET : ce sera votre environnement de développement.
2.  Aspose.Cells pour .NET : si vous ne l'avez pas encore installé, visitez le[Téléchargements Aspose](https://releases.aspose.com/cells/net/) page pour obtenir la dernière version.
3. Connaissances de base de C# : une connaissance de C# sera bénéfique. Si vous avez besoin d'éclaircissements sur certains concepts, n'hésitez pas à les consulter.
4. Exemple de fichier Excel : préparez un fichier Excel, tel que « samplePdfSaveOptions_StreamProvider.xlsx », qui contient les ressources externes que vous souhaitez convertir.
5. Fichier image pour les tests : utilisez un fichier image tel que « newPdfSaveOptions_StreamProvider.png » comme ressource externe pendant la conversion.

## Importer les packages nécessaires

Pour commencer, vous devez importer les espaces de noms requis à partir de la bibliothèque Aspose.Cells. Ajoutez les directives using suivantes en haut de votre fichier C# :

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Ces espaces de noms fournissent les classes et méthodes essentielles pour vos tâches.

## Étape 1 : créer une classe de fournisseur de flux

 Tout d’abord, créez une classe de fournisseur de flux qui implémente le`IStreamProvider` interface. Cette classe vous permettra de contrôler la manière dont les ressources externes sont chargées.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Charger l'image dans un flux mémoire
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream : cette méthode est appelée lorsque le flux est fermé, enregistrant actuellement un message de débogage.
- InitStream : cette méthode lit le fichier image externe sous forme de tableau d'octets, le convertit en flux mémoire et l'affecte au`options.Stream` propriété.

## Étape 2 : Configurer les répertoires source et de sortie

Ensuite, définissez les répertoires de votre fichier Excel et du PDF de sortie.

```csharp
// Répertoire des sources
string sourceDir = "Your Document Directory";
// Répertoire de sortie
string outputDir = "Your Document Directory";
```

 Remplacer`"Your Document Directory"` avec le chemin réel sur votre système où se trouvent vos fichiers.

## Étape 3 : Chargez votre fichier Excel

Maintenant, chargez le fichier Excel à partir duquel vous souhaitez créer le PDF.

```csharp
// Charger le fichier Excel source contenant des images externes
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 Le`Workbook` la classe d'Aspose.Cells représente votre fichier Excel, qui peut inclure diverses ressources externes comme des images.

## Étape 4 : définir les options d’enregistrement du PDF

Avant d’enregistrer le classeur au format PDF, spécifiez les options d’enregistrement souhaitées.

```csharp
// Spécifier les options d'enregistrement PDF - Fournisseur de flux
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Enregistrer chaque feuille sur une nouvelle page
};
```

 Cela crée une instance de`PdfSaveOptions` , vous permettant de personnaliser le format PDF.`OnePagePerSheet` L'option garantit que chaque feuille Excel apparaît sur une page distincte dans le PDF final.

## Étape 5 : Attribuez votre fournisseur de streaming

 Connectez votre`Workbook` exemple avec le`MyStreamProvider` classe que vous avez créée plus tôt.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Cette ligne garantit que chaque fois que des ressources externes sont rencontrées lors de la conversion, votre fournisseur personnalisé les gérera en conséquence.

## Étape 6 : Enregistrer le classeur au format PDF

Maintenant, enregistrez votre classeur Excel au format PDF.

```csharp
// Enregistrer le classeur au format PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 En appelant le`Save` en utilisant la méthode sur l'objet classeur et en passant le répertoire de sortie avec les options PDF, vous convertissez le fichier Excel en un PDF bien formaté.

## Étape 7 : Confirmer l’exécution réussie

Enfin, il est recommandé de confirmer que le processus s'est terminé avec succès.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Ce message vous informera de l'état de votre opération et vous fournira des commentaires utiles.

## Conclusion

Vous maîtrisez désormais le processus de contrôle des ressources externes lors des conversions Excel en PDF à l'aide d'Aspose.Cells ! En suivant ces étapes, vous pouvez vous assurer que vos documents incluent avec précision des images et d'autres éléments externes, ce qui permet d'obtenir un produit final soigné à chaque fois.

## FAQ

### Qu'est-ce qu'Aspose.Cells ?
Aspose.Cells est une bibliothèque puissante pour les développeurs .NET qui permet la création, la manipulation, la conversion et le rendu de fichiers Excel dans divers formats.

### Comment télécharger Aspose.Cells ?
 Vous pouvez télécharger la dernière version à partir du[Lien de téléchargement](https://releases.aspose.com/cells/net/).

### Puis-je essayer Aspose.Cells gratuitement ?
 Oui ! Vous pouvez accéder à un essai gratuit en visitant le[Page d'essai gratuite](https://releases.aspose.com/).

### Où puis-je trouver du support pour Aspose.Cells ?
 Pour toute question relative à l'assistance, visitez le[Forum d'assistance Aspose](https://forum.aspose.com/c/cells/9).

### Comment puis-je obtenir une licence temporaire pour Aspose.Cells ?
 Vous pouvez demander une licence temporaire[ici](https://purchase.aspose.com/temporary-license/).
