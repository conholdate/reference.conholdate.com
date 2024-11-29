---
title: GroupDocs.Signature を使用してドキュメントにテキスト署名を追加する
linktitle: 文書にテキスト署名を追加する
second_title: GroupDocs.Signature .NET API
description: GroupDocs.Signature for .NET を使用して、テキストでドキュメントに署名する方法を学びます。プログラムでテキスト署名を追加するためのステップバイステップ ガイド。
type: docs
weight: 17
url: /ja/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## 導入

今日のデジタル環境では、電子文書の署名はワークフローの効率化とリソースの節約に不可欠になっています。GroupDocs.Signature for .NET は、さまざまな文書形式にテキスト署名をプログラムで追加するための強力なソリューションを提供します。このチュートリアルでは、GroupDocs.Signature for .NET を使用してテキストで文書に署名する手順を説明します。

## 前提条件

始める前に、以下のものを用意してください。

1.  GroupDocs.Signature for .NET: ライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/signature/net/).
2. 開発環境: .NET 開発環境をセットアップします。
3. ドキュメント: 署名するドキュメント (PDF、Word など) を準備します。

## 必要な名前空間のインポート

まず、必要な名前空間を .NET プロジェクトにインポートします。

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## ステップ1: ドキュメントを読み込む

まず、署名する文書を読み込みます。

```csharp
string filePath = "sample.pdf"; //ドキュメントへのパス
string fileName = Path.GetFileName(filePath);
```

## ステップ2: 出力ファイルのパスを定義する

次に、署名されたドキュメントを保存する出力ファイル パスを設定します。

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## ステップ3: 署名オプションを作成する

テキスト署名の内容、位置、サイズ、色、フォント スタイルなどのオプションを構成します。

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // X位置
    Top = 200, //Y位置
    Width = 100, //署名の幅
    Height = 30, //署名の高さ
    ForeColor = Color.Red, //テキストの色
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } //フォント設定
};
```

## ステップ4: 文書に署名する

最後に、GroupDocs.Signature を使用してテキスト署名を適用し、署名されたドキュメントを保存します。

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); //文書に署名する
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## 結論

このチュートリアルでは、GroupDocs.Signature for .NET を使用して、プログラムによってドキュメントにテキスト署名を追加する方法を説明しました。これらの手順に従うことで、ドキュメントのセキュリティと信頼性を効率的に強化できます。

## よくある質問

### テキスト署名の外観をカスタマイズできますか?
はい、テキスト署名の色、フォント、サイズ、位置などのさまざまな属性をニーズに合わせてカスタマイズできます。

### GroupDocs.Signature は複数のドキュメント形式と互換性がありますか?
もちろんです! GroupDocs.Signature は、PDF、Word、Excel、PowerPoint など、幅広い形式をサポートしています。

### 1 つのドキュメントに複数のテキスト署名を追加できますか?
はい、それぞれ独自のカスタマイズ オプションを持つ複数のテキスト署名を追加できます。

### GroupDocs.Signature は署名後のドキュメントの整合性を保証しますか?
はい、ライブラリは強力な暗号化アルゴリズムを使用して、ドキュメントの整合性を確保し、署名後の改ざんを防止します。

### 購入前にテストできる試用版はありますか?
はい、無料試用版は以下からダウンロードできます。[ここ](https://releases.groupdocs.com/)購入する前に機能を調べてください。