---
title: Aspose.Email for .NET でメール変換の進行状況を追跡する
linktitle: Aspose.Email for .NET でメール変換の進行状況を追跡する
second_title: Aspose.Email .NET メール処理 API
description: Aspose.Email for .NET を使用して C# で電子メール変換の進行状況を追跡する方法を段階的に学習します。この詳細なチュートリアルでプロジェクトの効率を高めます。
type: docs
weight: 12
url: /ja/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## 導入

電子メール ドキュメントを効率的に管理するには、多くの場合、変換の進行状況を追跡する必要があります。Aspose.Email for .NET には、これを実現するための強力なツールが用意されており、開発者は電子メール操作をシームレスに処理できます。このチュートリアルでは、C# で電子メール ドキュメントの変換の進行状況を追跡する方法を詳しく説明し、プロセスをわかりやすく段階的に説明します。  

## 前提条件  

チュートリアルに進む前に、すべてが設定されていることを確認しましょう。  

1.  .NET 用 Aspose.Email: ダウンロードしてインストールする[Aspose.Email for .NET](https://releases.aspose.com/email/net/)図書館。  
2. 開発環境: Visual Studio またはその他の .NET 互換 IDE をインストールします。  
3. .NET Framework: .NET Framework 4.5 以降がインストールされていることを確認します。  
4. 一時ライセンス：取得を検討してください[一時ライセンス](https://purchase.aspose.com/temporary-license/)Aspose.Email の全機能をご確認ください。  
5. サンプルメールファイル:`.eml`ファイル（例：`test.eml`）をサンプルとして使用します。  

## パッケージのインポート  

プロジェクトで Aspose.Email を使用するには、必要な名前空間をインポートする必要があります。ファイルの先頭に次の using ステートメントを追加します。  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## ステップ1: プロジェクトを設定する  

まず、Visual Studio で新しい C# コンソール アプリケーションを作成します。これは、電子メール ドキュメントの変換追跡を実装するための基盤として機能します。  
  
1. Visual Studio を開き、新しいコンソール アプリケーション プロジェクトを作成します。  
2. Aspose.Email NuGet パッケージをインストールします。  
```sh
Install-Package Aspose.Email
```  
3. 追加する`.eml`ファイルをプロジェクト ディレクトリに追加します。  

## ステップ2: メールファイルを読み込む  

次に、メールファイルを`MailMessage`オブジェクト。これは、電子メール データを操作する最初のステップです。  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: 電子メール ファイルが保存されているディレクトリを指定します。  
- `MailMessage.Load` : 読み取り`.eml`ファイルを生成し、その後の操作のために準備します。  

## ステップ3: メモリストリームを初期化する  

次に、`MemoryStream`変換された電子メールデータを一時的に保存するオブジェクト。  
 
```csharp
MemoryStream ms = new MemoryStream();
```

あ`MemoryStream`ここでは、データを直接ディスクに保存せずに、変換プロセスの出力を管理するために使用されます。  

## ステップ4: 変換オプションを定義する  

セットアップ`EmlSaveOptions`変換の進行状況を追跡するためのカスタム進行状況ハンドラーを使用します。  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: 出力形式を指定します。  
- `CustomProgressHandler`: 進行状況を監視するためのカスタム ハンドラー関数を割り当てます。  

## ステップ5: メールをメモリストリームに保存する  

保存する`MailMessage`指定されたオプションを使用してオブジェクトを作成し、進行状況追跡機能を有効にします。  
 
```csharp
msg.Save(ms, opt);
```
 
このステップでは、電子メール変換プロセスを開始し、進行状況ハンドラーに更新を送信します。  

## ステップ6: 進行状況ハンドラーを実装する  

定義する`ShowEmlConversionProgress`進行状況の更新を処理し、コンソールに表示するメソッド。  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: 変換プロセスの詳細を提供します。  
-  Switch Cases: 変換のさまざまな段階を処理します。`MimeStructureCreated`, `MimePartSaved` 、 そして`SavedToStream`.  

### 何を期待しますか?  
変換が進むにつれて、次のような詳細な更新がコンソールに表示されます。  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## 結論  

Aspose.Email for .NET のおかげで、C# での電子メール ドキュメントの変換進行状況の追跡がこれまでになく簡単になりました。このチュートリアルでは、電子メール ファイルを読み込み、進行状況ハンドラーを設定し、プロセス全体を監視しながら電子メール データを保存する方法を学習しました。この機能により、電子メール ドキュメントの操作中に情報を入手し、制御を維持できます。  

## よくある質問  

### このコードは他の形式でも使用できますか？`.eml`?  
はい、変更します`MailMessageSaveType`MSG や MHTML などの他の形式に適合します。  

### 大きな電子メールファイルをどのように処理すればよいですか?  
使用を検討してください`FileStream`代わりに`MemoryStream`大きなファイルでのパフォーマンスが向上します。  

### 一時ライセンスとは何ですか? また、どのように取得できますか?  
一時ライセンスでは、ライブラリの全機能を無料で評価できます。入手[ここ](https://purchase.aspose.com/temporary-license/).  

### このコードを Web アプリケーションに統合できますか?  
はい、コードは ASP.NET または同様のフレームワークを使用する Web アプリケーションと互換性があります。  

### 追加のリソースはどこで見つかりますか?  
チェックしてください[ドキュメント](https://reference.aspose.com/email/net/)または、[サポートフォーラム](https://forum.aspose.com/c/email/12/)助けを求めて。  