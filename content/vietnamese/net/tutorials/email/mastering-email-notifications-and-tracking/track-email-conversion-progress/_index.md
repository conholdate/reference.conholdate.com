---
title: Theo dõi tiến trình chuyển đổi email với Aspose.Email cho .NET
linktitle: Theo dõi tiến trình chuyển đổi email với Aspose.Email cho .NET
second_title: API xử lý email Aspose.Email .NET
description: Tìm hiểu từng bước cách theo dõi tiến trình chuyển đổi email trong C# bằng Aspose.Email cho .NET. Tăng hiệu quả dự án của bạn với hướng dẫn chi tiết này.
type: docs
weight: 12
url: /vi/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## Giới thiệu

Quản lý tài liệu email hiệu quả thường liên quan đến việc theo dõi tiến trình chuyển đổi của chúng. Aspose.Email for .NET cung cấp các công cụ mạnh mẽ để thực hiện việc này, cho phép các nhà phát triển xử lý các hoạt động email một cách liền mạch. Hướng dẫn này đi sâu vào cách bạn có thể theo dõi tiến trình chuyển đổi tài liệu email trong C#, chia nhỏ quy trình từng bước để dễ hiểu.  

## Điều kiện tiên quyết  

Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn đã thiết lập mọi thứ:  

1.  Aspose.Email cho .NET: Tải xuống và cài đặt[Aspose.Email cho .NET](https://releases.aspose.com/email/net/) thư viện.  
2. Môi trường phát triển: Cài đặt Visual Studio hoặc bất kỳ IDE nào khác tương thích với .NET.  
3. .NET Framework: Đảm bảo đã cài đặt .NET Framework 4.5 trở lên.  
4.  Giấy phép tạm thời: Hãy cân nhắc việc xin cấp[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để khám phá đầy đủ các tính năng của Aspose.Email.  
5.  Mẫu tệp email: Chuẩn bị một`.eml` tập tin (ví dụ,`test.eml`) để sử dụng làm mẫu.  

## Nhập gói  

Để sử dụng Aspose.Email trong dự án của bạn, bạn sẽ cần nhập các không gian tên cần thiết. Thêm các câu lệnh using sau vào đầu tệp của bạn:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## Bước 1: Thiết lập dự án của bạn  

Bắt đầu bằng cách tạo một ứng dụng bảng điều khiển C# mới trong Visual Studio. Ứng dụng này sẽ đóng vai trò là nền tảng để triển khai theo dõi chuyển đổi tài liệu email.  
  
1. Mở Visual Studio và tạo một dự án Ứng dụng bảng điều khiển mới.  
2. Cài đặt gói Aspose.Email NuGet:  
```sh
Install-Package Aspose.Email
```  
3.  Thêm vào`.eml` tập tin vào thư mục dự án của bạn.  

## Bước 2: Tải tệp Email  

 Bây giờ, tải tệp email vào`MailMessage` đối tượng. Đây là bước đầu tiên trong việc làm việc với dữ liệu email.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: Chỉ định thư mục chứa tệp email của bạn.  
- `MailMessage.Load` : Đọc`.eml` lưu trữ và chuẩn bị cho các hoạt động tiếp theo.  

## Bước 3: Khởi tạo một luồng bộ nhớ  

 Tiếp theo, tạo một`MemoryStream` đối tượng để lưu trữ dữ liệu email đã chuyển đổi tạm thời.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 MỘT`MemoryStream` được sử dụng ở đây để quản lý đầu ra của quá trình chuyển đổi mà không lưu dữ liệu trực tiếp vào đĩa.  

## Bước 4: Xác định tùy chọn chuyển đổi  

 Thiết lập`EmlSaveOptions` với trình xử lý tiến trình tùy chỉnh để theo dõi tiến trình chuyển đổi.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: Chỉ định định dạng đầu ra.  
- `CustomProgressHandler`: Chỉ định một hàm xử lý tùy chỉnh để theo dõi tiến trình.  

## Bước 5: Lưu Email vào Luồng Bộ nhớ  

Lưu lại`MailMessage` đối tượng sử dụng các tùy chọn được chỉ định, kích hoạt chức năng theo dõi tiến trình.  
 
```csharp
msg.Save(ms, opt);
```
 
Bước này khởi tạo quá trình chuyển đổi email và gửi thông tin cập nhật đến trình xử lý tiến trình.  

## Bước 6: Triển khai Trình xử lý tiến trình  

 Xác định`ShowEmlConversionProgress` phương pháp xử lý cập nhật tiến độ và hiển thị chúng trong bảng điều khiển.  
 
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
 
- `ProgressEventHandlerInfo`: Cung cấp thông tin chi tiết về quá trình chuyển đổi.  
-  Chuyển đổi trường hợp: Xử lý các giai đoạn khác nhau của quá trình chuyển đổi:`MimeStructureCreated`, `MimePartSaved` , Và`SavedToStream`.  

### Có thể mong đợi điều gì?  
Khi quá trình chuyển đổi diễn ra, bạn sẽ thấy các bản cập nhật chi tiết được in ra bảng điều khiển, chẳng hạn như:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## Phần kết luận  

Theo dõi tiến trình chuyển đổi tài liệu email trong C# chưa bao giờ dễ dàng hơn thế, nhờ Aspose.Email cho .NET. Bằng cách làm theo hướng dẫn này, bạn đã học cách tải tệp email, thiết lập trình xử lý tiến trình và lưu dữ liệu email trong khi theo dõi toàn bộ quá trình. Chức năng này đảm bảo bạn luôn được thông báo và kiểm soát trong quá trình xử lý tài liệu email.  

## Câu hỏi thường gặp  

###  Tôi có thể sử dụng mã này cho các định dạng khác không?`.eml`?  
 Có, sửa đổi`MailMessageSaveType`để phù hợp với các định dạng khác như MSG hoặc MHTML.  

### Tôi phải xử lý các tập tin email lớn như thế nào?  
 Hãy cân nhắc sử dụng một`FileStream` thay vì một`MemoryStream` để có hiệu suất tốt hơn khi xử lý các tệp lớn.  

### Giấy phép tạm thời là gì và tôi có thể xin giấy phép này như thế nào?  
 Giấy phép tạm thời cho phép bạn đánh giá toàn bộ các tính năng của thư viện miễn phí. Nhận nó[đây](https://purchase.aspose.com/temporary-license/).  

### Tôi có thể tích hợp mã này vào ứng dụng web không?  
Có, mã này tương thích với các ứng dụng web sử dụng ASP.NET hoặc các nền tảng tương tự.  

### Tôi có thể tìm thêm tài nguyên ở đâu?  
 Kiểm tra các[tài liệu](https://reference.aspose.com/email/net/) hoặc ghé thăm[diễn đàn hỗ trợ](https://forum.aspose.com/c/email/12/) để được giúp đỡ.  