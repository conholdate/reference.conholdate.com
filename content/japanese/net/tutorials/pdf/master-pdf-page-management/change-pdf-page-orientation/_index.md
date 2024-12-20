---
title: PDFページの向きを変更する
linktitle: PDFページの向きを変更する
second_title: Aspose.PDF for .NET API リファレンス
description: Aspose.PDF for .NET を使用して PDF ファイルのページの向きを簡単に調整する方法を説明します。このステップ バイ ステップ ガイドでは、ドキュメントの読み込み、回転、保存に関する明確な手順を説明します。
type: docs
weight: 10
url: /ja/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## 導入

ページの向きがまったく間違っている PDF ファイルに遭遇したことはありませんか? ドキュメントが間違ってスキャンされているか、単にレイアウトを変更する必要がある場合でも、向きを調整するだけで大きな違いが生じます。幸いなことに、Aspose.PDF for .NET は、ページの向きの変更など、PDF ファイルを操作する強力で使いやすい方法を提供します。このガイドでは、縦向きから横向きに切り替える場合も、その逆の場合も、プロセスをステップごとに説明します。

## 前提条件

詳細に入る前に、次のものを用意しておいてください。

-  Aspose.PDF for .NET: Aspose.PDFライブラリがインストールされていることを確認してください。まだインストールしていない場合は、[ここからダウンロード](https://releases.aspose.com/pdf/net/).
- .NET 開発環境: .NET 開発には、Visual Studio、JetBrains Rider、またはその他の任意の IDE を使用できます。
- C# の基礎知識: C# に精通していると、より簡単に理解できるようになります。
- PDF ファイル: テスト用にサンプルの PDF ファイルを用意します。サンプルを作成するか、オンラインでダウンロードすることができます。

始めたばかりの方は、Aspose.PDFを試してみることを検討してください。[無料の一時ライセンス](https://purchase.aspose.com/temporary-license/)決める前に[フルバージョンを購入する](https://purchase.aspose.com/buy).

## 名前空間のインポート

PDF ページを操作するには、まず C# プロジェクトに必要な名前空間をインポートする必要があります。コード ファイルの先頭に次の行を追加します。

```csharp
using System.IO;
using Aspose.Pdf;
```

準備がすべて整ったので、始めましょう!

## ステップ1: PDFドキュメントを読み込む

最初のステップは、変更したいPDFファイルを読み込むことです。`Document` Aspose.PDF 名前空間からのクラス:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

必ず交換してください`"YOUR DOCUMENT DIRECTORY"` PDF ファイルへの実際のパスを入力します。

## ステップ2: 各ページをループする

次に、PDF ドキュメントの各ページをループします。これにより、すべてのページに向きの変更を適用できます。

```csharp
foreach (Page page in doc.Pages)
{
    //各ページを操作する
}
```

## ステップ3: ページのメディアボックスにアクセスする

各PDFページには`MediaBox`境界を定義します。現在の方向を確認し、調整するには、これにアクセスする必要があります。

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

の`MediaBox`幅と高さを含むページの寸法を提供します。

## ステップ4: 幅と高さを入れ替える

ページの向きを変更するには、幅と高さの値を入れ替えます。この調整により、ページのサイズが変更されます。

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

ここで、新しい寸法を計算し、左下隅（`LLY`） それに応じて。

## ステップ5: MediaBoxとCropBoxを更新する

新しいディメンションができたので、これらの変更を`MediaBox`そして`CropBox`ページが正しく表示されるようにするには:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## ステップ6: ページを回転する

方向の変更を完了するには、ページを回転させます。これは Aspose.PDF を使用すると簡単です。

```csharp
page.Rotate = Rotation.on90; // 90度回転
```

この行は、ページを目的の方向に効果的に反転します。

## ステップ7: 出力PDFを保存する

すべてのページの向きを変更したら、更新されたドキュメントを新しいファイルに保存します。

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

元のドキュメントが上書きされないように、必ず新しいファイル名を指定してください。

## 結論

これで完了です。Aspose.PDF for .NET を使用して PDF ファイルのページの向きを変更するのは簡単なプロセスです。ドキュメントを読み込み、ページをループし、MediaBox を更新して、ファイルを保存するだけで、ニーズに合わせてレイアウトを簡単に調整できます。スキャンが不十分なドキュメントを修正する場合でも、プレゼンテーション用にページをフォーマットする場合でも、このガイドは作業を効率的に行うのに役立ちます。

## よくある質問

### PDF 内のすべてのページではなく、特定のページを回転できますか?  
はい、すべてのページを反復処理するのではなく、インデックスによって特定のページをターゲットにするようにループを変更できます。

### 何ですか`MediaBox`?  
の`MediaBox` PDF ファイル内のページのサイズと形状を定義し、コンテンツが配置される場所を決定します。

### Aspose.PDF for .NET は他のファイル形式でも動作しますか?  
はい、Aspose.PDF は HTML、XML、XPS など、さまざまなファイル形式を処理できます。

### Aspose.PDF for .NET の無料バージョンはありますか?  
はい、まずは[無料トライアル](https://releases.aspose.com/)またはリクエスト[一時ライセンス](https://purchase.aspose.com/temporary-license/).

### 一度保存した変更を元に戻すことはできますか?  
ドキュメントを保存すると、変更は永続的になります。コピーで作業するか、元のファイルのバックアップを保存しておくことをお勧めします。