---
title: .NET プレゼンテーションに埋め込みビデオ フレームを追加する
linktitle: .NET プレゼンテーションに埋め込みビデオ フレームを追加する
second_title: Aspose.Slides .NET PowerPoint 処理 API
description: Aspose.Slides for .NET を使用してビデオを埋め込む方法を学習することで、プレゼンテーションの可能性を最大限に引き出します。この包括的なチュートリアルでは、マルチメディア要素を統合するプロセスを段階的に説明します。
type: docs
weight: 19
url: /ja/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## 導入

今日の急速に変化するプレゼンテーション環境では、マルチメディア要素を統合することで、エンゲージメントと視聴者の維持率を大幅に向上できます。Aspose.Slides for .NET は、スライドにビデオ フレームを埋め込むための強力なソリューションを提供します。このチュートリアルでは、プロセスを段階的に説明し、最初から最後までスムーズなエクスペリエンスを実現します。

## 前提条件

始める前に、次のものを用意してください。

-  Aspose.Slides for .NETライブラリ: ライブラリを以下のサイトからダウンロードしてインストールします。[リリースページ](https://releases.aspose.com/slides/net/).
- メディア コンテンツ: プレゼンテーションに埋め込むビデオ ファイル (例: 「Wildlife.mp4」)。

## 必要な名前空間をインポートする

まず、.NET プロジェクトに必要な名前空間をインポートします。

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## ステップ1: ディレクトリを設定する

プロジェクトにドキュメントおよびメディア ファイルに必要なディレクトリが含まれていることを確認します。

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

//ディレクトリが存在しない場合は作成する
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## ステップ2: プレゼンテーションクラスをインスタンス化する

インスタンスを作成する`Presentation`PPTX ファイルを表すクラス:

```csharp
using (Presentation pres = new Presentation())
{
    //最初のスライドを取得する
    ISlide sld = pres.Slides[0];
```

## ステップ3: ビデオを埋め込む

次のコードを使用して、ビデオをプレゼンテーションに埋め込みます。

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## ステップ4: ビデオフレームを追加する

次に、スライドにビデオ フレームを追加します。

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## ステップ5: ビデオのプロパティを構成する

再生モードや音量などのビデオのプロパティを設定します。

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; //ビデオを自動的に再生する
vf.Volume = AudioVolumeMode.Loud; //音量レベルを設定する
```

## ステップ6: プレゼンテーションを保存する

最後に、変更した PPTX ファイルをディスクに保存します。

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

プレゼンテーションに埋め込みたいビデオごとに、これらの手順を繰り返すことができます。

## 結論

おめでとうございます! Aspose.Slides for .NET を使用して、プレゼンテーションにビデオ フレームを埋め込むことができました。この動的な機能により、プレゼンテーションのレベルがさらに上がり、シームレスに統合されたマルチメディアで視聴者を魅了することができます。

## よくある質問

### プレゼンテーションのどのスライドにもビデオを埋め込むことはできますか?

はい、インデックスを調整することで任意のスライドを選択できます。`pres.Slides[index]`.

### どのビデオ形式がサポートされていますか?

Aspose.Slides は、MP4、AVI、WMV など、さまざまなビデオ形式をサポートしています。

### ビデオフレームのサイズと位置をカスタマイズできますか?

もちろんです！パラメータは`AddVideoFrame(x, y, width, height, video)`お客様のニーズに合わせて。

### 埋め込むことができる動画の数に制限はありますか?

埋め込みビデオの制限は通常、プレゼンテーション ソフトウェアの容量によって異なります。

### さらにサポートを求めたり、経験を共有したりするにはどこに行けばよいですか?

ぜひお越しください[Aspose.Slides フォーラム](https://forum.aspose.com/c/slides/11)コミュニティのサポートとディスカッションのため。