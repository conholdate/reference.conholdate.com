---
title: Adicionar texto de seções marcadas em documentos do Word
linktitle: Adicionar texto de seções marcadas em documentos do Word
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como anexar texto perfeitamente de seções marcadas de um documento do Word com o Aspose.Words para .NET. Este tutorial passo a passo.
type: docs
weight: 10
url: /pt/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## Introdução

Você já achou desafiador anexar texto de uma seção marcada em um documento do Word? Você está no lugar certo! Este tutorial irá guiá-lo pelo processo passo a passo usando o Aspose.Words para .NET. No final, você será capaz de anexar texto marcado como um profissional. Vamos começar!

## Pré-requisitos

Antes de começarmos, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Se você ainda não o instalou, você pode[baixe aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: Um ambiente de desenvolvimento .NET como o Visual Studio.
- Conhecimento básico de C#: Familiaridade com conceitos básicos de programação em C# será benéfica.
- Documento do Word com marcadores: Um documento do Word contendo marcadores que usaremos para anexar texto.

## Importar namespaces necessários

Primeiro, precisamos importar os namespaces necessários para acessar as funcionalidades do Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## Etapa 1: Carregue o documento e inicialize as variáveis

Vamos começar carregando nossos documentos do Word de origem e destino e inicializando as variáveis necessárias.

```csharp
//Carregue os documentos de origem e destino.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicialize o importador de documentos.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Encontre o marcador no documento de origem.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Etapa 2: Identifique os parágrafos inicial e final

Em seguida, precisamos localizar os parágrafos onde o marcador começa e termina. Isso é essencial para extrair o texto correto.

```csharp
// Identifique os parágrafos no início e no fim do marcador.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Valide os parágrafos.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## Etapa 3: Validar os pais do parágrafo

Precisamos garantir que tanto o parágrafo inicial quanto o final compartilhem o mesmo nó pai. Esta é uma abordagem simplificada para evitar complicações.

```csharp
// Verifique se os parágrafos inicial e final têm o mesmo pai.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## Etapa 4: Identifique o nó a ser interrompido

Agora, precisamos determinar onde parar de copiar o texto, que será o nó imediatamente após o parágrafo final.

```csharp
// Identifique o nó imediatamente após o parágrafo final.
Node endNode = endPara.NextSibling;
```

## Etapa 5: Anexar texto marcado ao documento de destino

Por fim, faremos um loop pelos nós do parágrafo inicial até o nó após o parágrafo final e os anexaremos ao documento de destino.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Importe o nó atual para o documento de destino.
    Node newNode = importer.ImportNode(curNode, true);

    // Anexe o nó importado ao documento de destino.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Salve o documento de destino atualizado.
dstDoc.Save("appended_document.docx");
```

## Conclusão

Parabéns! Você anexou com sucesso o texto de uma seção marcada em um documento do Word usando o Aspose.Words para .NET. Esta biblioteca poderosa torna a manipulação de documentos direta, e agora você tem outra habilidade útil em seu kit de ferramentas. Boa codificação!

## Perguntas frequentes

### Posso anexar texto de vários favoritos de uma só vez?
Sim, você pode repetir o processo para cada marcador e acrescentar o texto conforme necessário.

### E se os parágrafos inicial e final tiverem pais diferentes?
O exemplo atual assume que eles têm o mesmo pai. Se não tiverem, você precisará implementar um tratamento mais complexo.

### A formatação original do texto anexado será preservada?
 Absolutamente! Usando`ImportFormatMode.KeepSourceFormatting`garante que a formatação original seja mantida.

### É possível anexar texto a uma posição específica no documento de destino?
Sim, você pode acrescentar texto em qualquer posição desejada navegando até o nó apropriado no documento de destino.

### Posso anexar texto de um marcador a uma nova seção?
Sim, você pode criar uma nova seção no documento de destino e anexar o texto lá.