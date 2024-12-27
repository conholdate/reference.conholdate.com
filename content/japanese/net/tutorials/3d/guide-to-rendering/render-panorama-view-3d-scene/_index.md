---
title: Aspose.3D for .NET を使用して 3D シーンのパノラマ ビューをレンダリングする
linktitle: 3Dシーンのパノラマビューをレンダリングする
second_title: Aspose.3D .NET API
description: Aspose.3D を使用して、.NET アプリケーションで 3D シーンの見事なパノラマ ビューをレンダリングする方法を学びます。没入型シーンのレンダリングについては、ステップ バイ ステップ ガイドに従ってください。
type: docs
weight: 13
url: /ja/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## 導入

没入型のパノラマ 3D シーンの作成は、魅力的な視覚効果でアプリケーションを向上させたい開発者にとって画期的なことです。ゲーム エンジン、建築の視覚化、没入型の Web エクスペリエンスのいずれに取り組んでいる場合でも、3D シーンをパノラマとしてレンダリングすると、ユーザーはあらゆる角度からダイナミックなビューを体験できます。Aspose.3D for .NET は、この機能を .NET プロジェクトにシームレスに統合するのに最適なツールです。この包括的なガイドでは、Aspose.3D for .NET を使用して 3D シーンからパノラマをレンダリングするプロセスを順を追って説明します。

## 前提条件

レンダリング プロセスに進む前に、次のものが準備されていることを確認してください。

- Aspose.3D for .NET: まず、3D アセットの処理とレンダリングに必要なすべてのツールを提供する Aspose.3D をインストールする必要があります。[Aspose.3D for .NET をダウンロード](https://releases.aspose.com/3d/net/)始めましょう。
- .NET 開発環境: 完全に構成された .NET 開発環境が必要です。Visual Studio またはその他の互換性のある IDE があることを確認してください。
- サンプル3Dシーンファイル: 次のような形式の3Dシーンを使用できます。`.glb`, `.fbx` 、 または`.obj`このチュートリアルでは、単純な「VirtualCity.glb」ファイルを使用します。

これらの前提条件を満たしたら、シーンの設定に進むことができます。

## 必要な名前空間をインポートする

Aspose.3D を使用するには、プロジェクトにいくつかの名前空間をインポートする必要があります。これらの名前空間を使用すると、3D オブジェクト、カメラ設定、レンダリング オプションを効率的に操作できます。

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

これらの名前空間は、3D シーンの読み込み、カメラや照明の構成、パノラマ ビューを形成するレンダリング テクスチャの設定に不可欠です。

## ステップ1: 3Dシーンをアプリケーションに読み込む

最初のステップは、3Dシーンをアプリケーションに読み込むことです。これは、`Scene` Aspose.3Dが提供するクラス。`"VirtualCity.glb"` 3D シーン ファイルへのパスを指定します。

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

の`Scene`オブジェクトは 3D シーンをメモリに読み込み、シーンを操作してレンダリング テクニックを適用できるようにします。

## ステップ2: カメラとライトをセットアップする

3D シーンを正しくキャプチャするには、カメラと適切な照明を設定する必要があります。カメラを使用するとシーンの視点を制御でき、照明はオブジェクトを照らすのに役立ちます。

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

- カメラの設定: カメラの近距離平面と遠距離平面を設定して、3D シーンの表示範囲を定義します。
- ライトの設定: シーンに深みとリアリティを加えるために、ポイント ライトと特定の色のライトの 2 つのライトが追加されます。

## ステップ3: レンダラーを設定し、レンダリングターゲットを定義する

シーン、カメラ、ライトの設定が完了したら、次のステップはレンダラーを作成し、レンダリング ターゲットを定義することです。レンダラーは 3D 画像を生成する役割を担い、レンダリング ターゲットは最終出力が保存される場所を定義します。

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- キューブ レンダリング テクスチャ: パノラマ ビューのキューブ マップをレンダリングするために使用されます。ここでは 512x512 のテクスチャを定義します。
- 最終レンダリング テクスチャ: これは最終的な正距円筒パノラマ ビューを保持するテクスチャです。

## ステップ4: ビューポートを設定してシーンをレンダリングする

レンダリング テクスチャを作成したら、カメラがキャプチャする 3D シーンの領域を定義するビューポートを構成する必要があります。

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

このコードはキューブマップのビューポートを設定し、シーンを`rt`テクスチャをレンダリングします。

## ステップ5: 正距円筒図法の後処理を適用する

この時点で、キューブ マップを正距円筒パノラマ ビューに変換するための後処理を適用する必要があります。この変換により、最終画像が適切なパノラマになることが保証されます。

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- 正距円筒図法: この後処理効果は、キューブ マップを正距円筒図法のパノラマ投影に変換し、シームレスな 360 度ビューを提供します。

## ステップ6: レンダリングしたパノラマを保存する

レンダリングと後処理が完了したら、最後のステップとして、最終的なパノラマを PNG などの画像ファイルに保存します。

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

これにより、パノラマ画像が指定されたディレクトリに保存され、アプリケーションに統合したり、Web サイトに表示したりできるようになります。

## 結論

Aspose.3D for .NET を使用すると、3D シーンのパノラマ ビューのレンダリングがこれまでになく簡単になります。上記の手順に従うことで、3D シーンを簡単に読み込み、カメラとライトを構成し、シーンをレンダリングし、後処理効果を適用して、臨場感あふれるパノラマ イメージを生成できます。Aspose.3D for .NET は、3D 視覚化を実現し、アプリケーションにシームレスに統合するためのパワーと柔軟性を提供します。

## よくある質問

### パノラマのレンダリングに独自の 3D シーンを使用できますか?
もちろんです。サンプル シーン ファイルのパスを、カスタム 3D シーンの場所に置き換えるだけです。

### 追加の後処理効果は利用できますか?
はい、Aspose.3D は、被写界深度、ブルームなど、レンダリングされた画像を強化するために適用できるさまざまな後処理効果を提供します。

### レンダリングパフォーマンスを最適化するにはどうすればよいですか?
レンダリング パフォーマンスは、レンダリング テクスチャのサイズや解像度などのパラメータを調整したり、カメラの近距離平面と遠距離平面を微調整したりすることで最適化できます。

### これを Web アプリケーションに統合できますか?
はい、Aspose.3D for .NET を .NET Web アプリケーションに統合して、3D パノラマを動的にレンダリングできます。

### Aspose.3D サポートのコミュニティ フォーラムはありますか?
はい、訪問できます[Aspose.3D フォーラム](https://forum.aspose.com/c/3d/18)サポートとコミュニティのディスカッションのため。