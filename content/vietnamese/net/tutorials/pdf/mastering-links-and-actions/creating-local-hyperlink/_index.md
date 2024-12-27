---
title: Tạo siêu liên kết cục bộ trong tệp PDF
linktitle: Tạo siêu liên kết cục bộ trong tệp PDF
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Khám phá cách cải thiện khả năng điều hướng trong tài liệu PDF của bạn bằng cách tạo siêu liên kết cục bộ bằng Aspose.PDF cho .NET. Hướng dẫn từng bước này sẽ hướng dẫn bạn thực hiện toàn bộ quy trình.
type: docs
weight: 40
url: /vi/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Giới thiệu

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình tạo siêu liên kết cục bộ trong tệp PDF bằng Aspose.PDF cho .NET. Chúng tôi sẽ chia nhỏ từng bước một cách rõ ràng, đảm bảo rằng ngay cả khi bạn mới làm quen với thao tác PDF, bạn vẫn có thể dễ dàng thực hiện theo.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có những điều sau:

1.  Visual Studio: Tải xuống từ[Trang web Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.PDF cho .NET: Tải xuống thư viện thông qua[Trang web Aspose](https://releases.aspose.com/pdf/net/). Thư viện này cung cấp một bộ tính năng phong phú để thao tác với PDF.
3. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp ích, nhưng đừng lo lắng; chúng tôi sẽ giải thích từng dòng mã.
4. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy của mình. Kiểm tra các yêu cầu trên Aspose.PDF[tài liệu](https://reference.aspose.com/pdf/net/).

Với những điều kiện tiên quyết này, bạn đã sẵn sàng tìm hiểu cách tạo siêu liên kết cục bộ trong tài liệu PDF của mình!

## Nhập các gói cần thiết

Bây giờ bạn đã thiết lập xong, đã đến lúc nhập các gói cần thiết vào dự án C# của bạn.

### Mở dự án của bạn

Mở dự án .NET hiện tại của bạn hoặc tạo một dự án mới trong Visual Studio. Nếu bạn bắt đầu mới, hãy chọn "Create a new project" từ màn hình khởi động.

### Thêm tham chiếu đến Aspose.PDF

 Nhấp chuột phải vào "Dependencies" trong thư mục dự án của bạn trong Solution Explorer. Chọn "Manage NuGet Packages", tìm kiếm`Aspose.PDF`và cài đặt phiên bản mới nhất hiện có. Điều này sẽ mang đến tất cả các công cụ bạn cần để tạo và thao tác PDF.

### Nhập không gian tên

Ở đầu tệp .cs của bạn, hãy thêm lệnh sau bằng cách sử dụng:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Các chỉ thị này cho phép bạn truy cập các tính năng của thư viện một cách liền mạch.

Chúng ta hãy chia nhỏ quá trình tạo siêu liên kết cục bộ thành các bước đơn giản.

## Bước 1: Thiết lập phiên bản tài liệu

 Tạo một phiên bản mới của`Document` lớp, đại diện cho tệp PDF mà bạn sẽ làm việc.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Thiết lập thư mục tài liệu của bạn
Document doc = new Document(); // Tạo phiên bản Tài liệu
```

 Thay thế`"YOUR_DOCUMENT_DIRECTORY"` với đường dẫn thực tế trên hệ thống của bạn nơi tệp PDF sẽ được lưu.

## Bước 2: Thêm Trang vào Tài liệu

Tiếp theo, thêm một trang vào tài liệu PDF của bạn.

```csharp
Page page = doc.Pages.Add(); // Thêm một trang mới
```

Dòng này sẽ thêm một trang mới vào tài liệu, nơi bạn sẽ đặt toàn bộ nội dung của mình.

## Bước 3: Tạo một đoạn văn bản

Bây giờ, chúng ta hãy tạo một đoạn văn bản có chức năng như một liên kết có thể nhấp vào.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Tạo một đoạn văn bản
```

 Cái này`TextFragment` sẽ hiển thị văn bản mà người dùng có thể nhấp vào.

## Bước 4: Tạo siêu liên kết cục bộ

Bây giờ, hãy tạo một siêu liên kết cục bộ trỏ tới trang 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Tạo siêu liên kết cục bộ
link.TargetPageNumber = 7; // Đặt trang đích cho liên kết
text.Hyperlink = link; // Đặt siêu liên kết cho đoạn văn bản
```

 Các`LocalHyperlink` lớp cho phép bạn chỉ định số trang đích cho siêu liên kết.

## Bước 5: Thêm đoạn văn bản vào trang

Thêm văn bản có thể nhấp vào trang bạn đã tạo.

```csharp
page.Paragraphs.Add(text); // Thêm đoạn văn bản vào trang
```

Dòng này sẽ thêm văn bản của bạn vào tập hợp đoạn văn của trang.

## Bước 6: Tạo một đoạn văn bản khác (Tùy chọn)

Hãy thêm một siêu liên kết khác để quay lại trang 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Tạo một đoạn văn bản mới
textBack.IsInNewPage = true; // Chỉ ra nó phải ở một trang mới
```

## Bước 7: Thiết lập siêu liên kết cục bộ thứ hai

Tạo một siêu liên kết cục bộ khác cho trang 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Tạo một siêu liên kết cục bộ khác
linkBack.TargetPageNumber = 1; // Đặt trang đích cho siêu liên kết thứ hai
textBack.Hyperlink = linkBack; // Đặt siêu liên kết cho đoạn văn bản thứ hai
```

## Bước 8: Thêm đoạn văn bản thứ hai vào trang mới

Thêm đoạn văn bản thứ hai vào trang của nó.

```csharp
Page newPage = doc.Pages.Add(); // Thêm một trang mới cho liên kết thứ hai
newPage.Paragraphs.Add(textBack); // Thêm đoạn văn bản vào trang mới
```

## Bước 9: Lưu tài liệu

Cuối cùng, hãy lưu tài liệu của bạn.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Chỉ định tên tệp đầu ra
doc.Save(dataDir); // Lưu tài liệu đã cập nhật
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Dòng này kết hợp đường dẫn thư mục của bạn với tên tệp và`Save()` phương pháp lưu tài liệu của bạn.

## Phần kết luận

Tạo siêu liên kết cục bộ trong tệp PDF bằng Aspose.PDF cho .NET là một tính năng thực tế giúp tăng cường điều hướng và trải nghiệm của người dùng. Bây giờ bạn có kiến thức để hướng dẫn người đọc trực tiếp đến thông tin họ cần, giúp tệp PDF của bạn tương tác và thân thiện hơn với người dùng.

## Câu hỏi thường gặp

### Aspose.PDF dành cho .NET là gì?
Aspose.PDF for .NET là thư viện cho phép các nhà phát triển tạo, chỉnh sửa và chuyển đổi tài liệu PDF theo chương trình bằng cách sử dụng nền tảng .NET.

### Tôi có thể tạo siêu liên kết tới các trang web bên ngoài không?
Có, Aspose.PDF cũng hỗ trợ tạo siêu liên kết đến các URL bên ngoài ngoài các siêu liên kết cục bộ trong PDF.

### Có bản dùng thử miễn phí Aspose.PDF không?
 Chắc chắn rồi! Bạn có thể truy cập bản dùng thử miễn phí từ[Trang web Aspose](https://releases.aspose.com/).

### Aspose hỗ trợ những ngôn ngữ lập trình nào?
Aspose cung cấp các thư viện cho nhiều ngôn ngữ lập trình khác nhau, bao gồm Java, C++và Python, cùng nhiều ngôn ngữ khác.

### Làm thế nào để tôi nhận được hỗ trợ cho các sản phẩm Aspose?
 Bạn có thể tìm kiếm sự hỗ trợ thông qua[Diễn đàn Aspose](https://forum.aspose.com/c/pdf/10).