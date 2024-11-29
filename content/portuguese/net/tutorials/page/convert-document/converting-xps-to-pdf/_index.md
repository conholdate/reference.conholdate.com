---
title: Convertendo XPS para PDF com Aspose.Page para .NET
linktitle: Convertendo XPS para PDF
second_title: API Aspose.Page .NET
description: Descubra como converter facilmente documentos XPS (XML Paper Specification) para PDF (Portable Document Format) usando a poderosa biblioteca Aspose.Page para .NET.
type: docs
weight: 11
url: /pt/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Introdução

Neste tutorial, exploraremos como converter documentos XPS (XML Paper Specification) para PDF (Portable Document Format) usando a versátil biblioteca Aspose.Page for .NET. Esta poderosa biblioteca simplifica a conversão de documentos e oferece várias opções de personalização, tornando-a uma excelente escolha para desenvolvedores.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte em mãos:

-  Biblioteca Aspose.Page para .NET: Baixe e instale a biblioteca Aspose.Page para .NET do[Documentação do Aspose.Page](https://reference.aspose.com/page/net/).
  
- Ambiente de desenvolvimento: configure um ambiente de desenvolvimento .NET usando o Visual Studio ou outro IDE compatível.

- Documento XPS: tenha o arquivo XPS que você deseja converter pronto, armazenado em um diretório designado.

## Etapa 1: Importar os namespaces necessários

Comece importando o namespace necessário para acessar as funcionalidades do Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Etapa 2: Inicializar o diretório de documentos

Defina o caminho do diretório onde seus documentos são armazenados:

```csharp
string dataDir = "Your Document Directory";
```

 Certifique-se de substituir`"Your Document Directory"` com o caminho real para o diretório que contém seu documento XPS.

### Etapa 3: Abra os fluxos PDF e XPS

Em seguida, inicialize os fluxos para o arquivo XPS de entrada e o arquivo PDF de saída:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Certifique-se de ter o caminho correto definido para seus arquivos.

### Etapa 4: Carregue o documento XPS

Agora, carregue seu documento XPS usando a biblioteca Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Etapa 5: Configurar opções de salvamento de PDF

Configure as opções de salvamento do seu PDF, incluindo parâmetros de qualidade de imagem e compactação:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Defina o nível de qualidade JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Use compressão JPEG para imagens
    TextCompression = PdfTextCompression.Flate, // Aplicar compressão Flate para texto
    PageNumbers = new int[] { 1, 2, 6 } // Especifique os números de página a serem incluídos
};
```

Sinta-se à vontade para ajustar esses parâmetros de acordo com suas necessidades.

### Etapa 6: Crie o dispositivo de renderização de PDF

Crie um dispositivo de renderização para o formato PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Etapa 7: Salve o documento como PDF

Por fim, salve o documento XPS em PDF usando o dispositivo e as opções especificados:

```csharp
document.Save(device, options);
```

## Conclusão

Parabéns! Você converteu com sucesso um documento XPS para PDF usando Aspose.Page para .NET. Esta biblioteca não apenas simplifica a conversão de documentos, mas também oferece recursos extensivos para lidar com vários formatos.

## Perguntas frequentes

### Posso converter vários arquivos XPS em um único PDF?

Absolutamente! Você pode iterar por vários arquivos XPS e mesclá-los em um único documento PDF seguindo os mesmos passos de conversão.

### Quais outros formatos de saída o Aspose.Page for .NET suporta?

Além do PDF, o Aspose.Page para .NET suporta uma variedade de formatos, incluindo TIFF, JPEG e PNG.

### Como posso personalizar a aparência do PDF convertido?

 Você pode ajustar os parâmetros no`PdfSaveOptions` objeto, como qualidade JPEG e configurações de compactação, para obter a aparência desejada.

### Existe uma versão de teste disponível para o Aspose.Page para .NET?

 Sim, você pode experimentar o Aspose.Page para .NET com uma avaliação gratuita disponível[aqui](https://releases.aspose.com/).

### Onde posso encontrar suporte da comunidade para o Aspose.Page para .NET?

Para discussões e suporte da comunidade, visite o[Fórum Aspose.Page](https://forum.aspose.com/c/page/39).