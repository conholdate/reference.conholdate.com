---
title: Opções de marcador de gráfico em ponto de dados no Aspose.Slides .NET
linktitle: Opções de marcador de gráfico em ponto de dados no Aspose.Slides .NET
second_title: API de processamento do PowerPoint Aspose.Slides .NET
description: Aprenda como aprimorar seus gráficos do PowerPoint com opções de marcadores personalizados usando o Aspose.Slides para .NET. Este guia passo a passo abrange pré-requisitos, criação de gráficos, formatação de pontos de dados e muito mais.
type: docs
weight: 11
url: /pt/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Introdução

Incorporar recursos visuais em apresentações é essencial para uma comunicação impactante. O Aspose.Slides para .NET fornece ferramentas robustas para criar e personalizar gráficos, permitindo que os desenvolvedores aprimorem suas apresentações de dados. Um dos recursos de destaque é a capacidade de usar opções de marcadores de gráfico em pontos de dados, permitindo uma personalização precisa para gráficos com aparência profissional. Este artigo o guiará por todas as etapas necessárias para atingir isso.

## Pré-requisitos

Antes de prosseguir, certifique-se do seguinte:

-  Aspose.Slides para .NET instalado: Baixe-o em[aqui](https://releases.aspose.com/slides/net/).
- Configuração básica: Um arquivo de apresentação, como "Test.pptx", no seu diretório de trabalho.
- Ambiente de desenvolvimento: Visual Studio ou equivalente, configurado para .NET.

## Importando namespaces necessários

Adicione os namespaces necessários ao seu projeto para um desenvolvimento perfeito:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Etapa 1: Crie um gráfico em sua apresentação

Comece criando um gráfico padrão no primeiro slide da sua apresentação:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Isso adiciona um`LineWithMarkers` gráfico para seu slide com dimensões especificadas.

## Etapa 2: recuperar o índice da planilha de dados do gráfico

O índice padrão da planilha de dados do gráfico é essencial para personalização adicional:

```csharp
int defaultWorksheetIndex = 0;
```

## Etapa 3: Acesse a pasta de trabalho de dados do gráfico

Para manipular dados do gráfico, recupere a pasta de trabalho associada:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Etapa 4: Configurar séries de gráficos e adicionar pontos de dados

Limpe as séries padrão e adicione novos pontos de dados para sua série:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Adicionar pontos de dados à série
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Etapa 5: aplicar preenchimentos de imagem aos marcadores de pontos de dados

Imagens personalizadas podem tornar os marcadores de dados visualmente atraentes:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Definir imagens personalizadas para marcadores
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Etapa 6: Personalize o tamanho do marcador

Modifique o tamanho dos marcadores para melhorar a visibilidade:

```csharp
series.Marker.Size = 20;
```

## Etapa 7: Salve a apresentação atualizada

Salve a apresentação personalizada no local desejado:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Conclusão

O Aspose.Slides para .NET equipa os desenvolvedores com ferramentas para criar gráficos profissionais com opções de personalização avançadas. Ao aproveitar as opções de marcadores de gráfico, você pode melhorar significativamente o apelo visual e a clareza de suas apresentações. Este guia passo a passo garante que até mesmo personalizações complexas sejam simples de implementar.

## Perguntas frequentes

### Posso usar qualquer formato de imagem para personalização de marcadores?
Sim, o Aspose.Slides suporta vários formatos de imagem, incluindo JPEG, PNG e BMP, para personalização de marcadores.

### Como altero o tipo de gráfico após a criação?
 Para alterar o tipo de gráfico, acesse o`chart.Type` propriedade e atribuir um diferente`ChartType`.

### O Aspose.Slides para .NET é compatível com versões mais antigas do PowerPoint?
Sim, ele suporta compatibilidade com formatos mais antigos do PowerPoint, garantindo versatilidade.

### Posso atualizar dados do gráfico dinamicamente?
 Absolutamente. Use o`IChartDataWorkbook` para atualizar programaticamente os dados do gráfico.

### Onde posso encontrar mais recursos?
 Explorar o[Documentação do Aspose.Slides](https://reference.aspose.com/slides/net/)ou junte-se ao[fóruns da comunidade](https://forum.aspose.com/) para suporte.