---
title: Đọc Thời gian tạo của Bình luận có luồng với Aspose.Cells
linktitle: Đọc Thời gian tạo của Bình luận có luồng với Aspose.Cells
second_title: API xử lý Excel Aspose.Cells .NET
description: Tìm hiểu cách dễ dàng đọc thời gian tạo của các chú thích có luồng trong bảng tính Excel bằng Aspose.Cells cho .NET. Làm theo hướng dẫn chi tiết của chúng tôi với hướng dẫn từng bước.
type: docs
weight: 21
url: /vi/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## Giới thiệu

Khi làm việc với các tệp Excel, việc quản lý các bình luận có thể rất cần thiết cho việc cộng tác và theo dõi phản hồi. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình đọc thời gian tạo các bình luận theo luồng trong bảng tính Excel bằng Aspose.Cells for .NET. Công cụ mạnh mẽ này cung cấp một cách hiệu quả để tương tác với các tệp Excel, cho phép các nhà phát triển trích xuất thông tin chi tiết từ các bình luận, đặc biệt hữu ích để theo dõi thời gian phản hồi trong các tình huống cộng tác.

## Điều kiện tiên quyết

Trước khi bắt đầu, điều quan trọng là phải đảm bảo rằng môi trường phát triển của bạn được thiết lập đúng cách để sử dụng Aspose.Cells cho .NET. Sau đây là những gì bạn cần:

