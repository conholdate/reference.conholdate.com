---
title: Chuyển đổi XPS sang PDF bằng Aspose.Page cho .NET
linktitle: Chuyển đổi XPS sang PDF
second_title: API Aspose.Page .NET
description: Khám phá cách chuyển đổi dễ dàng các tài liệu XPS (XML Paper Specification) sang PDF (Portable Document Format) bằng thư viện Aspose.Page mạnh mẽ cho .NET.
type: docs
weight: 11
url: /vi/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Giới thiệu

Trong hướng dẫn này, chúng ta sẽ khám phá cách chuyển đổi tài liệu XPS (XML Paper Specification) sang PDF (Portable Document Format) bằng thư viện Aspose.Page for .NET đa năng. Thư viện mạnh mẽ này đơn giản hóa việc chuyển đổi tài liệu và cung cấp nhiều tùy chọn tùy chỉnh, khiến nó trở thành lựa chọn tuyệt vời cho các nhà phát triển.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã chuẩn bị những điều sau:

-  Aspose.Page cho Thư viện .NET: Tải xuống và cài đặt thư viện Aspose.Page cho .NET từ[Tài liệu Aspose.Page](https://reference.aspose.com/page/net/).
  
- Môi trường phát triển: Thiết lập môi trường phát triển .NET bằng Visual Studio hoặc IDE tương thích khác.

- Tài liệu XPS: Chuẩn bị sẵn tệp XPS bạn muốn chuyển đổi, lưu trữ trong một thư mục được chỉ định.

## Bước 1: Nhập không gian tên bắt buộc

Bắt đầu bằng cách nhập không gian tên cần thiết để truy cập các chức năng của Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Bước 2: Khởi tạo thư mục tài liệu

Xác định đường dẫn thư mục nơi lưu trữ tài liệu của bạn:

```csharp
string dataDir = "Your Document Directory";
```

 Hãy chắc chắn thay thế`"Your Document Directory"` với đường dẫn thực tế đến thư mục chứa tài liệu XPS của bạn.

### Bước 3: Mở luồng PDF và XPS

Tiếp theo, khởi tạo các luồng cho cả tệp XPS đầu vào và tệp PDF đầu ra:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Đảm bảo bạn đã thiết lập đúng đường dẫn cho các tệp của mình.

### Bước 4: Tải Tài liệu XPS

Bây giờ, hãy tải tài liệu XPS của bạn bằng thư viện Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Bước 5: Cấu hình tùy chọn lưu PDF

Thiết lập các tùy chọn lưu cho tệp PDF của bạn, bao gồm chất lượng hình ảnh và các thông số nén:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Đặt mức chất lượng JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Sử dụng nén JPEG cho hình ảnh
    TextCompression = PdfTextCompression.Flate, // Áp dụng nén Flate cho văn bản
    PageNumbers = new int[] { 1, 2, 6 } // Chỉ định số trang cần bao gồm
};
```

Bạn có thể thoải mái điều chỉnh các thông số này theo nhu cầu của mình.

### Bước 6: Tạo thiết bị kết xuất PDF

Tạo thiết bị kết xuất cho định dạng PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Bước 7: Lưu tài liệu dưới dạng PDF

Cuối cùng, lưu tài liệu XPS thành PDF bằng thiết bị và tùy chọn đã chỉ định:

```csharp
document.Save(device, options);
```

## Phần kết luận

Xin chúc mừng! Bạn đã chuyển đổi thành công một tài liệu XPS sang PDF bằng Aspose.Page cho .NET. Thư viện này không chỉ đơn giản hóa việc chuyển đổi tài liệu mà còn cung cấp khả năng mở rộng để xử lý nhiều định dạng khác nhau.

## Câu hỏi thường gặp

### Tôi có thể chuyển đổi nhiều tệp XPS thành một tệp PDF không?

Hoàn toàn có thể! Bạn có thể lặp lại nhiều tệp XPS và hợp nhất chúng thành một tài liệu PDF duy nhất bằng cách thực hiện các bước chuyển đổi tương tự.

### Aspose.Page for .NET còn hỗ trợ những định dạng đầu ra nào khác?

Ngoài PDF, Aspose.Page for .NET còn hỗ trợ nhiều định dạng khác nhau, bao gồm TIFF, JPEG và PNG.

### Làm thế nào để tùy chỉnh giao diện của tệp PDF đã chuyển đổi?

 Bạn có thể điều chỉnh các thông số trong`PdfSaveOptions` đối tượng, chẳng hạn như chất lượng JPEG và cài đặt nén, để đạt được giao diện mong muốn.

### Có phiên bản dùng thử nào của Aspose.Page dành cho .NET không?

Có, bạn có thể dùng thử Aspose.Page cho .NET với bản dùng thử miễn phí[đây](https://releases.aspose.com/).

### Tôi có thể tìm thấy sự hỗ trợ của cộng đồng cho Aspose.Page dành cho .NET ở đâu?

 Để thảo luận và hỗ trợ cộng đồng, hãy truy cập[Diễn đàn Aspose.Page](https://forum.aspose.com/c/page/39).