---
title: Đang tải các tài liệu được bảo vệ bằng mật khẩu
linktitle: Tải các tài liệu được bảo vệ bằng mật khẩu
second_title: API GroupDocs.Viewer .NET
description: Khám phá cách tích hợp dễ dàng các chức năng xem tài liệu vào ứng dụng .NET của bạn với GroupDocs.Viewer. Hướng dẫn này cung cấp hướng dẫn toàn diện, từng bước.
type: docs
weight: 12
url: /vi/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## Giới thiệu

Trong bối cảnh kỹ thuật số, khả năng quản lý và xem nhiều định dạng tài liệu khác nhau là rất quan trọng đối với các doanh nghiệp và cá nhân. GroupDocs.Viewer for .NET cung cấp giải pháp mạnh mẽ cho các nhà phát triển để tích hợp khả năng xem tài liệu vào ứng dụng của họ một cách dễ dàng. Hướng dẫn này sẽ hướng dẫn bạn từng bước trong quy trình tải các tài liệu được bảo vệ bằng mật khẩu, đảm bảo bạn có thể triển khai tính năng này một cách liền mạch trong các dự án của mình.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1.  GroupDocs.Viewer cho .NET đã cài đặt: Tải xuống từ[trang web](https://releases.groupdocs.com/viewer/net/).
2. Tài liệu được bảo vệ bằng mật khẩu: Chuẩn bị một tài liệu được bảo vệ bằng mật khẩu để thử nghiệm.

## Nhập không gian tên bắt buộc

Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Bước 1: Xác định thư mục đầu ra

Chỉ định nơi bạn muốn lưu kết quả đã kết xuất:

```csharp
string outputDirectory = "Your Document Directory";
```
 Hãy chắc chắn thay thế`"Your Document Directory"` với đường dẫn thực tế mà bạn muốn sử dụng.

## Bước 2: Thiết lập Định dạng Đường dẫn Tệp Trang

Xác định định dạng cho đường dẫn tệp của mỗi trang được hiển thị:

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

 Điều này sẽ tạo ra các đường dẫn như`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`, vân vân.

## Bước 3: Cấu hình Tùy chọn Tải

Thiết lập tùy chọn tải cho tài liệu được bảo vệ bằng mật khẩu của bạn, bao gồm cả mật khẩu:

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  // Thay thế bằng mật khẩu tài liệu của bạn
};
```

## Bước 4: Khởi tạo Viewer

Tạo một phiên bản của GroupDocs.Viewer với tài liệu của bạn và các tùy chọn tải:

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    // Mã cho các tùy chọn xem sẽ được thêm vào ở bước tiếp theo.
}
```
 Hãy chắc chắn thay thế`"Path_to_your_document"` với đường dẫn thực tế đến tài liệu của bạn.

## Bước 5: Cấu hình Tùy chọn chế độ xem HTML

Thiết lập tùy chọn chế độ xem HTML để hiển thị tài liệu có tài nguyên nhúng:

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## Bước 6: Kết xuất tài liệu

Bây giờ, hãy hiển thị tài liệu bằng trình xem đã cấu hình và các tùy chọn xem:

```csharp
viewer.View(options);
```

## Bước 7: Hiển thị thông báo thành công

Cuối cùng, thông báo cho người dùng rằng tài liệu đã được hiển thị thành công:

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã khám phá cách tải các tài liệu được bảo vệ bằng mật khẩu bằng GroupDocs.Viewer cho .NET. Bằng cách làm theo các bước này, các nhà phát triển có thể dễ dàng tích hợp chức năng này vào ứng dụng của họ, cho phép người dùng xem các tài liệu được bảo vệ một cách dễ dàng.

## Câu hỏi thường gặp

### GroupDocs.Viewer có thể xử lý các định dạng tài liệu khác ngoài các tài liệu được bảo vệ bằng mật khẩu không?

Có, GroupDocs.Viewer hỗ trợ nhiều định dạng khác nhau, bao gồm PDF, DOCX, XLSX, PPTX, v.v.

### GroupDocs.Viewer có tương thích với .NET Core không?

Hoàn toàn có thể! GroupDocs.Viewer tương thích với cả môi trường .NET Framework và .NET Core.

### Tôi có thể tùy chỉnh các tùy chọn hiển thị cho tài liệu không?

Có, GroupDocs.Viewer cung cấp nhiều tùy chọn hiển thị khác nhau, cho phép bạn tùy chỉnh trải nghiệm xem theo nhu cầu của mình.

### GroupDocs.Viewer có hỗ trợ chú thích tài liệu không?

Có, ứng dụng này hỗ trợ chú thích tài liệu, cho phép người dùng thêm bình luận, đánh dấu và các ghi chú khác.

### Có phiên bản dùng thử nào cho GroupDocs.Viewer không?

 Có, bạn có thể nhận được bản dùng thử miễn phí từ[trang web](https://releases.groupdocs.com/).