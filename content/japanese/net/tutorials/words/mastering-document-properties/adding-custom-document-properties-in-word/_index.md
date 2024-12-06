---
title: Word でカスタム ドキュメント プロパティを追加する
linktitle: Word でカスタム ドキュメント プロパティを追加する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、カスタム ドキュメント プロパティで Word ドキュメントを強化する方法を学びます。この包括的なガイドでは、プロセスを順を追って説明します。
type: docs
weight: 10
url: /ja/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## 導入

ようこそ! Aspose.Words for .NET を探索していて、Word ファイルにカスタム ドキュメント プロパティを追加する方法を知りたい場合は、ここが最適な場所です。カスタム プロパティは、組み込みプロパティではカバーされない追加のメタデータを保存するのに非常に役立ちます。ドキュメントの承認、リビジョン番号、特定の日付を追跡する必要がある場合でも、カスタム プロパティが役立ちます。このチュートリアルでは、Aspose.Words for .NET を使用してこれらのプロパティをシームレスに追加する手順を説明します。さあ、始めましょう!

## 前提条件

コードに進む前に、次のものを用意してください。

1.  Aspose.Words for .NET ライブラリ: ダウンロード[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio などの IDE。
3. C# の基礎知識: C# と .NET の知識があると役立ちます。
4. サンプル文書: サンプルのWord文書を準備します。`Properties.docx`変更のため。

## 名前空間のインポート

Aspose.Words の機能にアクセスするには、コードの先頭に必要な名前空間をインポートする必要があります。

```csharp
using System;
using Aspose.Words;
```

## ステップ1: ドキュメントパスの設定

次に、Word文書へのパスを定義しましょう。この手順は、Word文書を見つけて開くために不可欠です。`Properties.docx`ファイル。

```csharp
//ドキュメント ディレクトリへのパスを指定します。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

必ず交換してください`"YOUR DOCUMENT DIRECTORY"`ドキュメントへの実際のパスを入力します。

## ステップ2: カスタムドキュメントプロパティにアクセスする

ここで、カスタム メタデータが保存される Word 文書のカスタム ドキュメント プロパティにアクセスしてみましょう。

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

この行により、操作するカスタム プロパティのコレクションにアクセスできます。

## ステップ3: 既存のプロパティを確認する

新しいプロパティを追加する前に、重複を避けるためにプロパティが既に存在するかどうかを確認することをお勧めします。

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

このコードは、「Authorized」プロパティがすでに存在するかどうかを確認します。存在する場合、メソッドは早期に終了し、重複を防止します。

## ステップ4: ブールプロパティの追加

ドキュメントが承認されているかどうかを示すカスタム ブール プロパティを追加しましょう。

```csharp
customDocumentProperties.Add("Authorized", true);
```

この行は「Authorized」というプロパティを追加し、その値を`true`.

## ステップ5: 文字列プロパティの追加

次に、文字列プロパティを追加して、ドキュメントを承認したユーザーを指定します。

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

「John Smith」を好きな名前に置き換えてください。

## ステップ6: 日付プロパティの追加

ドキュメントがいつ承認されたかを追跡するには、日付プロパティを追加しましょう。

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

この行は「承認日」というプロパティを追加し、今日の日付を割り当てます。`DateTime.Today`.

## ステップ7: リビジョン番号の追加

バージョン管理のために、ドキュメントのリビジョン番号を追跡するためのプロパティを追加できます。

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

ここでは、ドキュメントの現在のリビジョン番号を保持する「承認済みリビジョン」プロパティを追加します。

## ステップ8: 数値プロパティの追加

最後に、予算額などの承認金額を格納するための数値プロパティを追加しましょう。

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

この行は、「Authorized Amount」という名前のプロパティを次の値で追加します。`123.45`必要に応じてこの数値を調整できます。

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、Word 文書にカスタム ドキュメント プロパティを正常に追加しました。これらのプロパティは、承認の詳細、リビジョン番号、特定の金額を追跡するなど、要件に合わせて調整されたメタデータを保存するための強力な方法です。

## よくある質問

### カスタム ドキュメント プロパティとは何ですか?
カスタム ドキュメント プロパティは、組み込みプロパティでカバーされていない追加情報を保存するために Word ドキュメントに追加できるメタデータです。

### 文字列や数値以外のプロパティを追加できますか?
はい、ブール値、日付、さらにはカスタム オブジェクトなど、さまざまな種類のプロパティを追加できます。

### Word 文書でこれらのプロパティにアクセスするにはどうすればよいでしょうか?
Aspose.Words を使用してプログラムでカスタム プロパティにアクセスしたり、ドキュメント プロパティを通じて Word で直接表示したりできます。

### カスタムプロパティを編集または削除することは可能ですか?
もちろんです! Aspose.Words が提供するメソッドを使用して、カスタム プロパティを簡単に編集または削除できます。

### ドキュメントのフィルタリングにカスタム プロパティを使用できますか?
はい。カスタム プロパティは、特定のメタデータに基づいてドキュメントを分類およびフィルタリングするのに最適です。