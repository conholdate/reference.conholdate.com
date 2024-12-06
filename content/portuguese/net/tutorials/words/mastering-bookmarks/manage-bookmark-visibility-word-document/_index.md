---
title: Gerenciar a visibilidade dos marcadores em documentos do Word
linktitle: Gerenciar a visibilidade dos marcadores em documentos do Word
second_title: API de processamento de documentos Aspose.Words
description: Descubra como controlar habilmente a visibilidade do conteúdo em documentos do Word usando o Aspose.Words para .NET. Este guia passo a passo.
type: docs
weight: 10
url: /pt/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Introdução

Você está pronto para elevar suas habilidades de manipulação de documentos com o Aspose.Words para .NET? Seja você um desenvolvedor experiente que automatiza tarefas de documentos ou um indivíduo curioso que explora o controle programático sobre arquivos do Word, este guia é feito sob medida para você. Hoje, vamos nos aprofundar em como mostrar e ocultar conteúdo com base em marcadores em um documento do Word. Vamos começar!

## Pré-requisitos

Antes de começarmos, certifique-se de ter o seguinte:

1. Visual Studio: Qualquer versão compatível com .NET.
2.  Aspose.Words para .NET: Baixe-o[aqui](https://releases.aspose.com/words/net/).
3. Conhecimento básico de C#: familiaridade com a escrita de programas simples em C# será suficiente.
4. Um exemplo de documento do Word: prepare um documento do Word (por exemplo, "Bookmarks.docx") contendo marcadores para este tutorial.

### Criar um novo projeto

1. Abra o Visual Studio e crie um novo projeto Console App (.NET Core). Dê a ele um nome como "BookmarkVisibilityManager".

### Instalar Aspose.Words para .NET

Adicione Aspose.Words ao seu projeto por meio do Gerenciador de Pacotes NuGet:

1. Navegue até Ferramentas > Gerenciador de Pacotes NuGet > Gerenciar Pacotes NuGet para Solução.
2. Pesquise por "Aspose.Words".
3. Instale o pacote.

Com seu projeto configurado, vamos prosseguir para carregar o documento.

## Importando namespaces

Comece importando os namespaces essenciais. Eles fornecem as classes e métodos necessários para manipular documentos do Word com Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Etapa 1: Carregando o documento

Para manipular o documento do Word, precisamos carregá-lo primeiro. Veja como fazer isso:

```csharp
// Defina o caminho para o diretório do seu documento.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Este snippet define o caminho para o diretório do seu documento e carrega o documento em um`Document` objeto.

## Etapa 2: Mostrar/Ocultar conteúdo marcado

 Agora, vamos criar um método para alternar a visibilidade do conteúdo com base nos favoritos. Chamaremos esse método de`ShowHideBookmarkedContent`.

Aqui está a implementação do método:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Recuperação de favoritos:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` busca o marcador especificado.
- Percurso de nós: iteramos pelos nós dentro do marcador.
-  Alternância de visibilidade: para cada`Run` nó (representando um segmento de texto), definimos seu`Hidden` propriedade baseada em`isHidden` parâmetro.

## Etapa 3: Aplicando o método

Agora que temos nosso método pronto, vamos usá-lo para mostrar ou ocultar conteúdo dentro de um favorito específico:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Oculta conteúdo dentro de "MyBookmark1"
```

Esta linha ocultará o conteúdo associado ao marcador chamado "MyBookmark1".

## Etapa 4: Salvando o documento

Depois de fazer as alterações, não se esqueça de salvar o documento modificado:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Isso salva o documento com as configurações de visibilidade atualizadas.

## Conclusão

Parabéns! Você aprendeu com sucesso como mostrar e ocultar conteúdo marcado em um documento do Word usando o Aspose.Words para .NET. Esta biblioteca poderosa simplifica a manipulação de documentos, tornando-a ideal para automatizar relatórios, criar modelos ou experimentar arquivos do Word. Boa codificação!

## Perguntas frequentes

### Posso alternar vários favoritos de uma só vez?
 Sim, basta ligar para o`ShowHideBookmarkedContent` método para cada marcador que você deseja alternar.

### Ocultar conteúdo afeta a estrutura do documento?
Não, ocultar conteúdo afeta apenas sua visibilidade; o conteúdo permanece intacto dentro do documento.

### Posso usar esse método para outros tipos de conteúdo?
Este método é projetado especificamente para execuções de texto. Para outros tipos de conteúdo, você precisará adaptar a lógica de travessia de nó adequadamente.

### O Aspose.Words para .NET é gratuito?
 Aspose.Words oferece um teste gratuito[aqui](https://releases.aspose.com/) , mas uma licença completa é necessária para uso em produção. Você pode comprá-lo[aqui](https://purchase.aspose.com/buy).

### Como posso obter suporte se tiver problemas?
 Para obter suporte, visite o fórum da comunidade Aspose[aqui](https://forum.aspose.com/c/words/8).