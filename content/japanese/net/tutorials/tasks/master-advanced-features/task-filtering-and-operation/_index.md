---
title: Aspose.Tasks でのタスク フィルタリング AND 操作
linktitle: Aspose.Tasks でのタスク フィルタリング AND 操作
second_title: Aspose.Tasks .NET API
description: Aspose.Tasks for .NET のクラスを活用して、複数の条件に基づいてプロジェクト タスクをフィルター処理する方法を学びます。サマリー タスクや null 以外の属性などの基準を組み合わせます。
type: docs
weight: 10
url: /ja/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## 導入

このチュートリアルでは、Aspose.Tasks for .NETでプロジェクトタスクの高度なフィルタリングを実行する方法について説明します。`Util.And`クラス。この強力な機能により、開発者は複数の基準に基づいてタスクを効率的にフィルタリングできます。

## 前提条件

始める前に、以下のものを用意してください。

1. C# プログラミングの基礎知識。
2.  Aspose.Tasks for .NET がインストールされている。まだインストールしていない場合は、こちらからダウンロードできます。[このリンク](https://releases.aspose.com/tasks/net/).
3. コードを記述して実行するための Visual Studio などの統合開発環境 (IDE)。

## 名前空間のインポート

まず、必要な名前空間を C# プロジェクトにインポートする必要があります。これにより、Aspose.Tasks が提供する機能にアクセスできるようになります。

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## ステップ1: プロジェクトを初期化し、タスクを収集する

まず、Aspose.Tasksプロジェクトを初期化し、その中にあるすべてのタスクを収集します。デモの目的で、次のプロジェクトファイルがあると仮定します。`Project2.mpp`.

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

//すべての子タスクを収集する
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## ステップ2: フィルター条件を定義する

このステップでは、タスクをフィルタリングするための条件を定義します。 この例では、サマリー タスクをフィルタリングするための条件と、タスクが null でないことを確認するための条件の 2 つを作成します。

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## ステップ3: AND演算で条件を組み合わせる

次のステップは、これらの条件を`Util.And`クラス。これにより、両方の基準を必須とする複合条件を作成できます。

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## ステップ4: 複合条件とフィルタータスクを適用する

ここで、収集されたタスクに結合条件を適用して、両方の条件を満たす特定のタスクをフィルター処理してみましょう。

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## ステップ5: フィルタリングされたタスクを出力する

最後に、フィルタリングされたタスクを反復処理し、関連する詳細を出力します。これにより、基準を満たすタスクを理解するのに役立ちます。

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## 結論

このチュートリアルでは、Aspose.Tasks for .NETで高度なフィルタリング操作を実行する方法を説明しました。`Util.And`クラス。複数の条件を組み合わせることで、タスクを効果的にフィルタリングし、プロジェクト管理アプリケーションの有用性を高めることができます。

## よくある質問

### Aspose.Tasks for .NET とは何ですか?

Aspose.Tasks for .NET は、開発者が .NET アプリケーション内でプログラムによって Microsoft Project ファイルを操作できるように設計された包括的な API です。

### Util.And を使用して 2 つ以上の条件を組み合わせることはできますか?

はい！`Util.And`クラスを使用すると、複数の条件を組み合わせて、ニーズに合わせた複雑なフィルタリング ロジックを実現できます。

### Aspose.Tasks の無料試用版はありますか?

はい、無料試用版は以下からダウンロードできます。[このリンク](https://releases.aspose.com/).

### Aspose.Tasks の詳細なドキュメントはどこで入手できますか?

詳細なドキュメントが利用可能[ここ](https://reference.aspose.com/tasks/net/).

### Aspose.Tasks のサポートを受けるにはどうすればよいですか?

サポートはAspose.Tasksコミュニティフォーラムを通じて提供され、以下のリンクからアクセスできます。[ここ](https://forum.aspose.com/c/tasks/15).