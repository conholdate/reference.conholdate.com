---
title: Kiểm soát tài nguyên bên ngoài với Aspose.Cells cho .NET
linktitle: Kiểm soát tài nguyên bên ngoài với Aspose.Cells cho .NET
second_title: API xử lý Excel Aspose.Cells .NET
description: Mở khóa toàn bộ tiềm năng chuyển đổi Excel sang PDF của bạn với Aspose.Cells cho .NET. Trong hướng dẫn toàn diện này, hãy tìm hiểu cách quản lý các tài nguyên bên ngoài, chẳng hạn như hình ảnh, đảm bảo PDF của bạn phản ánh chính xác các yêu cầu định dạng của bạn.
type: docs
weight: 12
url: /vi/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Giới thiệu

Trong bối cảnh kỹ thuật số ngày nay, việc chuyển đổi bảng tính Excel sang tài liệu PDF là một nhiệm vụ phổ biến và thiết yếu. Cho dù bạn đang chuẩn bị báo cáo, dữ liệu tài chính hay tài liệu thuyết trình, việc đảm bảo rằng PDF của bạn phản ánh định dạng mong muốn là rất quan trọng. Aspose.Cells for .NET cung cấp một thư viện mạnh mẽ cho phép bạn kiểm soát quá trình chuyển đổi này một cách chi tiết, đặc biệt là khi xử lý các tài nguyên bên ngoài như hình ảnh. Trong hướng dẫn này, chúng ta sẽ khám phá cách quản lý hiệu quả các tài nguyên bên ngoài trong quá trình chuyển đổi Excel sang PDF bằng Aspose.Cells. Hãy cùng tìm hiểu!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã chuẩn bị những thứ sau:

1. Visual Studio hoặc bất kỳ IDE nào tương thích với .NET: Đây sẽ là môi trường phát triển của bạn.
2.  Aspose.Cells cho .NET: Nếu bạn chưa cài đặt, hãy truy cập[Tải xuống Aspose](https://releases.aspose.com/cells/net/) trang để tải phiên bản mới nhất.
3. Kiến thức cơ bản về C#: Sự quen thuộc với C# sẽ có lợi. Nếu bạn cần làm rõ bất kỳ khái niệm nào, hãy thoải mái tra cứu.
4. Tệp Excel mẫu: Chuẩn bị một tệp Excel, chẳng hạn như "samplePdfSaveOptions_StreamProvider.xlsx", chứa các tài nguyên bên ngoài mà bạn muốn chuyển đổi.
5. Tệp hình ảnh để kiểm tra: Sử dụng tệp hình ảnh như "newPdfSaveOptions_StreamProvider.png" làm tài nguyên bên ngoài trong quá trình chuyển đổi.

## Nhập các gói cần thiết

Để bắt đầu, bạn sẽ cần nhập các không gian tên cần thiết từ thư viện Aspose.Cells. Thêm các chỉ thị sau vào đầu tệp C# của bạn:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Các không gian tên này cung cấp các lớp và phương thức cần thiết cho tác vụ của bạn.

## Bước 1: Tạo một lớp nhà cung cấp luồng

 Đầu tiên, tạo một lớp nhà cung cấp luồng thực hiện`IStreamProvider` giao diện. Lớp này sẽ cho phép bạn kiểm soát cách tải các tài nguyên bên ngoài.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Tải hình ảnh vào luồng bộ nhớ
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Phương thức này được gọi khi luồng bị đóng, hiện đang ghi nhật ký thông báo gỡ lỗi.
- InitStream: Phương pháp này đọc tệp hình ảnh bên ngoài dưới dạng một mảng byte, chuyển đổi nó thành một luồng bộ nhớ và gán nó cho`options.Stream` tài sản.

## Bước 2: Thiết lập thư mục nguồn và đầu ra

Tiếp theo, hãy xác định thư mục cho tệp Excel và tệp PDF đầu ra.

```csharp
// Thư mục nguồn
string sourceDir = "Your Document Directory";
// Thư mục đầu ra
string outputDir = "Your Document Directory";
```

 Thay thế`"Your Document Directory"` với đường dẫn thực tế trên hệ thống nơi lưu trữ các tập tin của bạn.

## Bước 3: Tải tệp Excel của bạn

Bây giờ, hãy tải tệp Excel mà bạn muốn dùng để tạo PDF.

```csharp
// Tải tệp Excel nguồn có chứa hình ảnh bên ngoài
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 Các`Workbook` lớp từ Aspose.Cells biểu diễn tệp Excel của bạn, có thể bao gồm nhiều tài nguyên bên ngoài như hình ảnh.

## Bước 4: Thiết lập tùy chọn lưu PDF

Trước khi lưu bảng tính dưới dạng PDF, hãy chỉ định tùy chọn lưu mong muốn.

```csharp
// Chỉ định tùy chọn lưu PDF - Nhà cung cấp luồng
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Lưu mỗi trang tính trên một trang mới
};
```

 Điều này tạo ra một trường hợp của`PdfSaveOptions` , cho phép bạn tùy chỉnh định dạng PDF.`OnePagePerSheet` Tùy chọn này đảm bảo rằng mỗi trang tính Excel sẽ xuất hiện trên một trang riêng biệt trong tệp PDF cuối cùng.

## Bước 5: Chỉ định Nhà cung cấp Luồng của Bạn

 Kết nối của bạn`Workbook` ví dụ với`MyStreamProvider` lớp bạn đã tạo trước đó.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Dòng này đảm bảo rằng bất cứ khi nào gặp phải tài nguyên bên ngoài trong quá trình chuyển đổi, nhà cung cấp tùy chỉnh của bạn sẽ quản lý chúng cho phù hợp.

## Bước 6: Lưu Workbook dưới dạng PDF

Bây giờ, hãy lưu bảng tính Excel của bạn dưới dạng PDF.

```csharp
// Lưu sổ làm việc vào PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Bằng cách gọi`Save` phương pháp trên đối tượng sổ làm việc và truyền thư mục đầu ra cùng với các tùy chọn PDF, bạn chuyển đổi tệp Excel thành tệp PDF được định dạng tốt.

