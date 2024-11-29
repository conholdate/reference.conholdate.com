---
title: Dominando a manipulação de arquivos DGN com Aspose.CAD em .NET
linktitle: Dominando a manipulação de arquivos DGN
second_title: Aspose.CAD .NET - Formato de arquivo CAD e BIM
description: Aprenda a carregar arquivos DGN, iterar por seus elementos, gerenciar entidades 2D e 3D e exportá-los como imagens raster, tudo isso aproveitando os poderosos recursos da biblioteca Aspose.CAD.
type: docs
weight: 18
url: /pt/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Introdução

Você é um desenvolvedor .NET ansioso para integrar arquivos DGN em seus aplicativos? O Aspose.CAD para .NET oferece uma biblioteca poderosa projetada especificamente para trabalhar com formatos de arquivo DGN. Neste tutorial, exploraremos como manipular eficientemente arquivos DGN, incluindo elementos suportados e como manipulá-los em seus projetos .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter a seguinte configuração:

- Conhecimento básico de programação .NET: familiaridade com C# ou VB.NET será benéfica.
- Visual Studio: instalado na sua máquina para desenvolvimento de projetos.
-  Biblioteca Aspose.CAD para .NET: Baixe em[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Etapa 1: Importar os namespaces necessários

Para aproveitar as funcionalidades do Aspose.CAD, comece importando os namespaces necessários para o seu projeto.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Etapa 2: carregue seu arquivo DGN

 Comece carregando um arquivo DGN existente em seu aplicativo. Isso é feito instanciando um`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Continue com sua lógica aqui
}
```

## Etapa 3: iterar pelos elementos DGN

Depois que o arquivo DGN for carregado, você pode iterar por seus elementos. O Aspose.CAD fornece uma variedade de tipos de elementos DGN para sua manipulação.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Processe cada elemento
}
```

## Etapa 4: Manipular entidades 2D e 3D

Você pode diferenciar entre elementos DGN 2D e 3D. Veja abaixo como lidar com eles de forma eficiente:

### Manipular entidades 2D

Você pode gerenciar entidades 2D suportadas anteriormente com um bloco switch-case.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Adicione sua lógica de processamento aqui
        break;
}
```

### Manipular entidades 3D

Da mesma forma, manipule entidades 3D da seguinte maneira:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Adicione sua lógica de processamento aqui
        break;
}
```

## Etapa 5: Exportar o arquivo DGN

Após manipular os elementos DGN, você pode querer exportar o arquivo como uma imagem raster. Isso pode ser facilmente feito com o Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Defina seu caminho de saída
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Conclusão

Neste tutorial, aprendemos como usar o Aspose.CAD para .NET para gerenciar efetivamente arquivos DGN. Seguindo as etapas descritas, você pode manipular facilmente elementos DGN 2D e 3D e exportá-los como imagens raster. Esta biblioteca poderosa permite a integração perfeita do processamento DGN em seus aplicativos .NET, aprimorando os recursos do seu projeto.

## Perguntas frequentes

### Onde posso encontrar a documentação do Aspose.CAD para .NET?

 A documentação completa está disponível[aqui](https://reference.aspose.com/cad/net/).

### Como faço para baixar o Aspose.CAD para .NET?

 Você pode baixar a versão mais recente da biblioteca[aqui](https://releases.aspose.com/cad/net/).

### Existe uma versão de avaliação gratuita disponível para o Aspose.CAD para .NET?

 Sim, um teste gratuito está disponível[aqui](https://releases.aspose.com/).

### Como posso obter licenças temporárias para Aspose.CAD para .NET?

 Você pode solicitar licenças temporárias[aqui](https://purchase.conholdate.com/temporary-license/).

### Precisa de ajuda ou tem dúvidas?

Para obter suporte ou fazer perguntas, visite a comunidade Aspose.CAD[fórum de suporte](https://forum.aspose.com/c/cad/19).