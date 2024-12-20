---
title: プリミティブ3Dモデリングの作成
linktitle: プリミティブ3Dモデリングの作成
second_title: Aspose.3D .NET API
description: ボックスや円柱などの基本的な 3D モデルを作成およびカスタマイズし、FBX 形式で簡単に保存する方法を学びます。
type: docs
weight: 10
url: /ja/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## 導入

Aspose.3D for .NET を使用した 3D モデリングの没入型の世界へようこそ。この包括的なチュートリアルでは、基本的な 3D モデルを作成するプロセスを段階的に説明します。経験豊富な開発者でも、学習意欲の高い初心者でも、このガイドを活用すれば、プロジェクトに視覚的に魅力的な 3D 要素を作成できます。

## 前提条件

3D モデリングを始める前に、次の前提条件が満たされていることを確認してください。

-  Aspose.3D for .NET: Aspose.3D for .NETライブラリを以下のサイトからダウンロードしてインストールします。[ダウンロードページ](https://releases.aspose.com/3d/net/).
  
- .NET 開発環境: Visual Studio など、Aspose.3D と互換性のある環境を設定します。

準備が整ったら、3D モデリングの冒険に出発しましょう。

## 必要な名前空間のインポート

まず、Aspose.3D の機能にアクセスするために必要な名前空間をインポートします。

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

これらの名前空間は、3D モデルを操作し、作成したモデルを保存するために必要なツールを提供します。

## ステップ1: シーンオブジェクトを初期化する

3D モデルのキャンバスとして機能する新しいシーン オブジェクトを作成します。

```csharp
//シーンオブジェクトを初期化する
Scene scene = new Scene();
```

このシーンには、これから作成するプリミティブ シェイプが含まれます。

## ステップ2: ボックスモデルを作成する

次に、シーンにボックス モデルを追加してみましょう。

```csharp
//ボックスモデルを作成する
scene.RootNode.CreateChildNode("box", new Box());
```

クリエイティブなビジョンに合わせて、ボックスの寸法とプロパティをカスタマイズできます。

## ステップ3: 円柱モデルを作成する

次に、円柱を追加してシーンを強化します。

```csharp
//円柱モデルを作成する
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

ボックスの場合と同様に、シリンダーのパラメータを自由に調整して、希望の外観を実現できます。

## ステップ4: シーンをFBX形式で保存する

3D モデルを保存するには、FBX 形式で保存します。

```csharp
//図面をFBX形式で保存する
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

モデルに適切な出力ディレクトリとファイル名を選択してください。

## ステップ5: 成功メッセージを表示する

最後に、次のメッセージを表示して成功を祝います。

```csharp
//成功メッセージを表示する
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

プリミティブ モデルで構成された 3D シーンが完成し、保存されました。

## 結論

Aspose.3D for .NET を使用した素晴らしい 3D モデルの作成、おめでとうございます。このチュートリアルではプリミティブ モデリングの基本について説明しましたが、可能性は無限です。[ドキュメント](https://reference.aspose.com/3d/net/).

## よくある質問

### Aspose.3D for .NET を .NET 以外のプログラミング言語で使用できますか?

Aspose.3D は主に .NET をサポートしていますが、Java やその他のプラットフォーム用のバージョンも用意されています。

### 無料トライアルはありますか？

はい、Aspose.3Dの機能を試すことができます。[無料トライアル](https://releases.aspose.com/).

### Aspose.3D for .NET のサポートはどこで受けられますか?

コミュニティサポートについては、[Aspose.3D フォーラム](https://forum.aspose.com/c/3d/18).

### 一時ライセンスを取得するにはどうすればいいですか?

一時ライセンスを申請できます[ここ](https://purchase.conholdate.com/temporary-license/).

### 追加のチュートリアルはありますか?

はい！その他のチュートリアルや例については、[ドキュメント](https://reference.aspose.com/3d/net/).