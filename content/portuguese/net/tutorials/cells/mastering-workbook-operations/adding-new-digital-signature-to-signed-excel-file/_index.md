---
title: Adicionar uma nova assinatura digital a um arquivo Excel assinado
linktitle: Adicionar uma nova assinatura digital a um arquivo Excel assinado
second_title: API de processamento do Aspose.Cells .NET Excel
description: Aprenda como adicionar uma nova assinatura digital a um arquivo Excel assinado existente usando Aspose.Cells para .NET. Este guia abrangente abrange todos os pré-requisitos, instruções passo a passo e exemplo de código.
type: docs
weight: 12
url: /pt/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Introdução

No cenário digital de hoje, garantir a autenticidade e a integridade dos documentos é mais crucial do que nunca. Assinaturas digitais fornecem uma maneira confiável de verificar se um documento não foi alterado e se ele se origina de uma fonte legítima. Se você estiver trabalhando com arquivos do Excel no .NET e precisar adicionar uma nova assinatura digital a um arquivo que já está assinado, este guia é para você! Vamos percorrer o processo de adicionar uma assinatura digital a um arquivo do Excel assinado existente usando o Aspose.Cells para .NET.

## Pré-requisitos

Antes de mergulharmos na implementação, certifique-se de ter o seguinte:

1.  Aspose.Cells para .NET: Baixe e instale o Aspose.Cells do[página de lançamento](https://releases.aspose.com/cells/net/).
2. .NET Framework: certifique-se de que sua máquina tenha o .NET Framework configurado e que você esteja familiarizado com os conceitos básicos de programação .NET.
3. Certificado Digital: Obtenha um certificado digital válido no formato .pfx. Para teste, você pode criar um certificado autoassinado.
4. Ambiente de desenvolvimento: use um IDE como o Visual Studio para escrever e executar seu código C#.
5. Exemplo de arquivo do Excel: tenha um arquivo do Excel existente que já esteja assinado digitalmente, que será o destino para adicionar uma nova assinatura.

Com esses pré-requisitos em vigor, vamos ao código!

## Importar pacotes necessários

No topo do seu arquivo C#, inclua os seguintes namespaces para acessar as classes e métodos necessários:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Etapa 1: Defina seus diretórios

Especifique os diretórios para seus arquivos de origem e onde salvar o arquivo de saída:

```csharp
// Diretório de origem
string sourceDir = "Your Document Directory"; // Substitua pelo seu diretório atual
// Diretório de saída
string outputDir = "Your Document Directory"; // Substitua pelo seu diretório atual
```

## Etapa 2: Carregue a pasta de trabalho assinada existente

Carregue a pasta de trabalho do Excel que já está assinada:

```csharp
// Carregue a pasta de trabalho que já está assinada digitalmente
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Etapa 3: Crie uma coleção de assinaturas digitais

Crie uma coleção para gerenciar suas assinaturas digitais:

```csharp
//Crie a coleção de assinaturas digitais
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Etapa 4: Carregue seu certificado

Carregue seu certificado digital, que será usado para criar a nova assinatura:

```csharp
// Arquivo de certificado e sua senha
string certFileName = sourceDir + "AsposeDemo.pfx"; // Seu arquivo de certificado
string password = "aspose"; // Sua senha de certificado

// Criar novo certificado
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Etapa 5: Crie uma nova assinatura digital

Agora, crie uma nova assinatura digital e adicione-a à sua coleção:

```csharp
// Crie uma nova assinatura digital e adicione-a à coleção
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Etapa 6: Adicionar a coleção de assinaturas à pasta de trabalho

Adicione a coleção de assinaturas digitais à pasta de trabalho:

```csharp
// Adicionar coleta de assinatura digital à pasta de trabalho
workbook.AddDigitalSignature(dsCollection);
```

## Etapa 7: Salve a pasta de trabalho

Salve a pasta de trabalho com a nova assinatura digital incluída:

```csharp
// Salvar a pasta de trabalho
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Etapa 8: Confirme o sucesso

Forneça feedback após a execução bem-sucedida:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Conclusão

Parabéns! Você adicionou com sucesso uma nova assinatura digital a um arquivo Excel já assinado usando o Aspose.Cells for .NET. Este processo aumenta a segurança dos seus documentos e garante sua autenticidade e integridade.

## Perguntas frequentes

### O que é uma assinatura digital?

Uma assinatura digital é um esquema matemático que verifica a autenticidade e a integridade de mensagens ou documentos digitais, garantindo que não foram alterados e confirmando a identidade do signatário.

### Preciso de um certificado especial para criar uma assinatura digital?

Sim, um certificado digital emitido por uma autoridade de certificação (CA) confiável é necessário para criar uma assinatura digital válida.

### Posso usar um certificado autoassinado para testes?

Claro! Você pode usar um certificado autoassinado para fins de desenvolvimento e teste, mas para produção, é aconselhável usar um certificado de uma CA confiável.

### O que acontece se eu tentar adicionar uma assinatura a um documento não assinado?

Se você tentar adicionar uma assinatura digital a um documento que ainda não esteja assinado, funcionará sem problemas, mas a assinatura original não estará presente.

### Onde posso encontrar mais informações sobre o Aspose.Cells?

 Para guias detalhados e referências de API, consulte o[Documentação do Aspose.Cells](https://reference.aspose.com/cells/net/).