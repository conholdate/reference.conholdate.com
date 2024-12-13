---
title: Convertissez DOCX en MHTML et envoyez un e-mail à l'aide d'Aspose.Words pour .NET
linktitle: Convertissez DOCX en MHTML et envoyez un e-mail à l'aide d'Aspose.Words pour .NET
second_title: API de traitement de documents Aspose.Words
description: Ce guide complet fournit un didacticiel étape par étape sur la conversion de documents DOCX au format MHTML et leur envoi par courrier électronique à l'aide des bibliothèques Aspose.Words et Aspose.Email dans .NET.
type: docs
weight: 10
url: /fr/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Introduction

Dans le paysage numérique actuel, la conversion de documents entre différents formats et leur envoi par courrier électronique sont des tâches courantes. Ce guide vous guidera dans la conversion d'un fichier DOCX au format MHTML et son envoi par courrier électronique à l'aide des puissantes bibliothèques Aspose.Words et Aspose.Email pour .NET. Nous détaillerons chaque étape clairement, afin que vous puissiez suivre facilement. Commençons !

## Prérequis

Avant de vous lancer dans le processus, assurez-vous d'avoir configuré les éléments suivants :

1.  Aspose.Words pour .NET : téléchargez et installez la bibliothèque à partir du[Page de sortie d'Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email pour .NET : téléchargez et installez cette bibliothèque à partir du[Page de sortie d'Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur.
4. Serveur SMTP : Vous aurez besoin d'accéder à un serveur SMTP pour envoyer des e-mails.

## Importer les espaces de noms nécessaires

Pour utiliser Aspose.Words et Aspose.Email dans votre projet, vous devez importer les espaces de noms requis. Ajoutez les directives using suivantes en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Étape 1 : Charger le document DOCX

 Commencez par charger le document DOCX que vous souhaitez convertir. Utilisez le`Document` classe d'Aspose.Words pour y parvenir.

```csharp
// Spécifiez le chemin d’accès à votre répertoire de documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Étape 2 : enregistrer le document au format MHTML

 Ensuite, convertissez le document chargé au format MHTML. Cela se fait à l'aide de l'`Save` méthode de la`Document`classe.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Réinitialiser la position du flux au début pour la lecture.
    stream.Position = 0;
}
```

## Étape 3 : Créer un message électronique

Créez maintenant un message électronique à partir du flux MHTML à l'aide d'Aspose.Email. Vous utiliserez le`MailMessage` classe à cet effet.

```csharp
// Chargez le flux MHTML dans un message électronique MIME Aspose.Email.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Étape 4 : Envoyer l'e-mail

 Enfin, envoyez l'e-mail à l'aide d'un client SMTP. Configurez le client SMTP avec les détails de votre serveur et utilisez le`Send` méthode pour envoyer le message.

```csharp
// Configurez et envoyez le message en utilisant Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Conclusion

Félicitations ! Vous avez converti avec succès un document DOCX en MHTML et l'avez envoyé par courrier électronique à l'aide d'Aspose.Words et d'Aspose.Email pour .NET. Ce processus implique le chargement du document, sa conversion en MHTML, la création d'un message électronique et son envoi via un client SMTP. Grâce à ces étapes, vous pouvez automatiser la conversion et l'envoi par courrier électronique de documents de manière transparente dans vos applications.

## FAQ

### Puis-je utiliser cette méthode pour convertir d’autres formats de documents ?
Absolument ! Aspose.Words prend en charge une large gamme de formats, vous permettant de convertir DOC, DOCX, RTF et plus encore en MHTML.

### Comment puis-je ajouter des pièces jointes à l'e-mail ?
 Vous pouvez facilement ajouter des pièces jointes à l'aide du`Attachments` propriété de la`MailMessage`classe.

### Aspose.Words est-il compatible avec .NET Core ?
Oui, Aspose.Words est compatible avec .NET Core, ce qui le rend adapté à une utilisation dans les applications .NET Core.

### Ai-je besoin d'une licence pour Aspose.Words et Aspose.Email ?
 Oui, les deux bibliothèques nécessitent une licence. Vous pouvez obtenir une licence temporaire à des fins d'évaluation auprès de[Page d'achat Aspose](https://purchase.conholdate.com/temporary-license/).

### Où puis-je trouver plus de documentation ?
 Pour une documentation détaillée, consultez Aspose.Words[ici](https://reference.aspose.com/words/net/) et Aspose.Email[ici](https://reference.aspose.com/email/net/).