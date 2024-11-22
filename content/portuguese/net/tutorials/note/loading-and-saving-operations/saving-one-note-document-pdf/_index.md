---
title: Salvando documentos do OneNote em PDF usando Aspose.Note para .NET
linktitle: Salvando documentos do OneNote em PDF
second_title: API Aspose.Note .NET
description: Aprenda como salvar documentos do Microsoft OneNote como arquivos PDF de forma eficiente usando o Aspose.Note para .NET. Este guia orienta você pelos pré-requisitos necessários e oferece FAQs úteis.
type: docs
weight: 26
url: /pt/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Introdução

Neste tutorial, exploraremos como salvar documentos em formato PDF usando o Aspose.Note para .NET. O Aspose.Note é uma biblioteca poderosa que permite que os desenvolvedores trabalhem com arquivos do Microsoft OneNote programaticamente. Abordaremos os pré-requisitos, importaremos namespaces e forneceremos guias passo a passo para salvar documentos em PDF em vários layouts de página.

## Pré-requisitos
1. Visual Studio: verifique se ele está instalado.
2. Aspose.Note para .NET: Baixe e instale a biblioteca.
3. Conhecimento em C#: É necessário conhecimento básico da linguagem.

## Importando namespaces necessários
Antes de prosseguir, importe os seguintes namespaces no seu código:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Etapa 1: Salvar em PDF com as configurações da página da carta
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Atualizar este caminho
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Carrega o documento do OneNote e o salva como PDF usando as configurações de página tamanho carta.

## Etapa 2: Salvar em PDF com configurações de página A4 (sem limite de altura)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Atualizar este caminho
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Semelhante à Etapa 1, mas usa configurações de página A4 sem limitações de altura.

## Conclusão
O tutorial demonstra com sucesso como converter arquivos do OneNote para o formato PDF usando o Aspose.Note. Ao utilizar diferentes configurações de página, os desenvolvedores ganham flexibilidade no gerenciamento de documentos.

## Perguntas frequentes
### O Aspose.Note pode manipular arquivos complexos do OneNote?
Sim, ele lida efetivamente com vários recursos de arquivos complexos do OneNote.

### O Aspose.Note é adequado para projetos comerciais?
Sim, você pode usá-lo para aplicações comerciais após comprar uma licença.

### O Aspose.Note oferece um teste gratuito?
Sim, uma avaliação gratuita está disponível para exploração.

### Onde posso encontrar documentação para o Aspose.Note?
A documentação detalhada está disponível no site de referência do Aspose.

### Precisa de mais ajuda?
Para dúvidas e suporte, consulte o fórum Aspose.Note.
