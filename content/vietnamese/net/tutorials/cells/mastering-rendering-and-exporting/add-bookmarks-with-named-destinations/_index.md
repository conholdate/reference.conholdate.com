---
title: Thêm dấu trang có đích đến được đặt tên vào tệp PDF từ tệp Excel
linktitle: Thêm dấu trang có đích đến được đặt tên vào tệp PDF từ tệp Excel
second_title: API xử lý Excel Aspose.Cells .NET
description: Tìm hiểu cách dễ dàng tạo PDF tương tác từ các tệp Excel bằng Aspose.Cells cho .NET. Hướng dẫn này bao gồm cách thêm dấu trang có đích đến được đặt tên để tăng cường điều hướng PDF.
type: docs
weight: 10
url: /vi/net/tutorials/cells/mastering-rendering-and-exporting/add-bookmarks-with-named-destinations/
---
## Giới thiệu

Việc điều hướng các tệp PDF lớn thường giống như việc mò kim đáy bể, đặc biệt là khi chúng được tạo từ các bảng tính Excel mở rộng. Dấu trang trong tài liệu PDF cung cấp một cách liền mạch để chuyển đổi giữa các phần có liên quan của tệp, nâng cao trải nghiệm của người dùng. Hướng dẫn chi tiết này sẽ hướng dẫn bạn quy trình thêm dấu trang có đích đến được đặt tên vào tệp PDF được tạo từ tệp Excel bằng Aspose.Cells cho .NET.

## Điều kiện tiên quyết để làm việc với Aspose.Cells cho .NET

Trước khi đi sâu vào mã, điều quan trọng là phải đảm bảo rằng bạn đã thiết lập tất cả các công cụ để triển khai thành công. Sau đây là các điều kiện tiên quyết:

