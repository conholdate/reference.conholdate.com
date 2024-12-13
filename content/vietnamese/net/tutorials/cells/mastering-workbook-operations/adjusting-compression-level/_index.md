---
title: Điều chỉnh mức độ nén trong Workbook
linktitle: Điều chỉnh mức độ nén trong Workbook
second_title: API xử lý Excel Aspose.Cells .NET
description: Khám phá cách quản lý hiệu quả các tệp Excel lớn bằng cách điều chỉnh mức độ nén bằng Aspose.Cells cho .NET. Hướng dẫn từng bước này bao gồm mọi thứ từ thiết lập thư mục đến đo thời gian nén, giúp bạn tối ưu hóa kích thước tệp và nâng cao hiệu suất.
type: docs
weight: 14
url: /vi/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Giới thiệu

Quản lý các tệp Excel lớn có thể là một thách thức, đặc biệt là khi nói đến hiệu quả lưu trữ và truyền tải. May mắn thay, nén tệp có thể giảm đáng kể kích thước của các tệp này, giúp xử lý chúng dễ dàng hơn. Nếu bạn đang sử dụng Aspose.Cells cho .NET, bạn có thể dễ dàng điều chỉnh mức độ nén của sổ làm việc. Hướng dẫn này sẽ hướng dẫn bạn từng bước trong quy trình, cung cấp giải thích rõ ràng về từng phần của mã.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có đủ các điều kiện tiên quyết sau:

1. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp bạn hiểu các đoạn mã tốt hơn.
2.  Thư viện Aspose.Cells: Tải xuống và cài đặt thư viện Aspose.Cells từ[đây](https://releases.aspose.com/cells/net/).
3. Visual Studio: Cần có môi trường phát triển như Visual Studio để chạy mã.
4. .NET Framework: Đảm bảo dự án của bạn được thiết lập với phiên bản .NET Framework tương thích.

## Nhập các gói cần thiết

Để bắt đầu, bạn cần nhập các gói cần thiết vào dự án C# của mình. Thêm các dòng sau vào đầu tệp mã của bạn:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Các gói này rất cần thiết để làm việc với các tệp Excel bằng thư viện Aspose.Cells.`Aspose.Cells` không gian tên chứa tất cả các lớp cần thiết để thao tác các tệp Excel, trong khi`Aspose.Cells.Xlsb` cung cấp các tùy chọn để lưu tệp theo định dạng XLSB.

## Bước 1: Xác định thư mục nguồn và thư mục đầu ra

Đầu tiên, hãy thiết lập thư mục chứa các tệp nguồn và nơi bạn muốn lưu các tệp đầu ra:

```csharp
// Xác định thư mục nguồn và thư mục đầu ra
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Hãy chắc chắn thay thế`"Your Document Directory\\"` với đường dẫn thực tế đến thư mục của bạn. Điều này đảm bảo chương trình của bạn có thể định vị được các tệp cần thiết để làm việc.

## Bước 2: Tải Workbook

Tiếp theo, tải bảng tính mà bạn muốn nén:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Ở đây, chúng ta tạo một phiên bản mới của`Workbook` lớp và tải tệp Excel hiện có. Đảm bảo tên tệp khớp với tên trong thư mục nguồn của bạn.

## Bước 3: Thiết lập tùy chọn lưu

Bây giờ, hãy cấu hình các tùy chọn lưu cho sổ làm việc của bạn:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 Các`XlsbSaveOptions`lớp này cho phép bạn chỉ định nhiều tùy chọn khác nhau khi lưu sổ làm việc của mình ở định dạng XLSB, bao gồm cả mức độ nén.

## Bước 4: Đo thời gian nén cho cấp độ 1

Bắt đầu với mức nén đầu tiên và đo thời gian cần thiết để lưu sổ làm việc:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Đoạn mã này đặt loại nén thành Mức 1, lưu sổ làm việc và đo thời gian đã trôi qua.

## Bước 5: Đo thời gian nén cho cấp độ 6

Tiếp theo, hãy kiểm tra hiệu suất với mức nén 6:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Bước này tương tự như bước trước nhưng ở mức độ nén cao hơn.

## Bước 6: Đo thời gian nén cho cấp độ 9

Cuối cùng, đánh giá hiệu suất ở mức nén cao nhất:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Bước này đặt mức nén thành Mức 9, mức mà bạn có thể thấy kích thước tệp được giảm đáng kể nhất, mặc dù có thể mất nhiều thời gian hơn để xử lý.

## Bước 7: Đầu ra cuối cùng

Sau khi hoàn tất tất cả các mức nén, hãy đưa ra thông báo cho biết quá trình đã hoàn tất thành công:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Dòng đơn giản này xác nhận rằng chương trình của bạn đã được thực thi mà không có vấn đề gì.

## Phần kết luận

Điều chỉnh mức độ nén của sổ làm việc của bạn bằng Aspose.Cells cho .NET là một quá trình đơn giản có thể dẫn đến những cải tiến đáng kể về kích thước tệp và hiệu suất. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể triển khai nén hiệu quả trong các ứng dụng của mình, nâng cao khả năng quản lý tệp Excel của bạn.

## Câu hỏi thường gặp

### Aspose.Cells là gì?  
Aspose.Cells là một thư viện mạnh mẽ dành cho .NET cho phép các nhà phát triển tạo, thao tác và chuyển đổi các tệp Excel mà không cần đến Microsoft Excel.

### Làm thế nào để cài đặt Aspose.Cells?  
 Bạn có thể tải xuống và cài đặt Aspose.Cells từ[Trang web Aspose](https://releases.aspose.com/cells/net/).

### Có những mức độ nén nào?  
Aspose.Cells hỗ trợ nhiều mức nén khác nhau, từ Mức 1 (nén thấp nhất) đến Mức 9 (nén cao nhất).

### Tôi có thể dùng thử Aspose.Cells miễn phí không?  
 Có! Bạn có thể dùng thử miễn phí Aspose.Cells[đây](https://releases.aspose.com/).

### Tôi có thể tìm thấy hỗ trợ cho Aspose.Cells ở đâu?  
 Đối với bất kỳ thắc mắc hoặc hỗ trợ nào, hãy truy cập diễn đàn hỗ trợ Aspose[đây](https://forum.aspose.com/c/cells/9).