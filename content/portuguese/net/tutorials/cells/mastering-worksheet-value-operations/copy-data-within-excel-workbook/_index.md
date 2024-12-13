---
title: Copiar dados dentro da pasta de trabalho do Excel usando Aspose.Cells para .NET
linktitle: Copiar dados dentro da pasta de trabalho do Excel usando Aspose.Cells para .NET
second_title: API de processamento do Aspose.Cells .NET Excel
description: Aprenda como copiar dados de forma eficiente dentro de uma pasta de trabalho do Excel usando o Aspose.Cells for .NET. Siga este guia passo a passo para duplicar planilhas, transferir dados e gerenciar arquivos do Excel com facilidade.
type: docs
weight: 12
url: /pt/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Introdução

Neste guia detalhado, demonstraremos como copiar dados dentro da mesma pasta de trabalho usando o Aspose.Cells for .NET. Seguindo as instruções passo a passo descritas abaixo, você aprenderá como duplicar planilhas programaticamente, preservando seus conteúdos e formatação.

## Pré-requisitos para copiar dados no Excel com Aspose.Cells

Antes de mergulhar no processo de codificação, vamos garantir que você tenha tudo pronto:

1. Biblioteca Aspose.Cells para .NET: Você precisa ter a biblioteca Aspose.Cells para .NET instalada. Você pode baixar a versão mais recente do[Página de download do Aspose.Cells para .NET](https://releases.aspose.com/cells/net/).
2. Ambiente de desenvolvimento: Um IDE compatível com .NET, como o Visual Studio, é necessário para escrever e executar seu código.
3.  Licença Aspose: Você pode usar uma avaliação gratuita ou uma licença comprada. Para mais informações, visite[aqui](https://purchase.aspose.com/temporary-license/).

Depois que os pré-requisitos forem definidos, você estará pronto para começar a trabalhar com a biblioteca.

## Importando Pacotes Necessários

Para começar, você precisará importar os namespaces relevantes do Aspose.Cells. Isso permite que você trabalhe com arquivos do Excel usando as classes e métodos fornecidos pelo Aspose.Cells.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Esses namespaces darão a você acesso ao`Workbook` classe (para trabalhar com arquivos Excel) e`WorksheetCollection` (para acessar várias planilhas dentro de uma pasta de trabalho).

## Etapa 1: inicializar caminhos de arquivo para pasta de trabalho

Para manter seu código organizado, é essencial definir os caminhos de arquivo onde sua pasta de trabalho está localizada e onde você pretende salvar o arquivo modificado. Veja como você pode especificar os caminhos:

```csharp
// Defina o caminho do diretório onde o arquivo Excel está localizado.
string dataDir = "Your Directory Path";

// Defina o caminho completo para a pasta de trabalho de entrada.
string inputPath = dataDir + "book1.xls";
```

 Substituir`"Your Directory Path"` com o caminho real para seu diretório contendo a pasta de trabalho. Isso ajuda a garantir que o código seja flexível e que você possa gerenciar caminhos de forma eficaz.

## Etapa 2: Abra a pasta de trabalho para acessar os dados

 Agora que os caminhos dos arquivos estão definidos, a próxima etapa é carregar a pasta de trabalho do Excel em um`Workbook` objeto. Isso permite que você acesse seu conteúdo para manipulação.

```csharp
// Carregue o arquivo Excel no objeto Pasta de Trabalho.
Workbook wb = new Workbook(inputPath);
```

 Com esta linha, você carregou com sucesso`book1.xls` para dentro do`wb` objeto, tornando seus dados acessíveis.

## Etapa 3: Acesse a coleção de planilhas

 Depois que a pasta de trabalho for carregada, você poderá acessar as planilhas contidas nela. Aspose.Cells fornece o`Worksheets`coleção, que permite que você interaja com cada planilha na pasta de trabalho.

```csharp
// Recupere a coleção de planilhas da pasta de trabalho.
WorksheetCollection sheets = wb.Worksheets;
```

 O`sheets` objeto agora dá acesso a todas as planilhas dentro`book1.xls`, e você pode executar várias operações nelas, incluindo copiar dados de uma planilha para outra.

## Etapa 4: Copie dados de uma planilha para outra

 Para copiar dados de uma planilha para outra dentro da mesma pasta de trabalho, o Aspose.Cells oferece um método fácil de usar chamado`AddCopy`. Este método cria uma duplicata da planilha especificada e a anexa à pasta de trabalho.

```csharp
// Copie dados da "Planilha1" para uma nova planilha dentro da pasta de trabalho.
sheets.AddCopy("Sheet1");
```

 Neste exemplo, estamos copiando dados de "Sheet1" para uma nova planilha. O`AddCopy` O método duplicará a planilha inteira, preservando todo o seu conteúdo, incluindo fórmulas, formatação e valores.

## Etapa 5: Salve a pasta de trabalho modificada

 Após copiar os dados, você pode salvar a pasta de trabalho modificada com um novo nome ou local. Isso é feito chamando o comando`Save`método sobre o`Workbook` objeto.

```csharp
//Salve a pasta de trabalho modificada com um novo nome.
wb.Save(dataDir + "book1_copy.xls");
```

 Isso salvará a pasta de trabalho com a planilha copiada como`book1_copy.xls` no diretório especificado. Você pode alterar o nome do arquivo e o caminho de acordo com suas necessidades.

## Conclusão

Copiar dados dentro de uma pasta de trabalho do Excel usando o Aspose.Cells para .NET é uma tarefa fácil, e este guia fornece as etapas necessárias para fazê-lo de forma eficiente. Não importa se você está duplicando planilhas inteiras ou intervalos de dados específicos, o Aspose.Cells oferece uma API robusta e flexível que torna a automação do Excel simples e eficaz.

## Perguntas frequentes

### Posso copiar várias planilhas de uma vez?

O Aspose.Cells não suporta copiar várias planilhas em uma única chamada. No entanto, você pode fazer um loop pelas planilhas que deseja copiar e copiá-las individualmente.

### Como posso renomear a planilha copiada?

Depois de copiar a planilha, você pode renomeá-la da seguinte maneira:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### O Aspose.Cells é compatível com o .NET Core?

Sim, o Aspose.Cells é totalmente compatível com os ambientes .NET Framework e .NET Core.

### Como o Aspose.Cells lida com a formatação durante a cópia?

 O`AddCopy` método preserva todo o conteúdo e formatação ao copiar planilhas, garantindo que os dados copiados sejam idênticos aos originais.

### Posso copiar uma planilha para uma pasta de trabalho diferente?

 Sim, você pode copiar uma planilha para uma pasta de trabalho diferente usando o`Copy` método com uma referência à pasta de trabalho de destino.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```