1. Visual Studio: IDE được đề xuất cho phát triển .NET. Đảm bảo rằng nó được cài đặt và cấu hình đúng trên hệ thống của bạn.
2.  Aspose.Cells cho .NET: Thư viện cốt lõi cần thiết để thao tác các tệp Excel theo chương trình. Bạn có thể[tải xuống ở đây](https://releases.aspose.com/cells/net/) . Nếu bạn mới sử dụng Aspose, bạn có thể bắt đầu bằng[dùng thử miễn phí](https://releases.aspose.com/).
3. .NET Framework: Đảm bảo bạn đang sử dụng phiên bản tương thích của .NET Framework. Aspose.Cells hỗ trợ nhiều phiên bản.
4. Kiến thức cơ bản về C#: Hiểu biết cơ bản về C# sẽ hữu ích khi theo dõi mã.

Với các thành phần này, bạn đã sẵn sàng để bắt đầu tạo tài liệu PDF có dấu trang!

## Thiết lập dự án của bạn

Khi môi trường phát triển của bạn đã sẵn sàng, bạn có thể tiến hành tạo một dự án C# mới trong Visual Studio. Để làm việc với các chức năng của Aspose.Cells, bạn sẽ cần phải nhập các không gian tên cần thiết.

## Nhập không gian tên bắt buộc

Ở đầu tệp C# của bạn, hãy thêm nội dung sau`using` các câu lệnh để đảm bảo rằng dự án của bạn có thể truy cập Aspose.Cells cho .NET:

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

Các không gian tên này cung cấp quyền truy cập vào các lớp thiết yếu giúp bạn thao tác dữ liệu Excel và chuyển đổi nó thành PDF.

## Bước 1: Thiết lập thư mục cho các tập tin đầu vào và đầu ra

Bước đầu tiên là xác định thư mục tệp đầu vào và đầu ra. Điều này đảm bảo tệp Excel nguồn và tệp PDF kết quả được định vị đúng.

```csharp
string sourceDir = "Your Document Directory";  // Đường dẫn đến tệp Excel của bạn
string outputDir = "Your Document Directory"; // Đường dẫn nơi tệp PDF đầu ra sẽ được lưu
```

Điều này tương tự như việc sắp xếp không gian làm việc trước khi bắt đầu một dự án.

## Bước 2: Tải sổ làm việc Excel

 Bước tiếp theo là tải tệp Excel nguồn của bạn. Aspose.Cells cho phép bạn dễ dàng tải tệp Excel vào`Workbook` đối tượng, cung cấp quyền truy cập vào tất cả các trang tính, ô và nội dung của đối tượng đó.

```csharp
Workbook wb = new Workbook(sourceDir + "sampleExcelFile.xlsx");
```

Thao tác này sẽ mở sổ làm việc và chuẩn bị cho thao tác. Bây giờ bạn có thể bắt đầu trích xuất dữ liệu và định dạng cho PDF.

## Bước 3: Truy cập vào Bảng tính

Bây giờ khi sổ làm việc đã được tải, đã đến lúc truy cập vào trang tính nơi chứa các ô liên quan cho dấu trang. Trong ví dụ này, chúng ta sẽ làm việc với trang tính đầu tiên:

```csharp
Worksheet ws = wb.Worksheets[0]; // Truy cập vào bảng tính đầu tiên
```

Bước này thiết lập canvas cho các dấu trang của bạn. Mỗi ô mà bạn sẽ tham chiếu cho một dấu trang sẽ đến từ bảng tính này.

## Bước 4: Tạo dấu trang với các đích đến được đặt tên

Tại thời điểm này, chúng ta có thể bắt đầu tạo dấu trang. Dấu trang về cơ bản là các liên kết cung cấp quyền truy cập nhanh đến các khu vực cụ thể trong tài liệu của bạn. Trong ví dụ này, chúng ta sẽ tạo dấu trang cho ô "C5".

### Tạo một dấu trang cho một ô đơn lẻ

 Để tạo dấu trang, trước tiên bạn phải truy cập vào ô bạn muốn liên kết đến. Sau đó, bạn sẽ tạo một`PdfBookmarkEntry` và liên kết nó với vị trí của tế bào.

```csharp
Cell cell = ws.Cells["C5"];
PdfBookmarkEntry bookmarkEntry = new PdfBookmarkEntry();
bookmarkEntry.Text = "Bookmark for C5"; // Văn bản cho dấu trang
bookmarkEntry.Destination = cell;  // Liên kết dấu trang với ô
bookmarkEntry.DestinationName = "AsposeCells--" + cell.Name; // Tên điểm đến duy nhất
```

Hãy nghĩ về điều này như việc đánh dấu một điểm trong tài liệu mà bạn có thể quay lại chỉ bằng một cú nhấp chuột. Bạn có thể gán bất kỳ văn bản nào vào dấu trang (như "Dấu trang cho C5") và liên kết nó với một ô cụ thể.

### Thêm Dấu trang phụ để Điều hướng Nâng cao

Bạn có thể nâng cao trải nghiệm người dùng bằng cách thêm các dấu trang phụ phân nhánh từ dấu trang chính. Các dấu trang phụ này có thể trỏ đến các khu vực khác nhau trong cùng một bảng tính hoặc đến các trang tính khác.

```csharp
cell = ws.Cells["G56"];
PdfBookmarkEntry subbookmarkEntry1 = new PdfBookmarkEntry();
subbookmarkEntry1.Text = "Sub-Bookmark 1"; // Văn bản cho dấu trang phụ đầu tiên
subbookmarkEntry1.Destination = cell;
subbookmarkEntry1.DestinationName = "AsposeCells--" + cell.Name;

cell = ws.Cells["L4"];
PdfBookmarkEntry subbookmarkEntry2 = new PdfBookmarkEntry();
subbookmarkEntry2.Text = "Sub-Bookmark 2"; // Văn bản cho dấu trang phụ thứ hai
subbookmarkEntry2.Destination = cell;
subbookmarkEntry2.DestinationName = "AsposeCells--" + cell.Name;
```

Các dấu trang phụ này đóng vai trò như các hướng dẫn bổ sung để điều hướng qua tài liệu, giống như các chương trong một cuốn sách.

### Nhóm các dấu trang phụ dưới một dấu trang chính

Để tạo cấu trúc phân cấp, bạn có thể thêm các dấu trang phụ này vào dấu trang chính. Điều này giúp người dùng dễ dàng điều hướng đến các phần khác nhau.

```csharp
ArrayList list = new ArrayList();
list.Add(subbookmarkEntry1);
list.Add(subbookmarkEntry2);
bookmarkEntry.SubEntry = list; // Thêm dấu trang phụ vào dấu trang chính
```

Điều này tạo ra một cấu trúc giống như cây, trong đó mỗi dấu trang có thể có nhiều dấu trang con.

## Bước 5: Lưu PDF bằng Bookmarks

### Thiết lập tùy chọn lưu PDF

 Trước khi lưu tài liệu dưới dạng PDF, chúng ta cần chỉ định các tùy chọn lưu và đảm bảo rằng các dấu trang được bao gồm. Chúng ta sẽ sử dụng`PdfSaveOptions` vì mục đích này.

```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = bookmarkEntry;  // Gán dấu trang cho PDF
```

Điều này yêu cầu Aspose.Cells tạo một tệp PDF bao gồm các dấu trang mà chúng ta vừa tạo.

### Lưu tài liệu

Bây giờ đã thiết lập xong dấu trang, chúng ta có thể lưu bảng tính dưới dạng PDF.

```csharp
wb.Save(outputDir + "outputWithBookmarks.pdf", opts);
```

Tính năng này sẽ tạo ra tệp PDF cuối cùng với các dấu trang có thể nhấp vào, cho phép người dùng nhanh chóng chuyển đến các phần cụ thể của tài liệu.

## Phần kết luận

Bằng cách làm theo các bước đơn giản này, bạn đã tạo thành công một tệp PDF có dấu trang và đích đến được đặt tên từ tệp Excel bằng Aspose.Cells cho .NET. Khả năng thêm dấu trang không chỉ nâng cao trải nghiệm của người dùng mà còn giúp điều hướng trong các tài liệu lớn hiệu quả hơn nhiều. Cho dù bạn đang làm việc trên báo cáo, hướng dẫn hay bản trình bày, việc đánh dấu các phần chính sẽ giúp người đọc tận dụng tối đa tài liệu của bạn.

## Câu hỏi thường gặp

### Aspose.Cells dành cho .NET là gì?
Aspose.Cells for .NET là một API mạnh mẽ để làm việc với các tệp Excel, cho phép bạn tạo, chỉnh sửa và chuyển đổi các tài liệu Excel theo chương trình. Bạn có thể dễ dàng thao tác dữ liệu, biểu đồ và định dạng bằng công cụ này.

### Làm thế nào tôi có thể nhận được bản dùng thử miễn phí Aspose.Cells cho .NET?
 Bạn có thể tải xuống phiên bản dùng thử miễn phí của Aspose.Cells cho .NET từ[đây](https://releases.aspose.com/).

### Aspose.Cells có thể hoạt động với những định dạng tệp nào?
Aspose.Cells hỗ trợ nhiều định dạng tệp, bao gồm XLSX, XLS, CSV, PDF và nhiều định dạng khác.

### Tôi có thể tự động hóa quá trình tạo dấu trang trong PDF không?
Có! Quá trình này có thể được tự động hóa hoàn toàn bằng cách tích hợp Aspose.Cells vào các ứng dụng của bạn, cho phép bạn tạo PDF dựa trên Excel một cách linh hoạt với các dấu trang như một phần của quy trình làm việc.

### Tôi có thể nhận hỗ trợ cho Aspose.Cells cho .NET ở đâu?
 Bạn có thể ghé thăm[Diễn đàn Aspose](https://forum.aspose.com/c/cells/9) để đặt câu hỏi hoặc báo cáo vấn đề.