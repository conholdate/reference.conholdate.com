---
title: .NET で PDF から組み込みプロパティを読み取る
linktitle: .NET で PDF から組み込みプロパティを読み取る
second_title: GroupDocs.メタデータ .NET API
description: GroupDocs.Metadata for .NET を効果的に利用して、PDF ファイルのメタデータを読み取り、編集、管理する方法を学びます。このチュートリアルでは、ステップ バイ ステップ ガイドを提供します。
type: docs
weight: 10
url: /ja/net/tutorials/metadata/pdf-metadata-management/reading-built-in-properties-from-pdf/
---
## 導入
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して PDF ファイルのメタデータを読み取り、操作する方法について説明します。この強力なライブラリを使用すると、開発者は作成者、作成日、件名などのさまざまなメタデータ属性にアクセスでき、アプリケーション内のドキュメント管理機能が強化されます。

## 前提条件
始める前に、以下のものを用意してください。

- Visual Studio: システムにインストールされていることを確認してください。
-  GroupDocs.Metadata for .NET: ダウンロードしてインストールしてください。[公式サイト](https://releases.groupdocs.com/metadata/net/).
- C# の基礎知識: C# と .NET フレームワークに精通していることが推奨されます。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間を含めます。

```csharp
using System;
using Formats.Document;
```

## ステップ1: PDFメタデータを読み込む
PDF ファイルからメタデータを読み取るには、次のコードを使用してドキュメントを読み込み、そのプロパティを抽出します。

```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    //PDFファイルのルートパッケージにアクセスする
    var root = metadata.GetRootPackage<PdfRootPackage>();
    
    //組み込みプロパティを取得して表示する
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    //必要に応じて他のプロパティにアクセスする
}
```

この簡単なアプローチにより、PDF ファイルに埋め込まれた重要なメタデータ属性を簡単に表示できます。

## 結論
このチュートリアルでは、GroupDocs.Metadata for .NET を使用して、C# で PDF ファイルから組み込みプロパティを抽出および管理する方法を説明しました。このライブラリをプロジェクトに統合すると、ドキュメント メタデータの処理が強化され、より効率的かつ合理化されます。

## よくある質問
### GroupDocs.Metadata は他のドキュメント形式でも動作しますか?
はい、DOCX、XLSX、PPTX、PDF、JPG、PNG など、幅広い形式をサポートしています。

### GroupDocs.Metadata の無料トライアルはありますか?
もちろんです！無料トライアルは[GroupDocs.Metadata ウェブサイト](https://releases.groupdocs.com/).

### GroupDocs.Metadata を使用してメタデータのプロパティを変更するにはどうすればよいですか?
関連するドキュメント パッケージにアクセスし、必要に応じて新しい値を設定することで、メタデータ プロパティを変更できます。

### GroupDocs.Metadata は .NET Core をサポートしていますか?
はい、.NET Framework と .NET Core の両方と互換性があります。

### GroupDocs.Metadata に関するサポートや質問はどこで受けられますか?
サポートやコミュニティのディスカッションについては、[GroupDocs.Metadata フォーラム](https://forum.groupdocs.com/c/metadata/14).