---
title: Trích xuất văn bản được tô sáng từ PDF bằng Aspose.PDF cho .NET
linktitle: Trích xuất văn bản được tô sáng từ PDF bằng Aspose.PDF cho .NET
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Mở khóa tiềm năng của tài liệu PDF của bạn bằng cách tìm hiểu cách trích xuất văn bản được tô sáng bằng Aspose.PDF cho .NET. Hướng dẫn toàn diện này hướng dẫn bạn từng bước, từ thiết lập đến triển khai.
type: docs
weight: 60
url: /vi/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## Giới thiệu

Khi làm việc với các tệp PDF, việc trích xuất văn bản được tô sáng có thể rất cần thiết để phân tích dữ liệu, xem xét nội dung hoặc sắp xếp ghi chú. Nếu bạn đang sử dụng Aspose.PDF cho .NET, bạn thật may mắn. Hướng dẫn này cung cấp hướng dẫn từng bước rõ ràng về cách trích xuất văn bản được tô sáng từ tài liệu PDF một cách hiệu quả.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã chuẩn bị những điều sau:

-  Aspose.PDF cho Thư viện .NET: Tải xuống thư viện từ[trang phát hành](https://releases.aspose.com/pdf/net/).
- Môi trường phát triển: Môi trường làm việc như Visual Studio.
- Kiến thức cơ bản về C#: Cần phải quen thuộc với C# và lập trình hướng đối tượng.
-  Giấy phép Aspose: Mặc dù bạn có thể bắt đầu bằng bản dùng thử miễn phí, nhưng[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) hoặc giấy phép đầy đủ từ[đây](https://purchase.aspose.com/buy) sẽ cung cấp quyền truy cập không hạn chế.

## Nhập các không gian tên cần thiết

Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án C# của bạn:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Các không gian tên này cung cấp quyền truy cập vào các lớp và phương thức cần thiết để xử lý tài liệu PDF và chú thích.

## Bước 1: Thiết lập thư mục dự án của bạn

Chỉ định thư mục chứa tệp PDF của bạn:

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Hãy đảm bảo thay thế đường dẫn bằng thư mục thực tế của tệp PDF của bạn.

## Bước 2: Tải Tài liệu PDF

Tải tài liệu PDF bằng mã sau:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Đảm bảo rằng tập tin được chỉ định tồn tại trong thư mục đã cho.

## Bước 3: Truy cập chú thích trên trang

Để truy cập vào các chú thích, hãy lặp qua các chú thích trên trang bạn muốn (trong trường hợp này là trang đầu tiên):

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 Mã này lọc cho`TextMarkupAnnotation` các loại biểu thị điểm nổi bật.

## Bước 4: Trích xuất văn bản được tô sáng

Bây giờ, hãy trích xuất và hiển thị văn bản từ các chú thích được tô sáng:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

Thao tác này sẽ lấy tất cả các đoạn văn bản được đánh dấu có liên quan đến phần tô sáng và in chúng ra bảng điều khiển.

## Phần kết luận

Trích xuất văn bản được tô sáng từ PDF bằng Aspose.PDF cho .NET rất đơn giản và có thể cải thiện đáng kể quy trình xử lý tài liệu của bạn. Bằng cách làm theo các bước nêu trên, bạn có thể thu thập hiệu quả văn bản được tô sáng cho nhiều ứng dụng khác nhau, chẳng hạn như chuẩn bị báo cáo hoặc phân tích dữ liệu.

## Câu hỏi thường gặp

### Tôi có thể trích xuất các loại chú thích khác không?
 Vâng, chỉ cần điều chỉnh`if` điều kiện để bao gồm các loại chú thích khác nhau như`TextAnnotation` hoặc`StampAnnotation`.

### Làm thế nào để trích xuất văn bản được tô sáng từ tất cả các trang PDF?
Bạn có thể lặp qua tất cả các trang bằng cách sử dụng:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Có cần giấy phép cho Aspose.PDF dành cho .NET không?
 Có bản dùng thử miễn phí, nhưng hãy cân nhắc[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) hoặc giấy phép đầy đủ để truy cập toàn diện.

### Tôi có thể lưu văn bản đã trích xuất vào một tệp không?
Hoàn toàn có thể! Bạn có thể sửa đổi mã để ghi văn bản đã trích xuất vào tệp văn bản.

### Aspose.PDF có hỗ trợ các nền tảng khác không?
Có, Aspose.PDF cũng hỗ trợ Java và các nền tảng khác, cung cấp chức năng tương tự.