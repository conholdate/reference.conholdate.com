---
title: Adicionando componentes de botão com GroupDocs.Annotation para .NET
linktitle: Adicionando componentes de botão
second_title: GroupDocs.Annotation API .NET
description: Descubra como elevar seus documentos PDF adicionando Button Components interativos usando GroupDocs.Annotation para .NET. Este tutorial passo a passo.
type: docs
weight: 10
url: /pt/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## Introdução

Neste tutorial, vamos orientá-lo no processo direto de adicionar um Button Component a um documento PDF usando a biblioteca GroupDocs.Annotation para .NET. Ao final deste guia, você estará equipado para aprimorar seus documentos PDF com recursos interativos.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte em mãos:

1.  GroupDocs.Annotation para .NET: Baixe e instale a biblioteca GroupDocs.Annotation para .NET de[aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: configure um ambiente de desenvolvimento adequado com o .NET framework instalado.

## Etapa 1: Importar os namespaces necessários

Comece importando os namespaces necessários para seu projeto:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Etapa 2: Inicializar o caminho de saída

Defina o caminho de saída onde o PDF modificado será salvo:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Etapa 3: Adicionar um componente de botão

Agora, vamos criar e adicionar o Componente Botão ao seu PDF:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // Posição e tamanho do botão
        PenColor = 65535,                       // Cor da borda do botão
        Style = BorderStyle.Dashed,             // Estilo de borda
        BorderWidth = 0,                        // Largura da borda
        BorderColor = 0,                        // Cor da borda
        AlternateName = "Name",                 // Nome alternativo para o botão
        PartialName = "Partial Name",           // Nome parcial do botão
        NormalCaption = "Caption",               // Texto exibido no botão
        ButtonColor = 16761035,                 // Cor de fundo do botão
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // Adicione o botão ao anotador
    annotator.Save("result.pdf"); // Salvar o PDF modificado
}
```

## Etapa 4: Exibir caminho de saída

Por fim, informe ao usuário onde o arquivo de saída foi salvo:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Parabéns! Você adicionou com sucesso um Button Component a um documento PDF usando GroupDocs.Annotation for .NET.

## Conclusão

Neste tutorial, demonstramos como incorporar Button Components em documentos PDF com GroupDocs.Annotation for .NET. Seguindo essas etapas, você pode melhorar significativamente a interatividade dos seus documentos PDF.

## Perguntas frequentes

### Posso personalizar a aparência do botão?

Absolutamente! Você pode modificar várias propriedades, como tamanho, cor e estilo, para atender às suas necessidades.

### O GroupDocs.Annotation for .NET é compatível com todas as versões de PDF?

Sim, o GroupDocs.Annotation for .NET oferece suporte a uma ampla variedade de versões em PDF, garantindo compatibilidade com a maioria dos documentos.

### Posso adicionar vários componentes de botão a um único documento PDF?

Sim, você pode adicionar quantos componentes de botão forem necessários a um documento PDF.

### O GroupDocs.Annotation for .NET oferece suporte a outros formatos de arquivo?

Sim, ele suporta vários formatos de documento, incluindo DOCX, PPTX e XLSX, além de PDF.

### Existe uma versão de teste disponível para fins de teste?

 Sim, você pode acessar uma avaliação gratuita do GroupDocs.Annotation para .NET em[aqui](https://releases.groupdocs.com/).
