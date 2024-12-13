---
title: Encontre o máximo de linhas e colunas nos formatos XLS e XLSX
linktitle: Encontre o máximo de linhas e colunas nos formatos XLS e XLSX
second_title: API de processamento do Aspose.Cells .NET Excel
description: Descubra como gerenciar com eficiência grandes conjuntos de dados no Excel utilizando a biblioteca Aspose.Cells for .NET. Este guia fornece uma abordagem passo a passo para identificar o número máximo de linhas e colunas suportadas pelos formatos de arquivo XLS e XLSX.
type: docs
weight: 11
url: /pt/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Introdução

Gerenciar grandes conjuntos de dados no Excel pode ser desafiador, especialmente em relação aos limites de vários formatos de arquivo. Este tutorial o guiará pelo uso da biblioteca Aspose.Cells for .NET para determinar o número máximo de linhas e colunas suportadas pelos formatos XLS (Excel 97-2003) e XLSX (Excel 2007 e posterior). No final, você estará equipado para lidar com tarefas relacionadas ao Excel de forma eficiente.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1. [Estrutura .NET](https://dotnet.microsoft.com/en-us/download) ou[.NET Núcleo](https://dotnet.microsoft.com/en-us/download) instalado no seu sistema.
2. [Aspose.Cells para .NET](https://releases.aspose.com/cells/net/) biblioteca baixada e referenciada em seu projeto (você também pode instalá-la via[NuGet](https://www.nuget.org/packages/Aspose.Cells/)).

## Importando Pacotes Necessários

Adicione as seguintes instruções using no topo do seu arquivo C# para importar os pacotes necessários da biblioteca Aspose.Cells:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Etapa 1: Máximo de linhas e colunas para o formato XLS

Vamos começar encontrando o máximo de linhas e colunas suportadas pelo formato XLS.

```csharp
// Imprimir mensagem sobre o formato XLS.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Crie uma pasta de trabalho no formato XLS.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Recuperar o máximo de linhas e colunas.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Exibir os resultados.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Imprima uma mensagem para indicar que estamos trabalhando com o formato XLS.
2.  Criar um`Workbook` instância para o formato XLS usando`FileFormatType.Excel97To2003`.
3.  Obtenha o máximo de linhas e colunas com`wb.Settings.MaxRow` e`wb.Settings.MaxColumn`, adicionando 1, pois são de base zero.
4. Exibe o máximo de linhas e colunas no console.

## Etapa 2: Máximo de linhas e colunas para o formato XLSX

A seguir, exploraremos o número máximo de linhas e colunas suportadas pelo formato XLSX.

```csharp
// Imprimir mensagem sobre o formato XLSX.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Crie uma pasta de trabalho no formato XLSX.
wb = new Workbook(FileFormatType.Xlsx);

// Recuperar o máximo de linhas e colunas.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Exibir os resultados.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Imprima uma mensagem indicando que estamos trabalhando com o formato XLSX.
2.  Criar um`Workbook` instância para o formato XLSX usando`FileFormatType.Xlsx`.
3. Recupere e produza o máximo de linhas e colunas como antes.

## Etapa 3: Exibindo uma mensagem de sucesso

Após executar os passos, vamos indicar sucesso.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Conclusão

Neste tutorial, você aprendeu a usar a biblioteca Aspose.Cells for .NET para encontrar o máximo de linhas e colunas suportadas pelos formatos de arquivo XLS e XLSX. Entender esses limites é essencial para o gerenciamento eficaz de dados do Excel, garantindo que seus conjuntos de dados estejam alinhados com os recursos do formato.

## Perguntas frequentes

### Qual é o número máximo de linhas suportadas pelo formato XLS?
O número máximo de linhas suportadas pelo formato XLS é 65.536.

### Qual é o número máximo de colunas suportadas pelo formato XLS?
O número máximo de colunas suportadas pelo formato XLS é 256.

### Qual é o número máximo de linhas suportadas pelo formato XLSX?
O número máximo de linhas suportadas pelo formato XLSX é 1.048.576.

### Qual é o número máximo de colunas suportadas pelo formato XLSX?
número máximo de colunas suportadas pelo formato XLSX é 16.384.

### Posso usar a biblioteca Aspose.Cells para .NET com outros formatos de arquivo do Excel?
 Sim, o Aspose.Cells for .NET suporta vários formatos de arquivo, incluindo XLS, XLSX, ODS e mais. Verifique o[documentação](https://reference.aspose.com/cells/net/) para obter detalhes sobre recursos e funcionalidades suportados.