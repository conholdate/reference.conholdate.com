---
title: Chuyển đổi DOCX sang MHTML và gửi email bằng Aspose.Words cho .NET
linktitle: Chuyển đổi DOCX sang MHTML và gửi email bằng Aspose.Words cho .NET
second_title: API xử lý tài liệu Aspose.Words
description: Hướng dẫn toàn diện này cung cấp hướng dẫn từng bước về cách chuyển đổi tài liệu DOCX sang định dạng MHTML và gửi email bằng thư viện Aspose.Words và Aspose.Email trong .NET.
type: docs
weight: 10
url: /vi/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Giới thiệu

Trong bối cảnh kỹ thuật số ngày nay, việc chuyển đổi tài liệu giữa các định dạng và gửi email là một nhiệm vụ phổ biến. Hướng dẫn này sẽ hướng dẫn bạn cách chuyển đổi tệp DOCX sang định dạng MHTML và gửi qua email bằng các thư viện Aspose.Words và Aspose.Email mạnh mẽ dành cho .NET. Chúng tôi sẽ chia nhỏ từng bước một cách rõ ràng, đảm bảo bạn có thể dễ dàng theo dõi. Hãy bắt đầu nào!

## Điều kiện tiên quyết

Trước khi bắt đầu quá trình, hãy đảm bảo bạn đã thiết lập xong những điều sau:

1.  Aspose.Words cho .NET: Tải xuống và cài đặt thư viện từ[Trang phát hành Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email cho .NET: Tải xuống và cài đặt thư viện này từ[Trang phát hành Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Đảm bảo rằng bạn đã cài đặt .NET Framework trên máy của mình.
4. Máy chủ SMTP: Bạn sẽ cần truy cập vào máy chủ SMTP để gửi email.

## Nhập các không gian tên cần thiết

Để sử dụng Aspose.Words và Aspose.Email trong dự án của bạn, bạn phải nhập các không gian tên bắt buộc. Thêm các chỉ thị using sau vào đầu tệp C# của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Bước 1: Tải Tài liệu DOCX

 Bắt đầu bằng cách tải tài liệu DOCX mà bạn muốn chuyển đổi. Sử dụng`Document` lớp từ Aspose.Words để thực hiện việc này.

```csharp
// Chỉ định đường dẫn đến thư mục tài liệu của bạn.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Bước 2: Lưu tài liệu dưới dạng MHTML

 Tiếp theo, chuyển đổi tài liệu đã tải thành định dạng MHTML. Điều này được thực hiện bằng cách sử dụng`Save` phương pháp của`Document` lớp học.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Đặt lại vị trí luồng về đầu để đọc.
    stream.Position = 0;
}
```

## Bước 3: Tạo tin nhắn email

Bây giờ, hãy tạo một tin nhắn email từ luồng MHTML bằng Aspose.Email. Bạn sẽ sử dụng`MailMessage` lớp học dành cho mục đích này.

```csharp
// Tải luồng MHTML vào tin nhắn email MIME của Aspose.Email.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Bước 4: Gửi Email

 Cuối cùng, gửi email bằng máy khách SMTP. Cấu hình máy khách SMTP với thông tin chi tiết máy chủ của bạn và sử dụng`Send` phương pháp gửi tin nhắn.

```csharp
// Cấu hình và gửi tin nhắn bằng Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Phần kết luận

Xin chúc mừng! Bạn đã chuyển đổi thành công một tài liệu DOCX sang MHTML và gửi qua email bằng Aspose.Words và Aspose.Email cho .NET. Quá trình này bao gồm việc tải tài liệu, chuyển đổi sang MHTML, tạo tin nhắn email và gửi qua máy khách SMTP. Với các bước này, bạn có thể tự động chuyển đổi và gửi email tài liệu một cách liền mạch trong các ứng dụng của mình.

## Câu hỏi thường gặp

### Tôi có thể sử dụng phương pháp này để chuyển đổi các định dạng tài liệu khác không?
Chắc chắn rồi! Aspose.Words hỗ trợ nhiều định dạng, cho phép bạn chuyển đổi DOC, DOCX, RTF, v.v. sang MHTML.

### Làm thế nào để thêm tệp đính kèm vào email?
 Bạn có thể dễ dàng thêm tệp đính kèm bằng cách sử dụng`Attachments` tài sản của`MailMessage` lớp học.

### Aspose.Words có tương thích với .NET Core không?
Có, Aspose.Words tương thích với .NET Core, do đó phù hợp để sử dụng trong các ứng dụng .NET Core.

### Tôi có cần giấy phép sử dụng Aspose.Words và Aspose.Email không?
 Có, cả hai thư viện đều yêu cầu giấy phép. Bạn có thể xin giấy phép tạm thời cho mục đích đánh giá từ[Trang mua hàng Aspose](https://purchase.conholdate.com/temporary-license/).

### Tôi có thể tìm thêm tài liệu ở đâu?
 Để biết tài liệu chi tiết, hãy xem Aspose.Words[đây](https://reference.aspose.com/words/net/) và Aspose.Email[đây](https://reference.aspose.com/email/net/).