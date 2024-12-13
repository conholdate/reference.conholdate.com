---
title: Crie uma nova linha de assinatura digital e defina o ID do provedor
linktitle: Crie uma nova linha de assinatura digital e defina o ID do provedor
second_title: API de processamento de documentos Aspose.Words
description: Descubra como adicionar linhas de assinatura programaticamente aos seus documentos do Word usando o Aspose.Words para .NET. Este guia abrangente abrange tudo, desde a configuração do seu ambiente de desenvolvimento até a inserção de linhas de assinatura e assinatura segura de documentos.
type: docs
weight: 10
url: /pt/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Introdução

Olá, entusiastas da tecnologia! Vocês já quiseram automatizar a inclusão de linhas de assinatura em seus documentos do Word? Hoje, vamos mergulhar em como fazer isso usando o Aspose.Words para .NET. Este guia passo a passo vai orientá-los na criação de uma linha de assinatura e na configuração do ID do provedor, tornando suas tarefas de processamento de documentos mais eficientes e simplificadas.

## Pré-requisitos

Antes de começarmos, vamos garantir que você tenha tudo configurado:

1.  Aspose.Words para .NET: Se você ainda não o instalou, baixe-o[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: use o Visual Studio ou qualquer configuração de desenvolvimento em C#.
3. .NET Framework: certifique-se de ter o .NET Framework instalado na sua máquina.
4. Certificado PFX: você precisará de um certificado PFX para assinar documentos, que pode ser obtido de uma autoridade de certificação confiável.

## Importando namespaces necessários

Para começar, importe os namespaces necessários para seu projeto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Agora, vamos nos aprofundar nos detalhes da criação de uma nova linha de assinatura e definir o ID do provedor.

## Etapa 1: Crie um novo documento

Primeiro, precisamos criar um novo documento do Word, que servirá como tela para nossa linha de assinatura:

```csharp
// Especifique o caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aqui, inicializamos um novo`Document` e um`DocumentBuilder`, o que nos permite adicionar elementos facilmente.

## Etapa 2: Definir opções de linha de assinatura

Em seguida, definiremos as opções para nossa linha de assinatura, incluindo o nome do signatário, cargo, e-mail e outros detalhes relevantes:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Essas opções ajudam a personalizar a linha de assinatura, tornando-a clara e profissional.

## Etapa 3: Insira a linha de assinatura

Com nossas opções prontas, agora podemos inserir a linha de assinatura no documento:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 O`InsertSignatureLine` O método adiciona a linha de assinatura e atribuímos um ID de provedor exclusivo a ela.

## Etapa 4: Salve o documento

Após inserir a linha de assinatura, vamos salvar o documento:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Isso salva seu documento com a linha de assinatura recém-adicionada.

## Etapa 5: Configurar opções de assinatura

Agora, vamos configurar as opções de assinatura, incluindo o ID da linha de assinatura, o ID do provedor, os comentários e o horário da assinatura:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Essas configurações garantem que o documento seja assinado com os detalhes corretos.

## Etapa 6: Criar detentor de certificado

Para assinar o documento, precisamos criar um titular de certificado usando o certificado PFX:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Substituir`"morzal.pfx"` com o nome real do arquivo do seu certificado e`"aw"` com a senha do seu certificado.

## Etapa 7: Assine o documento

Por fim, assinaremos o documento usando o utilitário de assinatura digital:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Este processo assina o documento e o salva como um novo arquivo.

## Conclusão

Parabéns! Você criou com sucesso uma linha de assinatura e definiu o ID do provedor em um documento do Word usando o Aspose.Words para .NET. Esta biblioteca poderosa simplifica as tarefas de processamento de documentos, tornando seu fluxo de trabalho mais eficiente. Experimente e veja como ela pode aprimorar seus projetos!

## Perguntas frequentes

### Posso personalizar a aparência da linha de assinatura?
 Absolutamente! Você pode ajustar várias opções no`SignatureLineOptions` para se adequar ao seu estilo e às suas necessidades.

### E se eu não tiver um certificado PFX?
Você precisará obter um de uma autoridade de certificação confiável, pois ele é essencial para assinar documentos digitalmente.

### Posso adicionar várias linhas de assinatura a um documento?
Sim, você pode adicionar várias linhas de assinatura repetindo o processo de inserção com opções diferentes.

### O Aspose.Words para .NET é compatível com o .NET Core?
Sim, o Aspose.Words para .NET oferece suporte ao .NET Core, o que o torna versátil para vários ambientes de desenvolvimento.

### Quão seguras são as assinaturas digitais?
Assinaturas digitais criadas com o Aspose.Words são altamente seguras, desde que você use um certificado válido e confiável.