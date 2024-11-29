---
title: パスワードで保護されたドキュメントの読み込み
linktitle: パスワードで保護された文書を読み込む
second_title: GroupDocs.Viewer .NET API
description: GroupDocs.Viewer を使用して、ドキュメント表示機能を .NET アプリケーションに簡単に統合する方法を学びます。このチュートリアルでは、包括的なステップ バイ ステップ ガイドを提供します。
type: docs
weight: 12
url: /ja/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## 導入

デジタルの世界では、さまざまなドキュメント形式を管理および表示する機能は、企業や個人にとって非常に重要です。GroupDocs.Viewer for .NET は、開発者がドキュメント表示機能をアプリケーションに簡単に統合できる強力なソリューションを提供します。このチュートリアルでは、パスワードで保護されたドキュメントを読み込むプロセスを段階的に説明し、この機能をプロジェクトにシームレスに実装できるようにします。

## 前提条件

始める前に、以下のものを用意してください。

1.  GroupDocs.Viewer for .NET インストール済み: ダウンロードはこちら[Webサイト](https://releases.groupdocs.com/viewer/net/).
2. パスワードで保護されたドキュメント: テスト用にパスワードで保護されたドキュメントを用意します。

## 必要な名前空間をインポートする

まず、必要な名前空間をプロジェクトにインポートします。

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## ステップ1: 出力ディレクトリを定義する

レンダリングされた出力を保存する場所を指定します。

```csharp
string outputDirectory = "Your Document Directory";
```
必ず交換してください`"Your Document Directory"`実際に使用するパスを入力します。

## ステップ2: ページファイルパス形式を設定する

レンダリングされる各ページのファイル パスの形式を定義します。

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

次のようなパスが生成されます`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`など

## ステップ3: ロードオプションを構成する

パスワードを含む、パスワードで保護されたドキュメントの読み込みオプションを設定します。

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  //ドキュメントのパスワードに置き換えます
};
```

## ステップ4: ビューアを初期化する

ドキュメントと読み込みオプションを使用して GroupDocs.Viewer のインスタンスを作成します。

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    //表示オプションのコードは次の手順で追加されます。
}
```
必ず交換してください`"Path_to_your_document"`ドキュメントへの実際のパスを入力します。

## ステップ5: HTML表示オプションを構成する

埋め込まれたリソースを含むドキュメントをレンダリングするための HTML ビュー オプションを設定します。

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## ステップ6: ドキュメントをレンダリングする

次に、設定されたビューアと表示オプションを使用してドキュメントをレンダリングします。

```csharp
viewer.View(options);
```

## ステップ7: 成功メッセージを表示する

最後に、ドキュメントが正常にレンダリングされたことをユーザーに通知します。

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## 結論

このチュートリアルでは、GroupDocs.Viewer for .NET を使用してパスワードで保護されたドキュメントを読み込む方法について説明しました。これらの手順に従うことで、開発者はこの機能をアプリケーションに簡単に統合でき、ユーザーは保護されたドキュメントを簡単に表示できるようになります。

## よくある質問

### GroupDocs.Viewer は、パスワードで保護されたドキュメント以外のドキュメント形式も処理できますか?

はい、GroupDocs.Viewer は PDF、DOCX、XLSX、PPTX など、幅広い形式をサポートしています。

### GroupDocs.Viewer は .NET Core と互換性がありますか?

もちろんです! GroupDocs.Viewer は、.NET Framework 環境と .NET Core 環境の両方と互換性があります。

### ドキュメントのレンダリング オプションをカスタマイズできますか?

はい、GroupDocs.Viewer にはさまざまなレンダリング オプションが用意されており、ニーズに合わせて表示エクスペリエンスをカスタマイズできます。

### GroupDocs.Viewer はドキュメントの注釈をサポートしていますか?

はい、ドキュメントの注釈をサポートしており、ユーザーはコメント、ハイライト、その他のメモを追加できます。

### GroupDocs.Viewer の試用版はありますか?

はい、無料トライアルは[Webサイト](https://releases.groupdocs.com/).