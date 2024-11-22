---
title: Xuất CAD sang Chuyển đổi hình ảnh Raster với Aspose.CAD cho .NET
linktitle: Xuất CAD sang Chuyển đổi hình ảnh Raster
second_title: Aspose.CAD .NET - Định dạng tệp CAD và BIM
description: Tìm hiểu cách chuyển đổi hiệu quả các bố cục CAD thành nhiều định dạng hình ảnh raster khác nhau bằng Aspose.CAD cho .NET. Hướng dẫn toàn diện này hướng dẫn bạn thực hiện quy trình với mã rõ ràng.
type: docs
weight: 10
url: /vi/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## Giới thiệu

Bạn có muốn chuyển đổi bố cục CAD sang định dạng hình ảnh raster một cách dễ dàng bằng Aspose.CAD cho .NET không? Hướng dẫn từng bước này được thiết kế để giúp bạn điều hướng quy trình, hoàn chỉnh với các đoạn mã ngắn gọn để có trải nghiệm mượt mà. Cho dù bạn là nhà phát triển có kinh nghiệm hay mới bắt đầu, hướng dẫn này cung cấp những hiểu biết có giá trị cho mọi cấp độ kỹ năng.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Thư viện Aspose.CAD cho .NET: Tải xuống và cài đặt thư viện từ[Trang web Aspose.CAD](https://releases.aspose.com/cad/net/).
-  Tệp bản vẽ CAD: Có tệp bản vẽ CAD của bạn (ví dụ:`conic_pyramid.dxf`) sẵn sàng để chuyển đổi.

## Nhập không gian tên bắt buộc

Trong dự án .NET của bạn, bạn sẽ cần nhập các không gian tên cần thiết để sử dụng các hàm Aspose.CAD. Thêm nội dung sau vào đầu mã của bạn:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Bước 1: Tải bản vẽ CAD của bạn

Đầu tiên, hãy chỉ định thư mục và tải tệp CAD của bạn vào một phiên bản Image:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// Tải bản vẽ CAD
using (var image = Image.Load(sourceFilePath))
{
    // Tiến hành các bước tiếp theo
}
```

## Bước 2: Tạo tùy chọn Rasterization

Tiếp theo, thiết lập các tùy chọn rasterization, xác định kích thước mong muốn cho hình ảnh đầu ra:

```csharp
// Khởi tạo CadRasterizationOptions
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Bước 3: Chỉ định các lớp để chuyển đổi

Nếu bạn muốn chuyển đổi các lớp cụ thể, hãy thêm chúng vào tùy chọn rasterization của bạn:

```csharp
// Chỉ định lớp để chuyển đổi
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Bước 4: Thiết lập tùy chọn xuất JPEG

Bây giờ, hãy tạo tùy chọn cho định dạng hình ảnh bạn muốn xuất sang (trong trường hợp này là JPEG):

```csharp
// Tạo JpegOptions để xuất
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Bước 5: Xuất sang định dạng JPEG

Cuối cùng, lưu hình ảnh đã chuyển đổi:

```csharp
// Xác định đường dẫn tệp đầu ra và lưu hình ảnh
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Tính năng bổ sung: Chuyển đổi tất cả các lớp

Để chuyển đổi tất cả các lớp trong bản vẽ CAD của bạn, bạn có thể triển khai phương pháp như sau:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Lặp lại qua các lớp và lưu từng lớp dưới dạng tệp JPEG riêng biệt
    // Mã triển khai của bạn ở đây
}
```

## Phần kết luận

Xin chúc mừng! Bạn đã học được cách chuyển đổi hiệu quả các bố cục CAD sang định dạng hình ảnh raster bằng Aspose.CAD cho .NET. Hướng dẫn này cung cấp một phương pháp tiếp cận đơn giản phù hợp với các nhà phát triển hướng đến mục tiêu chuyển đổi CAD hiệu quả.

## Câu hỏi thường gặp

### Tôi có thể xuất sang các định dạng hình ảnh khác không?

 Chắc chắn rồi! Chỉ cần đổi thôi`JpegOptions` với các tùy chọn định dạng khác, chẳng hạn như`PngOptions` hoặc`BmpOptions`, tùy thuộc vào nhu cầu của bạn.

### Có phiên bản dùng thử không?

 Có, bạn có thể tải xuống phiên bản dùng thử để khám phá chức năng bằng cách làm theo hướng dẫn này[liên kết](https://releases.aspose.com/cad/net/).

### Tôi có thể tìm thấy sự hỗ trợ cho Aspose.CAD ở đâu?

 Để được cộng đồng hỗ trợ, hãy xem Aspose.CAD[diễn đàn](https://forum.aspose.com/c/cad/19)hoặc cân nhắc mua giấy phép để được hỗ trợ chuyên sâu hơn.

### Có thể cấp giấy phép tạm thời được không?

 Có, giấy phép tạm thời có sẵn; bạn có thể yêu cầu một giấy phép[đây](https://purchase.conholdate.com/temporary-license/).

### Tôi có thể truy cập tài liệu chi tiết ở đâu?

 Truy cập tài liệu toàn diện[đây](https://reference.aspose.com/cad/net/) để biết thêm thông tin.