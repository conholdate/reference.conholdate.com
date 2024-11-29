---
title: GroupDocs.Signature を使用してカスタム画像でドキュメントに署名する
linktitle: カスタム画像で文書に署名する
second_title: GroupDocs.Signature .NET API
description: GroupDocs.Signature for .NET を使用してカスタム画像で署名することで、ドキュメントの信頼性とセキュリティを強化する方法を学びます。このステップバイステップのチュートリアルでは、ドキュメントの読み込みからすべてを説明します。
type: docs
weight: 13
url: /ja/net/tutorials/signature/master-advanced-sign-techniques/sign-documents-with-custom-image/
---
## 導入

このチュートリアルでは、GroupDocs.Signature for .NET を使用して画像付きのドキュメントに署名する方法を学習します。ドキュメントに署名すると、ファイルの信頼性とセキュリティが強化され、改ざん防止と法的拘束力が確保されます。ドキュメント署名機能を .NET アプリケーションに統合すると、ワークフローを大幅に効率化できます。

## 前提条件

チュートリアルに進む前に、次のものを用意してください。

1.  GroupDocs.Signature for .NET: GroupDocs.Signature for .NETを以下のサイトからダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/signature/net/).
2. .NET 開発環境: .NET 開発用の作業環境をセットアップします。

## 名前空間のインポート

必要なクラスとメソッドにアクセスするには、まずプロジェクトに必要な名前空間をインポートします。

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## ステップ1: ドキュメントを読み込む

署名するドキュメントへのパスを指定します。たとえば、PDF ファイルを読み込むには、次のようにします。

```csharp
string filePath = "sample.pdf";
```

## ステップ2: 署名画像を指定する

使用する署名画像へのパスを定義します。

```csharp
string imagePath = "signature_handwrite.jpg";
```

## ステップ3: 出力ファイルのパスを設定する

署名された文書を保存する場所を決定します。

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithImage", "SignedDocument.pdf");
```

## ステップ4: 署名オブジェクトを初期化する

インスタンスを作成する`Signature`クラスにドキュメント ファイルのパスを渡します。

```csharp
using (Signature signature = new Signature(filePath))
{
    //追加コードはここに記入します
}
```

## ステップ5: イメージ署名オプションを構成する

ドキュメントに署名するためのオプションを設定します。ここでは、署名の位置と、すべてのページに署名を表示するかどうかを指定できます。

```csharp
ImageSignOptions options = new ImageSignOptions(imagePath)
{
    Left = 50,   //水平位置
    Top = 50,    //垂直位置
    AllPages = true //すべてのページに署名する
};
```

## ステップ6: 文書に署名する

設定されたオプションを利用してドキュメントに署名します。

```csharp
SignResult result = signature.Sign(outputFilePath, options);
```

## ステップ7: 結果を表示する

最後に、署名されたドキュメントの場所を含め、署名プロセスが成功したことをユーザーに通知します。

```csharp
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## 結論

このチュートリアルでは、GroupDocs.Signature for .NET を使用して、.NET アプリケーションで画像を使用してドキュメントに署名する方法について説明しました。ドキュメントの署名は、ファイルの信頼性とセキュリティを維持するために不可欠であり、ドキュメント管理機能を大幅に強化します。

## よくある質問

### 1 つのドキュメントで複数の署名画像を使用できますか?

はい、複数の画像を使用して文書に署名できます。必要に応じて、画像ごとに署名プロセスを繰り返すだけです。

### GroupDocs.Signature for .NET はすべてのドキュメント タイプと互換性がありますか?

GroupDocs.Signature for .NET は、PDF、Word、Excel など、さまざまなドキュメント形式をサポートしています。

### 署名の外観をカスタマイズできますか?

もちろんです! サイズ、位置、透明度など、署名の外観のさまざまな側面を調整できます。

### テスト用に試用版はありますか?

はい、購入する前に、Web サイトから無料試用版をダウンロードして機能を試すことができます。

### GroupDocs.Signature for .NET のテクニカル サポートを受けるにはどうすればよいですか?

技術的なサポートについては、[GroupDocs.Signature フォーラム](https://forum.groupdocs.com/c/signature/13).