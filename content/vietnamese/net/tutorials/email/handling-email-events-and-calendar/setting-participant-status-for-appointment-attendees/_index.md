---
title: Thiết lập trạng thái người tham gia cho người tham dự cuộc hẹn bằng C#
linktitle: Thiết lập trạng thái người tham gia cho người tham dự cuộc hẹn bằng C#
second_title: API xử lý email Aspose.Email .NET
description: Tìm hiểu cách quản lý trạng thái người tham dự cuộc hẹn bằng C# và Aspose.Email cho .NET. Hướng dẫn từng bước có mã nguồn.
type: docs
weight: 16
url: /vi/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Giới thiệu

Aspose.Email for .NET là một thư viện mạnh mẽ và giàu tính năng được thiết kế để hợp lý hóa việc xử lý email trong các ứng dụng .NET. Hướng dẫn này cung cấp hướng dẫn từng bước về cách tạo và quản lý cuộc hẹn, thêm người tham dự và thiết lập trạng thái của người tham gia, đảm bảo tích hợp hiệu quả vào các dự án .NET của bạn.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

- Cài đặt Visual Studio hoặc IDE C# tương thích.
- Phiên bản mới nhất của thư viện Aspose.Email cho .NET.
- Kiến thức cơ bản về C# và lập trình hướng đối tượng.

 Để cài đặt thư viện, hãy tham khảo[trang tải xuống](https://releases.aspose.com/).

## Nhập không gian tên bắt buộc

Để bắt đầu, hãy bao gồm các không gian tên cần thiết để truy cập các chức năng quản lý cuộc hẹn và thành phần email.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Tạo một phiên bản cuộc hẹn

Cuộc hẹn trong Aspose.Email đại diện cho các sự kiện đã lên lịch như cuộc họp hoặc nhiệm vụ. Sau đây là cách bạn tạo một cuộc hẹn:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Địa điểm: Chỉ định nơi cuộc hẹn sẽ diễn ra.
- StartTime và EndTime: Xác định thời lượng của cuộc hẹn.
- Người tổ chức và người tham dự: Xác định người tham gia và vai trò của họ.

## Thêm người tham dự vào cuộc hẹn

Aspose.Email cho phép bạn quản lý người tham dự theo chương trình với địa chỉ email và trạng thái tham gia của họ.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Quản lý trạng thái của người tham gia

 Các`ParticipantStatus` thuộc tính giúp xác định xem người tham dự đã chấp nhận, từ chối hay chấp nhận tạm thời lời mời hẹn gặp. Sử dụng các giá trị liệt kê sau:

- Đã chấp nhận
- Từ chối
- Dự kiến

Ví dụ:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Gửi cuộc hẹn dưới dạng lời mời họp

Sau khi cuộc hẹn đã được chuẩn bị, bạn có thể gửi nó dưới dạng email mời:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Phần kết luận

Aspose.Email for .NET đơn giản hóa việc quản lý cuộc hẹn trong các ứng dụng .NET, cung cấp các công cụ để tạo, tùy chỉnh và quản lý các sự kiện theo lịch trình một cách hiệu quả. Với API trực quan, bạn có thể hợp lý hóa quy trình giao tiếp và đảm bảo tích hợp liền mạch.

## Câu hỏi thường gặp

### Aspose.Email cho .NET là gì?

Aspose.Email for .NET là một thư viện toàn diện để xử lý tin nhắn email, cuộc hẹn và các chức năng liên quan khác trong các ứng dụng .NET.

### Tôi có thể tùy chỉnh thuộc tính cuộc hẹn không?

Có, các thuộc tính như địa điểm, thời gian bắt đầu và người tham gia có thể được tùy chỉnh hoàn toàn.

### Thư viện có hỗ trợ đặt lịch hẹn định kỳ không?

Có, Aspose.Email for .NET hỗ trợ các cuộc hẹn định kỳ bằng API mẫu lặp lại.

### Tôi có thể nhận hỗ trợ cho Aspose.Email cho .NET ở đâu?

 Bạn có thể truy cập tài liệu chi tiết và hỗ trợ cộng đồng tại[trang hỗ trợ](https://forum.aspose.com/c/email/11).