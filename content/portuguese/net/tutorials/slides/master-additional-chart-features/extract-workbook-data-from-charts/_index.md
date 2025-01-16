---
title: Extraia dados da pasta de trabalho de gráficos com Aspose.Slides para .NET
linktitle: Extraia dados da pasta de trabalho de gráficos com Aspose.Slides para .NET
second_title: API de processamento do PowerPoint Aspose.Slides .NET
description: Desbloqueie o potencial das suas apresentações do PowerPoint aprendendo como recuperar dados de planilhas de gráficos usando o Aspose.Slides for .NET. Este tutorial passo a passo o guia pelo processo, facilitando a extração e utilização eficaz de dados de gráficos.
type: docs
weight: 12
url: /pt/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## Introdução

Trabalhar com apresentações do PowerPoint pode ser desafiador, especialmente ao extrair dados valiosos de gráficos incorporados. Felizmente, o Aspose.Slides for .NET fornece uma solução robusta que simplifica esse processo. Neste tutorial, nós o guiaremos passo a passo sobre como recuperar uma pasta de trabalho de um gráfico dentro de uma apresentação do PowerPoint.

## Pré-requisitos

Antes de começarmos o código, certifique-se de ter o seguinte pronto:

### Aspose.Slides para .NET

Você precisa ter o Aspose.Slides for .NET instalado no seu ambiente de desenvolvimento. Se você ainda não fez isso, pode baixá-lo do site:

[Baixe Aspose.Slides para .NET](https://releases.aspose.com/slides/net/)

### Apresentação em PowerPoint

Tenha seu arquivo de apresentação do PowerPoint em mãos, especialmente um que contenha um gráfico com dados associados que você deseja recuperar.

## Etapa 1: Importar os namespaces necessários

Para trabalhar efetivamente com o Aspose.Slides, primeiro você precisa importar os namespaces necessários:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Etapa 2: Defina o diretório do documento

Especifique o diretório onde seu arquivo de apresentação está localizado:

```csharp
string dataDir = "Your Document Directory"; // Ajuste este caminho conforme necessário
```

## Etapa 3: Carregue a apresentação

Você pode carregar a apresentação do PowerPoint enquanto habilita a recuperação da pasta de trabalho do cache do gráfico. Veja como fazer isso:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // Acesse e trabalhe com os dados do gráfico
    // Seu código irá aqui
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 Nesta etapa, o`LoadOptions` objeto permite que você habilite a recuperação da pasta de trabalho usando o`RecoverWorkbookFromChartCache` propriedade.

## Etapa 4: recuperar o gráfico e acessar sua pasta de trabalho

Agora é hora de analisar o gráfico e recuperar seus dados associados:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // Ajuste o índice conforme necessário
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// Agora você pode trabalhar com os dados da pasta de trabalho conforme sua necessidade
```

Ao acessar a primeira forma do primeiro slide (que deve ser um gráfico), você obtém a pasta de trabalho de dados do gráfico e pode manipular ou extrair os dados conforme necessário.

## Conclusão

Neste tutorial, demonstramos como recuperar efetivamente uma pasta de trabalho de um gráfico em uma apresentação do PowerPoint usando o Aspose.Slides for .NET. Seguindo essas etapas, você pode facilmente extrair e utilizar dados do gráfico para suas necessidades analíticas.

## Perguntas frequentes

### O que é Aspose.Slides para .NET?

Aspose.Slides para .NET é uma biblioteca poderosa que permite aos desenvolvedores criar, manipular e converter apresentações do Microsoft PowerPoint programaticamente.

### Posso testar o Aspose.Slides para .NET antes de comprar?

 Sim! A Aspose oferece uma versão de teste gratuita do Aspose.Slides para .NET. Você pode avaliar suas capacidades antes de fazer uma compra.[Obtenha o teste gratuito aqui](https://releases.aspose.com/).

### Onde posso encontrar a documentação do Aspose.Slides para .NET?

 Você pode acessar a documentação abrangente do Aspose.Slides para .NET[aqui](https://reference.aspose.com/slides/net/), que inclui exemplos e referências de API.

### Como faço para adquirir uma licença do Aspose.Slides para .NET?

 Para comprar uma licença, visite o site da Aspose e use o seguinte link:[Compre Aspose.Slides para .NET](https://purchase.aspose.com/buy).