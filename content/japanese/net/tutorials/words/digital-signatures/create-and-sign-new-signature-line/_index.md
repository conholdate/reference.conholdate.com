---
title: 新しい署名欄を作成して署名する
linktitle: 新しい署名欄を作成して署名する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書にデジタル署名をシームレスに追加する方法を学びます。この包括的なチュートリアルでは、環境の設定、署名行の挿入から、署名済み文書の保存と検証まで、すべてを網羅しています。
type: docs
weight: 10
url: /ja/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## 導入

Word 文書にデジタル署名を追加したいですか? Aspose.Words for .NET を使用すると、思ったより簡単にできます。このチュートリアルでは、環境の設定、署名行の追加、文書へのデジタル署名の手順を説明します。さあ、始めましょう!

## 前提条件

コードに進む前に、次のものを用意してください。

1.  Aspose.Words for .NET -[ここからダウンロード](https://releases.aspose.com/words/net/).
2. .NET 開発環境 - Visual Studio はこのタスクに最適です。
3. 署名する文書 - 新しい Word 文書を作成することも、既存の文書を使用することもできます。
4. 証明書ファイル - A`.pfx`デジタル署名にはこのファイルが必要です。
5. 署名行の画像 (オプション) - 署名用の画像ファイルを含めることができます。

## 必要な名前空間をインポートする

Aspose.Words の機能を使用するには、次の名前空間をインポートする必要があります。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## ステップ1: ドキュメントディレクトリの設定

まず、ドキュメント ディレクトリへのパスを定義します。これは、ドキュメントを保存および取得する場所になります。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; //ドキュメントディレクトリのパスを指定します
```

## ステップ2: 新しいドキュメントを作成する

次に、新しい Word 文書を作成しましょう。この文書は署名行のキャンバスとして機能します。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ3: 署名欄の挿入

さて、`DocumentBuilder`ドキュメントに署名行を挿入するクラス:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## ステップ4: ドキュメントを保存する

署名欄を挿入したら、文書を保存します。これは署名する前の重要なステップです。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## ステップ5: 署名オプションの設定

署名プロセスのオプションを設定します。これには、署名行 ID と、署名とともに表示するオプションの画像の指定が含まれます。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") //あなたのイメージへの道
};
```

## ステップ6: 証明書の読み込み

ドキュメントの署名に必要な証明書ファイルをロードします。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); //ファイル名とパスワードを調整する
```

## ステップ7: 文書に署名する

最後に、`DigitalSignatureUtil`クラス。署名されたドキュメントを、将来の参照用に新しい名前で保存します。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、Word 文書を作成し、署名欄を追加し、デジタル署名しました。この強力なツールは、文書の自動化を簡素化し、契約書や正式な文書が安全に署名され、認証されることを保証します。

## よくある質問

### 署名欄に他の画像形式を使用できますか?

はい、PNG、JPG、BMP など、さまざまな画像形式を使用できます。

### 使用する必要があるか`.pfx` file for the certificate?

はい、`.pfx`ファイルは、デジタル署名用の証明書と秘密鍵を保存するための標準形式です。

### 1 つの文書に複数の署名行を追加できますか?

もちろんです! 必要に応じて挿入手順を繰り返すことで、複数の署名行を挿入できます。

### デジタル証明書を持っていない場合はどうなりますか?

信頼できる証明機関からデジタル証明書を取得するか、OpenSSL などのツールを使用してデジタル証明書を生成する必要があります。

### 文書内のデジタル署名を検証するにはどうすればよいですか?

署名された文書を Word で開き、署名の詳細をチェックしてその信頼性と整合性を確認することで、デジタル署名を検証できます。