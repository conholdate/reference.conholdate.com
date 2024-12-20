---
title: Algoritmo de Binarização de Bradley
linktitle: Algoritmo de Binarização de Bradley
second_title: Referência da API do Aspose.PDF para .NET
description: Aprenda como converter páginas PDF em imagens TIFF binárias de alta qualidade usando o algoritmo de binarização de Bradley no Aspose.PDF para .NET. Este guia passo a passo inclui um exemplo de código.
type: docs
weight: 30
url: /pt/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Introdução

Neste tutorial, guiaremos você pelo processo de conversão de uma página PDF em uma imagem TIFF usando o Bradley Binarization Algorithm. O Aspose.PDF para .NET simplifica essa tarefa, permitindo que você automatize e agilize seus fluxos de trabalho de documentos com facilidade.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

-  Aspose.PDF para .NET: Baixe a biblioteca em[aqui](https://releases.aspose.com/pdf/net/).
- Visual Studio (ou qualquer IDE C#).
- Conhecimento básico de C#.
-  Uma licença válida ou uma[licença temporária](https://purchase.aspose.com/temporary-license/) de Aspose.

## Etapa 1: configure seu projeto

Primeiro, crie um novo projeto C# no seu IDE e importe os namespaces necessários:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Etapa 2: Defina o diretório do documento

Especifique o caminho para o diretório onde seu documento PDF está localizado, bem como os caminhos de saída para as imagens TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Caminho para seu arquivo PDF
```

Este diretório armazenará o PDF de origem e os arquivos TIFF convertidos.

## Etapa 3: Carregue o documento PDF

Abra o documento PDF que você deseja converter:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Substituir`PageToTIFF.pdf` com o nome do seu arquivo PDF.

## Etapa 4: especificar caminhos de saída

Defina os caminhos de saída para os arquivos TIFF gerados:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Etapa 5: Defina a resolução da imagem

Defina a resolução para as imagens TIFF. Um DPI mais alto produzirá melhor qualidade de imagem:

```csharp
Resolution resolution = new Resolution(300);
```

## Etapa 6: Configurar as configurações do TIFF

Configure as configurações da imagem TIFF, incluindo compactação e profundidade de cor:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Usar 1bpp (1 bit por pixel) prepara a imagem para saída binária.

## Etapa 7: Crie o dispositivo TIFF

Crie um dispositivo TIFF que lidará com a conversão:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Etapa 8: converter a página PDF em TIFF

Converta a primeira página do PDF em uma imagem TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Etapa 9: Aplique o Algoritmo de Binarização de Bradley

Agora, aplique o Algoritmo de Bradley para converter a imagem TIFF em tons de cinza em uma imagem binária:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 O`BinarizeBradley` O método usa dois fluxos de arquivo (entrada e saída) e um valor limite. Ajuste o limite conforme necessário para obter resultados ideais.

## Etapa 10: Confirme a conversão bem-sucedida

Por fim, confirme se a conversão foi bem-sucedida:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Conclusão

Parabéns! Você converteu com sucesso uma página PDF em uma imagem TIFF e aplicou o Bradley Binarization Algorithm usando Aspose.PDF para .NET. Este processo é essencial para arquivamento de documentos, OCR e outros aplicativos profissionais. Com resolução de alta qualidade e compactação eficiente, suas imagens de documentos serão claras e gerenciáveis em tamanho.

## Perguntas frequentes

### O que é o Algoritmo de Bradley?
O Algoritmo de Bradley é uma técnica de binarização que converte imagens em tons de cinza em imagens binárias determinando um limite adaptativo para cada pixel com base em seus arredores.

### Posso converter várias páginas de PDF em TIFF usando este método?
 Sim, você pode modificar o`Process` método para percorrer todas as páginas do documento para conversão.

### Qual é a resolução ideal para converter PDFs em TIFF?
Uma resolução de 300 DPI é geralmente recomendada para imagens de alta qualidade, mas você pode ajustá-la de acordo com suas necessidades específicas.

### O que significa 1bpp em profundidade de cor?
1bpp (1 bit por pixel) indica que a imagem será em preto e branco, com cada pixel sendo totalmente preto ou totalmente branco.

### O Algoritmo de Bradley é adequado para OCR?
Sim, o Algoritmo de Bradley é frequentemente usado no pré-processamento de OCR porque melhora o contraste do texto em documentos digitalizados, melhorando a precisão do reconhecimento.