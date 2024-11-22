---
title: Thêm Java Script vào tệp PDF
linktitle: Thêm tệp PDF Java Script
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Tài liệu này cung cấp hướng dẫn toàn diện về cách thêm các thành phần tương tác như cảnh báo bật lên hoặc chức năng tự động in vào tài liệu PDF bằng Aspose.PDF cho .NET.
type: docs
weight: 10
url: /vi/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## Giới thiệu
Tài liệu này cung cấp hướng dẫn toàn diện về cách thêm các thành phần tương tác như cảnh báo bật lên hoặc chức năng tự động in vào tài liệu PDF bằng Aspose.PDF cho .NET. Bằng cách tận dụng các khả năng của thư viện này, bạn có thể tạo các tệp PDF động và hấp dẫn đáp ứng nhiều nhu cầu khác nhau của người dùng.

## Điều kiện tiên quyết
 Trước khi tiếp tục, hãy đảm bảo rằng bạn đã tải xuống phiên bản mới nhất của Aspose.PDF cho .NET từ[Aspose phát hành](https://phát hành.aspose.com/pdf/net/) hoặc nhận bản dùng thử miễn phí thông qua trang web của họ:[releases.aspose.com](http://releases.aspose.com).

Bạn cũng nên có hiểu biết cơ bản về C# và quen thuộc với môi trường phát triển mà bạn đang sử dụng. Ngoài ra, nếu bạn cần tránh những hạn chế trong quá trình phát triển, hãy cân nhắc mua giấy phép tạm thời từ Aspose.

## Nhập các gói cần thiết
Để bắt đầu viết mã, hãy nhập các không gian tên cần thiết từ thư viện Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Bước 1: Tải PDF hiện có
Tải một tài liệu PDF hiện có mà bạn muốn thêm các thành phần tương tác:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến tệp PDF của bạn.

## Bước 2: Thêm JavaScript ở cấp độ tài liệu

 Để áp dụng một tập lệnh kích hoạt khi tài liệu mở ra, hãy khởi tạo một`JavascriptAction` sự vật:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Bước 3: Thêm JavaScript ở cấp độ trang

 Để kích hoạt các hành động cụ thể dựa trên việc mở hoặc đóng trang, hãy tạo một`JavascriptAction` đối tượng cho mỗi trang:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Bước 4: Lưu tài liệu PDF

Để lưu tài liệu PDF đã sửa đổi, hãy chỉ định đường dẫn tệp đầu ra:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Phần kết luận
Bằng cách làm theo hướng dẫn này và sử dụng Aspose.PDF cho .NET, bạn có thể cải thiện hiệu quả các tệp PDF của mình bằng các thành phần tương tác. Thư viện này cung cấp giải pháp toàn diện để tạo các tài liệu động và hấp dẫn đáp ứng nhiều nhu cầu khác nhau của người dùng.

## Câu hỏi thường gặp

### Tôi có thể thêm nhiều hành động JavaScript vào các trang khác nhau trong một tệp PDF không?
Có, bạn có thể chỉ định các hành động JavaScript khác nhau cho từng trang hoặc toàn bộ tài liệu.

### Có thể xóa JavaScript khỏi PDF sau khi đã thêm vào không?
 Có, bạn có thể xóa hoặc sửa đổi các hành động JavaScript hiện có bằng cách xóa`Actions` thuộc tính của tài liệu hoặc trang.

### Tôi có thể sử dụng loại hàm JavaScript nào trong PDF?
Bạn có thể sử dụng bất kỳ JavaScript nào được công cụ JavaScript của Adobe Acrobat hỗ trợ, chẳng hạn như in, cảnh báo và thao tác biểu mẫu.

### JavaScript có hoạt động trên tất cả các trình xem PDF không?
Hầu hết các hành động JavaScript sẽ hoạt động trong trình xem PDF hỗ trợ PDF tương tác, như Adobe Acrobat. Tuy nhiên, một số trình đọc PDF cơ bản có thể không hỗ trợ JavaScript.