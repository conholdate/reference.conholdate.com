---
title: Criando hiperlink local em arquivo PDF
linktitle: Criando hiperlink local em arquivo PDF
second_title: Referência da API do Aspose.PDF para .NET
description: Descubra como melhorar a navegação em seus documentos PDF criando hiperlinks locais usando o Aspose.PDF para .NET. Este tutorial passo a passo o guia por todo o processo.
type: docs
weight: 40
url: /pt/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Introdução

Neste guia, nós o guiaremos pelo processo de criação de hiperlinks locais em um arquivo PDF usando o Aspose.PDF para .NET. Nós detalharemos cada etapa claramente, garantindo que mesmo se você for novo na manipulação de PDF, você será capaz de acompanhar sem esforço.

## Pré-requisitos

Antes de mergulhar no código, certifique-se de ter o seguinte:

1.  Visual Studio: Baixe-o do[Site do Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.PDF para .NET: Baixe a biblioteca através do[Site Aspose](https://releases.aspose.com/pdf/net/). Esta biblioteca fornece um rico conjunto de recursos para manipulação de PDF.
3. Conhecimento básico de C#: Familiaridade com programação em C# ajudará, mas não se preocupe; explicaremos o código linha por linha.
4. .NET Framework: Certifique-se de ter o .NET Framework instalado em sua máquina. Verifique os requisitos no Aspose.PDF[documentação](https://reference.aspose.com/pdf/net/).

Com esses pré-requisitos em vigor, você está pronto para aprender a criar hiperlinks locais em seus documentos PDF!

## Importando Pacotes Necessários

Agora que tudo está configurado, é hora de importar os pacotes necessários para seu projeto C#.

### Abra seu projeto

Abra seu projeto .NET existente ou crie um novo no Visual Studio. Se estiver começando do zero, selecione “Create a new project” na tela de inicialização.

### Adicionar referência ao Aspose.PDF

 Clique com o botão direito em "Dependencies" na pasta do seu projeto no Solution Explorer. Selecione "Manage NuGet Packages", pesquise por`Aspose.PDF`, e instale a versão mais recente disponível. Isso trará todas as ferramentas que você precisa para criar e manipular PDFs.

### Importar namespaces

No topo do seu arquivo .cs, adicione as seguintes diretivas using:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Essas diretivas permitem que você acesse os recursos da biblioteca sem problemas.

Vamos dividir o processo de criação de hiperlinks locais em etapas simples.

## Etapa 1: Configurar instância do documento

 Crie uma nova instância do`Document` classe, representando o arquivo PDF com o qual você trabalhará.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Defina seu diretório de documentos
Document doc = new Document(); // Criar instância de documento
```

 Substituir`"YOUR_DOCUMENT_DIRECTORY"` com o caminho real no seu sistema onde o PDF será salvo.

## Etapa 2: Adicionar uma página ao documento

Em seguida, adicione uma página ao seu documento PDF.

```csharp
Page page = doc.Pages.Add(); // Adicionar uma nova página
```

Esta linha adiciona uma nova página ao documento, onde todo o seu conteúdo será colocado.

## Etapa 3: Crie um fragmento de texto

Agora, vamos criar um pedaço de texto que funcionará como um link clicável.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Crie um fragmento de texto
```

 Esse`TextFragment` exibirá o texto no qual os usuários podem clicar.

## Etapa 4: Criar hiperlink local

Agora, crie um hiperlink local que aponte para a página 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Crie um hiperlink local
link.TargetPageNumber = 7; // Defina a página de destino para o link
text.Hyperlink = link; // Defina o hiperlink para o fragmento de texto
```

 O`LocalHyperlink` A classe permite que você especifique o número da página de destino para o hiperlink.

## Etapa 5: adicione o fragmento de texto à página

Adicione o texto clicável à página que você criou.

```csharp
page.Paragraphs.Add(text); // Adicione o fragmento de texto à página
```

Esta linha adiciona seu texto ao conjunto de parágrafos da página.

## Etapa 6: Crie outro fragmento de texto (opcional)

Vamos adicionar outro hiperlink para navegar de volta à página 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Crie um novo fragmento de texto
textBack.IsInNewPage = true; // Indique que deve estar em uma nova página
```

## Etapa 7: Configurar o segundo hiperlink local

Crie outro hiperlink local para a página 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Crie outro hiperlink local
linkBack.TargetPageNumber = 1; // Definir página de destino para o segundo hiperlink
textBack.Hyperlink = linkBack; // Defina o hiperlink para o segundo fragmento de texto
```

## Etapa 8: Adicione o segundo fragmento de texto à nova página

Adicione o segundo fragmento de texto à sua página.

```csharp
Page newPage = doc.Pages.Add(); // Adicione uma nova página para o segundo link
newPage.Paragraphs.Add(textBack); // Adicione o fragmento de texto à nova página
```

## Etapa 9: Salve o documento

Por fim, salve seu documento.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Especificar nome do arquivo de saída
doc.Save(dataDir); // Salvar o documento atualizado
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Esta linha combina o caminho do seu diretório com o nome do arquivo e o`Save()` método salva seu documento.

## Conclusão

Criar hiperlinks locais em arquivos PDF usando o Aspose.PDF para .NET é um recurso prático que melhora a navegação e a experiência do usuário. Agora você tem o conhecimento para guiar seus leitores diretamente para as informações de que precisam, tornando seus PDFs mais interativos e fáceis de usar.

## Perguntas frequentes

### O que é Aspose.PDF para .NET?
Aspose.PDF para .NET é uma biblioteca que permite aos desenvolvedores criar, manipular e converter documentos PDF programaticamente usando o .NET framework.

### Posso criar hiperlinks para páginas da web externas?
Sim, o Aspose.PDF também suporta a criação de hiperlinks para URLs externas, além de hiperlinks locais dentro do PDF.

### Existe uma versão de avaliação gratuita do Aspose.PDF?
 Com certeza! Você pode acessar o teste gratuito no[Site Aspose](https://releases.aspose.com/).

### Quais linguagens de programação o Aspose suporta?
Aspose oferece bibliotecas para várias linguagens de programação, incluindo Java, C++, e Python, entre outros.

### Como obtenho suporte para produtos Aspose?
 Você pode buscar suporte através do[Fórum Aspose](https://forum.aspose.com/c/pdf/10).