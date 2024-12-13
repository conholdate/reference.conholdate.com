---
title: Copiar planilha entre pastas de trabalho do Excel usando Aspose.Cells
linktitle: Copiar planilha entre pastas de trabalho do Excel usando Aspose.Cells
second_title: API de processamento do Aspose.Cells .NET Excel
description: Aprenda como transferir dados perfeitamente entre planilhas do Excel em seus aplicativos .NET com o Aspose.Cells. Este tutorial abrangente o guia por cada etapa da cópia de planilhas.
type: docs
weight: 13
url: /pt/net/tutorials/cells/mastering-worksheet-value-operations/copy-worksheet-between-workbooks/
---
## Introdução

Transferir dados entre planilhas do Excel é uma tarefa comum em aplicativos .NET, especialmente para gerar relatórios ou gerenciar modelos. Felizmente, usar o Aspose.Cells para .NET torna esse processo direto e eficiente. Neste tutorial, guiaremos você pelas etapas para copiar uma planilha de uma planilha para outra, fornecendo a você um controle poderoso sobre seu gerenciamento de dados.

## Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas:

1.  Biblioteca Aspose.Cells para .NET: Baixe a biblioteca[aqui](https://releases.aspose.com/cells/net/).
2. Visual Studio ou IDE similar: você usará isso para escrever e executar seu código .NET.
3.  Licença Aspose: Para contornar as limitações de avaliação, você pode[solicite um teste gratuito](https://releases.aspose.com/) ou obter um[licença temporária](https://purchase.aspose.com/temporary-license/).

## Pacotes de importação

Comece importando os namespaces necessários para seu projeto:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Esses namespaces darão acesso às classes necessárias para manipular planilhas e pastas de trabalho do Excel de forma eficaz.

## Etapa 1: Defina o caminho do diretório

Primeiro, defina o diretório para armazenar suas planilhas do Excel. Isso simplificará o acesso aos arquivos mais tarde.

```csharp
// Defina o caminho para o diretório de documentos.
string dataDir = "Your Document Directory";
```
 Substituir`"Your Document Directory"` com seu caminho atual.

## Etapa 2: Crie a primeira pasta de trabalho

Vamos criar uma nova pasta de trabalho e adicionar uma planilha a ela.

```csharp
// Crie uma nova pasta de trabalho.
Workbook excelWorkbook0 = new Workbook();
// Acesse a primeira planilha na pasta de trabalho.
Worksheet ws0 = excelWorkbook0.Worksheets[0];
```

## Etapa 3: Adicionar dados de cabeçalho

Preencha a planilha com linhas de cabeçalho para representar seu conjunto de dados claramente.

```csharp
// Preencha as linhas de cabeçalho (A1:A4).
for (int i = 0; i < 5; i++)
{
    ws0.Cells[i, 0].PutValue($"Header Row {i}");
}
```

## Etapa 4: preencher linhas de dados detalhados

Adicione conteúdo detalhado para fornecer contexto para sua planilha.

```csharp
// Preencha linhas de detalhes (A5:A999).
for (int i = 5; i < 1000; i++)
{
    ws0.Cells[i, 0].PutValue($"Detail Row {i}");
}
```

## Etapa 5: Configurar a configuração de impressão

Defina a configuração da página para repetir linhas de cabeçalho em páginas impressas, o que é especialmente útil para relatórios grandes.

```csharp
// Configure a configuração da página para repetir linhas de cabeçalho em cada página.
PageSetup pageSetup = ws0.PageSetup;
pageSetup.PrintTitleRows = "$1:$5";
```

## Etapa 6: Crie a segunda pasta de trabalho

Em seguida, crie a segunda pasta de trabalho que receberá a planilha copiada.

```csharp
// Crie outra pasta de trabalho.
Workbook excelWorkbook1 = new Workbook();
// Acesse a primeira planilha na pasta de trabalho.
Worksheet ws1 = excelWorkbook1.Worksheets[0];
```

## Etapa 7: renomeie a planilha de destino

Renomeie a planilha na segunda pasta de trabalho para facilitar a identificação.

```csharp
// Renomeie a planilha.
ws1.Name = "MySheet";
```

## Etapa 8: Copie os dados para a planilha de destino

 Utilize o`Copy` método para transferir a planilha inteira da primeira pasta de trabalho para a segunda.

```csharp
//Copie os dados da primeira planilha da primeira pasta de trabalho para a primeira planilha da segunda pasta de trabalho.
ws1.Copy(ws0);
```

## Etapa 9: Salve a pasta de trabalho final

Por fim, salve a pasta de trabalho modificada.

```csharp
// Salve a segunda pasta de trabalho.
excelWorkbook1.Save(dataDir + "CopyWorksheetFromWorkbookToOther_out.xls");
```

## Conclusão

E aí está! Você pode facilmente copiar uma planilha de uma pasta de trabalho para outra usando o Aspose.Cells for .NET. Este método é ideal para grandes conjuntos de dados, criação de modelos e geração de relatórios. 

## Perguntas frequentes

### Posso copiar várias planilhas de uma vez?  
Sim, você pode iterar por várias planilhas e copiá-las individualmente para outra pasta de trabalho.

### O Aspose.Cells mantém a formatação durante a cópia?  
 Absolutamente! O`Copy` O método preserva toda a formatação e estilos.

### Como posso acessar células específicas na planilha copiada?  
 Você pode acessar células específicas usando o`Cells` propriedade dentro da planilha.

### E se eu quiser apenas copiar valores sem formatação?  
Você pode implementar um método personalizado para copiar valores célula por célula, se preferir.

### Posso testar esse recurso sem uma licença?  
 Sim, a Aspose oferece uma[teste gratuito](https://releases.aspose.com/) para explorar suas características.