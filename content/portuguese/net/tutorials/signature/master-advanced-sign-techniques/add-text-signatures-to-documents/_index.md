---
title: Adicionar assinaturas de texto a documentos usando GroupDocs.Signature
linktitle: Adicionar assinaturas de texto a documentos
second_title: GroupDocs.Assinatura .NET API
description: Aprenda a assinar documentos com texto usando o GroupDocs.Signature for .NET. Guia passo a passo para adicionar assinaturas de texto programaticamente.
type: docs
weight: 17
url: /pt/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Introdução

No cenário digital de hoje, a assinatura eletrônica de documentos se tornou essencial para agilizar fluxos de trabalho e economizar recursos. O GroupDocs.Signature for .NET fornece uma solução poderosa para adicionar assinaturas de texto programaticamente a vários formatos de documentos. Este tutorial o guiará pelas etapas para assinar um documento com texto usando o GroupDocs.Signature for .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. GroupDocs.Signature para .NET: Baixe e instale a biblioteca de[aqui](https://releases.groupdocs.com/signature/net/).
2. Ambiente de desenvolvimento: configure seu ambiente de desenvolvimento .NET.
3. Documento: Prepare o documento que deseja assinar (por exemplo, PDF, Word).

## Importando namespaces necessários

Comece importando os namespaces necessários para seu projeto .NET:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Etapa 1: Carregue o documento

Comece carregando o documento que você pretende assinar:

```csharp
string filePath = "sample.pdf"; // Caminho para o seu documento
string fileName = Path.GetFileName(filePath);
```

## Etapa 2: Defina o caminho do arquivo de saída

Em seguida, defina o caminho do arquivo de saída onde o documento assinado será salvo:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Etapa 3: Criar opções de assinatura

Configure as opções para sua assinatura de texto, incluindo conteúdo, posição, tamanho, cor e estilo de fonte:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // Posição X
    Top = 200, // Posição Y
    Width = 100, // Largura da assinatura
    Height = 30, // Altura da assinatura
    ForeColor = Color.Red, // Cor do texto
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Configurações de fonte
};
```

## Etapa 4: Assine o documento

Por fim, use GroupDocs.Signature para aplicar a assinatura de texto e salvar o documento assinado:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Assine o documento
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Conclusão

Neste tutorial, demonstramos como adicionar programaticamente uma assinatura de texto a um documento usando GroupDocs.Signature for .NET. Seguindo essas etapas, você pode aumentar a segurança e a autenticidade dos seus documentos de forma eficiente.

## Perguntas frequentes

### Posso personalizar a aparência da assinatura de texto?
Sim, você pode personalizar vários atributos, como cor, fonte, tamanho e posição da assinatura de texto para atender às suas necessidades.

### O GroupDocs.Signature é compatível com vários formatos de documentos?
Com certeza! O GroupDocs.Signature suporta uma ampla variedade de formatos, incluindo PDF, Word, Excel, PowerPoint e muito mais.

### Posso adicionar várias assinaturas de texto a um único documento?
Sim, você pode adicionar várias assinaturas de texto, cada uma com suas próprias opções de personalização.

### O GroupDocs.Signature garante a integridade do documento após a assinatura?
Sim, a biblioteca usa algoritmos criptográficos robustos para garantir a integridade do documento e evitar adulteração após a assinatura.

### Existe uma versão de teste disponível para testar antes da compra?
 Sim, você pode baixar uma versão de teste gratuita em[aqui](https://releases.groupdocs.com/) para explorar os recursos antes de fazer uma compra.