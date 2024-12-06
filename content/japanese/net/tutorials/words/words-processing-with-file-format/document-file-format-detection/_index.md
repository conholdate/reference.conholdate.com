---
title: ドキュメントファイル形式の検出
linktitle: ドキュメントファイル形式の検出
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、さまざまなドキュメント ファイル形式をシームレスに検出し、管理する方法を学びます。実用的な例、ヒント、FAQ を含む詳細なガイドに従ってください。
type: docs
weight: 10
url: /ja/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## 導入

今日のデジタル環境では、さまざまなドキュメント形式を効率的に管理および整理することが重要です。Aspose.Words for .NET は、さまざまなファイルの種類を検出して処理するための堅牢なソリューションを提供します。このガイドでは、ドキュメント形式を検出し、正確性を確保して貴重な時間を節約する手順を詳しく説明します。

## ドキュメント検出の前提条件

始める前に、次の要件が満たされていることを確認してください。

1. Aspose.Words for .NET ライブラリ  
   ライブラリをダウンロードするには[Aspose Words リリース](https://releases.aspose.com/words/net/)有効なライセンスを使用してアクティベートしてください。一時ライセンスについては、[Aspose 一時ライセンス](https://purchase.aspose.com/temporary-license/).

2. 開発環境  
   .NET Framework がインストールされた Visual Studio (最新バージョン) を使用します。

3. 基本的なファイル設定  
   入力ファイルを整理し、検出された形式を並べ替えるためのディレクトリを準備します。

## 必須の名前空間をインポートする

プログラムの先頭に次の名前空間を含めます。

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

これらのインポートは、ファイル形式の検出に必要なクラスとメソッドへのアクセスを提供します。

## ステップ1: 整理された出力のためにディレクトリを初期化する

検出された形式に基づいてファイルを保存するためのディレクトリを作成します。

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

//ディレクトリが存在することを確認する
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

この構造によりファイル管理が簡素化されます。

## ステップ2: ファイルリストを取得する

破損したドキュメントやサポートされていないドキュメントを除外して、処理を効率化します。

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

フィルタリングされたリストにより、有効なファイルのみを操作できるようになります。

## ステップ3: ファイル形式の検出と分類

各ファイルをループしてその形式を識別し、適切なディレクトリに移動します。

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    //検出された出力形式
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

の`FileFormatUtil.DetectFileFormat`この方法は、文書の特性を識別する上で中心的な役割を果たします。

## 結論

Aspose.Words for .NET を活用することで、ドキュメント ファイル形式の検出が簡単に行えます。さまざまな形式を識別して分類できるため、シームレスなドキュメント管理が実現し、生産性とワークフローの効率が向上します。

## よくある質問

### ドキュメント形式を検出する主な目的は何ですか?  
形式を検出すると、特定のワークフローやアプリケーションに合わせてファイルを分類することで、ドキュメント処理を効率化できます。

### Aspose.Words は暗号化されたファイルをサポートしていますか?  
はい、暗号化を検出し、それに応じて暗号化されたドキュメントを処理できます。

### このソリューションを他のファイルタイプに拡張できますか?  
はい、コードを変更して追加の形式を含めたり、他の Aspose ライブラリを統合したりできます。

### 不明な形式をどのように処理しますか?  
不明な形式を個別に保存し、手動で検査したり、専用のツールでさらに処理したりします。

### 追加のドキュメントはどこで入手できますか?  
訪問する[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/)包括的なガイドと例については、こちらをご覧ください。
