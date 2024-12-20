---
title: Thuật toán nhị phân hóa Bradley
linktitle: Thuật toán nhị phân hóa Bradley
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Tìm hiểu cách chuyển đổi các trang PDF thành hình ảnh TIFF nhị phân chất lượng cao bằng thuật toán nhị phân bradley trong Aspose.PDF cho .NET. Hướng dẫn từng bước này bao gồm ví dụ về mã.
type: docs
weight: 30
url: /vi/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Giới thiệu

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình chuyển đổi trang PDF thành hình ảnh TIFF bằng Thuật toán nhị phân hóa Bradley. Aspose.PDF cho .NET đơn giản hóa nhiệm vụ này, cho phép bạn tự động hóa và hợp lý hóa quy trình làm việc tài liệu của mình một cách dễ dàng.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Aspose.PDF cho .NET: Tải xuống thư viện từ[đây](https://releases.aspose.com/pdf/net/).
- Visual Studio (hoặc bất kỳ IDE C# nào).
- Kiến thức cơ bản về C#.
-  Một giấy phép hợp lệ hoặc một[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) từ Aspose.

## Bước 1: Thiết lập dự án của bạn

Đầu tiên, hãy tạo một dự án C# mới trong IDE của bạn và nhập các không gian tên cần thiết:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Bước 2: Xác định thư mục tài liệu

Chỉ định đường dẫn đến thư mục chứa tài liệu PDF của bạn cũng như đường dẫn đầu ra cho hình ảnh TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Đường dẫn đến tệp PDF của bạn
```

Thư mục này sẽ lưu trữ cả tệp PDF nguồn và tệp TIFF đã chuyển đổi.

## Bước 3: Tải tài liệu PDF

Mở tài liệu PDF bạn muốn chuyển đổi:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Thay thế`PageToTIFF.pdf` bằng tên tệp PDF của bạn.

## Bước 4: Chỉ định Đường dẫn đầu ra

Xác định đường dẫn đầu ra cho các tệp TIFF được tạo:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Bước 5: Thiết lập độ phân giải hình ảnh

Đặt độ phân giải cho hình ảnh TIFF. DPI cao hơn sẽ mang lại chất lượng hình ảnh tốt hơn:

```csharp
Resolution resolution = new Resolution(300);
```

## Bước 6: Cấu hình cài đặt TIFF

Cấu hình cài đặt cho hình ảnh TIFF, bao gồm nén và độ sâu màu:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Sử dụng 1bpp (1 bit cho mỗi pixel) để chuẩn bị hình ảnh cho đầu ra nhị phân.

## Bước 7: Tạo thiết bị TIFF

Tạo một thiết bị TIFF để xử lý việc chuyển đổi:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Bước 8: Chuyển đổi trang PDF sang TIFF

Chuyển đổi trang đầu tiên của PDF thành hình ảnh TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Bước 9: Áp dụng thuật toán nhị phân hóa Bradley

Bây giờ, hãy áp dụng Thuật toán Bradley để chuyển đổi ảnh TIFF thang độ xám thành ảnh nhị phân:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 Các`BinarizeBradley` phương pháp này sử dụng hai luồng tệp (đầu vào và đầu ra) và một giá trị ngưỡng. Điều chỉnh ngưỡng khi cần để có kết quả tối ưu.

## Bước 10: Xác nhận chuyển đổi thành công

Cuối cùng, hãy xác nhận việc chuyển đổi đã thành công:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Phần kết luận

Xin chúc mừng! Bạn đã chuyển đổi thành công một trang PDF thành hình ảnh TIFF và áp dụng Thuật toán nhị phân hóa Bradley bằng Aspose.PDF cho .NET. Quy trình này rất cần thiết cho việc lưu trữ tài liệu, OCR và các ứng dụng chuyên nghiệp khác. Với độ phân giải chất lượng cao và khả năng nén hiệu quả, hình ảnh tài liệu của bạn sẽ rõ nét và có kích thước dễ quản lý.

## Câu hỏi thường gặp

### Thuật toán Bradley là gì?
Thuật toán Bradley là một kỹ thuật nhị phân hóa chuyển đổi ảnh thang độ xám thành ảnh nhị phân bằng cách xác định ngưỡng thích ứng cho từng pixel dựa trên môi trường xung quanh.

### Tôi có thể chuyển đổi nhiều trang PDF sang TIFF bằng phương pháp này không?
 Có, bạn có thể sửa đổi`Process` phương pháp lặp qua tất cả các trang trong tài liệu để chuyển đổi.

### Độ phân giải tối ưu để chuyển đổi PDF sang TIFF là bao nhiêu?
Độ phân giải 300 DPI thường được khuyến nghị cho hình ảnh chất lượng cao, nhưng bạn có thể điều chỉnh tùy theo nhu cầu cụ thể của mình.

### Độ sâu màu 1bpp có nghĩa là gì?
1bpp (1 bit cho mỗi pixel) biểu thị rằng hình ảnh sẽ có màu đen và trắng, trong đó mỗi pixel có màu đen hoàn toàn hoặc màu trắng hoàn toàn.

### Thuật toán Bradley có phù hợp với OCR không?
Có, Thuật toán Bradley thường được sử dụng trong quá trình xử lý trước OCR vì nó tăng cường độ tương phản của văn bản trong các tài liệu được quét, cải thiện độ chính xác khi nhận dạng.