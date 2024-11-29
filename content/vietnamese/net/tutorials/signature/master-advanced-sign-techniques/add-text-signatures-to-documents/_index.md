---
title: Thêm chữ ký văn bản vào tài liệu bằng GroupDocs.Signature
linktitle: Thêm chữ ký văn bản vào tài liệu
second_title: API GroupDocs.Signature .NET
description: Tìm hiểu cách ký tài liệu bằng văn bản bằng GroupDocs.Signature cho .NET. Hướng dẫn từng bước để thêm chữ ký văn bản theo chương trình.
type: docs
weight: 17
url: /vi/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Giới thiệu

Trong bối cảnh kỹ thuật số ngày nay, việc ký tài liệu điện tử đã trở nên thiết yếu để hợp lý hóa quy trình làm việc và tiết kiệm tài nguyên. GroupDocs.Signature cho .NET cung cấp giải pháp mạnh mẽ để thêm chữ ký văn bản theo chương trình vào nhiều định dạng tài liệu khác nhau. Hướng dẫn này sẽ hướng dẫn bạn các bước để ký tài liệu bằng văn bản bằng GroupDocs.Signature cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1.  GroupDocs.Signature cho .NET: Tải xuống và cài đặt thư viện từ[đây](https://releases.groupdocs.com/signature/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển .NET của bạn.
3. Tài liệu: Chuẩn bị tài liệu bạn muốn ký (ví dụ: PDF, Word).

## Nhập các không gian tên cần thiết

Bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án .NET của bạn:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Bước 1: Tải tài liệu

Bắt đầu bằng cách tải tài liệu bạn định ký:

```csharp
string filePath = "sample.pdf"; // Đường dẫn đến tài liệu của bạn
string fileName = Path.GetFileName(filePath);
```

## Bước 2: Xác định Đường dẫn Tệp Đầu ra

Tiếp theo, hãy thiết lập đường dẫn tệp đầu ra nơi tài liệu đã ký sẽ được lưu:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Bước 3: Tạo tùy chọn chữ ký

Cấu hình các tùy chọn cho chữ ký văn bản của bạn, bao gồm nội dung, vị trí, kích thước, màu sắc và kiểu phông chữ:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // Vị trí X
    Top = 200, // Vị trí Y
    Width = 100, // Chiều rộng của chữ ký
    Height = 30, // Chiều cao của chữ ký
    ForeColor = Color.Red, // Màu chữ
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Cài đặt phông chữ
};
```

## Bước 4: Ký vào tài liệu

Cuối cùng, sử dụng GroupDocs.Signature để áp dụng chữ ký văn bản và lưu tài liệu đã ký:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Ký vào tài liệu
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã trình bày cách lập trình thêm chữ ký văn bản vào tài liệu bằng GroupDocs.Signature cho .NET. Bằng cách làm theo các bước này, bạn có thể tăng cường tính bảo mật và tính xác thực của tài liệu một cách hiệu quả.

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh giao diện của chữ ký văn bản không?
Có, bạn có thể tùy chỉnh nhiều thuộc tính khác nhau như màu sắc, phông chữ, kích thước và vị trí của chữ ký văn bản để phù hợp với nhu cầu của bạn.

### GroupDocs.Signature có tương thích với nhiều định dạng tài liệu không?
Chắc chắn rồi! GroupDocs.Signature hỗ trợ nhiều định dạng, bao gồm PDF, Word, Excel, PowerPoint, v.v.

### Tôi có thể thêm nhiều chữ ký văn bản vào một tài liệu không?
Có, bạn có thể thêm nhiều chữ ký văn bản, mỗi chữ ký có tùy chọn tùy chỉnh riêng.

### GroupDocs.Signature có đảm bảo tính toàn vẹn của tài liệu sau khi ký không?
Có, thư viện sử dụng các thuật toán mã hóa mạnh mẽ để đảm bảo tính toàn vẹn của tài liệu và ngăn chặn việc giả mạo sau khi ký.

### Có phiên bản dùng thử để kiểm tra trước khi mua không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/) để khám phá các tính năng trước khi mua hàng.