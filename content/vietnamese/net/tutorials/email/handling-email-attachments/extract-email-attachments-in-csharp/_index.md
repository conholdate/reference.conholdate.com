---
title: Trích xuất tệp đính kèm email trong C# - Hướng dẫn Aspose.Email
linktitle: Trích xuất tệp đính kèm email trong C# - Hướng dẫn Aspose.Email
second_title: API xử lý email Aspose.Email .NET
description: Tìm hiểu cách trích xuất tệp đính kèm email trong C# bằng Aspose.Email cho .NET. Hướng dẫn từng bước với các ví dụ cho PDF, hình ảnh và nhiều nội dung khác.
type: docs
weight: 14
url: /vi/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## Giới thiệu

Bạn đã bao giờ thấy mình phải tải xuống thủ công từng tệp đính kèm email chưa? Việc này không chỉ tốn thời gian mà còn dễ xảy ra lỗi. May mắn thay, Aspose.Email for .NET cung cấp một cách mạnh mẽ và hiệu quả để tự động hóa tác vụ này. Cho dù bạn đang xử lý PDF, hình ảnh hay bất kỳ loại tệp nào khác, bạn có thể trích xuất tệp đính kèm một cách dễ dàng bằng C#.

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn qua một hướng dẫn đầy đủ, bắt đầu từ các điều kiện tiên quyết đến một ví dụ hoạt động đầy đủ. Sẵn sàng tiết kiệm hàng giờ làm việc thủ công? Hãy cùng bắt đầu!

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, hãy đảm bảo bạn có những điều sau:

- Đã cài đặt Visual Studio trên máy của bạn.
-  Aspose.Email cho thư viện .NET. Bạn có thể[tải xuống ở đây](https://releases.aspose.com/email/net/) hoặc cài đặt thông qua NuGet.
- Một tài khoản email hợp lệ (hỗ trợ IMAP/POP3).
- Hiểu biết cơ bản về lập trình C#.

 Nếu bạn mới sử dụng Aspose.Email, hãy cân nhắc yêu cầu[dùng thử miễn phí](https://releases.aspose.com/) hoặc một[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để mở khóa đầy đủ tính năng.

## Nhập gói

Trước khi đi sâu vào mã, hãy đảm bảo bạn đã nhập các không gian tên cần thiết. Thêm nội dung sau vào đầu tệp C# của bạn:

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

Hãy chia nhỏ quy trình thành các bước dễ hiểu. Thực hiện cẩn thận từng bước để đảm bảo thực hiện suôn sẻ.


## Bước 1: Thiết lập máy khách IMAP của bạn

Bước đầu tiên là kết nối với máy chủ email của bạn bằng giao thức IMAP. IMAP cho phép chúng ta truy cập và lấy thư email từ máy chủ.

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

-  Thay thế`imap.example.com` với địa chỉ máy chủ IMAP của nhà cung cấp email của bạn (ví dụ:`imap.gmail.com` dành cho Gmail).
-  Sử dụng email thực tế của bạn`username` Và`password`.
- `SelectFolder(ImapFolderInfo.InBox)`chỉ rõ rằng chúng ta muốn làm việc với hộp thư đến.


## Bước 2: Lấy lại Email từ Hộp thư đến

Sau khi kết nối, bạn cần lấy tin nhắn email từ hộp thư đến. Aspose.Email cung cấp một phương pháp đơn giản để liệt kê tất cả tin nhắn.

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()` lấy siêu dữ liệu cho tất cả email trong hộp thư đến.
-  Các`ImapMessageInfoCollection` đối tượng chứa các chi tiết như người gửi, chủ đề và ID duy nhất.


## Bước 3: Lấy từng tin nhắn email

Để truy cập nội dung và tệp đính kèm, bạn cần lấy từng email bằng ID duy nhất của email đó.


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

-  Các`foreach` vòng lặp lặp lại tất cả các tin nhắn.
- `FetchMessage()` lấy nội dung email thực tế cho một ID tin nhắn nhất định.


## Bước 4: Lặp qua các tệp đính kèm

 Bây giờ bạn đã có nội dung email, đã đến lúc trích xuất các tệp đính kèm. Mỗi`MailMessage` đối tượng chứa một tập hợp các tệp đính kèm.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

-  Các`Attachments` Thuộc tính này liệt kê tất cả các tệp đính kèm trong email.
-  Sử dụng`attachment.Name` để lấy tên tệp.


## Bước 5: Lưu tệp đính kèm vào đĩa

Cuối cùng, lưu tệp đính kèm vào máy cục bộ của bạn. Bạn có thể lọc tệp theo loại, kích thước hoặc tiêu chí khác.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

-  Thay thế`"C:\\Attachments"`bằng đường dẫn thư mục bạn muốn.
-  Các`attachment.Save()` phương pháp ghi tập tin vào đĩa.


## Bước 6: Xử lý tệp đính kèm theo loại

Nếu bạn cần xử lý các tệp đính kèm khác nhau dựa trên loại tệp (ví dụ: PDF so với JPEG), Aspose.Email sẽ giúp bạn thực hiện dễ dàng.

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType` xác định loại tệp (ví dụ:`application/pdf` đối với PDF,`image/jpeg` (đối với hình ảnh).
- Thêm logic tùy chỉnh cho các loại tệp khác nhau khi cần.


## Phần kết luận

Và bạn đã có nó! Trích xuất tệp đính kèm từ email không còn là một nhiệm vụ tẻ nhạt nữa. Với Aspose.Email for .NET, bạn có thể tự động hóa quy trình này chỉ bằng một vài dòng mã. Từ thiết lập máy khách IMAP đến lưu tệp đính kèm cục bộ, hướng dẫn này đã đề cập đến mọi thứ bạn cần để bắt đầu. 

 Vậy thì tại sao phải chờ đợi?[Tải xuống Aspose.Email](https://releases.aspose.com/email/net/) và bắt đầu hợp lý hóa quy trình làm việc email của bạn ngay hôm nay!


## Câu hỏi thường gặp

### Tôi có thể sử dụng mã này với Gmail hoặc Outlook không?
 Vâng! Thay thế`imap.example.com` với Gmail (`imap.gmail.com`) hoặc Outlook (`outlook.office365.com`) Địa chỉ máy chủ IMAP.

### Aspose.Email có miễn phí sử dụng không?
 Aspose.Email yêu cầu giấy phép để có đầy đủ tính năng. Bạn có thể yêu cầu[dùng thử miễn phí](https://releases.aspose.com/) hoặc một[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).

### Tôi có thể xử lý bảo mật mật khẩu như thế nào?
Hãy cân nhắc sử dụng biến môi trường hoặc lưu trữ thông tin xác thực an toàn thay vì mã hóa cứng mật khẩu.

### Tôi có thể trích xuất tệp đính kèm từ các mục đã gửi không?
 Vâng, chỉ cần sử dụng`SelectFolder(ImapFolderInfo.Sent)` thay vì hộp thư đến.

### Aspose.Email có hỗ trợ POP3 không?
Chắc chắn rồi! Bên cạnh IMAP, nó còn hỗ trợ POP3 và SMTP.