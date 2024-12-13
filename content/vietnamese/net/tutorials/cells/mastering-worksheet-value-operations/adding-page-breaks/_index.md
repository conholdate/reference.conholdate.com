---
title: Thêm ngắt trang trong trang tính bằng Aspose.Cells
linktitle: Thêm ngắt trang trong trang tính bằng Aspose.Cells
second_title: API xử lý Excel Aspose.Cells .NET
description: Khám phá cách cải thiện bảng tính Excel của bạn bằng cách thêm ngắt trang theo chiều ngang và chiều dọc hiệu quả bằng Aspose.Cells cho .NET. Hướng dẫn toàn diện này hướng dẫn bạn qua các bước thiết lập, mã hóa cần thiết.
type: docs
weight: 10
url: /vi/net/tutorials/cells/mastering-worksheet-value-operations/adding-page-breaks/
---
## Giới thiệu

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn cách thêm cả ngắt trang theo chiều ngang và chiều dọc vào bảng tính Excel của bạn bằng Aspose.Cells for .NET. Cuối cùng, bạn sẽ được trang bị để triển khai các kỹ thuật này trong các dự án của mình một cách liền mạch. Hãy bắt đầu nào!

## Điều kiện tiên quyết
Trước khi tìm hiểu mã, hãy đảm bảo bạn đã chuẩn bị những thông tin sau:
- Visual Studio: Đảm bảo Visual Studio đã được cài đặt trên hệ thống của bạn.
-  Aspose.Cells cho .NET: Tải xuống và cài đặt thư viện Aspose.Cells. Bạn có thể nhận phiên bản dùng thử miễn phí[đây](https://releases.aspose.com/cells/net/).
- .NET Framework: Hướng dẫn này giả định bạn đang sử dụng .NET Framework hoặc .NET Core. Quy trình có thể hơi khác nhau đối với các môi trường khác.
- Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# và khái niệm ngắt trang trong Excel sẽ rất hữu ích.

## Nhập gói
Để làm việc với Aspose.Cells, hãy bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Khi đã nhập các không gian tên này, bạn có thể bắt đầu tương tác với các tệp Excel và áp dụng các sửa đổi, bao gồm cả ngắt trang.

## Bước 1: Thiết lập sổ làm việc của bạn
 Tạo một bảng tính mới bằng cách sử dụng`Workbook` lớp này đóng vai trò là nền tảng để thao tác với các tệp Excel.

```csharp
// Xác định đường dẫn đến thư mục nơi tập tin của bạn sẽ được lưu
string dataDir = "Your Document Directory";
// Tạo một đối tượng Workbook mới
Workbook workbook = new Workbook();
```
Trong đoạn mã này:
- `dataDir` chỉ định vị trí lưu tệp của bạn.
-  Các`Workbook` đối tượng đã được khởi tạo, sẵn sàng để sửa đổi.

## Bước 2: Thêm Ngắt trang theo chiều ngang
Để thêm ngắt trang theo chiều ngang, chia trang tính thành hai phần theo chiều dọc, hãy sử dụng mã sau:

```csharp
// Thêm ngắt trang theo chiều ngang ở hàng 30
workbook.Worksheets[0].HorizontalPageBreaks.Add("Y30");
```
 Đây,`Worksheets[0]` đề cập đến trang tính đầu tiên trong sổ làm việc và`HorizontalPageBreaks.Add("Y30")` thêm một ngắt dòng ở hàng 30, khiến nội dung phía trên xuất hiện trên một trang và nội dung phía dưới bắt đầu trên một trang mới.

## Bước 3: Thêm Ngắt trang theo chiều dọc
Tiếp theo, bạn có thể thêm ngắt trang theo chiều dọc để phân tách nội dung theo chiều ngang trên các cột:

```csharp
// Thêm ngắt trang theo chiều dọc ở cột Y
workbook.Worksheets[0].VerticalPageBreaks.Add("Y30");
```
 Trong ví dụ này,`VerticalPageBreaks.Add("Y30")`tạo một khoảng ngắt sau cột X, đảm bảo rằng nội dung bên trái xuất hiện trên một trang và nội dung bên phải xuất hiện trên trang tiếp theo.

## Bước 4: Lưu sổ làm việc
Cuối cùng, hãy lưu sổ làm việc để lưu lại những thay đổi:

```csharp
// Lưu tệp Excel
workbook.Save(dataDir + "AddingPageBreaks_out.xls");
```
Dòng này lưu sổ làm việc với các ngắt trang được thêm vào đường dẫn đã chỉ định (`AddingPageBreaks_out.xls`).

## Phần kết luận
Thêm ngắt trang trong Excel là điều cần thiết để quản lý các tập dữ liệu lớn và chuẩn bị tài liệu để in. Với Aspose.Cells for .NET, bạn có thể tự động chèn ngắt trang theo chiều ngang và chiều dọc, giúp tài liệu của bạn được sắp xếp hợp lý hơn và dễ đọc hơn.

## Câu hỏi thường gặp

### Làm thế nào để thêm nhiều ngắt trang trong Aspose.Cells cho .NET?
 Bạn có thể thêm nhiều ngắt trang bằng cách gọi`HorizontalPageBreaks.Add()` hoặc`VerticalPageBreaks.Add()` phương pháp nhiều lần với các tham chiếu ô khác nhau.

### Tôi có thể thêm ngắt trang vào một trang tính cụ thể trong một sổ làm việc không?
 Có, hãy chỉ định bảng tính bằng cách sử dụng`Worksheets[index]` tài sản, nơi`index` là chỉ số bắt đầu từ số 0 của bảng tính mong muốn.

### Làm thế nào để xóa ngắt trang trong Aspose.Cells cho .NET?
Xóa ngắt trang bằng cách sử dụng`HorizontalPageBreaks.RemoveAt()` hoặc`VerticalPageBreaks.RemoveAt()` bằng cách chỉ định mục lục của ngắt trang mà bạn muốn xóa.

### Tôi có thể tự động thêm ngắt trang dựa trên kích thước nội dung không?
Aspose.Cells không cung cấp tính năng tự động cho việc này, nhưng bạn có thể tính toán vị trí ngắt dựa trên số lượng hàng/cột theo chương trình.

### Tôi có thể thiết lập ngắt trang dựa trên phạm vi ô cụ thể không?
Có, bạn có thể chỉ định ngắt trang cho bất kỳ ô hoặc phạm vi nào bằng cách cung cấp tham chiếu ô tương ứng, chẳng hạn như "A1" hoặc "B15".