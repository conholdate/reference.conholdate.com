---
title: Lưu tài liệu OneNote ở dạng PDF bằng Aspose.Note cho .NET
linktitle: Lưu tài liệu OneNote ở dạng PDF
second_title: API Aspose.Note .NET
description: Tìm hiểu cách lưu tài liệu Microsoft OneNote dưới dạng tệp PDF hiệu quả bằng Aspose.Note cho .NET. Hướng dẫn này hướng dẫn bạn qua các điều kiện tiên quyết cần thiết và cung cấp các câu hỏi thường gặp hữu ích.
type: docs
weight: 26
url: /vi/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Giới thiệu

Trong hướng dẫn này, chúng ta sẽ khám phá cách lưu tài liệu ở định dạng PDF bằng Aspose.Note cho .NET. Aspose.Note là một thư viện mạnh mẽ cho phép các nhà phát triển làm việc với các tệp Microsoft OneNote theo chương trình. Chúng tôi sẽ đề cập đến các điều kiện tiên quyết, nhập không gian tên và cung cấp hướng dẫn từng bước để lưu tài liệu ở định dạng PDF trong nhiều bố cục trang khác nhau.

## Điều kiện tiên quyết
1. Visual Studio: Đảm bảo rằng nó đã được cài đặt.
2. Aspose.Note cho .NET: Tải xuống và cài đặt thư viện.
3. Kiến thức về C#: Cần có hiểu biết cơ bản về ngôn ngữ này.

## Nhập các không gian tên cần thiết
Trước khi tiếp tục, hãy nhập các không gian tên sau vào mã của bạn:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Bước 1: Lưu vào PDF bằng Cài đặt trang thư
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Cập nhật đường dẫn này
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Tải tài liệu OneNote và lưu dưới dạng PDF bằng cách sử dụng cài đặt trang có kích thước khổ letter.

## Bước 2: Lưu thành PDF với Cài đặt trang A4 (Không giới hạn chiều cao)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Cập nhật đường dẫn này
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Tương tự như Bước 1 nhưng sử dụng cài đặt trang A4 mà không giới hạn chiều cao.

## Phần kết luận
Hướng dẫn này trình bày thành công cách chuyển đổi tệp OneNote sang định dạng PDF bằng Aspose.Note. Bằng cách sử dụng các cài đặt trang khác nhau, các nhà phát triển có được sự linh hoạt trong việc quản lý tài liệu.

## Câu hỏi thường gặp
### Aspose.Note có thể xử lý các tệp OneNote phức tạp không?
Có, nó xử lý hiệu quả nhiều tính năng khác nhau của các tệp OneNote phức tạp.

### Aspose.Note có phù hợp cho các dự án thương mại không?
Có, bạn có thể sử dụng nó cho các ứng dụng thương mại sau khi mua giấy phép.

### Aspose.Note có cung cấp bản dùng thử miễn phí không?
Có, bạn có thể dùng thử miễn phí để khám phá.

### Tôi có thể tìm tài liệu về Aspose.Note ở đâu?
Tài liệu chi tiết có sẵn trên trang tham khảo Aspose.

### Cần thêm trợ giúp?
Nếu có thắc mắc và cần hỗ trợ, hãy tham khảo diễn đàn Aspose.Note.
