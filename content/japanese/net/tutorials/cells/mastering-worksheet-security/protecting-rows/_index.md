---
title: Aspose.Cells を使用してワークシートの行を保護する
linktitle: Aspose.Cells を使用してワークシートの行を保護する
second_title: Aspose.Cells .NET Excel 処理 API
description: Aspose.Cells for .NET を使用して特定の行を保護し、Excel ワークシート内の機密情報を保護する方法を学びます。この包括的なチュートリアルでは、環境の設定からすべてをカバーしています。
type: docs
weight: 18
url: /ja/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## 導入

Excel ファイルをプログラムで操作する場合、多くの場合、データ操作だけでなくデータ保護も必要になります。ワークシート内の特定の行を保護することは、機密情報を保護したり、誤って編集されないようにするために重要です。このチュートリアルでは、Aspose.Cells for .NET を使用して Excel ワークシート内の行を保護する方法について説明します。環境の設定から行保護機能の実装まで、必要な手順をわかりやすく説明します。

## 前提条件
始める前に、次のものを用意してください。

1.  Aspose.Cells for .NET: ダウンロードしてインストールしてください。[Aspose Cells ダウンロード ページ](https://releases.aspose.com/cells/net/).
2. Visual Studio または任意の .NET IDE: 開発環境が必要です。Visual Studio が推奨されますが、.NET と互換性のある IDE であればどれでも十分です。
3. 基本的な C# の知識: C# プログラミングの知識があれば、サンプル コードを理解し、必要に応じて変更するのに役立ちます。
4.  Aspose.Cells APIドキュメント:[Aspose.Cells for .NET ドキュメント](https://reference.aspose.com/cells/net/)クラス構造とメソッドの概要については、こちらをご覧ください。

前提条件が整えば、実装に進むことができます。

## 必要なパッケージをインポートする
まず、C# プロジェクトに必要なパッケージをインポートします。これらのライブラリは、Excel ファイルの操作に不可欠です。

```csharp
using System.IO;
using Aspose.Cells;
```

## ステップ1: 新しいワークブックとワークシートを作成する
保護設定を適用する前に、新しいブックを作成し、作業するワークシートを選択します。

```csharp
//ドキュメント ディレクトリへのパスを定義します。
string dataDir = "Your Document Directory";
//ディレクトリが存在しない場合は作成します。
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

//新しいワークブックを作成し、最初のワークシートを選択します。
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## ステップ2: スタイルとスタイルフラグオブジェクトを定義する
スタイルとスタイル フラグ オブジェクトを定義します。これにより、セルのロックやロック解除などのセル プロパティを変更できるようになります。

```csharp
//スタイルとスタイル フラグ オブジェクトを定義します。
Style style;
StyleFlag flag;
```

## ステップ3: ワークシート内のすべての列のロックを解除する
デフォルトでは、Excel ワークシート内のすべてのセルがロックされています。特定の行のみを保護するには、まずすべての列のロックを解除します。

```csharp
//すべての列をループしてロックを解除します。
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## ステップ4: 特定の行をロックする
次に、保護する行をロックします。この例では、最初の行をロックします。

```csharp
//最初の行をロックします。
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

ロックする追加の行がある場合は、この手順を繰り返すことができます。

## ステップ5: シートを保護する
必要な行をロックしたら、ワークシートを保護します。これにより、保護を解除しない限り、ロックされた行が変更されなくなります。

```csharp
//シートを保護します。
sheet.Protect(ProtectionType.All);
```

## ステップ6: ワークブックを保存する
最後に、変更を適用したブックを保存します。Excel 97-2003 以降のバージョンなど、さまざまな形式から選択できます。

```csharp
// Excel ファイルを保存します。
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## 結論
おめでとうございます。Aspose.Cells for .NET を使用して Excel ワークシートの行を保護する方法を学習しました。これらの手順に従うことで、必要に応じて行または列のロックを解除またはロックし、保護を適用してデータの整合性を維持することができます。

## よくある質問
### 複数の行を一度に保護するにはどうすればよいですか?
複数の行インデックスをループし、それぞれにロック スタイルを個別に適用できます。

### シート保護のためにパスワードを設定できますか?
はい、パスワードを渡すことは可能です`sheet.Protect()`パスワード保護を強制する方法。

### 列全体ではなく特定のセルのロックを解除できますか?
はい、列全体のロックを解除するのではなく、スタイル プロパティを変更することで個々のセルのロックを解除できます。

### 保護された行を編集しようとするとどうなりますか?
行が保護されている場合、シートが保護されていない限り、Excel ではロックされたセルへの編集ができなくなります。

### 行内の特定の範囲を保護することはできますか?
はい！設定することで、行内の個々の範囲をロックできます。`IsLocked`その範囲内の特定のセルのプロパティ。