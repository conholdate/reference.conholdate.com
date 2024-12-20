---
title: Danh sách đánh số phong cách sử dụng Aspose.PDF cho .NET
linktitle: Danh sách đánh số phong cách sử dụng Aspose.PDF cho .NET
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Khám phá cách tạo danh sách được đánh số đẹp mắt trong tài liệu PDF của bạn bằng Aspose.PDF cho .NET. Hướng dẫn này hướng dẫn bạn quy trình áp dụng nhiều kiểu đánh số khác nhau—như số La Mã.
type: docs
weight: 10
url: /vi/net/programming-with-headings/stylish-numbered-lists/
---
## Giới thiệu

Bạn đã bao giờ cần tạo danh sách được đánh số, có cấu trúc tốt trong tài liệu PDF của mình chưa? Cho dù đó là tài liệu pháp lý, báo cáo hay bài thuyết trình, thì các kiểu đánh số hiệu quả đều rất quan trọng để sắp xếp nội dung của bạn. Với Aspose.PDF for .NET, bạn có thể dễ dàng áp dụng nhiều kiểu đánh số khác nhau cho tiêu đề PDF của mình, tạo ra các tài liệu được trau chuốt và chuyên nghiệp.

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, hãy đảm bảo bạn đã chuẩn bị những thứ sau:

1.  Aspose.PDF cho .NET: Tải xuống phiên bản mới nhất từ[đây](https://releases.aspose.com/pdf/net/).
2. Môi trường phát triển: Bạn sẽ cần Visual Studio hoặc bất kỳ IDE nào tương thích với .NET.
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework 4.0 trở lên.
4.  Giấy phép: Bạn có thể sử dụng giấy phép tạm thời từ[đây](https://purchase.aspose.com/temporary-license/) hoặc khám phá[dùng thử miễn phí](https://releases.aspose.com/) tùy chọn.

## Nhập các gói cần thiết

Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Bước 1: Thiết lập tài liệu

Hãy bắt đầu bằng cách tạo một tài liệu PDF mới và cấu hình bố cục của nó, bao gồm kích thước trang và lề.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document pdfDoc = new Document();

// Đặt kích thước và lề trang
pdfDoc.PageInfo.Width = 612.0; // 8,5 inch
pdfDoc.PageInfo.Height = 792.0; // 11 inch
pdfDoc.PageInfo.Margin = new Aspose.Pdf.MarginInfo(72, 72, 72, 72); // Lề 1 inch
```

Thiết lập này cung cấp cho tài liệu của bạn kích thước chữ chuẩn với lề một inch ở tất cả các cạnh.

## Bước 2: Thêm trang vào PDF

Tiếp theo, chúng ta sẽ thêm một trang trống vào tài liệu PDF, nơi chúng ta sẽ áp dụng các kiểu đánh số sau đó.

```csharp
// Thêm một trang mới vào tài liệu PDF
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();
pdfPage.PageInfo = pdfDoc.PageInfo; //Sử dụng các thiết lập giống như tài liệu
```

## Bước 3: Tạo hộp nổi

FloatingBox cho phép bạn định vị nội dung độc lập với luồng trang, giúp bạn kiểm soát bố cục tốt hơn.

```csharp
// Tạo FloatingBox cho nội dung có cấu trúc
Aspose.Pdf.FloatingBox floatBox = new Aspose.Pdf.FloatingBox
{
    Margin = pdfPage.PageInfo.Margin
};
pdfPage.Paragraphs.Add(floatBox);
```

## Bước 4: Thêm tiêu đề bằng số La Mã

Bây giờ, chúng ta hãy thêm tiêu đề đầu tiên bằng cách đánh số La Mã thường.

```csharp
// Tạo tiêu đề đầu tiên bằng số La Mã
Aspose.Pdf.Heading heading1 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 1,
    Text = "List 1",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading1);
```

## Bước 5: Thêm Tiêu đề Thứ hai với Số Bắt đầu Tùy chỉnh

Tiếp theo, chúng ta sẽ thêm tiêu đề thứ hai, bắt đầu từ số La Mã 13.

```csharp
// Tạo tiêu đề thứ hai bắt đầu bằng số La Mã 13
Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1)
{
    IsInList = true,
    StartNumber = 13,
    Text = "List 2",
    Style = NumberingStyle.NumeralsRomanLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading2);
```

## Bước 6: Thêm Tiêu đề theo Số thứ tự chữ cái

Để đa dạng hơn, chúng ta hãy thêm tiêu đề thứ ba bằng cách đánh số theo chữ cái thường.

```csharp
// Tạo tiêu đề với số thứ tự chữ cái
Aspose.Pdf.Heading heading3 = new Aspose.Pdf.Heading(2)
{
    IsInList = true,
    StartNumber = 1,
    Text = "The value, as of the effective date of the plan, of property to be distributed under the plan on account of each allowed",
    Style = NumberingStyle.LettersLowercase,
    IsAutoSequence = true
};
floatBox.Paragraphs.Add(heading3);
```

## Bước 7: Lưu PDF

Cuối cùng, hãy lưu tệp PDF vào thư mục bạn mong muốn.

```csharp
// Lưu tài liệu PDF
dataDir = dataDir + "ApplyNumberStyle_out.pdf";
pdfDoc.Save(dataDir);
Console.WriteLine($"\nNumber style applied successfully in headings.\nFile saved at {dataDir}");
```

## Phần kết luận

Xin chúc mừng! Bạn đã áp dụng thành công nhiều kiểu đánh số khác nhau—chữ số La Mã và chữ cái—vào tiêu đề trong tệp PDF bằng Aspose.PDF cho .NET. Tính linh hoạt của Aspose.PDF cho phép bạn kiểm soát bố cục trang, kiểu đánh số và vị trí nội dung, giúp bạn tạo các tài liệu PDF được tổ chức tốt và chuyên nghiệp.

## Câu hỏi thường gặp

### Tôi có thể áp dụng nhiều kiểu số khác nhau cho cùng một tài liệu PDF không?  
Có, bạn có thể kết hợp nhiều kiểu đánh số khác nhau, chẳng hạn như số La Mã, số Ả Rập và đánh số theo chữ cái trong cùng một tài liệu.

### Làm thế nào tôi có thể tùy chỉnh số bắt đầu cho tiêu đề?  
 Bạn có thể thiết lập số bắt đầu cho bất kỳ tiêu đề nào bằng cách sử dụng`StartNumber` tài sản.

### Có cách nào để thiết lập lại trình tự đánh số không?  
 Có, bạn có thể thiết lập lại số bằng cách điều chỉnh`StartNumber` thuộc tính cho mỗi tiêu đề.

### Tôi có thể áp dụng kiểu in đậm hoặc in nghiêng cho tiêu đề ngoài việc đánh số không?  
 Chắc chắn rồi! Bạn có thể tùy chỉnh kiểu tiêu đề bằng cách sửa đổi các thuộc tính như phông chữ, kích thước, in đậm và in nghiêng bằng cách sử dụng`TextState` sự vật.

### Làm thế nào để tôi có được giấy phép tạm thời cho Aspose.PDF?  
 Bạn có thể xin giấy phép tạm thời từ[đây](https://purchase.aspose.com/temporary-license/)để thử nghiệm Aspose.PDF mà không có hạn chế.