---
title: Personalização avançada de gráficos com Aspose.Slides para .NET
linktitle: Personalização avançada de gráficos com Aspose.Slides para .NET
second_title: API de processamento do PowerPoint Aspose.Slides .NET
description: Desbloqueie todo o potencial do Aspose.Slides para .NET dominando técnicas avançadas de personalização de gráficos. Este guia passo a passo abrange tudo, desde a criação básica de gráficos até detalhes complexos, como linhas de grade, títulos de eixo e cores personalizadas.
type: docs
weight: 10
url: /pt/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Introdução

Criar gráficos visualmente atraentes e informativos é crucial para uma apresentação de dados eficaz. O Aspose.Slides for .NET oferece ferramentas poderosas para personalização de gráficos, permitindo que você personalize cada aspecto dos seus gráficos. Neste tutorial, exploraremos técnicas avançadas para personalização de gráficos usando o Aspose.Slides for .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes pré-requisitos:

1.  Biblioteca Aspose.Slides para .NET: Baixe e instale a biblioteca Aspose.Slides em[aqui](https://releases.aspose.com/slides/net/).
2. Ambiente de desenvolvimento .NET: configure um ambiente de desenvolvimento .NET, como o Visual Studio.
3. Conhecimento básico de C#: Familiaridade com programação em C# será benéfica, pois escreveremos código em C#.

Agora, vamos dividir o processo de personalização avançada de gráficos em etapas claras.

## Etapa 1: Crie uma nova apresentação

Comece criando uma nova apresentação para conter seu gráfico.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "Your Document Directory";

// Crie um diretório se ele não existir.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Instanciar a apresentação
Presentation pres = new Presentation();
```

## Etapa 2: Acesse o primeiro slide

Em seguida, acesse o primeiro slide onde você deseja adicionar o gráfico.

```csharp
// Acesse o primeiro slide
ISlide slide = pres.Slides[0];
```

## Etapa 3: Adicionar um gráfico de amostra

Agora, vamos adicionar um gráfico de linhas com marcadores ao slide.

```csharp
// Adicionar um gráfico de amostra
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Etapa 4: Defina o título do gráfico

Definir um título para seu gráfico fornece um contexto essencial.

```csharp
// Defina o título do gráfico
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Etapa 5: personalizar as principais linhas de grade

Você pode aprimorar as linhas de grade do eixo de valor para melhor legibilidade.

```csharp
// Personalize as principais linhas de grade para o eixo de valor
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Etapa 6: personalizar linhas de grade secundárias

Da mesma forma, personalize as linhas de grade secundárias para o eixo de valor.

```csharp
// Personalize linhas de grade secundárias para o eixo de valor
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Etapa 7: Definir o formato do número do eixo de valor

Você pode formatar os números exibidos no eixo de valores.

```csharp
// Definir formato de número do eixo de valor
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Etapa 8: Defina os valores máximo e mínimo

Defina os valores máximo e mínimo para o gráfico.

```csharp
// Definir valores máximos e mínimos do gráfico
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Etapa 9: personalizar as propriedades do texto do eixo de valor

Melhorar as propriedades de texto do eixo de valor melhora a legibilidade.

```csharp
// Personalizar propriedades de texto do eixo de valor
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Etapa 10: Adicionar título do eixo de valor

Adicionar um título ao eixo de valor pode esclarecer o que os dados representam.

```csharp
// Definir título do eixo de valor
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Etapa 11: personalizar as principais linhas de grade para o eixo de categoria

Agora, vamos aprimorar as principais linhas de grade do eixo de categorias.

```csharp
// Personalize as principais linhas de grade para o eixo de categoria
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Etapa 12: personalizar linhas de grade secundárias para o eixo de categoria

Da mesma forma, personalize as linhas de grade secundárias para o eixo de categoria.

```csharp
// Personalize as linhas de grade secundárias para o eixo da categoria
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Etapa 13: personalizar as propriedades do texto do eixo da categoria

Melhore o estilo da fonte e a aparência dos rótulos dos eixos de categoria.

```csharp
// Personalizar propriedades de texto do eixo de categoria
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Etapa 14: Adicionar título do eixo da categoria

Se necessário, você também pode adicionar um título para o eixo de categoria.

```csharp
// Definir título do eixo da categoria
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Etapa 15: Personalizações adicionais

Melhore ainda mais seu gráfico com personalizações adicionais, como legendas, cores de parede e configurações de área de plotagem.

```csharp
// Personalizações adicionais (opcional)

// Personalizar propriedades de texto de legendas
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Mostrar legendas de gráficos sem sobreposição de gráficos
chart.Legend.Overlay = true;

// Definindo a cor da parede de fundo do gráfico
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Definir cor do piso do gráfico
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Definir cor da área de plotagem
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Salvar a apresentação
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Conclusão

Neste guia abrangente, cobrimos técnicas avançadas de personalização de gráficos usando Aspose.Slides para .NET. Você aprendeu como criar uma apresentação, adicionar um gráfico, refinar sua aparência e personalizar vários elementos de gráfico, como linhas de grade, rótulos de eixo e legendas. 

## Perguntas frequentes

### Quais versões do .NET são suportadas pelo Aspose.Slides para .NET?
Aspose.Slides para .NET oferece suporte a várias versões do .NET, incluindo .NET Framework e .NET Core. Consulte a documentação para obter uma lista completa das versões com suporte.

### Posso criar gráficos a partir de fontes de dados como arquivos do Excel?
Sim, o Aspose.Slides permite que você crie gráficos a partir de fontes de dados externas, como planilhas do Excel. Consulte a documentação para obter exemplos detalhados.

### Como posso adicionar rótulos de dados personalizados às minhas séries de gráficos?
 Para adicionar rótulos de dados personalizados, acesse o`DataLabels` propriedade da série e adapte os rótulos conforme necessário. Você pode encontrar exemplos de código na documentação.

### É possível exportar o gráfico para diferentes formatos, como PDF ou imagens?
Absolutamente! O Aspose.Slides permite que você exporte suas apresentações com gráficos para vários formatos, incluindo PDF e formatos de imagem.

### Onde posso encontrar mais tutoriais e exemplos para Aspose.Slides para .NET?
 Visite o Aspose.Slides[site](https://reference.aspose.com/slides/net/) para tutoriais abrangentes, exemplos de código e documentação.