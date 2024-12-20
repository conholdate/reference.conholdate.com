---
title: Crie um marcador em um documento do Word com Aspose.Words para .NET
linktitle: Crie um marcador em um documento do Word com Aspose.Words para .NET
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como aprimorar seus documentos do Word criando e gerenciando marcadores usando o Aspose.Words para .NET. Este guia tutorial passo a passo.
type: docs
weight: 10
url: /pt/net/tutorials/words/mastering-bookmarks/create-bookmark-in-word-document/
---
## Introdução

Navegar por documentos grandes pode ser desafiador, mas os marcadores tornam isso fácil! Este tutorial o guiará pela criação de marcadores em um documento do Word usando o Aspose.Words para .NET. Você aprenderá passo a passo como configurar seu documento, adicionar marcadores e salvá-lo como PDF. Vamos começar!

## Pré-requisitos

Antes de mergulhar, certifique-se de ter o seguinte:

1.  Biblioteca Aspose.Words para .NET: Baixe e instale em[aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: use o Visual Studio ou qualquer IDE compatível com .NET.
3. Conhecimento básico de C#: familiaridade com conceitos de programação em C# será útil.

## Importando namespaces

Primeiro, importe os namespaces necessários para trabalhar com Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: Configurar o documento e o DocumentBuilder

 Crie um novo documento e inicialize-o`DocumentBuilder`, que permite adicionar conteúdo e favoritos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Crie o marcador principal

Para criar um marcador, você precisa especificar seus pontos de início e fim. Veja como criar um marcador chamado "Meu marcador":

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside the main bookmark.");
```
- `StartBookmark`: Marca o início do marcador.
- `Writeln`: Adiciona texto dentro do marcador.

## Etapa 3: Crie um marcador aninhado

Você pode aninhar marcadores para melhor organização. Veja como adicionar "Marcador aninhado" dentro de "Meu marcador":

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside the nested bookmark.");
builder.EndBookmark("Nested Bookmark");
```
- O aninhamento permite que você crie uma estrutura hierárquica. 
- `EndBookmark`: Fecha o marcador atual.

## Etapa 4: adicione texto fora do marcador aninhado

Depois de criar o marcador aninhado, continue adicionando conteúdo dentro do marcador principal:

```csharp
builder.Writeln("Text after the nested bookmark.");
builder.EndBookmark("My Bookmark");
```
Isso garante que o marcador principal inclua o marcador aninhado e qualquer texto adicional.

## Etapa 5: Configurar opções de salvamento de PDF

Para incluir marcadores no PDF, configure as opções de salvamento:

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```
- `PdfSaveOptions`: Define como o documento é salvo como PDF.
- `BookmarksOutlineLevels`: Define a hierarquia de marcadores no PDF.

## Etapa 6: Salve o documento

Por fim, salve o documento como PDF:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```
 O`Save` O método salva o documento no formato e local especificados, completo com marcadores.

## Conclusão

Criar marcadores em um documento do Word com o Aspose.Words para .NET é simples e melhora a navegação no documento. Não importa se você está gerando relatórios, eBooks ou gerenciando documentos extensos, os marcadores são inestimáveis. Siga este tutorial e você terá um PDF bem organizado e marcado em pouco tempo!

## Perguntas frequentes

### Posso criar vários favoritos em níveis diferentes?
Sim! Você pode criar vários marcadores e definir sua hierarquia ao salvar como PDF.

### Como atualizo o texto de um favorito?
 Usar`DocumentBuilder.MoveToBookmark`para navegar até o marcador e atualizar o texto.

### É possível excluir um favorito?
 Absolutamente! Use o`Bookmarks.Remove` método especificando o nome do marcador.

### Posso criar favoritos em outros formatos além de PDF?
Sim, o Aspose.Words suporta marcadores em formatos como DOCX, HTML e EPUB.

### Como posso garantir que os marcadores apareçam corretamente no PDF?
 Definir`BookmarksOutlineLevels` corretamente em`PdfSaveOptions` para garantir que os marcadores sejam incluídos no esboço do PDF.