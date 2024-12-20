---
title: Thay đổi hướng trang PDF
linktitle: Thay đổi hướng trang PDF
second_title: Tài liệu tham khảo Aspose.PDF cho API .NET
description: Khám phá cách dễ dàng điều chỉnh hướng trang của tệp PDF bằng Aspose.PDF cho .NET. Hướng dẫn từng bước này cung cấp hướng dẫn rõ ràng về cách tải, xoay và lưu tài liệu của bạn.
type: docs
weight: 10
url: /vi/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Giới thiệu

Bạn đã bao giờ gặp phải một tệp PDF có hướng trang hoàn toàn sai chưa? Cho dù đó là một tài liệu đã được quét không đúng cách hay chỉ đơn giản là một tài liệu cần một bố cục khác, việc điều chỉnh hướng có thể tạo ra sự khác biệt lớn. May mắn thay, Aspose.PDF cho .NET cung cấp một cách mạnh mẽ và thân thiện với người dùng để thao tác các tệp PDF, bao gồm cả việc thay đổi hướng của các trang. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước trong quy trình, cho dù bạn muốn chuyển từ chế độ dọc sang chế độ ngang hoặc ngược lại.

## Điều kiện tiên quyết

Trước khi đi sâu vào chi tiết, hãy đảm bảo bạn đã chuẩn bị những điều sau:

-  Aspose.PDF cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.PDF. Nếu bạn chưa thực hiện việc này, bạn có thể[tải xuống ở đây](https://releases.aspose.com/pdf/net/).
- Môi trường phát triển .NET: Bạn có thể sử dụng Visual Studio, JetBrains Rider hoặc bất kỳ IDE nào khác mà bạn thích để phát triển .NET.
- Kiến thức cơ bản về C#: Sự quen thuộc với C# sẽ giúp bạn theo dõi dễ dàng hơn.
- Tệp PDF: Chuẩn bị tệp PDF mẫu để thử nghiệm. Bạn có thể tạo một tệp hoặc tải xuống mẫu trực tuyến.

 Nếu bạn mới bắt đầu, hãy cân nhắc dùng thử Aspose.PDF với[giấy phép tạm thời miễn phí](https://purchase.aspose.com/temporary-license/) trước khi quyết định[mua phiên bản đầy đủ](https://purchase.aspose.com/buy).

## Nhập không gian tên

Để thao tác các trang PDF, trước tiên bạn cần nhập các không gian tên cần thiết vào dự án C# của mình. Thêm các dòng sau vào đầu tệp mã của bạn:

```csharp
using System.IO;
using Aspose.Pdf;
```

Bây giờ mọi thứ đã được thiết lập xong, chúng ta hãy bắt đầu nhé!

## Bước 1: Tải Tài liệu PDF

 Bước đầu tiên là tải tệp PDF bạn muốn sửa đổi. Sử dụng`Document` lớp từ không gian tên Aspose.PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Hãy chắc chắn thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến tệp PDF của bạn.

## Bước 2: Lặp qua từng trang

Tiếp theo, chúng ta sẽ lặp qua từng trang trong tài liệu PDF. Điều này cho phép chúng ta áp dụng thay đổi hướng cho tất cả các trang:

```csharp
foreach (Page page in doc.Pages)
{
    // Thao tác từng trang
}
```

## Bước 3: Truy cập MediaBox của Trang

 Mỗi trang PDF có một`MediaBox` xác định ranh giới của nó. Chúng ta cần truy cập vào đây để kiểm tra hướng hiện tại và thực hiện điều chỉnh:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 Các`MediaBox` cung cấp kích thước của trang, bao gồm chiều rộng và chiều cao.

## Bước 4: Hoán đổi chiều rộng và chiều cao

Để thay đổi hướng trang, chúng ta sẽ hoán đổi giá trị chiều rộng và chiều cao. Điều chỉnh này sẽ thay đổi kích thước của trang:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Ở đây, chúng tôi tính toán các kích thước mới và định vị lại góc dưới bên trái (`LLY`) theo đó.

## Bước 5: Cập nhật MediaBox và CropBox

 Bây giờ chúng ta đã có các kích thước mới, chúng ta sẽ áp dụng những thay đổi này vào`MediaBox` Và`CropBox` để đảm bảo trang hiển thị chính xác:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Bước 6: Xoay trang

Để hoàn tất việc thay đổi hướng, chúng ta sẽ xoay trang. Điều này rất đơn giản với Aspose.PDF:

```csharp
page.Rotate = Rotation.on90; // Xoay 90 độ
```

Dòng này có tác dụng lật trang theo hướng mong muốn.

## Bước 7: Lưu PDF đầu ra

Sau khi sửa đổi hướng của tất cả các trang, hãy lưu tài liệu đã cập nhật vào một tệp mới:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Hãy đảm bảo cung cấp tên tệp mới để tránh ghi đè lên tài liệu gốc.

## Phần kết luận

Và bạn đã có nó! Thay đổi hướng trang của tệp PDF bằng Aspose.PDF cho .NET là một quá trình đơn giản. Bằng cách tải tài liệu, lặp qua các trang, cập nhật MediaBox và lưu tệp, bạn có thể dễ dàng điều chỉnh bố cục để đáp ứng nhu cầu của mình. Cho dù bạn đang sửa tài liệu được quét kém hay định dạng các trang để trình bày, hướng dẫn này sẽ giúp bạn hoàn thành công việc một cách hiệu quả.

## Câu hỏi thường gặp

### Tôi có thể xoay các trang cụ thể thay vì tất cả các trang trong PDF không?  
Có, bạn có thể sửa đổi vòng lặp để nhắm mục tiêu vào các trang cụ thể theo chỉ mục của chúng thay vì lặp qua tất cả các trang.

### Cái gì là`MediaBox`?  
 Các`MediaBox` xác định kích thước và hình dạng của trang trong tệp PDF, xác định vị trí đặt nội dung.

### Aspose.PDF cho .NET có hoạt động với các định dạng tệp khác không?  
Có, Aspose.PDF có thể xử lý nhiều định dạng tệp khác nhau, bao gồm HTML, XML, XPS, v.v.

### Có phiên bản miễn phí của Aspose.PDF dành cho .NET không?  
 Vâng, bạn có thể bắt đầu với một[dùng thử miễn phí](https://releases.aspose.com/) hoặc yêu cầu một[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).

### Tôi có thể hoàn tác những thay đổi sau khi đã lưu không?  
Sau khi bạn lưu tài liệu, các thay đổi sẽ có hiệu lực vĩnh viễn. Bạn nên làm việc trên một bản sao hoặc giữ bản sao lưu của tệp gốc.