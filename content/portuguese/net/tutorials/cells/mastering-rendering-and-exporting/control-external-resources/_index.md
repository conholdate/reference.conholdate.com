---
title: Controle recursos externos com Aspose.Cells para .NET
linktitle: Controle recursos externos com Aspose.Cells para .NET
second_title: API de processamento do Aspose.Cells .NET Excel
description: Desbloqueie todo o potencial das suas conversões de Excel para PDF com o Aspose.Cells para .NET. Neste guia abrangente, aprenda a gerenciar recursos externos, como imagens, garantindo que seus PDFs reflitam seus requisitos exatos de formatação.
type: docs
weight: 12
url: /pt/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Introdução

No cenário digital de hoje, converter planilhas do Excel em documentos PDF é uma tarefa comum e essencial. Não importa se você está preparando relatórios, dados financeiros ou materiais de apresentação, garantir que seus PDFs reflitam o formato pretendido é crucial. O Aspose.Cells para .NET fornece uma biblioteca poderosa que permite controlar esse processo de conversão em detalhes, especialmente ao lidar com recursos externos, como imagens. Neste guia, exploraremos como gerenciar efetivamente recursos externos durante o processo de conversão do Excel para PDF usando o Aspose.Cells. Vamos mergulhar!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte pronto:

1. Visual Studio ou qualquer IDE compatível com .NET: Este será seu ambiente de desenvolvimento.
2.  Aspose.Cells para .NET: Se você ainda não o instalou, visite o[Downloads do Aspose](https://releases.aspose.com/cells/net/) página para obter a versão mais recente.
3. Conhecimento básico de C#: Familiaridade com C# será benéfica. Se precisar de esclarecimentos sobre quaisquer conceitos, sinta-se à vontade para procurá-los.
4. Arquivo Excel de exemplo: prepare um arquivo Excel, como "samplePdfSaveOptions_StreamProvider.xlsx", que contém os recursos externos que você deseja converter.
5. Arquivo de imagem para teste: use um arquivo de imagem como "newPdfSaveOptions_StreamProvider.png" como um recurso externo durante a conversão.

## Importar pacotes necessários

Para começar, você precisará importar os namespaces necessários da biblioteca Aspose.Cells. Adicione as seguintes diretivas using no topo do seu arquivo C#:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Esses namespaces fornecem as classes e métodos essenciais para suas tarefas.

## Etapa 1: Crie uma classe de provedor de fluxo

 Primeiro, crie uma classe de provedor de fluxo que implemente o`IStreamProvider` interface. Esta classe permitirá que você controle como os recursos externos são carregados.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Carregue a imagem em um fluxo de memória
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Este método é chamado quando o fluxo é fechado, registrando uma mensagem de depuração.
- InitStream: Este método lê o arquivo de imagem externo como uma matriz de bytes, converte-o em um fluxo de memória e o atribui ao`options.Stream` propriedade.

## Etapa 2: Configurar diretórios de origem e saída

Em seguida, defina os diretórios para o arquivo Excel e o PDF de saída.

```csharp
// Diretório de origem
string sourceDir = "Your Document Directory";
// Diretório de saída
string outputDir = "Your Document Directory";
```

 Substituir`"Your Document Directory"` com o caminho real no seu sistema onde seus arquivos estão localizados.

## Etapa 3: Carregue seu arquivo Excel

Agora, carregue o arquivo Excel a partir do qual você deseja criar o PDF.

```csharp
// Carregue o arquivo Excel de origem contendo imagens externas
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 O`Workbook` A classe do Aspose.Cells representa seu arquivo Excel, que pode incluir vários recursos externos, como imagens.

## Etapa 4: Defina as opções de salvamento de PDF

Antes de salvar a pasta de trabalho como PDF, especifique as opções de salvamento desejadas.

```csharp
// Especificar opções de salvamento de PDF - Provedor de fluxo
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Salve cada folha em uma nova página
};
```

 Isso cria uma instância de`PdfSaveOptions` , permitindo que você personalize o formato PDF. O`OnePagePerSheet` opção garante que cada planilha do Excel apareça em uma página separada no PDF final.

## Etapa 5: Atribua seu provedor de transmissão

 Conecte seu`Workbook` instância com o`MyStreamProvider` classe que você criou anteriormente.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Essa linha garante que sempre que recursos externos forem encontrados durante a conversão, seu provedor personalizado os gerenciará adequadamente.

## Etapa 6: Salve a pasta de trabalho como PDF

Agora, salve sua pasta de trabalho do Excel como um PDF.

```csharp
// Salvar a pasta de trabalho em PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Ao chamar o`Save` método no objeto de pasta de trabalho e passando o diretório de saída junto com as opções de PDF, você converte o arquivo Excel em um PDF bem formatado.

## Etapa 7: Confirme a execução bem-sucedida

Por fim, é uma boa prática confirmar se o processo foi concluído com sucesso.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Esta mensagem informará você sobre o status da sua operação, fornecendo um feedback útil.

## Conclusão

Agora você domina o processo de controle de recursos externos durante conversões de Excel para PDF usando Aspose.Cells! Seguindo essas etapas, você pode garantir que seus documentos incluam imagens e outros elementos externos com precisão, resultando em um produto final polido todas as vezes.

## Perguntas frequentes

### O que é Aspose.Cells?
Aspose.Cells é uma biblioteca poderosa para desenvolvedores .NET que permite a criação, manipulação, conversão e renderização de arquivos Excel em vários formatos.

### Como faço para baixar o Aspose.Cells?
 Você pode baixar a versão mais recente do[Link para download](https://releases.aspose.com/cells/net/).

### Posso testar o Aspose.Cells gratuitamente?
 Sim! Você pode acessar um teste gratuito visitando o[Página de teste grátis](https://releases.aspose.com/).

### Onde posso encontrar suporte para o Aspose.Cells?
 Para consultas relacionadas ao suporte, visite o[Fórum de suporte Aspose](https://forum.aspose.com/c/cells/9).

### Como posso obter uma licença temporária para o Aspose.Cells?
 Você pode solicitar uma licença temporária[aqui](https://purchase.aspose.com/temporary-license/).
