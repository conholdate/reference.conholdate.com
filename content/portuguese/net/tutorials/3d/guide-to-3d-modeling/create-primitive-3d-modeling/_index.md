---
title: Crie modelagem 3D primitiva
linktitle: Crie modelagem 3D primitiva
second_title: API Aspose.3D .NET
description: Aprenda a criar e personalizar modelos 3D primitivos, incluindo caixas e cilindros, e salve-os no formato FBX sem esforço.
type: docs
weight: 10
url: /pt/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Introdução

Bem-vindo ao mundo imersivo da modelagem 3D usando Aspose.3D para .NET! Neste tutorial abrangente, nós o guiaremos pelo processo de criação de modelos 3D primitivos passo a passo. Seja você um desenvolvedor experiente ou um iniciante ansioso para aprender, este guia o capacitará a criar elementos 3D visualmente impressionantes para seus projetos.

## Pré-requisitos

Antes de mergulhar na modelagem 3D, certifique-se de ter os seguintes pré-requisitos:

-  Aspose.3D para .NET: Baixe e instale a biblioteca Aspose.3D para .NET do[página de download](https://releases.aspose.com/3d/net/).
  
- Ambiente de desenvolvimento .NET: configure um ambiente compatível com o Aspose.3D, como o Visual Studio.

Com tudo preparado, vamos embarcar em nossa aventura de modelagem 3D!

## Importando namespaces necessários

Comece importando os namespaces necessários para acessar as funcionalidades do Aspose.3D:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Esses namespaces fornecerão as ferramentas necessárias para manipular modelos 3D e salvar suas criações.

## Etapa 1: inicializar um objeto de cena

Crie um novo objeto de cena que atue como tela para seus modelos 3D:

```csharp
// Inicializar um objeto Scene
Scene scene = new Scene();
```

Esta cena conterá as formas primitivas que você está prestes a criar.

## Etapa 2: Crie um modelo de caixa

Em seguida, vamos adicionar um modelo de caixa à sua cena:

```csharp
// Criar um modelo de caixa
scene.RootNode.CreateChildNode("box", new Box());
```

Você pode personalizar as dimensões e propriedades da caixa para adaptá-la à sua visão criativa.

## Etapa 3: Crie um modelo de cilindro

Agora, melhore sua cena adicionando um cilindro:

```csharp
// Crie um modelo de cilindro
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Assim como na caixa, sinta-se à vontade para ajustar os parâmetros do cilindro para obter a aparência desejada.

## Etapa 4: Salve a cena no formato FBX

Para preservar seu modelo 3D, salve-o no formato FBX:

```csharp
// Salvar desenho no formato FBX
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Certifique-se de escolher um diretório de saída e um nome de arquivo apropriados para seu modelo.

## Etapa 5: Exibir uma mensagem de sucesso

Por fim, comemore seu sucesso exibindo uma mensagem:

```csharp
// Exibir mensagem de sucesso
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Sua cena 3D composta de modelos primitivos agora está completa e salva!

## Conclusão

 Parabéns por criar modelos 3D impressionantes usando Aspose.3D para .NET! Este tutorial cobriu os fundamentos da modelagem primitiva, mas as possibilidades são infinitas. Explore mais sobre recursos e técnicas avançadas no[documentação](https://reference.aspose.com/3d/net/).

## Perguntas frequentes

### Posso usar o Aspose.3D para .NET com linguagens de programação diferentes do .NET?

O Aspose.3D suporta principalmente .NET, mas há versões disponíveis para Java e outras plataformas.

### Há um teste gratuito disponível?

 Sim, você pode experimentar os recursos do Aspose.3D com um[teste gratuito](https://releases.aspose.com/).

### Onde posso encontrar suporte para o Aspose.3D para .NET?

 Para obter suporte da comunidade, visite o[Fórum Aspose.3D](https://forum.aspose.com/c/3d/18).

### Como posso obter uma licença temporária?

 Você pode solicitar uma licença temporária[aqui](https://purchase.conholdate.com/temporary-license/).

### Há tutoriais adicionais disponíveis?

 Sim! Explore mais tutoriais e exemplos no[documentação](https://reference.aspose.com/3d/net/).