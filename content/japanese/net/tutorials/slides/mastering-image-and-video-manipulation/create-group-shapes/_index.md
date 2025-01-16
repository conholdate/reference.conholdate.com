---
title: Aspose.Slides for .NET を使用して PowerPoint でグループ図形を作成する
linktitle: Aspose.Slides for .NET を使用して PowerPoint でグループ図形を作成する
second_title: Aspose.Slides .NET PowerPoint 処理 API
description: Aspose.Slides for .NET を使用してグループ図形を作成および管理する方法を学びます。この包括的なガイドでは、明確な手順が段階的に説明されています。
type: docs
weight: 11
url: /ja/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## 導入

PowerPoint プレゼンテーションの視覚的な魅力と構成を強化すると、視聴者の関心を大きく高めることができます。これを実現する効果的な方法の 1 つは、グループ シェイプを使用することです。このチュートリアルでは、Aspose.Slides for .NET を利用してプレゼンテーションでグループ シェイプを作成および操作する方法について説明します。

## 前提条件

チュートリアルに進む前に、次のものを用意してください。

-  Aspose.Slides for .NET: Aspose.Slidesライブラリの最新バージョンをダウンロードしてインストールします。[Aspose ウェブサイト](https://releases.aspose.com/slides/net/).
- 開発環境: プロジェクトで作業するために、Visual Studio などの .NET 互換 IDE をセットアップします。
- 基本的な C# の知識: 基本的な C# の概念を理解します。


## 必要な名前空間をインポートする

C# プロジェクトでは、まず次の名前空間を含めます。

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## ステップ1: プレゼンテーションクラスをインスタンス化する

インスタンスを作成する`Presentation`スライドを作成するクラス。ドキュメントを保存するディレクトリを指定します。

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    //図形を作成および操作する手順はここに記載します
}
```

## ステップ2: 最初のスライドにアクセスする

新しく作成したプレゼンテーションの最初のスライドを取得します。

```csharp
ISlide slide = pres.Slides[0];
```

## ステップ3: シェイプコレクションにアクセスする

スライド上の図形のコレクションを取得します。

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## ステップ4: グループ図形を追加する

次に、スライドにグループ図形を追加します。

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## ステップ5: グループ内に図形を追加する

グループ シェイプに、長方形などの個別のシェイプを追加できます。

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); //形状1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); //形状2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); //形状3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); //形状4
```

## ステップ6: グループシェイプのフレームを定義する

グループ シェイプにフレームを設定すると、定義された境界が与えられます。

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## ステップ7: プレゼンテーションを保存する

最後に、変更したプレゼンテーションを指定されたディレクトリに保存します。

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## 結論

おめでとうございます! Aspose.Slides for .NET を使用して、PowerPoint プレゼンテーションにグループ図形を作成しました。このように図形を整理すると、視覚的なレイアウトとコンテンツの明瞭性が大幅に向上し、プレゼンテーションのインパクトが高まります。

## よくある質問

### Aspose.Slides は最新バージョンの .NET と互換性がありますか?

はい、Aspose.Slidesは最新の.NETバージョンとの互換性を保つために定期的に更新されています。[ドキュメント](https://reference.aspose.com/slides/net/)最新の互換性の詳細については、こちらをご覧ください。

### 購入前に Aspose.Slides を試すことはできますか?

もちろんです！無料試用版をダウンロードできます[ここ](https://releases.aspose.com/).

### Aspose.Slides 関連のクエリのサポートはどこで見つかりますか?

 Aspose.Slidesをご覧ください[フォーラム](https://forum.aspose.com/c/slides/11)コミュニティのサポートとディスカッションのため。

### Aspose.Slides の一時ライセンスを取得するにはどうすればよいですか?

一時ライセンスを申請できます[ここ](https://purchase.aspose.com/temporary-license/).

### Aspose.Slides のフルライセンスはどこで購入できますか?

ライセンスは以下から購入できます。[購入ページ](https://purchase.aspose.com/buy).