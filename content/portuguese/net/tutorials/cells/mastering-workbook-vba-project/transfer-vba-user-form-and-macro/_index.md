---
title: Transferir formulários de usuário e macros do VBA entre pastas de trabalho do Excel
linktitle: Transferir formulários de usuário e macros do VBA entre pastas de trabalho do Excel
second_title: API de processamento do Aspose.Cells .NET Excel
description: Desbloqueie o poder da automação do Excel com este guia abrangente sobre transferência de Formulários de Usuário VBA e macros entre pastas de trabalho usando Aspose.Cells para .NET. Perfeito tanto para iniciantes quanto para desenvolvedores experientes.
type: docs
weight: 11
url: /pt/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Introdução

Bem-vindo ao seu guia definitivo para aprimorar sua experiência no Excel usando macros VBA e formulários de usuário! Neste tutorial, exploraremos como transferir um VBA Macro UserForm Designer de uma pasta de trabalho para outra usando a poderosa biblioteca Aspose.Cells for .NET. Seja você um desenvolvedor experiente ou apenas iniciante, este guia passo a passo o equipará com o conhecimento para lidar com arquivos do Excel programaticamente. Pronto para mergulhar? Vamos começar!

## Pré-requisitos
Antes de começarmos a codificar, vamos garantir que você tenha tudo o que precisa:

1. Ambiente de desenvolvimento C#: Um ambiente de trabalho para desenvolvimento C#, com o Visual Studio altamente recomendado.
2.  Biblioteca Aspose.Cells para .NET: Certifique-se de integrar a biblioteca Aspose.Cells em seu projeto. Você pode facilmente[baixe aqui](https://releases.aspose.com/cells/net/).
3. Conhecimento básico de VBA e macros do Excel: A familiaridade com o VBA e o funcionamento das macros do Excel melhorará sua compreensão deste tutorial.
4. Um arquivo Excel com um formulário de usuário: crie ou obtenha uma pasta de trabalho do Excel contendo um formulário de usuário (de preferência com macros habilitadas, como`.xlsm` arquivos).

## Importando Pacotes Necessários
Para utilizar as funcionalidades fornecidas pelo Aspose.Cells, inclua os seguintes namespaces no topo do seu arquivo C#:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Esses namespaces darão acesso às ferramentas poderosas incorporadas na biblioteca Aspose.Cells.

## Etapa 1: Defina seus diretórios de origem e saída
Primeiro, estabeleça os locais dos seus arquivos:

```csharp
// Defina os diretórios de origem e saída
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Substitua os caminhos do espaço reservado pelos diretórios reais onde seus arquivos estão armazenados.

## Etapa 2: Crie uma pasta de trabalho de destino vazia
Em seguida, crie uma nova pasta de trabalho onde você copiará o formulário do usuário e as macros:

```csharp
// Crie uma pasta de trabalho de destino vazia
Workbook target = new Workbook();
```

Isso inicializa uma pasta de trabalho em branco, servindo como tela para a próxima transferência de dados.

## Etapa 3: Carregue sua pasta de trabalho de modelo
Carregue a pasta de trabalho contendo seu formulário de usuário e macros:

```csharp
// Carregue o arquivo Excel contendo o formulário do usuário do VBA-Macro Designer
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Ajustar`"sampleDesignerForm.xlsm"` para o nome do seu arquivo atual.

## Etapa 4: Copie as planilhas para a pasta de trabalho de destino
Agora, vamos copiar as planilhas do modelo para a pasta de trabalho de destino:

```csharp
// Copie todas as planilhas de modelo para a pasta de trabalho de destino
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Adicione uma mensagem na célula A2 da planilha de destino
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Este código percorre cada planilha no modelo e as copia para a pasta de trabalho de destino, garantindo que todos os seus dados sejam transferidos sem problemas.

## Etapa 5: Copie as macros VBA do modelo
Em seguida, copiaremos as macros do VBA, incluindo os módulos do UserForm Designer, para a nova pasta de trabalho:

```csharp
// Copie o VBA-Macro Designer UserForm do Template para o Target
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Copie o código do módulo ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Copie o código e os dados de outros módulos
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Obtenha o armazenamento do designer de formulários do usuário
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Adicione o armazenamento do designer ao projeto Vba de destino
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Esse código garante que não apenas o código, mas também o design do formulário do usuário seja copiado, preservando a funcionalidade de suas macros.

## Etapa 6: Salve a pasta de trabalho de destino
Após concluir o processo de cópia, salve sua nova pasta de trabalho:

```csharp
// Salvar a pasta de trabalho de destino
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Modifique o nome do arquivo de saída conforme necessário. Esta etapa cria sua pasta de trabalho personalizada preenchida com macros e formulários de usuário.

## Etapa 7: Confirme o sucesso
Por fim, imprima uma mensagem de sucesso no console:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Esta linha simples garante que seu processo ocorreu sem problemas — uma confirmação essencial do seu trabalho duro!

## Conclusão
Parabéns! Você aprendeu com sucesso como copiar um VBA Macro User Form Designer de uma pasta de trabalho para outra usando o Aspose.Cells para .NET. Embora possa parecer assustador no começo, a prática o tornará proficiente em manipulações de pastas de trabalho. Lembre-se, codificação é sobre experimentação, então não hesite em explorar diferentes funcionalidades dentro de seus arquivos Excel. Se você tiver alguma dúvida ou precisar de assistência, os fóruns e a documentação do Aspose são excelentes recursos de suporte.

## Perguntas frequentes

### Quais versões do Excel o Aspose.Cells suporta?
Aspose.Cells suporta vários formatos do Excel, incluindo XLSX, XLSM, CSV e muito mais.

### Posso usar o Aspose.Cells gratuitamente?
 Sim! Você pode começar com um teste gratuito para avaliar a biblioteca:[Teste grátis](https://releases.aspose.com/).

### Preciso do Visual Studio para executar este código?
Embora o Visual Studio seja recomendado por seus recursos fáceis de usar, qualquer IDE C# que suporte desenvolvimento .NET será suficiente.

### Onde posso encontrar mais exemplos e documentação?
 Você pode explorar o[Documentação do Aspose.Cells](https://reference.aspose.com/cells/net/) para mais exemplos e explicações mais detalhadas.

### Como resolvo problemas ao usar o Aspose.Cells?
 Você deveria visitar o[Fórum de suporte Aspose](https://forum.aspose.com/c/cells/9) para obter ajuda da comunidade e da equipe de suporte da Aspose.