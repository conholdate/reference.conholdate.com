---
title: Criar e assinar nova linha de assinatura
linktitle: Criar e assinar nova linha de assinatura
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como adicionar facilmente uma assinatura digital aos seus documentos do Word usando o Aspose.Words para .NET. Este tutorial abrangente abrange tudo, desde a configuração do seu ambiente e inserção de uma linha de assinatura até salvar e verificar seus documentos assinados.
type: docs
weight: 10
url: /pt/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Introdução

Quer adicionar uma assinatura digital a um documento do Word? Com o Aspose.Words para .NET, é mais fácil do que você imagina! Este tutorial o guiará pelas etapas de configuração do seu ambiente, adição de uma linha de assinatura e assinatura digital do seu documento. Vamos começar!

## Pré-requisitos

Antes de mergulhar no código, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET -[Baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento .NET - O Visual Studio é ideal para essa tarefa.
3. Documento para assinar - Você pode criar um novo documento do Word ou usar um existente.
4.  Arquivo de certificado - A`.pfx` arquivo é necessário para assinaturas digitais.
5. Imagem da linha de assinatura (opcional) - Você pode incluir um arquivo de imagem para a assinatura.

## Importar namespaces necessários

Para usar as funcionalidades do Aspose.Words, você precisa importar os seguintes namespaces:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Etapa 1: Configurando o diretório de documentos

Comece definindo o caminho para o diretório do seu documento. Este será o lugar onde você salvará e recuperará seus documentos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Especifique o caminho do diretório do seu documento
```

## Etapa 2: Criando um novo documento

Em seguida, vamos criar um novo documento do Word. Este documento servirá como tela para sua linha de assinatura.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 3: Inserindo a linha de assinatura

 Agora, use o`DocumentBuilder` classe para inserir uma linha de assinatura em seu documento:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Etapa 4: Salvando o documento

Após inserir a linha de assinatura, salve o documento. Este é um passo crucial antes de assinar.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Etapa 5: Configurando opções de assinatura

Configure as opções para o processo de assinatura. Isso inclui especificar o ID da linha de assinatura e a imagem opcional para exibir com a assinatura.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Caminho para sua imagem
};
```

## Etapa 6: Carregando o certificado

Carregue o arquivo de certificado necessário para assinar o documento:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Ajuste o nome do arquivo e a senha
```

## Etapa 7: Assinando o documento

 Por fim, assine o documento usando o`DigitalSignatureUtil` classe. Salve o documento assinado com um novo nome para referência futura.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Conclusão

Parabéns! Você criou com sucesso um documento do Word, adicionou uma linha de assinatura e assinou digitalmente usando o Aspose.Words para .NET. Esta ferramenta poderosa simplifica a automação de documentos, garantindo que seus contratos e documentos formais sejam assinados e autenticados com segurança.

## Perguntas frequentes

### Posso usar outros formatos de imagem para a linha de assinatura?

Sim, você pode usar vários formatos de imagem, incluindo PNG, JPG e BMP.

###  É necessário usar um`.pfx` file for the certificate?

 Sim, um`.pfx` arquivo é um formato padrão para armazenar certificados e chaves privadas para assinaturas digitais.

### Posso adicionar várias linhas de assinatura em um único documento?

Absolutamente! Você pode inserir várias linhas de assinatura repetindo a etapa de inserção conforme necessário.

### E se eu não tiver um certificado digital?

Você precisará obter um certificado digital de uma autoridade de certificação confiável ou gerar um usando ferramentas como o OpenSSL.

### Como verifico a assinatura digital no documento?

Você pode verificar a assinatura digital abrindo o documento assinado no Word e verificando os detalhes da assinatura para confirmar sua autenticidade e integridade.