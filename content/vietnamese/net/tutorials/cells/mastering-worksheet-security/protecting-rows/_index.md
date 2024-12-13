---
title: Bảo vệ các hàng trong bảng tính bằng Aspose.Cells
linktitle: Bảo vệ các hàng trong bảng tính bằng Aspose.Cells
second_title: API xử lý Excel Aspose.Cells .NET
description: Tìm hiểu cách bảo mật thông tin nhạy cảm trong bảng tính Excel của bạn bằng cách bảo vệ các hàng cụ thể bằng Aspose.Cells cho .NET. Hướng dẫn toàn diện này bao gồm mọi thứ từ thiết lập môi trường của bạn.
type: docs
weight: 18
url: /vi/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Giới thiệu

Làm việc với các tệp Excel theo chương trình thường không chỉ đòi hỏi thao tác dữ liệu mà còn phải bảo vệ dữ liệu. Việc bảo vệ các hàng cụ thể trong một bảng tính có thể rất quan trọng để bảo vệ thông tin nhạy cảm hoặc ngăn ngừa việc chỉnh sửa vô tình. Trong hướng dẫn này, chúng ta sẽ khám phá cách bảo vệ các hàng trong bảng tính Excel bằng Aspose.Cells cho .NET. Chúng tôi sẽ hướng dẫn bạn qua các bước cần thiết, từ thiết lập môi trường của bạn đến triển khai các tính năng bảo vệ hàng theo cách đơn giản.

## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn đã chuẩn bị những điều sau:

1.  Aspose.Cells cho .NET: Tải xuống và cài đặt từ[Trang tải xuống Aspose Cells](https://releases.aspose.com/cells/net/).
2. Visual Studio hoặc bất kỳ IDE .NET nào: Bạn cần một môi trường phát triển. Visual Studio được khuyến nghị, nhưng bất kỳ IDE tương thích .NET nào cũng đủ.
3. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp bạn theo dõi và sửa đổi mã ví dụ khi cần.
4.  Tài liệu API Aspose.Cells: Xem lại[Aspose.Cells cho tài liệu .NET](https://reference.aspose.com/cells/net/) để có cái nhìn tổng quan về cấu trúc và phương pháp của lớp.

Khi bạn đã chuẩn bị đủ các điều kiện tiên quyết, chúng ta có thể tiến hành triển khai.

## Nhập các gói cần thiết
Bắt đầu bằng cách nhập các gói cần thiết vào dự án C# của bạn. Các thư viện này rất cần thiết để tương tác với các tệp Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## Bước 1: Tạo một bảng tính và bảng tính mới
Trước khi áp dụng bất kỳ thiết lập bảo vệ nào, hãy tạo một bảng tính mới và chọn bảng tính bạn muốn làm việc.

```csharp
// Xác định đường dẫn đến thư mục tài liệu.
string dataDir = "Your Document Directory";
// Tạo thư mục nếu nó chưa tồn tại.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Tạo một bảng tính mới và chọn trang tính đầu tiên.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Bước 2: Xác định đối tượng Style và StyleFlag
Xác định các đối tượng kiểu và cờ kiểu, cho phép bạn sửa đổi các thuộc tính của ô, chẳng hạn như khóa hoặc mở khóa chúng.

```csharp
// Xác định kiểu và đối tượng cờ kiểu.
Style style;
StyleFlag flag;
```

## Bước 3: Mở khóa tất cả các cột trong bảng tính
Theo mặc định, tất cả các ô trong bảng tính Excel đều bị khóa. Để chỉ bảo vệ các hàng cụ thể, trước tiên hãy mở khóa tất cả các cột.

```csharp
// Lặp qua tất cả các cột và mở khóa chúng.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Bước 4: Khóa các hàng cụ thể
Bây giờ, hãy khóa các hàng bạn muốn bảo vệ. Trong ví dụ này, chúng ta sẽ khóa hàng đầu tiên.

```csharp
// Khóa hàng đầu tiên.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Bạn có thể lặp lại bước này cho bất kỳ hàng nào bạn muốn khóa.

## Bước 5: Bảo vệ tờ giấy
Khi các hàng cần thiết đã được khóa, đã đến lúc bảo vệ bảng tính. Điều này sẽ ngăn chặn việc sửa đổi các hàng đã khóa trừ khi chế độ bảo vệ bị gỡ bỏ.

```csharp
// Bảo vệ tờ giấy.
sheet.Protect(ProtectionType.All);
```

## Bước 6: Lưu sổ làm việc
Cuối cùng, lưu sổ làm việc với các thay đổi đã áp dụng. Bạn có thể chọn từ nhiều định dạng khác nhau, chẳng hạn như Excel 97-2003 hoặc các phiên bản mới hơn.

```csharp
// Lưu tệp Excel.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Phần kết luận
Xin chúc mừng! Bạn đã học thành công cách bảo vệ các hàng trong bảng tính Excel bằng Aspose.Cells cho .NET. Bằng cách làm theo các bước này, bạn có thể mở khóa hoặc khóa các hàng hoặc cột khi cần và áp dụng biện pháp bảo vệ để duy trì tính toàn vẹn của dữ liệu.

## Câu hỏi thường gặp
### Làm thế nào tôi có thể bảo vệ nhiều hàng cùng một lúc?
Bạn có thể lặp qua nhiều chỉ mục hàng và áp dụng kiểu khóa cho từng chỉ mục riêng lẻ.

### Tôi có thể đặt mật khẩu để bảo vệ trang tính không?
 Có, bạn có thể truyền mật khẩu cho`sheet.Protect()` phương pháp thực thi bảo vệ bằng mật khẩu.

### Tôi có thể mở khóa các ô cụ thể thay vì toàn bộ cột không?
Có, bạn có thể mở khóa từng ô bằng cách sửa đổi thuộc tính kiểu của chúng thay vì mở khóa toàn bộ cột.

### Điều gì xảy ra nếu tôi cố gắng chỉnh sửa một hàng được bảo vệ?
Khi một hàng được bảo vệ, Excel sẽ ngăn chặn mọi chỉnh sửa vào các ô bị khóa trừ khi trang tính đó không được bảo vệ.

### Tôi có thể bảo vệ các phạm vi cụ thể trong một hàng không?
 Có! Bạn có thể khóa các phạm vi riêng lẻ trong một hàng bằng cách thiết lập`IsLocked` thuộc tính cho các ô cụ thể trong phạm vi đó.