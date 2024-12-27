---
title: Listas numeradas elegantes usando Aspose.PDF para .NET
linktitle: Listas numeradas elegantes usando Aspose.PDF para .NET
second_title: Referência da API do Aspose.PDF para .NET
description: Descubra como criar listas lindamente numeradas em seus documentos PDF com Aspose.PDF para .NET. Este guia o orienta no processo de aplicação de vários estilos de numeração — como algarismos romanos.
type: docs
weight: 10
url: /pt/net/programming-with-headings/stylish-numbered-lists/
---
## Introdução

Você já precisou criar listas bem estruturadas e numeradas em seus documentos PDF? Seja para documentos jurídicos, relatórios ou apresentações, estilos de numeração eficazes são cruciais para organizar seu conteúdo. Com o Aspose.PDF para .NET, você pode facilmente aplicar vários estilos de numeração aos seus títulos de PDF, resultando em documentos polidos e profissionais.

## Pré-requisitos

Antes de começarmos a codificação, certifique-se de ter o seguinte pronto:

1.  Aspose.PDF para .NET: Baixe a versão mais recente em[aqui](https://releases.aspose.com/pdf/net/).
2. Ambiente de desenvolvimento: você precisará do Visual Studio ou qualquer IDE compatível com .NET.
3. .NET Framework: certifique-se de ter o .NET Framework 4.0 ou superior instalado.
4.  Licença: Você pode usar uma licença temporária de[aqui](https://purchase.aspose.com/temporary-license/) ou explorar o[teste gratuito](https://releases.aspose.com/) opções.

## Importando Pacotes Necessários

Comece importando os namespaces necessários no seu projeto:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Etapa 1: Configurando o documento

Vamos começar criando um novo documento PDF e configurando seu layout, incluindo tamanho de página e margens.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Definir dimensões e margens da página
pdfDoc.PageInfo.Width = 612.0; // 8,5 polegadas
pdfDoc.PageInfo.Height = 792.0; // 11 polegadas
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // Margens de 1 polegada
```

Essa configuração dá ao seu documento um tamanho de carta padrão com margens de uma polegada em todos os lados.

## Etapa 2: Adicionar uma página ao PDF

Em seguida, adicionaremos uma página em branco ao documento PDF, onde posteriormente aplicaremos os estilos de numeração.

```csharp
// Adicionar uma nova página ao documento PDF
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; // Use as mesmas configurações do documento
```

## Etapa 3: Criando uma caixa flutuante

Um FloatingBox permite que você posicione o conteúdo independentemente do fluxo da página, dando a você maior controle sobre seu layout.

```csharp
//Crie um FloatingBox para conteúdo estruturado
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Etapa 4: Adicionar títulos com algarismos romanos

Agora, vamos adicionar nosso primeiro título com numeração em algarismos romanos minúsculos.

```csharp
// Crie o primeiro título com algarismos romanos
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Etapa 5: Adicionar um segundo título com número inicial personalizado

Em seguida, adicionaremos um segundo título, começando pelo numeral romano 13.

```csharp
// Crie um segundo título começando no numeral romano 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Etapa 6: Adicionar um título com numeração alfabética

Para variar, vamos adicionar um terceiro título usando numeração alfabética em letras minúsculas.

```csharp
// Crie um título com numeração alfabética
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Etapa 7: Salvando o PDF

Por fim, vamos salvar o arquivo PDF no diretório desejado.

```csharp
// Salvar o documento PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Conclusão

Parabéns! Você aplicou com sucesso vários estilos de numeração — algarismos romanos e alfabéticos — a títulos em um arquivo PDF usando o Aspose.PDF para .NET. A flexibilidade do Aspose.PDF permite que você controle o layout da página, os estilos de numeração e o posicionamento do conteúdo, capacitando você a criar documentos PDF bem organizados e profissionais.

## Perguntas frequentes

### Posso aplicar diferentes estilos numéricos ao mesmo documento PDF?  
Sim, você pode misturar diferentes estilos de numeração, como algarismos romanos, algarismos arábicos e numeração alfabética no mesmo documento.

### Como posso personalizar o número inicial dos títulos?  
 Você pode definir o número inicial para qualquer título usando o`StartNumber` propriedade.

### Existe uma maneira de redefinir a sequência de numeração?  
 Sim, você pode redefinir a numeração ajustando o`StartNumber` propriedade para cada título.

### Posso aplicar estilo negrito ou itálico aos títulos, além da numeração?  
 Absolutamente! Você pode personalizar os estilos de título modificando propriedades como fonte, tamanho, negrito e itálico usando o`TextState` objeto.

### Como obtenho uma licença temporária para o Aspose.PDF?  
 Você pode obter uma licença temporária em[aqui](https://purchase.aspose.com/temporary-license/)para testar o Aspose.PDF sem restrições.