---
title: Aspose.Zip for .NET で Zip ファイルを変更する
linktitle: Zipファイルの変更
second_title: ファイル圧縮とアーカイブのための Aspose.Zip .NET API
description: プログラムによって zip ファイルのエントリを効率的に抽出、削除、追加し、ファイル操作機能を強化する方法を学習します。
type: docs
weight: 15
url: /ja/net/tutorials/zip/file-compress/modify-zip-files/
---
## 導入

Zip ファイルはデータの整理と圧縮に不可欠ですが、その内容をプログラムで変更するにはどうすればよいでしょうか。解決策は、C# による Zip ファイルの操作を簡素化する強力なライブラリである Aspose.Zip for .NET にあります。このチュートリアルでは、Zip ファイルの抽出、削除、エントリの追加を手順ごとに説明します。

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Zip for .NETライブラリ: プロジェクトにライブラリをインストールします。ダウンロードできます。[ここ](https://releases.aspose.com/zip/net/).
   
2. ドキュメントディレクトリ: zipファイルを保存するディレクトリを設定します。`"Your Document Directory"`コード内の実際のパスを入力します。

## 必要な名前空間をインポートする

まず、必要な名前空間をインポートします。

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## ステップ1: 外側のZipファイルを開く

まず、メインの zip ファイル (外側の zip) を開きます。

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    //内部のZIPエントリの識別に進みます
}
```

## ステップ2: 内部のZIPエントリを特定する

次に、内部の zip ファイルを特定し、削除する準備をします。

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            //内部エントリの抽出
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## ステップ3: 内部アーカイブエントリを削除する

必要なエントリを収集したら、内部の zip エントリを削除します。

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## ステップ4: 外部Zipに変更されたエントリを追加する

これで、新しく抽出したエントリを外部の zip ファイルに戻すことができます。

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## ステップ5: 変更したZipファイルを保存する

最後に、変更を新しい zip ファイルに保存します。

```csharp
outer.Save(dataDir + "flatten.zip");
```

## 結論

Aspose.Zip for .NET は、プログラムで zip ファイルを操作する強力で簡単な方法を提供します。このチュートリアルでは、zip ファイルのエントリの抽出、削除、追加について説明し、ライブラリの汎用性を示しました。さまざまなシナリオを調べて、ファイル操作スキルを高めましょう。

## よくある質問

### Aspose.Zip for .NET を他のプログラミング言語で使用できますか?
Aspose.Zip は主に .NET アプリケーション用に設計されていますが、Aspose はさまざまなプログラミング言語向けに同様のライブラリを提供しています。

### Aspose.Zip for .NET の無料試用版はありますか?
はい、無料トライアルをダウンロードできます[ここ](https://releases.aspose.com/).

### Aspose.Zip for .NET のサポートを受けるにはどうすればよいですか?
訪問する[Aspose.Zip フォーラム](https://forum.aspose.com/c/zip/37)サポートとディスカッションのため。

### Aspose.Zip for .NET の一時ライセンスを購入できますか?
はい、一時ライセンスを取得できます[ここ](https://purchase.conholdate.com/temporary-license/).

### Aspose.Zip for .NET のドキュメントはどこにありますか?
完全なドキュメントは入手可能です[ここ](https://reference.aspose.com/zip/net/).