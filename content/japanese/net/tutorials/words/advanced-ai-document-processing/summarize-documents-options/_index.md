---
title: ドキュメントの要約オプション
linktitle: ドキュメントの要約オプション
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用してドキュメントを効率的に要約する方法を学びます。この包括的なガイドでは、セットアップ、ドキュメントの読み込み、AI モデルの統合について説明します。
type: docs
weight: 10
url: /ja/net/tutorials/words/advanced-ai-document-processing/summarize-documents-options/
---
## 導入

長いドキュメントを扱う場合、重要なポイントを見つけるために、密集した情報をふるいにかけることがよくあります。ドキュメントの要約により、このプロセスが効率化され、時間が節約され、理解が深まります。Aspose.Words for .NET は、ドキュメントの要約を自動化する強力なツールを提供し、専門家が重要なデータにすばやくアクセスして活用できるようにします。このチュートリアルでは、ビジネス、学術、コンテンツ管理のアプリケーションに最適な Aspose.Words for .NET を使用して、Word ドキュメントを効率的に要約する方法を説明します。

## 前提条件

始める前に、次のものを用意してください。

1. Aspose.Words for .NETライブラリ: ダウンロードはこちらから[Aspose のリリース](https://releases.aspose.com/words/net/).
2. .NET 環境: Visual Studio などの .NET 開発環境をセットアップします。
3. 基本的な C# の知識: このチュートリアルにはコーディングが含まれるため、C# 構文に精通していると役立ちます。
4. AI モデル API キー: 要約を生成するために使用する、優先 AI 要約モデル (例: GPT-4) の API キーを取得します。

## 必要なパッケージのインポート

まず、C# コードに必要な名前空間をインポートします。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
```

これらの名前空間を追加した後、必要に応じて Visual Studio から追加の NuGet パッケージをインストールします。これで、Aspose.Words for .NET を使用してドキュメントを要約する準備が整いました。

## ステップ1: ドキュメント管理用のディレクトリを定義する

ドキュメントをロードする前に、入力ファイルと出力ファイルを整理するためのディレクトリを作成します。これにより、ワークフローが改善され、ファイルの構造が維持されます。

```csharp
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

交換する`"YOUR_DOCUMENT_DIRECTORY"`そして`"YOUR_ARTIFACTS_DIRECTORY"`システム上の実際のパスを使用します。

## ステップ2: 要約用のドキュメントを読み込む

要約する予定の文書を読み込みます。`Document`Aspose.Words のクラスを使用して Word ファイルにアクセスします。

```csharp
Document firstDoc = new Document(MyDir + "BigDocument.docx");
Document secondDoc = new Document(MyDir + "SupportingDocument.docx");
```

の`firstDoc`そして`secondDoc`変数には、要約のために読み込まれたドキュメントが保存されるようになりました。

## ステップ3: 要約用のAIモデルを初期化する

要約を実行するには、AI モデルを設定します。まず、モデルにアクセスするために環境変数に API キーを設定します。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

の`Gpt4OMini`モデルはドキュメント要約を処理するためにAPIキーで初期化されます。`"API_KEY"`実際の API キーを使用します。

## ステップ4: 1つのドキュメントを要約する

ここで、1 つのドキュメントを要約する方法を説明します。要約の長さは必要に応じて調整してください。

```csharp
Document summaryDoc = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
summaryDoc.Save(ArtifactsDir + "SingleDocumentSummary.docx");
```

ここで、AIモデルは、`firstDoc`要約されたドキュメントは、指定された出力ディレクトリに保存されます。

## ステップ5: 複数のドキュメントを要約する

複数のドキュメントにわたる包括的な要約が必要な場合、このコード スニペットでその実現方法を示します。

```csharp
Document combinedSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
combinedSummary.Save(ArtifactsDir + "MultiDocumentSummary.docx");
```

このコードは、`firstDoc`そして`secondDoc`両方のドキュメントにわたるコンテンツのより広範な概要を提供します。

## 結論

Aspose.Words for .NET を使用したドキュメント要約により、長いファイルから重要な情報を簡単に抽出できます。このステップ バイ ステップ ガイドでは、単一または複数のドキュメントを要約する方法、さらには大規模なワークロードの要約をバッチ処理する方法を実演しました。カスタマイズ可能な要約オプションを備えた Aspose.Words は、効率的なドキュメント管理のための強力なソリューションを提供します。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者が Word ドキュメントをプログラムで作成、変更、操作できるようにする包括的なライブラリであり、Microsoft Word を使用せずにドキュメント処理タスクの自動化をサポートします。

### この方法を使用して PDF ドキュメントを要約できますか?
Aspose.Words は、DOCX や DOC などの Word ドキュメント形式に重点を置いています。PDF の要約には、Aspose.PDF の使用を検討してください。

### Aspose.Words の無料版はありますか?
はい、Aspose.Wordsは[無料試用版](https://releases.aspose.com/)機能が制限されており、テストに最適です。

### この AI を活用した要約をオフラインで実行できますか?
いいえ、要約プロセスでは、AI モデルの API と通信するためにインターネット接続が必要です。

### Aspose.Words の追加サポートはどこで見つかりますか?
訪問する[Aspose サポート フォーラム](https://forum.aspose.com/c/words/8/)サポートおよびさらなるお問い合わせについては、