## Bước 7: Xác nhận thực hiện thành công

Cuối cùng, bạn nên xác nhận quá trình đã hoàn tất thành công.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Tin nhắn này sẽ thông báo cho bạn về trạng thái hoạt động của bạn và cung cấp phản hồi hữu ích.

## Phần kết luận

Bây giờ bạn đã thành thạo quy trình kiểm soát các tài nguyên bên ngoài trong quá trình chuyển đổi Excel sang PDF bằng Aspose.Cells! Bằng cách làm theo các bước này, bạn có thể đảm bảo rằng tài liệu của mình bao gồm chính xác hình ảnh và các thành phần bên ngoài khác, tạo ra sản phẩm cuối cùng hoàn thiện mọi lúc.

## Câu hỏi thường gặp

### Aspose.Cells là gì?
Aspose.Cells là một thư viện mạnh mẽ dành cho các nhà phát triển .NET, cho phép tạo, chỉnh sửa, chuyển đổi và hiển thị các tệp Excel ở nhiều định dạng khác nhau.

### Làm thế nào để tải xuống Aspose.Cells?
 Bạn có thể tải xuống phiên bản mới nhất từ[Liên kết tải xuống](https://releases.aspose.com/cells/net/).

### Tôi có thể dùng thử Aspose.Cells miễn phí không?
 Có! Bạn có thể truy cập bản dùng thử miễn phí bằng cách truy cập[Trang dùng thử miễn phí](https://releases.aspose.com/).

### Tôi có thể tìm thấy hỗ trợ cho Aspose.Cells ở đâu?
 Đối với các truy vấn liên quan đến hỗ trợ, hãy truy cập[Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/cells/9).

### Làm thế nào tôi có thể xin được giấy phép tạm thời cho Aspose.Cells?
 Bạn có thể nộp đơn xin giấy phép tạm thời[đây](https://purchase.aspose.com/temporary-license/).
