---
title: Adicionar um índice a um documento PDF
linktitle: Adicionar um índice a um documento PDF
second_title: Referência da API do Aspose.PDF para .NET
description: Este tutorial demonstra como adicionar um Índice (TOC) a um documento PDF usando o Aspose.Pdf para .NET.
type: docs
weight: 40
url: /pt/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Introdução

Criar um índice (TOC) em um documento PDF pode melhorar muito sua navegação e acessibilidade. Neste guia, demonstraremos como adicionar um TOC a um arquivo PDF usando Aspose.Pdf para .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1.   Aspose.PDF para .NET: Baixe e instale a versão mais recente de[aqui](https://releases.aspose.com/pdf/net/).
2.  Ambiente de desenvolvimento: configure um ambiente de desenvolvimento .NET como o Visual Studio.
3.   Licença: Solicite uma licença temporária, se necessário; visite[Página de licenciamento Aspose.Pdf](https://asposepdf.com/developers) para maiores informações.

Importando bibliotecas necessárias

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Etapa 1: Carregue o documento PDF

Carregue seu arquivo PDF existente onde você deseja adicionar o TOC. Especifique o caminho para seu diretório de documentos.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Etapa 2: Insira uma nova página para o TOC

Insira uma nova página no início do documento PDF. Esta página servirá como Índice (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Etapa 3: Crie um objeto de informação do TOC

Crie um objeto que representará as informações do TOC. Adicione um título e um link para ele para melhor navegação.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Etapa 4: Definir elementos do TOC

Defina os elementos (ou títulos) que serão exibidos no TOC. Esses elementos podem ajudar os leitores a navegar para seções específicas do documento.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Etapa 5: Criar títulos de TOC

Crie títulos para os dois primeiros elementos no TOC. Esses títulos serão vinculados às suas respectivas páginas.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Etapa 6: Salve o PDF com o TOC

Por fim, salve o arquivo PDF atualizado.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Mensagem de confirmação

Exiba uma mensagem de confirmação para informar ao usuário que o processo foi concluído.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Conclusão

Com o Aspose.PDF para .NET, adicionar um Índice a um PDF não é apenas fácil, mas também personalizável. Se você precisa criar links de navegação simples ou estruturas complexas, esta ferramenta tem tudo o que você precisa. Então, da próxima vez que estiver trabalhando em um PDF longo, não se esqueça de adicionar um TOC para aquele toque profissional.

## Perguntas frequentes

### Posso personalizar a aparência do TOC no Aspose.PDF?

Sim, você pode personalizar totalmente a aparência do índice, incluindo estilo, tamanho e alinhamento da fonte.

### Como adiciono subtítulos ao índice?

 Você pode adicionar subtítulos ajustando o`Heading` nível (por exemplo,`Heading(2)`).

### É possível atualizar o TOC automaticamente se o documento for alterado?

Não, o TOC não será atualizado automaticamente. Você precisará recriá-lo se a estrutura do documento mudar.

### Posso vincular entradas do TOC a documentos externos?

Sim, você pode usar hiperlinks para vincular entradas do índice a PDFs ou URLs externos.

### O Aspose.PDF suporta TOCs multinível?

Sim, o Aspose.PDF suporta TOCs multinível para documentos complexos com subseções.
