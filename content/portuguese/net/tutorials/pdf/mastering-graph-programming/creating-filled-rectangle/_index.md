---
title: Criando retângulo preenchido
linktitle: Criando retângulo preenchido
second_title: Referência da API do Aspose.PDF para .NET
description: Desbloqueie o poder da manipulação de PDF com Aspose.PDF para .NET neste tutorial passo a passo. Aprenda a criar programaticamente documentos PDF visualmente atraentes desenhando retângulos preenchidos.
type: docs
weight: 50
url: /pt/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Introdução

Você já quis criar PDFs visualmente impressionantes programaticamente? Se sim, você está no lugar certo! Neste tutorial, exploraremos o Aspose.PDF para .NET, uma biblioteca poderosa que simplifica a manipulação de documentos PDF. Hoje, focaremos na criação de um retângulo preenchido dentro de um arquivo PDF. Seja você um desenvolvedor experiente ou apenas iniciante, este guia o guiará por cada etapa de uma maneira amigável e envolvente. Então, pegue seu chapéu de codificação e vamos começar!

## Pré-requisitos

Antes de mergulharmos no código, certifique-se de ter o seguinte:

1. Visual Studio: Instale o Visual Studio em sua máquina, pois é um excelente IDE para desenvolvimento .NET.
2. Aspose.PDF para .NET: Baixe e instale a biblioteca Aspose.PDF de[aqui](https://releases.aspose.com/pdf/net/).
3. Conhecimento básico de C#: A familiaridade com a programação em C# ajudará você a entender melhor os trechos de código.

## Etapa 1: Crie um novo projeto

1. Abra o Visual Studio e crie um novo projeto de aplicativo de console.
2. Dê um nome apropriado ao seu projeto.

## Etapa 2: Adicionar referência Aspose.PDF

1. Clique com o botão direito do mouse no seu projeto no Solution Explorer.
2. Selecione Gerenciar pacotes NuGet.
3. Procure por Aspose.PDF e instale a versão mais recente.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Agora que configuramos tudo, vamos mergulhar no código!

## Etapa 3: configure seu diretório de documentos

Especifique o caminho onde seu PDF será salvo:

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real na sua máquina onde você deseja salvar o PDF.

## Etapa 4: Criar uma instância de documento

Inicializar um novo documento PDF:

```csharp
// Criar instância de documento
Document doc = new Document();
```

## Etapa 5: Adicionar uma página ao documento

Todo PDF precisa de pelo menos uma página. Vamos adicionar uma:

```csharp
// Adicionar página à coleção de páginas do arquivo PDF
Page page = doc.Pages.Add();
```

## Etapa 6: Criar uma instância de gráfico

 UM`Graph` instância atua como uma tela para desenhar formas:

```csharp
// Criar instância do Graph
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Etapa 7: adicione o gráfico à página

Anexe o gráfico à página:

```csharp
// Adicionar objeto gráfico à coleção de parágrafos da instância da página
page.Paragraphs.Add(graph);
```

## Etapa 8: Crie uma instância de retângulo

Defina a posição e o tamanho do retângulo:

```csharp
// Criar instância Rectangle
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Etapa 9: especifique a cor de preenchimento

Escolha uma cor para seu retângulo. Para este exemplo, usaremos vermelho:

```csharp
// Especificar cor de preenchimento para objeto Graph
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Etapa 10: Adicione o retângulo ao gráfico

Adicione o retângulo ao gráfico:

```csharp
// Adicionar objeto retângulo à coleção de formas do objeto Graph
graph.Shapes.Add(rect);
```

## Etapa 11: Salve o documento PDF

Por fim, salve seu documento no diretório especificado:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// Salvar arquivo PDF
doc.Save(dataDir);
```

## Etapa 12: Mensagem de confirmação

Imprima uma mensagem de confirmação para indicar sucesso:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Conclusão

Parabéns! Você criou com sucesso um retângulo preenchido em um documento PDF usando o Aspose.PDF para .NET. Esta biblioteca poderosa abre um mundo de possibilidades para manipulação de PDF, permitindo que você gere documentos impressionantes programaticamente. Não importa se você está criando relatórios, faturas ou qualquer outro tipo de PDF, o Aspose.PDF tem tudo o que você precisa.

## Perguntas frequentes

### O que é Aspose.PDF para .NET?
Aspose.PDF para .NET é uma biblioteca que permite aos desenvolvedores criar, manipular e converter documentos PDF programaticamente.

### Posso usar o Aspose.PDF gratuitamente?
 Sim, o Aspose oferece uma versão de teste gratuita que você pode usar para explorar os recursos da biblioteca. Você pode baixá-la[aqui](https://releases.aspose.com/).

### Existe uma maneira de obter suporte para o Aspose.PDF?
 Absolutamente! Você pode obter suporte através do fórum Aspose[aqui](https://forum.aspose.com/c/pdf/10).

### Como posso comprar o Aspose.PDF?
 Você pode comprar Aspose.PDF visitando a página de compra[aqui](https://purchase.aspose.com/buy).

### Que tipos de formas posso criar com o Aspose.PDF?
Você pode criar várias formas, incluindo retângulos, círculos, linhas e muito mais, usando a biblioteca Aspose.PDF.