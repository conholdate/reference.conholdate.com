---
title: Thêm Mục lục vào Tài liệu PDF
linktitle: Thêm Mục lục vào Tài liệu PDF
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Hướng dẫn này trình bày cách thêm Mục lục (TOC) vào tài liệu PDF bằng Aspose.Pdf cho .NET.
type: docs
weight: 40
url: /vi/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Giới thiệu

Tạo mục lục (TOC) trong tài liệu PDF có thể cải thiện đáng kể khả năng điều hướng và khả năng truy cập của tài liệu. Trong hướng dẫn này, chúng tôi sẽ trình bày cách thêm mục lục vào tệp PDF bằng Aspose.Pdf cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1.   Aspose.PDF cho .NET: Tải xuống và cài đặt phiên bản mới nhất từ[đây](https://releases.aspose.com/pdf/net/).
2.  Môi trường phát triển: Thiết lập môi trường phát triển .NET như Visual Studio.
3.   Giấy phép: Yêu cầu cấp giấy phép tạm thời nếu cần; vui lòng truy cập[Trang cấp phép Aspose.Pdf](https://asposepdf.com/developers) để biết thêm thông tin.

Nhập các thư viện cần thiết

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Bước 1: Tải Tài liệu PDF

Tải tệp PDF hiện tại của bạn vào nơi bạn muốn thêm TOC. Chỉ định đường dẫn đến thư mục tài liệu của bạn.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Bước 2: Chèn một trang mới cho mục lục

Chèn một trang mới vào đầu tài liệu PDF. Trang này sẽ đóng vai trò là Mục lục (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Bước 3: Tạo Đối tượng thông tin TOC

Tạo một đối tượng sẽ biểu diễn thông tin TOC. Thêm tiêu đề và liên kết đến tiêu đề đó để điều hướng tốt hơn.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Bước 4: Xác định các phần tử mục lục

Xác định các thành phần (hoặc tiêu đề) sẽ được hiển thị trong Mục lục. Các thành phần này có thể giúp người đọc điều hướng đến các phần cụ thể của tài liệu.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Bước 5: Tạo tiêu đề mục lục

Tạo tiêu đề cho hai phần tử đầu tiên trong Mục lục. Các tiêu đề này sẽ liên kết đến các trang tương ứng.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Bước 6: Lưu PDF với TOC

Cuối cùng, lưu tệp PDF đã cập nhật.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Tin nhắn xác nhận

Hiển thị thông báo xác nhận để người dùng biết rằng quá trình đã hoàn tất.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Phần kết luận

Với Aspose.PDF for .NET, việc thêm Mục lục vào PDF không chỉ dễ dàng mà còn có thể tùy chỉnh. Cho dù bạn cần tạo liên kết điều hướng đơn giản hay cấu trúc phức tạp, công cụ này đều có thể đáp ứng. Vì vậy, lần tới khi bạn làm việc trên một tệp PDF dài, đừng quên thêm Mục lục để tạo nét chuyên nghiệp.

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh giao diện của mục lục trong Aspose.PDF không?

Có, bạn có thể tùy chỉnh hoàn toàn giao diện của mục lục, bao gồm kiểu phông chữ, kích thước và căn chỉnh.

### Làm thế nào để thêm tiêu đề phụ vào Mục lục?

Bạn có thể thêm tiêu đề phụ bằng cách điều chỉnh`Heading` mức độ (ví dụ,`Heading(2)`).

### Có thể tự động cập nhật Mục lục nếu tài liệu thay đổi không?

Không, TOC sẽ không tự động cập nhật. Bạn sẽ cần phải tạo lại nếu cấu trúc tài liệu thay đổi.

### Tôi có thể liên kết mục lục với các tài liệu bên ngoài không?

Có, bạn có thể sử dụng siêu liên kết để liên kết mục lục với các tệp PDF hoặc URL bên ngoài.

### Aspose.PDF có hỗ trợ mục lục đa cấp không?

Có, Aspose.PDF hỗ trợ mục lục nhiều cấp cho các tài liệu phức tạp có nhiều tiểu mục.
