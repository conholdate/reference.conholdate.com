---
title: Chuyển đổi DGN sang PDF trong Aspose.CAD cho .NET
linktitle: Chuyển đổi DGN sang PDF trong Aspose.CAD cho .NET
second_title: Aspose.CAD .NET - Định dạng tệp CAD và BIM
description: Tìm hiểu cách chuyển đổi tệp DGN sang PDF dễ dàng bằng thư viện Aspose.CAD mạnh mẽ dành cho .NET. Hướng dẫn từng bước này được thiết kế cho các nhà phát triển ở mọi cấp độ.
type: docs
weight: 12
url: /vi/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Giới thiệu

Việc điều hướng thế giới tệp CAD có thể là một thách thức, nhưng với Aspose.CAD for .NET, các nhà phát triển có thể dễ dàng thao tác và chuyển đổi nhiều định dạng CAD khác nhau. Một nhu cầu phổ biến là chuyển đổi tệp DGN sang PDF, chúng ta sẽ khám phá từng bước trong hướng dẫn này.

## Điều kiện tiên quyết

Để thực hiện theo, hãy đảm bảo bạn có những điều sau:

- Thành thạo cơ bản về C# và .NET framework.
-  Đã cài đặt thư viện Aspose.CAD cho .NET. Bạn có thể tải xuống[đây](https://releases.aspose.com/cad/net/).
- Một tệp DGN mẫu (ví dụ: Nikon_D90_Camera.dgn). 

## Bước 1: Nhập không gian tên bắt buộc

Bắt đầu bằng cách nhập các không gian tên có liên quan vào dự án C# của bạn:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Bước 2: Tải tệp DGN

Chỉ định thư mục cho tệp DGN của bạn và tải nó bằng mã sau:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Quá trình xử lý bổ sung sẽ diễn ra ở đây...
}
```

## Bước 3: Cấu hình tùy chọn Rasterization

Tiếp theo, thiết lập các tùy chọn rasterization để xác định cách DGN của bạn sẽ được hiển thị trong PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Điều chỉnh chiều rộng theo nhu cầu
    PageHeight = 300, // Điều chỉnh chiều cao khi cần thiết
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Bước 4: Tạo tùy chọn PDF

Xác định các tùy chọn PDF, tích hợp các thiết lập rasterization được cấu hình trước đó:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Bước 5: Lưu DGN dưới dạng PDF

Cuối cùng, lưu tệp DGN dưới dạng PDF bằng các tùy chọn bạn đã cấu hình:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Phần kết luận

Xin chúc mừng! Bạn đã chuyển đổi thành công tệp DGN thành PDF bằng Aspose.CAD cho .NET. Hướng dẫn đơn giản này hướng dẫn bạn cách tải tệp DGN, thiết lập tùy chọn rasterization và lưu đầu ra dưới dạng PDF.

## Câu hỏi thường gặp

### Tôi có cần kiến thức CAD trước để sử dụng Aspose.CAD không?  
Chắc chắn rồi! Aspose.CAD được thiết kế để đơn giản hóa các tác vụ CAD phức tạp, giúp mọi nhà phát triển đều có thể sử dụng, bất kể kiến thức về CAD của họ.

### Tôi có thể tìm thêm tài nguyên và tài liệu về Aspose.CAD ở đâu?  
 Bạn có thể khám phá các hướng dẫn và ví dụ toàn diện trong[Tài liệu Aspose.CAD](https://reference.aspose.com/cad/net/).

### Có bản dùng thử miễn phí Aspose.CAD không?  
 Có, bạn có thể dùng thử miễn phí[đây](https://releases.aspose.com/).

### Làm thế nào tôi có thể nhận được giấy phép tạm thời cho Aspose.CAD?  
 Bạn có thể yêu cầu giấy phép tạm thời[đây](https://purchase.conholdate.com/temporary-license/).

### Bạn cần hỗ trợ hoặc có thắc mắc?  
 Tham gia cuộc trò chuyện trong[Diễn đàn Aspose.CAD](https://forum.aspose.com/c/cad/19) để hỗ trợ cộng đồng và giải đáp thắc mắc.