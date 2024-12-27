---
title: C# で予定出席者の参加者ステータスを設定する
linktitle: C# で予定出席者の参加者ステータスを設定する
second_title: Aspose.Email .NET メール処理 API
description: C# と Aspose.Email for .NET を使用して予定の出席者のステータスを管理する方法を学びます。ソース コード付きのステップ バイ ステップ ガイド。
type: docs
weight: 16
url: /ja/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## 導入

Aspose.Email for .NET は、.NET アプリケーションでの電子メール処理を効率化するために設計された、堅牢で機能豊富なライブラリです。このガイドでは、予定の作成と管理、出席者の追加、参加者のステータスの設定について段階的に説明し、.NET プロジェクトへの効率的な統合を実現します。

## 前提条件

始める前に、次のものがあることを確認してください。

- Visual Studio または互換性のある C# IDE の正常なインストール。
- Aspose.Email for .NET ライブラリの最新バージョン。
- C# とオブジェクト指向プログラミングの基礎知識。

ライブラリのインストールについては、[ダウンロードページ](https://releases.aspose.com/).

## 必要な名前空間をインポートする

開始するには、予定と電子メール コンポーネントを管理するための機能にアクセスするために必要な名前空間を含めます。

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## 予約インスタンスを作成する

Aspose.Email の予定は、会議やタスクなどのスケジュールされたイベントを表します。作成方法は次のとおりです。

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- 場所: 予定が行われる場所を指定します。
- StartTime と EndTime: 予定の期間を定義します。
- 主催者と出席者: 参加者とその役割を定義します。

## 予定に出席者を追加する

Aspose.Email を使用すると、出席者の電子メール アドレスと参加ステータスをプログラムで管理できます。

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## 参加者のステータスの管理

の`ParticipantStatus`プロパティは、出席者が予定の招待を承諾したか、辞退したか、または暫定的に承諾したかを判断するのに役立ちます。次の列挙値を使用します。

- 承認済み
- 拒否
- 仮の

例：

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## 会議の招待状として予定を送信する

予約の準備ができたら、招待メールとして送信できます。

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## 結論

Aspose.Email for .NET は、.NET アプリケーションでの予定管理を簡素化し、スケジュールされたイベントを効率的に作成、カスタマイズ、管理するためのツールを提供します。直感的な API により、コミュニケーション ワークフローを合理化し、シームレスな統合を実現できます。

## よくある質問

### Aspose.Email for .NET とは何ですか?

Aspose.Email for .NET は、.NET アプリケーションで電子メール メッセージ、予定、およびその他の関連機能を処理するための包括的なライブラリです。

### 予約プロパティをカスタマイズできますか?

はい、場所、開始時間、参加者などのプロパティは完全にカスタマイズできます。

### 図書館は定期的な予約をサポートしていますか?

はい、Aspose.Email for .NET は、繰り返しパターン API を使用して定期的な予定をサポートします。

### Aspose.Email for .NET のサポートはどこで受けられますか?

詳細なドキュメントとコミュニティサポートについては、[サポートページ](https://forum.aspose.com/c/email/11).