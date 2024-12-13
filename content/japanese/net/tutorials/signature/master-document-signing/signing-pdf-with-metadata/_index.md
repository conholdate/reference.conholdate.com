---
title: GroupDocs.Signature を使用してメタデータで PDF に署名するためのガイド
linktitle: メタデータを使用して PDF に署名するためのガイド
second_title: GroupDocs.Signature .NET API
description: GroupDocs.Signature for .NET を使用してメタデータで署名し、強化されたセキュリティと追跡可能性で PDF ドキュメントを強化する方法を学びます。この包括的なチュートリアルでは、明確な手順を説明します。
type: docs
weight: 11
url: /ja/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## 導入

このチュートリアルでは、GroupDocs.Signature for .NET を使用して PDF ドキュメントに署名し、メタデータを追加する方法を学習します。メタデータを追加すると、作成者、作成日、ドキュメント ID などの重要な情報が提供され、ドキュメントが強化されます。

## 前提条件

始める前に、以下のものを用意してください。

1.  GroupDocs.Signature for .NET: ダウンロードはこちらから[ここ](https://releases.groupdocs.com/signature/net/).
2. PDF ドキュメント: 署名用のサンプル PDF ファイルを用意します。
3. C# プログラミングの基礎知識: コード例を理解するには、C# 構文に精通している必要があります。

## 名前空間のインポート

必要なクラスとメソッドにアクセスするために必要な名前空間をインポートすることから始めます。

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## ステップ1: PDFドキュメントを読み込む

署名する PDF ドキュメントのパスを指定します。

```csharp
string filePath = "sample.pdf";
```

## ステップ2: 出力ファイルのパスを指定する

メタデータ付きの署名済み PDF を保存する場所を定義します。

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## ステップ3: 署名インスタンスを作成する

初期化する`Signature`PDF ドキュメントへのパスを持つインスタンス:

```csharp
using (Signature signature = new Signature(filePath))
{
    //署名関連のコードはここに記入します
}
```

## ステップ4: メタデータオプションを定義する

作成する`MetadataSignOptions`メタデータ フィールドとその値を追加します。

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) //文字列値
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       //日時値
    .Add(new PdfMetadataSignature("DocumentId", 123456))            //整数値
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         //二重価値
    .Add(new PdfMetadataSignature("Amount", 123.456M))              //小数値
    .Add(new PdfMetadataSignature("Total", 123.456F));              //浮動小数点値
```

## ステップ5: 文書に署名する

指定されたメタデータ オプションを使用して PDF ドキュメントに署名し、署名されたドキュメントを保存します。

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## 結論

このチュートリアルでは、GroupDocs.Signature for .NET を使用してメタデータで PDF ドキュメントに署名する方法について説明しました。これらの手順に従うことで、貴重なメタデータで PDF ファイルを簡単に充実させ、追跡可能性と実用性を向上させることができます。

## よくある質問

### PDF ドキュメントにカスタム メタデータ フィールドを追加できますか?

はい、GroupDocs.Signature for .NET を使用してフィールド名と対応する値を指定することにより、カスタム メタデータ フィールドを追加できます。

### GroupDocs.Signature for .NET は、.NET Framework のすべてのバージョンと互換性がありますか?

GroupDocs.Signature for .NET は、さまざまなバージョンの .NET Framework と互換性があり、柔軟性と統合の容易さを保証します。

### GroupDocs.Signature は PDF 以外のドキュメント形式への署名をサポートしていますか?

はい、GroupDocs.Signature は、Word、Excel、PowerPoint など、幅広いドキュメント形式をサポートしています。

### GroupDocs.Signature for .NET を使用して複数のドキュメントに一括で署名できますか?

もちろんです! ファイルのリストを反復処理し、署名プロセスをプログラムで適用することで、複数のドキュメントに一括で署名できます。

### GroupDocs.Signature ユーザー向けのテクニカル サポートは利用できますか?

はい、GroupDocsはフォーラムを通じて専用の技術サポートを提供しています。サポートフォーラムにアクセスできます。[ここ](https://forum.groupdocs.com/c/signature/13).