1.  Aspose.Cells cho .NET: Bạn sẽ cần cài đặt thư viện Aspose.Cells. Bạn có thể tải phiên bản mới nhất từ[Trang web Aspose](https://releases.aspose.com/cells/net/).
2. IDE: Visual Studio (hoặc bất kỳ IDE .NET nào bạn chọn) để viết và thực thi mã của bạn.
3. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp bạn dễ dàng theo dõi các ví dụ hơn.
4.  Tệp Excel: Đối với hướng dẫn này, chúng tôi sẽ sử dụng tệp Excel có tên`ThreadedCommentsSample.xlsx`, bao gồm một số bình luận có chủ đề. Đảm bảo tệp của bạn có chứa các bình luận để theo dõi.

## Nhập các gói cần thiết

Để bắt đầu, bạn cần nhập các không gian tên cần thiết để làm việc với Aspose.Cells. Mở dự án C# của bạn và thêm các chỉ thị using sau vào đầu tệp mã của bạn:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

 Các`Aspose.Cells` không gian tên cho phép bạn truy cập tất cả các lớp và phương thức cần thiết để thao tác các tệp Excel, trong khi`System` là cần thiết cho chức năng chung như xử lý đầu ra và ngoại lệ.

## Bước 1: Chỉ định thư mục của tệp Excel

Bước đầu tiên là xác định đường dẫn nơi lưu trữ tệp Excel của bạn. Đường dẫn này sẽ được sử dụng để định vị tệp theo chương trình.

```csharp
// Xác định thư mục của tệp Excel
string sourceDir = "Your Document Directory";
```

 Thay thế`"C:\\YourDirectory\\"`với đường dẫn thực tế đến tệp của bạn. Điều này đảm bảo rằng chương trình biết nơi tìm`ThreadedCommentsSample.xlsx`.

## Bước 2: Tải Workbook

 Với thư mục được thiết lập, bây giờ chúng ta có thể tải sổ làm việc Excel. Điều này được thực hiện bằng cách tạo một`Workbook` đối tượng và truyền đường dẫn tệp tới đối tượng đó.

```csharp
// Tải bảng tính Excel
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

Nếu không tìm thấy tệp ở đường dẫn đã chỉ định, một ngoại lệ sẽ được đưa ra, do đó hãy đảm bảo đường dẫn tệp là chính xác trước khi tiếp tục.

## Bước 3: Truy cập vào bảng tính mong muốn

Sau khi sổ làm việc được tải, bạn cần truy cập vào trang tính chứa các chú thích theo luồng. Trong ví dụ này, chúng ta sẽ lấy trang tính đầu tiên của sổ làm việc.

```csharp
// Truy cập trang tính đầu tiên trong sổ làm việc
Worksheet worksheet = workbook.Worksheets[0];
```

 Nếu bình luận của bạn nằm trong một bảng tính khác, chỉ cần sửa đổi chỉ mục cho phù hợp. Ví dụ, sử dụng`Worksheets[1]` cho bài tập thứ hai, v.v.

## Bước 4: Lấy lại các bình luận có chủ đề

Để lấy các bình luận theo luồng, bạn sẽ cần chỉ định ô chứa các bình luận. Trong trường hợp này, chúng tôi tập trung vào ô`A1` . Phương pháp`GetThreadedComments` được sử dụng để lấy tất cả các bình luận liên quan đến một ô cụ thể.

```csharp
// Nhận các bình luận theo chủ đề từ ô A1
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

Điều này sẽ trả về một tập hợp các chú thích theo luồng cho ô A1. Nếu không có chú thích nào tồn tại trong ô được chỉ định, tập hợp sẽ trống.

## Bước 5: Lặp lại qua các bình luận và trích xuất thời gian đã tạo

 Với các bình luận theo luồng được lấy ra, bước tiếp theo là lặp lại qua bộ sưu tập và trích xuất các chi tiết có liên quan, bao gồm thời gian tạo cho mỗi bình luận. Chúng ta có thể dễ dàng thực hiện điều này bằng cách lặp qua`ThreadedCommentCollection`.

```csharp
// Lặp qua từng bình luận có chủ đề và hiển thị thông tin chi tiết
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

 Mã này sẽ xuất ra nội dung bình luận, tên tác giả và thời gian bình luận được tạo.`CreatedTime` thuộc tính trả về dấu thời gian khi bình luận được tạo ban đầu.

## Bước 6: Hiển thị tin nhắn xác nhận

Sau khi đọc thành công các bình luận theo luồng và hiển thị thông tin, bạn nên đưa thông báo xác nhận vào mã của mình. Điều này giúp xác nhận rằng quy trình đã được thực hiện đúng.

```csharp
// Tin nhắn xác nhận
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

Thông báo này sẽ được in ra bảng điều khiển sau khi quá trình thực thi mã hoàn tất, xác nhận rằng quy trình chạy mà không có lỗi.

## Phần kết luận

Bây giờ bạn đã học cách dễ dàng đọc thời gian tạo ra các bình luận theo luồng trong bảng tính Excel bằng Aspose.Cells cho .NET. Chức năng này vô cùng hữu ích để theo dõi các bình luận và phản hồi trong môi trường cộng tác, cung cấp các dấu thời gian cần thiết cho các quy trình xem xét tài liệu. Bằng cách làm theo hướng dẫn này, bạn có thể trích xuất và sử dụng hiệu quả dữ liệu bình luận trong các ứng dụng .NET của mình, nâng cao quy trình làm việc và cải thiện sự cộng tác với các thành viên trong nhóm.

## Câu hỏi thường gặp

### Aspose.Cells dành cho .NET là gì?

Aspose.Cells for .NET là một thư viện toàn diện cho phép các nhà phát triển tạo, thao tác và quản lý các tệp Excel trong các ứng dụng .NET. Nó cung cấp các công cụ mạnh mẽ để đọc, viết và sửa đổi các tệp Excel theo chương trình.

### Làm thế nào tôi có thể tải xuống Aspose.Cells cho .NET?

 Bạn có thể tải xuống phiên bản mới nhất của Aspose.Cells cho .NET từ[Trang web Aspose](https://releases.aspose.com/cells/net/).

### Có bản dùng thử miễn phí không?

 Có, Aspose cung cấp bản dùng thử miễn phí cho Aspose.Cells dành cho .NET. Bạn có thể tải xuống phiên bản dùng thử từ[trang dùng thử miễn phí](https://releases.aspose.com/).

### Tôi có thể truy cập vào bình luận từ các ô khác không?

 Có, bạn có thể truy cập các chú thích theo luồng từ bất kỳ ô nào trong bảng tính bằng cách sửa đổi tham chiếu ô trong`GetThreadedComments` phương pháp. Chỉ cần thay đổi`"A1"` đến ô tham chiếu mong muốn.

### Tôi có thể nhận hỗ trợ cho Aspose.Cells ở đâu?

 Nếu bạn cần hỗ trợ hoặc có thắc mắc, hãy truy cập[Diễn đàn Aspose](https://forum.aspose.com/c/cells/9), nơi bạn có thể tìm thấy câu trả lời hoặc yêu cầu trợ giúp từ cộng đồng.