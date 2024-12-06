---
title: Tạo và ký dòng chữ ký mới
linktitle: Tạo và ký dòng chữ ký mới
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thêm chữ ký số vào tài liệu Word của bạn một cách liền mạch bằng Aspose.Words cho .NET. Hướng dẫn toàn diện này bao gồm mọi thứ từ thiết lập môi trường của bạn và chèn dòng chữ ký đến lưu và xác minh tài liệu đã ký của bạn.
type: docs
weight: 10
url: /vi/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Giới thiệu

Bạn muốn thêm chữ ký số vào tài liệu Word? Với Aspose.Words for .NET, việc này dễ hơn bạn nghĩ! Hướng dẫn này sẽ hướng dẫn bạn các bước thiết lập môi trường, thêm dòng chữ ký và ký tài liệu kỹ thuật số. Hãy bắt đầu nào!

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có những điều sau:

1.  Aspose.Words cho .NET -[Tải xuống tại đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển .NET - Visual Studio là lý tưởng cho nhiệm vụ này.
3. Tài liệu cần ký - Bạn có thể tạo một tài liệu Word mới hoặc sử dụng một tài liệu hiện có.
4.  Tệp chứng chỉ - A`.pfx` tập tin này là cần thiết cho chữ ký số.
5. Hình ảnh dòng chữ ký (Tùy chọn) - Bạn có thể bao gồm tệp hình ảnh cho chữ ký.

## Nhập không gian tên bắt buộc

Để sử dụng các chức năng của Aspose.Words, bạn cần nhập các không gian tên sau:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Bước 1: Thiết lập thư mục tài liệu

Bắt đầu bằng cách xác định đường dẫn đến thư mục tài liệu của bạn. Đây sẽ là nơi bạn lưu và lấy tài liệu của mình.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Chỉ định đường dẫn thư mục tài liệu của bạn
```

## Bước 2: Tạo một tài liệu mới

Tiếp theo, hãy tạo một tài liệu Word mới. Tài liệu này sẽ đóng vai trò là khung cho dòng chữ ký của bạn.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 3: Chèn dòng chữ ký

 Bây giờ, sử dụng`DocumentBuilder` lớp để chèn dòng chữ ký vào tài liệu của bạn:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Bước 4: Lưu tài liệu

Sau khi chèn dòng chữ ký, hãy lưu tài liệu. Đây là bước quan trọng trước khi ký.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Bước 5: Cấu hình tùy chọn ký

Thiết lập các tùy chọn cho quy trình ký. Bao gồm chỉ định ID dòng chữ ký và hình ảnh tùy chọn để hiển thị cùng với chữ ký.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Đường dẫn đến hình ảnh của bạn
};
```

## Bước 6: Tải chứng chỉ

Tải tệp chứng chỉ cần thiết để ký tài liệu:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Điều chỉnh tên tập tin và mật khẩu
```

## Bước 7: Ký tài liệu

 Cuối cùng, ký tài liệu bằng cách sử dụng`DigitalSignatureUtil` lớp. Lưu tài liệu đã ký với tên mới để tham khảo sau này.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Phần kết luận

Xin chúc mừng! Bạn đã tạo thành công một tài liệu Word, thêm dòng chữ ký và ký số bằng Aspose.Words cho .NET. Công cụ mạnh mẽ này đơn giản hóa việc tự động hóa tài liệu, đảm bảo hợp đồng và tài liệu chính thức của bạn được ký và xác thực an toàn.

## Câu hỏi thường gặp

### Tôi có thể sử dụng định dạng hình ảnh khác cho dòng chữ ký không?

Có, bạn có thể sử dụng nhiều định dạng hình ảnh khác nhau, bao gồm PNG, JPG và BMP.

###  Có cần thiết phải sử dụng một`.pfx` file for the certificate?

 Vâng, một`.pfx` tệp là định dạng chuẩn để lưu trữ chứng chỉ và khóa riêng cho chữ ký số.

### Tôi có thể thêm nhiều dòng chữ ký vào một tài liệu không?

Hoàn toàn có thể! Bạn có thể chèn nhiều dòng chữ ký bằng cách lặp lại bước chèn khi cần.

### Nếu tôi không có chứng chỉ số thì sao?

Bạn sẽ cần phải xin chứng chỉ số từ một cơ quan cấp chứng chỉ đáng tin cậy hoặc tạo chứng chỉ bằng các công cụ như OpenSSL.

### Làm thế nào để xác minh chữ ký số trong tài liệu?

Bạn có thể xác minh chữ ký số bằng cách mở tài liệu đã ký trong Word và kiểm tra thông tin chi tiết về chữ ký để xác nhận tính xác thực và toàn vẹn của chữ ký.