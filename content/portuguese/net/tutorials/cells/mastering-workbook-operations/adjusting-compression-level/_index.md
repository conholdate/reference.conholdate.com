---
title: Ajustando o nível de compressão na pasta de trabalho
linktitle: Ajustando o nível de compressão na pasta de trabalho
second_title: API de processamento do Aspose.Cells .NET Excel
description: Descubra como gerenciar arquivos grandes do Excel de forma eficiente ajustando os níveis de compactação usando o Aspose.Cells para .NET. Este guia passo a passo abrange tudo, desde a configuração de diretórios até a medição dos tempos de compactação, ajudando você a otimizar o tamanho do arquivo e melhorar o desempenho.
type: docs
weight: 14
url: /pt/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Introdução

Gerenciar arquivos grandes do Excel pode ser um desafio, especialmente quando se trata de eficiência de armazenamento e transferência. Felizmente, a compactação de arquivos pode reduzir significativamente o tamanho desses arquivos, tornando-os mais fáceis de manusear. Se você estiver usando o Aspose.Cells para .NET, você tem a capacidade de ajustar o nível de compactação de suas pastas de trabalho facilmente. Este guia o guiará pelo processo passo a passo, fornecendo explicações claras de cada parte do código.

## Pré-requisitos

Antes de mergulharmos no código, certifique-se de ter os seguintes pré-requisitos:

1. Conhecimento básico de C#: A familiaridade com a programação em C# ajudará você a entender melhor os trechos de código.
2.  Biblioteca Aspose.Cells: Baixe e instale a biblioteca Aspose.Cells de[aqui](https://releases.aspose.com/cells/net/).
3. Visual Studio: Um ambiente de desenvolvimento como o Visual Studio é necessário para executar o código.
4. .NET Framework: certifique-se de que seu projeto esteja configurado com uma versão compatível do .NET Framework.

## Importando Pacotes Necessários

Para começar, você precisa importar os pacotes necessários no seu projeto C#. Adicione as seguintes linhas no topo do seu arquivo de código:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Esses pacotes são essenciais para trabalhar com arquivos Excel usando a biblioteca Aspose.Cells. O`Aspose.Cells` namespace contém todas as classes necessárias para manipular arquivos Excel, enquanto`Aspose.Cells.Xlsb` fornece opções para salvar arquivos no formato XLSB.

## Etapa 1: Definir diretórios de origem e saída

Primeiro, configure os diretórios onde seus arquivos de origem estão localizados e onde você deseja salvar os arquivos de saída:

```csharp
// Definir diretórios de origem e saída
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Certifique-se de substituir`"Your Document Directory\\"` com os caminhos reais para seus diretórios. Isso garante que seu programa possa localizar os arquivos com os quais precisa trabalhar.

## Etapa 2: Carregue a pasta de trabalho

Em seguida, carregue a pasta de trabalho que você deseja compactar:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Aqui, criamos uma nova instância do`Workbook` class e carregue um arquivo Excel existente. Certifique-se de que o nome do arquivo corresponde ao do seu diretório de origem.

## Etapa 3: Configurar opções de salvamento

Agora, configure as opções de salvamento para sua pasta de trabalho:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 O`XlsbSaveOptions` classe permite que você especifique várias opções ao salvar sua pasta de trabalho no formato XLSB, incluindo níveis de compactação.

## Etapa 4: Meça o tempo de compressão para o nível 1

Comece com o primeiro nível de compactação e meça o tempo que leva para salvar a pasta de trabalho:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Este snippet define o tipo de compactação como Nível 1, salva a pasta de trabalho e mede o tempo decorrido.

## Etapa 5: Meça o tempo de compressão para o nível 6

Em seguida, teste o desempenho com compressão de nível 6:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Esta etapa é semelhante à anterior, mas com um nível de compressão mais alto.

## Etapa 6: Meça o tempo de compressão para o nível 9

Por fim, avalie o desempenho com o maior nível de compressão:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Esta etapa define o nível de compactação para o Nível 9, onde você provavelmente verá a redução mais significativa no tamanho do arquivo, embora possa levar mais tempo para processar.

## Etapa 7: Resultado final

Após concluir todos os níveis de compactação, emita uma mensagem indicando que o processo foi concluído com sucesso:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Esta linha simples confirma que seu programa foi executado sem problemas.

## Conclusão

Ajustar o nível de compactação de suas pastas de trabalho usando o Aspose.Cells for .NET é um processo simples que pode levar a melhorias significativas no tamanho e no desempenho do arquivo. Seguindo as etapas descritas neste guia, você pode implementar a compactação de forma eficiente em seus aplicativos, aprimorando seus recursos de gerenciamento de arquivos do Excel.

## Perguntas frequentes

### O que é Aspose.Cells?  
Aspose.Cells é uma biblioteca poderosa para .NET que permite aos desenvolvedores criar, manipular e converter arquivos do Excel sem precisar do Microsoft Excel.

### Como instalo o Aspose.Cells?  
 Você pode baixar e instalar o Aspose.Cells do[Site Aspose](https://releases.aspose.com/cells/net/).

### Quais níveis de compressão estão disponíveis?  
O Aspose.Cells suporta vários níveis de compactação, que vão do Nível 1 (menor compactação) ao Nível 9 (maior compactação).

### Posso testar o Aspose.Cells gratuitamente?  
 Sim! Você pode obter uma avaliação gratuita do Aspose.Cells[aqui](https://releases.aspose.com/).

### Onde posso encontrar suporte para o Aspose.Cells?  
 Para qualquer dúvida ou suporte, visite o fórum de suporte do Aspose[aqui](https://forum.aspose.com/c/cells/9).