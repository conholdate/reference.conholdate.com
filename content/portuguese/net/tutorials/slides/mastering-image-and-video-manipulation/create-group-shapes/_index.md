---
title: Crie formas de grupo no PowerPoint com Aspose.Slides para .NET
linktitle: Crie formas de grupo no PowerPoint com Aspose.Slides para .NET
second_title: API de processamento do PowerPoint Aspose.Slides .NET
description: Aprenda a criar e gerenciar formas de grupo usando o Aspose.Slides para .NET. Este guia abrangente fornece instruções claras e passo a passo.
type: docs
weight: 11
url: /pt/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Introdução

Melhorar o apelo visual e a organização das suas apresentações do PowerPoint pode impactar significativamente o engajamento do seu público. Um método eficaz de conseguir isso é por meio de formas de grupo. Neste tutorial, exploraremos como aproveitar o Aspose.Slides for .NET para criar e manipular formas de grupo em suas apresentações.

## Pré-requisitos

Antes de mergulhar no tutorial, certifique-se de ter o seguinte:

-  Aspose.Slides para .NET: Baixe e instale a versão mais recente da biblioteca Aspose.Slides do[Site Aspose](https://releases.aspose.com/slides/net/).
- Ambiente de desenvolvimento: configure um IDE compatível com .NET, como o Visual Studio, para trabalhar no seu projeto.
- Conhecimento básico de C#: familiarize-se com os conceitos fundamentais de C#.


## Importar namespaces necessários

No seu projeto C#, comece incluindo os seguintes namespaces:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Etapa 1: Instanciar a classe de apresentação

 Crie uma instância do`Presentation`classe onde você trabalhará em seus slides. Especifique o diretório onde seus documentos estão armazenados:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // As etapas para criar e manipular formas serão exibidas aqui
}
```

## Etapa 2: Acesse o primeiro slide

Recupere o primeiro slide da sua apresentação recém-criada:

```csharp
ISlide slide = pres.Slides[0];
```

## Etapa 3: Acesse a coleção de formas

Veja a coleção de formas no slide:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Etapa 4: Adicionar uma forma de grupo

Agora é hora de adicionar uma forma de grupo ao slide:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Etapa 5: adicione formas dentro do grupo

Você pode preencher a forma do grupo com formas individuais, como retângulos:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Forma 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Forma 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Forma 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Forma 4
```

## Etapa 6: Defina o quadro para a forma do grupo

Definir um quadro para a forma do grupo fornece a ele um limite definido:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Etapa 7: Salve a apresentação

Por fim, salve sua apresentação modificada no diretório especificado:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Conclusão

Parabéns! Você criou com sucesso formas de grupo em suas apresentações do PowerPoint usando o Aspose.Slides for .NET. Ao organizar formas dessa forma, você pode melhorar muito o layout visual e a clareza do seu conteúdo, tornando suas apresentações mais impactantes.

## Perguntas frequentes

### O Aspose.Slides é compatível com a versão mais recente do .NET?

 Sim, o Aspose.Slides é atualizado regularmente para compatibilidade com as versões mais recentes do .NET. Verifique o[documentação](https://reference.aspose.com/slides/net/) para obter os detalhes de compatibilidade mais recentes.

### Posso testar o Aspose.Slides antes de comprar?

 Absolutamente! Você pode baixar uma versão de teste gratuita[aqui](https://releases.aspose.com/).

### Onde posso encontrar suporte para consultas relacionadas ao Aspose.Slides?

 Visite o Aspose.Slides[fórum](https://forum.aspose.com/c/slides/11) para apoio e discussões da comunidade.

### Como obtenho uma licença temporária para o Aspose.Slides?

 Você pode solicitar uma licença temporária[aqui](https://purchase.aspose.com/temporary-license/).

### Onde posso comprar uma licença completa para o Aspose.Slides?

 Você pode comprar uma licença do[página de compra](https://purchase.aspose.com/buy).