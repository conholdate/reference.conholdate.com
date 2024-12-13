---
title: Triển khai Header và Footer với Aspose.Cells cho .NET
linktitle: Triển khai Header và Footer với Aspose.Cells cho .NET
second_title: API xử lý Excel Aspose.Cells .NET
description: Khám phá cách nâng cao tài liệu Excel của bạn bằng cách tùy chỉnh tiêu đề và chân trang theo chương trình bằng Aspose.Cells cho .NET. Hướng dẫn toàn diện này hướng dẫn bạn từng bước—từ thiết lập sổ làm việc đến chèn tên bảng tính động.
type: docs
weight: 22
url: /vi/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## Giới thiệu

Tiêu đề và chân trang là các thành phần thiết yếu trong bảng tính Excel, cung cấp thông tin ngữ cảnh quan trọng như tên tệp, ngày tháng và số trang. Cho dù bạn đang tự động hóa báo cáo hay tạo tệp động, Aspose.Cells for .NET đều đơn giản hóa quy trình tùy chỉnh tiêu đề và chân trang theo chương trình. Hướng dẫn này cung cấp phương pháp từng bước để cải thiện tệp Excel của bạn bằng tiêu đề và chân trang được trau chuốt và chuyên nghiệp.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những thứ sau:

1.  Aspose.Cells cho .NET: Tải xuống và cài đặt từ[đây](https://releases.aspose.com/cells/net/).
2. Thiết lập IDE: Sử dụng Visual Studio hoặc IDE bạn thích với .NET framework.
3.  Giấy phép: Bắt đầu bằng bản dùng thử miễn phí, nhưng hãy cân nhắc việc lấy giấy phép đầy đủ hoặc tạm thời để có đầy đủ chức năng. Bạn có thể[xin giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).

## Nhập các gói cần thiết

Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Điều này sẽ giúp bạn truy cập vào các lớp và phương thức cần thiết để làm việc với tiêu đề, chân trang và các chức năng Excel khác trong Aspose.Cells.

## Bước 1: Tạo Workbook và Access Page Setup

Bắt đầu bằng cách tạo một sổ làm việc mới và truy cập vào thiết lập trang của trang tính. Đây là nơi bạn sẽ sửa đổi cài đặt tiêu đề và chân trang.

```csharp
// Xác định đường dẫn để lưu tài liệu của bạn
string dataDir = "Your Document Directory";

// Khởi tạo một đối tượng Workbook
Workbook excel = new Workbook();
```

 Ở đây, một`Workbook` đối tượng đại diện cho tệp Excel của bạn.`PageSetup` Thuộc tính của bảng tính sẽ cho phép bạn tùy chỉnh đầu trang và chân trang.

## Bước 2: Truy cập Thuộc tính Worksheet và PageSetup

 Mỗi bảng tính trong Aspose.Cells có một`PageSetup` thuộc tính điều khiển các tính năng bố trí, bao gồm cả phần đầu trang và phần chân trang. Có được`PageSetup` đối tượng cho bảng tính của bạn:

```csharp
// Lấy tham chiếu đến PageSetup của trang tính đầu tiên
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Hiện nay,`pageSetup` chứa các thiết lập cần thiết để tùy chỉnh đầu trang và chân trang.

## Bước 3: Đặt Phần Bên Trái của Tiêu Đề

Tiêu đề bao gồm ba phần: trái, giữa và phải. Hãy bắt đầu bằng cách thiết lập phần bên trái để hiển thị tên bảng tính.

```csharp
// Đặt tên bảng tính ở phần bên trái của tiêu đề
pageSetup.SetHeader(0, "&A");
```

 Sử dụng`&A`hiển thị tên trang tính một cách động, đặc biệt hữu ích cho các sổ làm việc có nhiều trang tính.

## Bước 4: Thêm Ngày và Giờ vào Giữa Tiêu đề

Tiếp theo, thêm ngày và giờ hiện tại vào phần giữa của tiêu đề, áp dụng phông chữ tùy chỉnh để tạo kiểu.

```csharp
// Đặt ngày và giờ ở phần giữa của tiêu đề với phông chữ đậm
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

Trong dòng này:
- `&D` chèn ngày hiện tại.
- `&T` chèn thời gian hiện tại.
- `"Times New Roman,Bold"` áp dụng phông chữ Times New Roman đậm.

## Bước 5: Hiển thị Tên Tệp ở Phần Bên Phải của Tiêu đề

Để hoàn thiện phần tiêu đề, hãy hiển thị tên tệp ở bên phải với kích thước phông chữ được chỉ định.

```csharp
// Hiển thị tên tệp ở phần bên phải của tiêu đề với kích thước phông chữ tùy chỉnh
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Đây,`&F` đại diện cho tên tập tin và`&12` đặt kích thước phông chữ là 12.

## Bước 6: Thêm văn bản tùy chỉnh vào phần chân trang bên trái

Bây giờ, chúng ta hãy thiết lập phần chân trang bên trái bằng văn bản tùy chỉnh và kiểu phông chữ cụ thể.

```csharp
// Thêm văn bản tùy chỉnh với kiểu phông chữ vào phần bên trái của chân trang
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

Trong ví dụ này, văn bản`123` được thiết kế theo phông chữ "Courier New" cỡ 14, trong khi phần còn lại vẫn giữ nguyên phông chữ chân trang mặc định.

## Bước 7: Chèn số trang vào giữa chân trang

Việc thêm số trang vào chân trang giúp người đọc theo dõi các tài liệu nhiều trang.

```csharp
// Chèn số trang vào phần giữa của chân trang
pageSetup.SetFooter(1, "&P");
```

 Các`&P` mã thêm số trang hiện tại vào phần giữa của chân trang.

## Bước 8: Hiển thị Tổng số trang trong Phần chân trang bên phải

Hoàn thiện phần chân trang bằng cách hiển thị tổng số trang ở phần bên phải.

```csharp
// Hiển thị tổng số trang ở phần bên phải của chân trang
pageSetup.SetFooter(2, "&N");
```

 Các`&N` mã cung cấp tổng số trang, thông báo cho người đọc về độ dài của tài liệu.

## Bước 9: Lưu sổ làm việc

Cuối cùng, lưu bảng tính để tạo tệp Excel có tiêu đề và chân trang tùy chỉnh.

```csharp
// Lưu sổ làm việc
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Dòng này lưu tệp với các tùy chỉnh của bạn.

## Phần kết luận

Tùy chỉnh tiêu đề và chân trang trong bảng tính Excel giúp nâng cao tính chuyên nghiệp của tài liệu. Với Aspose.Cells for .NET, bạn có thể dễ dàng kiểm soát các thành phần này, từ việc hiển thị tên bảng tính đến chèn văn bản tùy chỉnh, ngày tháng, thời gian và số trang động. Bây giờ bạn đã học được các bước, bạn có thể nâng cao các dự án tự động hóa Excel của mình.

## Câu hỏi thường gặp

### Tôi có thể sử dụng các phông chữ khác nhau cho các phần khác nhau của đầu trang và chân trang không?
Có, Aspose.Cells cho phép bạn chỉ định phông chữ duy nhất cho từng phần của đầu trang và chân trang.

### Làm thế nào để xóa phần đầu trang và phần chân trang?
 Xóa tiêu đề và chân trang bằng cách đặt văn bản của chúng thành một chuỗi trống bằng cách sử dụng`SetHeader` hoặc`SetFooter`.

### Tôi có thể chèn hình ảnh vào đầu trang hoặc chân trang bằng Aspose.Cells cho .NET không?
Hiện tại, Aspose.Cells chủ yếu hỗ trợ văn bản trong tiêu đề và chân trang. Hình ảnh có thể yêu cầu các phương pháp thay thế, như chèn trực tiếp vào bảng tính.

### Aspose.Cells có hỗ trợ dữ liệu động ở phần đầu trang và chân trang không?  
 Có, bạn có thể sử dụng nhiều mã động khác nhau (như`&D`cho ngày hoặc`&P` để thêm số trang) để thêm nội dung động.

### Làm thế nào để điều chỉnh chiều cao của phần đầu trang hoặc phần chân trang?  
 Aspose.Cells cung cấp các tùy chọn trong`PageSetup` lớp để điều chỉnh lề đầu trang và chân trang, cho phép bạn kiểm soát khoảng cách.