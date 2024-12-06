---
title: Adicionar propriedades de documento personalizadas no Word
linktitle: Adicionar propriedades de documento personalizadas no Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como aprimorar seus documentos do Word com propriedades de documento personalizadas usando o Aspose.Words para .NET. Este guia abrangente orienta você no processo.
type: docs
weight: 10
url: /pt/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## Introdução

Bem-vindo! Se você está explorando o Aspose.Words para .NET e quer aprender como adicionar propriedades de documento personalizadas aos seus arquivos do Word, você está no lugar certo. Propriedades personalizadas são inestimáveis para armazenar metadados adicionais que as propriedades integradas não cobrem. Se você precisa rastrear autorização de documento, números de revisão ou datas específicas, as propriedades personalizadas podem ajudar. Neste tutorial, nós o guiaremos pelas etapas para adicionar essas propriedades perfeitamente usando o Aspose.Words para .NET. Vamos começar!

## Pré-requisitos

Antes de mergulhar no código, certifique-se de ter o seguinte:

1.  Biblioteca Aspose.Words para .NET: Baixe-a[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Um IDE como o Visual Studio.
3. Conhecimento básico de C#: familiaridade com C# e .NET será útil.
4.  Documento de exemplo: Prepare um documento de exemplo do Word chamado`Properties.docx` para modificação.

## Importando namespaces

Para acessar as funcionalidades do Aspose.Words, você precisará importar os namespaces necessários no início do seu código:

```csharp
using System;
using Aspose.Words;
```

## Etapa 1: Configurando o caminho do documento

 Em seguida, vamos definir o caminho para o seu documento do Word. Esta etapa é essencial para localizar e abrir seu`Properties.docx` arquivo.

```csharp
// Especifique o caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Certifique-se de substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real para o seu documento.

## Etapa 2: Acessando propriedades personalizadas do documento

Agora, vamos acessar as propriedades personalizadas do documento do Word, onde seus metadados personalizados residirão.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Esta linha dá acesso à coleção de propriedades personalizadas com as quais você trabalhará.

## Etapa 3: Verificação de propriedades existentes

Antes de adicionar novas propriedades, é aconselhável verificar se uma propriedade já existe para evitar duplicação.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Este código verifica se a propriedade "Authorized" já existe. Se existir, o método sai mais cedo, prevenindo duplicatas.

## Etapa 4: Adicionando uma propriedade booleana

Vamos adicionar uma propriedade booleana personalizada para indicar se o documento está autorizado.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Esta linha adiciona uma propriedade chamada "Autorizado" e define seu valor como`true`.

## Etapa 5: Adicionando uma propriedade String

Em seguida, especificaremos quem autorizou o documento adicionando uma propriedade de string.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Sinta-se à vontade para substituir "John Smith" por qualquer nome que preferir.

## Etapa 6: Adicionando uma propriedade de data

Para rastrear quando o documento foi autorizado, vamos adicionar uma propriedade de data.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Esta linha adiciona uma propriedade chamada "Data Autorizada" e atribui a ela a data de hoje usando`DateTime.Today`.

## Etapa 7: Adicionar um número de revisão

Para controle de versão, podemos adicionar uma propriedade para rastrear o número de revisão do documento.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Aqui, adicionamos uma propriedade "Revisão Autorizada" que contém o número de revisão atual do documento.

## Etapa 8: Adicionando uma propriedade numérica

Por fim, vamos adicionar uma propriedade numérica para armazenar um valor autorizado, como um valor de orçamento.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Esta linha adiciona uma propriedade chamada "Valor Autorizado" com um valor de`123.45`. Você pode ajustar esse número conforme necessário.

## Conclusão

Parabéns! Você adicionou com sucesso propriedades de documento personalizadas a um documento do Word usando o Aspose.Words para .NET. Essas propriedades são uma maneira poderosa de armazenar metadados adaptados aos seus requisitos, seja rastreando detalhes de autorização, números de revisão ou quantidades específicas.

## Perguntas frequentes

### O que são propriedades de documentos personalizadas?
Propriedades de documentos personalizadas são metadados que você pode adicionar a um documento do Word para armazenar informações adicionais não cobertas pelas propriedades integradas.

### Posso adicionar outras propriedades além de strings e números?
Sim, você pode adicionar vários tipos de propriedades, incluindo valores booleanos, datas e até objetos personalizados.

### Como posso acessar essas propriedades em um documento do Word?
Você pode acessar propriedades personalizadas programaticamente usando o Aspose.Words ou visualizá-las diretamente no Word por meio das propriedades do documento.

### É possível editar ou excluir propriedades personalizadas?
Absolutamente! Você pode facilmente editar ou excluir propriedades personalizadas usando métodos fornecidos pelo Aspose.Words.

### Propriedades personalizadas podem ser usadas para filtrar documentos?
Sim! Propriedades personalizadas são excelentes para categorizar e filtrar documentos com base em metadados específicos.