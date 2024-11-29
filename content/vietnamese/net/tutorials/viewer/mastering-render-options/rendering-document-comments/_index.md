---
title: Kết xuất tài liệu với chú thích
linktitle: Kết xuất tài liệu với chú thích
second_title: API GroupDocs.Viewer .NET
description: Hướng dẫn toàn diện này cung cấp hướng dẫn từng bước về cách hiển thị tài liệu có chú thích trong các ứng dụng .NET bằng thư viện GroupDocs.Viewer.
type: docs
weight: 13
url: /vi/net/tutorials/viewer/mastering-render-options/rendering-document-comments/
---
## Giới thiệu

GroupDocs.Viewer for .NET là một thư viện mạnh mẽ được thiết kế để trao quyền cho các nhà phát triển với khả năng kết xuất tài liệu cho nhiều định dạng khác nhau. Cho dù bạn cần hiển thị tài liệu Word, bảng tính Excel, bản trình bày PowerPoint hay tệp PDF, GroupDocs.Viewer đều hợp lý hóa quy trình tích hợp. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn qua các bước cần thiết để kết xuất tài liệu có chú thích, đảm bảo rằng bạn hiểu rõ từng khía cạnh liên quan.

## Điều kiện tiên quyết
Trước khi đi sâu vào chi tiết về cách hiển thị tài liệu có chú thích, hãy đảm bảo bạn đã thiết lập những điều sau:

### Môi trường phát triển .NET
Đảm bảo rằng bạn có môi trường phát triển sẵn sàng cho .NET. Bạn sẽ cần một IDE tương thích như Visual Studio cùng với .NET SDK được cài đặt trên máy của bạn.

### GroupDocs.Viewer để cài đặt .NET
Bạn có thể tải xuống và cài đặt GroupDocs.Viewer cho .NET từ trang web hoặc trực tiếp thông qua liên kết này:
[Tải xuống GroupDocs.Viewer cho .NET](https://releases.groupdocs.com/viewer/net/)

## Nhập không gian tên
Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án .NET của bạn. Bước này cấp cho bạn quyền truy cập vào các lớp và phương thức cần thiết để hiển thị tài liệu.

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Bước 1: Xác định thư mục đầu ra
Chọn thư mục đầu ra nơi tài liệu được kết xuất có chú thích sẽ được lưu.

```csharp
string outputDirectory = @"C:\Your\Document\Directory"; // Chỉ định đường dẫn thư mục của bạn
```

## Bước 2: Xác định định dạng đường dẫn tệp trang
Đặt định dạng đường dẫn tệp cho từng trang riêng lẻ của tài liệu được kết xuất.

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

## Bước 3: Khởi tạo đối tượng Viewer
 Tạo một phiên bản của`Viewer` lớp, truyền vào đường dẫn đến tài liệu có chứa chú thích.

```csharp
using (Viewer viewer = new Viewer(@"C:\Path\To\Your\DocumentWithComments.docx"))
{
    // Tiến hành cấu hình các tùy chọn kết xuất
}
```

## Bước 4: Cấu hình tùy chọn kết xuất
Thiết lập tùy chọn hiển thị, đảm bảo bật hiển thị tài nguyên nhúng và bình luận.

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
options.RenderComments = true; // Cho phép hiển thị bình luận
```

## Bước 5: Hiển thị Tài liệu với Bình luận
 Gọi cho`View` phương pháp trên`Viewer` đối tượng với các tùy chọn được cấu hình.

```csharp
viewer.View(options);
```

## Bước 6: Hiển thị thông báo thành công
Sau quá trình kết xuất, hãy cung cấp phản hồi cho người dùng.

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Phần kết luận
Trong hướng dẫn này, bạn đã học cách kết xuất tài liệu có chú thích bằng GroupDocs.Viewer cho .NET. Bằng cách làm theo các bước được nêu, bạn có thể dễ dàng kết hợp chức năng kết xuất tài liệu vào ứng dụng của mình, nâng cao trải nghiệm của người dùng.

## Câu hỏi thường gặp

### GroupDocs.Viewer có thể xử lý định dạng tài liệu phức tạp không?
Có, GroupDocs.Viewer có thể hiển thị hiệu quả các tài liệu chứa nhiều thành phần định dạng khác nhau, bao gồm bảng, hình ảnh và phông chữ tùy chỉnh.

### GroupDocs.Viewer có tương thích với nhiều định dạng tài liệu không?
Chắc chắn rồi! Thư viện hỗ trợ nhiều định dạng khác nhau, chẳng hạn như PDF, DOCX, XLSX, PPTX và nhiều định dạng khác.

### Tôi có thể tùy chỉnh tùy chọn kết xuất để phù hợp với nhu cầu cụ thể không?
Có, GroupDocs.Viewer cung cấp nhiều tùy chọn kết xuất linh hoạt để điều chỉnh đầu ra theo yêu cầu ứng dụng của bạn.

### Tôi có thể trích xuất tài liệu từ nguồn bên ngoài không?
Có, thư viện cho phép hiển thị tài liệu từ nhiều nguồn khác nhau, bao gồm đường dẫn tệp cục bộ, luồng và URL.

### Có phiên bản dùng thử của GroupDocs.Viewer không?
Có, bạn có thể bắt đầu khám phá GroupDocs.Viewer bằng bản dùng thử miễn phí để đánh giá các tính năng và khả năng của nó.