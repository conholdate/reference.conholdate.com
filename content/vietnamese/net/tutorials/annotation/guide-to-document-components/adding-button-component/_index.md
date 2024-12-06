---
title: Thêm thành phần nút với GroupDocs.Annotation cho .NET
linktitle: Thêm thành phần nút
second_title: GroupDocs.Chú thích API .NET
description: Khám phá cách nâng cao tài liệu PDF của bạn bằng cách thêm các thành phần nút tương tác bằng GroupDocs.Annotation cho .NET. Hướng dẫn từng bước này.
type: docs
weight: 10
url: /vi/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## Giới thiệu

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình đơn giản để thêm Thành phần Nút vào tài liệu PDF bằng thư viện GroupDocs.Annotation cho .NET. Đến cuối hướng dẫn này, bạn sẽ được trang bị để nâng cao tài liệu PDF của mình bằng các tính năng tương tác.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã chuẩn bị những điều sau:

1.  GroupDocs.Annotation cho .NET: Tải xuống và cài đặt thư viện GroupDocs.Annotation cho .NET từ[đây](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển phù hợp với .NET framework được cài đặt.

## Bước 1: Nhập các không gian tên cần thiết

Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Bước 2: Khởi tạo Đường dẫn đầu ra

Xác định đường dẫn đầu ra nơi tệp PDF đã sửa đổi sẽ được lưu:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Bước 3: Thêm thành phần nút

Bây giờ, chúng ta hãy tạo và thêm Thành phần Nút vào PDF của bạn:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // Vị trí và kích thước của nút
        PenColor = 65535,                       // Màu viền nút
        Style = BorderStyle.Dashed,             // Kiểu viền
        BorderWidth = 0,                        // Chiều rộng đường viền
        BorderColor = 0,                        // Màu viền
        AlternateName = "Name",                 // Tên thay thế cho nút
        PartialName = "Partial Name",           // Tên một phần của nút
        NormalCaption = "Caption",               // Văn bản hiển thị trên nút
        ButtonColor = 16761035,                 // Màu nền của nút
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // Thêm nút vào chú thích
    annotator.Save("result.pdf"); // Lưu PDF đã sửa đổi
}
```

## Bước 4: Hiển thị đường dẫn đầu ra

Cuối cùng, hãy thông báo cho người dùng nơi lưu tệp đầu ra:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Xin chúc mừng! Bạn đã thêm thành công Thành phần Nút vào tài liệu PDF bằng GroupDocs.Annotation cho .NET.

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã trình bày cách kết hợp Button Components vào tài liệu PDF với GroupDocs.Annotation cho .NET. Bằng cách làm theo các bước này, bạn có thể cải thiện đáng kể tính tương tác của tài liệu PDF.

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh giao diện của nút không?

Chắc chắn rồi! Bạn có thể sửa đổi nhiều thuộc tính khác nhau như kích thước, màu sắc và kiểu dáng để phù hợp với yêu cầu của mình.

### GroupDocs.Annotation cho .NET có tương thích với tất cả các phiên bản PDF không?

Có, GroupDocs.Annotation cho .NET hỗ trợ nhiều phiên bản PDF, đảm bảo khả năng tương thích với hầu hết các tài liệu.

### Tôi có thể thêm nhiều thành phần nút vào một tài liệu PDF không?

Có, bạn có thể thêm bao nhiêu thành phần nút tùy ý vào tài liệu PDF.

### GroupDocs.Annotation cho .NET có hỗ trợ các định dạng tệp khác không?

Có, ngoài PDF, nó còn hỗ trợ nhiều định dạng tài liệu khác nhau, bao gồm DOCX, PPTX và XLSX.

### Có phiên bản dùng thử nào để thử nghiệm không?

 Có, bạn có thể truy cập dùng thử miễn phí GroupDocs.Annotation cho .NET từ[đây](https://releases.groupdocs.com/).
