---
title: Renderizar uma vista panorâmica de uma cena 3D usando Aspose.3D para .NET
linktitle: Renderizar uma vista panorâmica de uma cena 3D
second_title: API Aspose.3D .NET
description: Aprenda como renderizar uma vista panorâmica impressionante de uma cena 3D em seus aplicativos .NET usando Aspose.3D. Siga nosso guia passo a passo para renderização de cena imersiva.
type: docs
weight: 13
url: /pt/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Introdução

Criar cenas 3D panorâmicas e imersivas é uma virada de jogo para desenvolvedores que buscam elevar seus aplicativos com efeitos visuais impressionantes. Não importa se você está trabalhando em um mecanismo de jogo, visualização arquitetônica ou experiências imersivas na web, renderizar cenas 3D como panoramas permite que os usuários experimentem uma visão dinâmica de todos os ângulos. O Aspose.3D para .NET é a ferramenta perfeita para integrar perfeitamente esse recurso em seus projetos .NET. Este guia abrangente o guiará pelo processo de renderização de um panorama de uma cena 3D usando o Aspose.3D para .NET.

## Pré-requisitos

Antes de mergulhar no processo de renderização, certifique-se de ter o seguinte em mãos:

- Aspose.3D para .NET: para começar, você precisa instalar o Aspose.3D, que fornece todas as ferramentas necessárias para manipular ativos 3D e renderização.[Baixe Aspose.3D para .NET](https://releases.aspose.com/3d/net/) para começar.
- Ambiente de desenvolvimento .NET: Um ambiente de desenvolvimento .NET totalmente configurado é necessário. Certifique-se de ter o Visual Studio ou qualquer outro IDE compatível.
-  Arquivo de cena 3D de amostra: você pode usar qualquer cena 3D em formatos como`.glb`, `.fbx` , ou`.obj`. Para este tutorial, usaremos um arquivo simples "VirtualCity.glb".

Depois de atender a esses pré-requisitos, podemos prosseguir para a configuração do cenário.

## Importar namespaces necessários

Para trabalhar com Aspose.3D, precisaremos importar vários namespaces para o nosso projeto. Esses namespaces permitem que você manipule objetos 3D, configurações de câmera e opções de renderização de forma eficiente.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Esses namespaces são essenciais para carregar a cena 3D, configurar a câmera, a iluminação e definir as texturas de renderização que formam a vista panorâmica.

## Etapa 1: carregue a cena 3D em seu aplicativo

 O primeiro passo é carregar a cena 3D em seu aplicativo. Isso pode ser feito usando o`Scene` classe fornecida por Aspose.3D. Substituir`"VirtualCity.glb"` com o caminho para seu arquivo de cena 3D.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 O`Scene` O objeto carrega a cena 3D na memória, permitindo que você interaja com ela e aplique técnicas de renderização.

## Etapa 2: Configurar a câmera e as luzes

Para garantir que sua cena 3D seja capturada corretamente, você precisará configurar uma câmera e iluminação apropriada. A câmera permite que você controle a perspectiva da cena, enquanto as luzes ajudam a iluminar os objetos.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Configuração da câmera: os planos próximo e distante da câmera são definidos para definir o alcance visível na cena 3D.
- Configuração de luz: Duas luzes são adicionadas — uma luz pontual e outra com uma cor específica para adicionar profundidade e realismo à cena.

## Etapa 3: Configurar o renderizador e definir os alvos de renderização

Agora que sua cena, câmera e luzes estão definidas, o próximo passo é criar o renderizador e definir os alvos de renderização. O renderizador é responsável por gerar as imagens 3D, e os alvos de renderização definem onde a saída final será armazenada.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Cube Render Texture: Isto é usado para renderizar um mapa de cubo para a vista panorâmica. Definimos uma textura 512x512 aqui.
- Textura de renderização final: esta é a textura que manterá a vista panorâmica equirretangular final.

## Etapa 4: Configurar a janela de visualização e renderizar a cena

Depois de criar as texturas de renderização, precisamos configurar a viewport, que define a região da cena 3D que a câmera irá capturar.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Este código define a janela de visualização para o mapa do cubo e renderiza a cena no`rt` renderizar textura.

## Etapa 5: Aplicar pós-processamento para projeção equirretangular

Neste ponto, precisamos aplicar pós-processamento para converter o mapa de cubo em uma vista panorâmica equirretangular. Essa transformação garante que a imagem final será um panorama adequado.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Projeção Equiretangular: Este efeito de pós-processamento pega o mapa do cubo e o transforma em uma projeção panorâmica equirretangular, proporcionando uma visão perfeita de 360 graus.

## Etapa 6: Salve o panorama renderizado

Depois que a renderização e o pós-processamento estiverem concluídos, a última etapa é salvar o panorama final em um arquivo de imagem, como um PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Isso salva a imagem panorâmica no diretório especificado, permitindo que você a integre ao seu aplicativo ou a exiba em um site.

## Conclusão

Renderizar vistas panorâmicas de cenas 3D nunca foi tão fácil com o Aspose.3D para .NET. Seguindo os passos descritos acima, você pode facilmente carregar uma cena 3D, configurar a câmera e as luzes, renderizar a cena e aplicar efeitos de pós-processamento para gerar imagens panorâmicas imersivas. O Aspose.3D para .NET fornece o poder e a flexibilidade para dar vida às suas visualizações 3D e integrá-las perfeitamente aos seus aplicativos.

## Perguntas frequentes

### Posso usar minha própria cena 3D para renderizar panoramas?
Absolutamente. Simplesmente substitua o caminho do arquivo de cena de amostra pelo local da sua cena 3D personalizada.

### Há algum efeito de pós-processamento adicional disponível?
Sim, o Aspose.3D oferece uma variedade de efeitos de pós-processamento, como profundidade de campo, bloom e muito mais, que podem ser aplicados para aprimorar suas imagens renderizadas.

### Como posso otimizar o desempenho da renderização?
desempenho da renderização pode ser otimizado ajustando parâmetros como o tamanho e a resolução da textura de renderização, além de ajustar os planos próximo e distante da câmera.

### Posso integrar isso em um aplicativo web?
Sim, o Aspose.3D para .NET pode ser integrado aos seus aplicativos web .NET para renderizar panoramas 3D dinamicamente.

### Existe um fórum da comunidade para suporte ao Aspose.3D?
 Sim, você pode visitar o[Fórum Aspose.3D](https://forum.aspose.com/c/3d/18) para suporte e discussões na comunidade.