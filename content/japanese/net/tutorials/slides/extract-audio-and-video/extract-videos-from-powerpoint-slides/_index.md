---
title: Aspose.Slides を使用して PowerPoint スライドからビデオを抽出する
linktitle: PowerPoint スライドからビデオを抽出する
second_title: Aspose.Slides .NET PowerPoint 処理 API
description: Aspose.Slides for .NET を使用して、PowerPoint プレゼンテーションから埋め込まれたビデオ ファイルを簡単に抽出する方法を説明します。この包括的なステップ バイ ステップ ガイドでは、環境の設定から抽出したビデオの保存まで、すべてを網羅しています。
type: docs
weight: 14
url: /ja/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## 導入

Aspose.Slides for .NET は、開発者が PowerPoint プレゼンテーションをプログラムで操作できるようにする強力なライブラリです。このガイドでは、Aspose.Slides for .NET を使用して PowerPoint スライドに埋め込まれたビデオを抽出するプロセスについて説明します。 

## 前提条件

始める前に、次のものがあることを確認してください。

-  Aspose.Slides for .NET: ライブラリを入手してインストールします。[Aspose ウェブサイト](https://purchase.aspose.com/buy).
-  PowerPointプレゼンテーション: PowerPointファイル（例：`Video.pptx`）を抽出したいビデオに置き換えます。

## 必要な名前空間

Aspose.Slides for .NET を使用するには、適切な名前空間をインポートする必要があります。コードに次の内容を含めます。

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## ステップ1: ドキュメントディレクトリを指定する

まず、PowerPoint プレゼンテーションへのパスを定義します。

```csharp
string dataDir = "Your Document Directory";
```

交換する`"Your Document Directory"` PowerPoint ファイルを含むディレクトリへの実際のパスを入力します。

## ステップ2: プレゼンテーションを読み込む

 PowerPointプレゼンテーションを`Presentation`物体：

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

これにより、`Presentation`指定した PowerPoint ファイルでオブジェクトを作成します。

## ステップ3: スライドと図形を反復処理する

次に、プレゼンテーションの各スライドをループして、ビデオ フレームを確認します。

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            //ビデオの抽出に進む
        }
    }
}
```

## ステップ4: ビデオデータを抽出する

ビデオ フレームを見つけたら、そのプロパティとバイナリ データを抽出します。

```csharp
IVideoFrame vf = (IVideoFrame)shape;  //形状をビデオフレームとして保存する
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

//ファイル拡張子を取得する
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## ステップ5: ビデオを保存する

最後に、抽出したビデオ データをファイルに書き込みます。

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

このコードは、指定されたディレクトリに新しいファイルを作成し、そこにビデオ データを書き込みます。

## 結論

Aspose.Slides for .NET を使用すると、PowerPoint スライドからビデオを抽出するプロセスが簡単になります。このガイドに従うことで、.NET アプリケーション内でマルチメディア コンテンツを簡単に管理し、ユーザー エクスペリエンスと機能を強化できます。

## よくある質問

### Aspose.Slides for .NET とは何ですか?
Aspose.Slides for .NET は、PowerPoint プレゼンテーションを操作するために設計されたライブラリであり、ユーザーはプログラムを使用してプレゼンテーション ファイルを作成、編集、操作できます。

### Aspose.Slides for .NET のドキュメントはどこにありますか?
完全なドキュメントにアクセスできます[ここ](https://reference.aspose.com/slides/net/).

### Aspose.Slides for .NET は無料試用版として利用できますか?
はい、無料試用版は以下からダウンロードできます。[このリンク](https://releases.aspose.com/).

### Aspose.Slides for .NET の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスの申請は[ここ](https://purchase.aspose.com/temporary-license/).

### Aspose.Slides for .NET のサポートはどこで受けられますか?
サポートは以下からご利用いただけます。[Aspose.Slides フォーラム](https://forum.aspose.com/).