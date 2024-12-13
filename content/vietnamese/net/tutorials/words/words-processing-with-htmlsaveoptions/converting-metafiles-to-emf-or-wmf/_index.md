---
title: Chuyển đổi Metafile sang Emf hoặc Wmf
linktitle: Chuyển đổi Metafile sang Emf hoặc Wmf
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách chuyển đổi liền mạch hình ảnh SVG sang định dạng EMF hoặc WMF trong tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn từng bước với các ví dụ mã để có kết quả chính xác và tương thích.
type: docs
weight: 10
url: /vi/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-emf-or-wmf/
---
## Giới thiệu

Quản lý và chuyển đổi định dạng hình ảnh hiệu quả là một phần quan trọng trong việc tạo tài liệu Word chuyên nghiệp. Trong hướng dẫn này, chúng tôi sẽ đi sâu vào việc sử dụng Aspose.Words cho .NET để chuyển đổi hình ảnh SVG sang định dạng EMF (Enhanced Metafile) hoặc WMF (Windows Metafile) để tích hợp liền mạch. Hướng dẫn này cung cấp hướng dẫn từng bước rõ ràng để giúp các nhà phát triển triển khai chuyển đổi dễ dàng.

## Điều kiện tiên quyết để chuyển đổi SVG sang EMF hoặc WMF

Để đảm bảo trải nghiệm phát triển diễn ra suôn sẻ, hãy xác nhận các điều kiện tiên quyết sau được đáp ứng:

-  Aspose.Words cho .NET: Tải phiên bản mới nhất từ[Trang phát hành Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: Kiểm tra cài đặt .NET Framework (hoặc .NET Core/5/6 tùy thuộc vào môi trường của bạn).
- Môi trường phát triển: Visual Studio được khuyến khích sử dụng vì các tính năng mạnh mẽ của nó.
- Thành thạo C#: Có kiến thức cơ bản về lập trình C# là điều cần thiết.

## Nhập không gian tên bắt buộc

Trong dự án của bạn, hãy nhập các không gian tên cần thiết để truy cập các chức năng của Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Xác định thư mục tài liệu

Thiết lập đường dẫn thư mục nơi lưu trữ tài liệu Word của bạn. Điều này rất cần thiết để quản lý các tệp đầu ra hiệu quả.

```csharp
string dataDir = @"C:\MyDocuments\";
```

 Thay thế`@"C:\MyDocuments\"` với con đường bạn mong muốn.

## Bước 2: Chuẩn bị chuỗi HTML chứa SVG

Soạn một chuỗi HTML nhúng nội dung SVG của bạn. Điều này cho phép Aspose.Words hiển thị và xử lý SVG.

```csharp
string htmlContent = 
    @"<html>
        <body>
            <svg xmlns='http://www.w3.org/2000/svg' width='300' height='100' viewBox='0 0 300 100'>
                <rect x='10' y='10' width='280' height='80' fill='blue' stroke='black' stroke-width='2'/>
                <text x='20' y='60' fill='white' font-size='20'>Aspose SVG Example</text>
            </svg>
        </body>
    </html>";
```

## Bước 3: Cấu hình Tùy chọn Tải HTML

 Để đảm bảo xử lý đúng cách chuyển đổi SVG, hãy cấu hình`HtmlLoadOptions` với`ConvertSvgToEmf`.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    ConvertSvgToEmf = true
};
```

## Bước 4: Tải HTML vào Tài liệu Word

 Sử dụng các tùy chọn tải được cấu hình để tạo`Document` đối tượng từ chuỗi HTML.

```csharp
using (MemoryStream htmlStream = new MemoryStream(Encoding.UTF8.GetBytes(htmlContent)))
{
    Document document = new Document(htmlStream, loadOptions);
}
```

## Bước 5: Cấu hình tùy chọn lưu cho EMF/WMF

 Tùy chỉnh các tùy chọn lưu để xác định định dạng tệp siêu dữ liệu mong muốn. Ở đây, chúng tôi chọn`HtmlMetafileFormat.Emf`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Emf
};
```

## Bước 6: Lưu tài liệu

Lưu tài liệu bằng các tùy chọn lưu đã chỉ định.

```csharp
document.Save(dataDir + "ConvertedDocument.emf", saveOptions);
```

Tệp kết quả sẽ chứa nội dung SVG được chuyển đổi sang định dạng EMF.

## Phần kết luận

Hướng dẫn này đã trình bày cách chuyển đổi hình ảnh SVG sang định dạng EMF hoặc WMF bằng Aspose.Words cho .NET. Bằng cách làm theo các bước này, bạn có thể nâng cao khả năng tương thích và độ trung thực trực quan của tài liệu Word. Cho dù bạn đang tự động hóa việc tạo tài liệu hay chuẩn bị báo cáo chất lượng cao, phương pháp này đảm bảo kết quả liền mạch.

## Câu hỏi thường gặp

### Tôi có thể sử dụng phương pháp này để xử lý hàng loạt nhiều SVG không?
Có, bạn có thể lặp qua nhiều tệp HTML chứa SVG, áp dụng cùng một quy trình trong một vòng lặp.

### Sự khác biệt giữa EMF và WMF là gì?
EMF là phiên bản nâng cao của WMF, hỗ trợ tốt hơn cho đồ họa phức tạp và kích thước dữ liệu lớn hơn.

### Aspose.Words có tương thích với .NET Core không?
Có, Aspose.Words for .NET hỗ trợ .NET Core và .NET 5/6, phù hợp với các ứng dụng đa nền tảng hiện đại.

### Tôi có thể giữ nguyên định dạng SVG gốc khi xuất ra không?
Không, phương pháp này chuyển đổi SVG sang EMF/WMF. Tuy nhiên, bạn có thể giữ nguyên SVG gốc bằng cách nhúng trực tiếp vào tài liệu mà không cần chuyển đổi.

### Tôi có thể tải xuống bản dùng thử miễn phí Aspose.Words ở đâu?
 Bạn có thể tải xuống bản dùng thử miễn phí từ[Trang phát hành Aspose](https://releases.aspose.com/).