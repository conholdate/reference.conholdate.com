---
title: Tạo Dòng Chữ Ký Số Mới Và Thiết Lập ID Nhà Cung Cấp
linktitle: Tạo Dòng Chữ Ký Số Mới Và Thiết Lập ID Nhà Cung Cấp
second_title: API xử lý tài liệu Aspose.Words
description: Khám phá cách lập trình thêm dòng chữ ký vào tài liệu Word của bạn bằng Aspose.Words cho .NET. Hướng dẫn toàn diện này bao gồm mọi thứ từ thiết lập môi trường phát triển của bạn đến chèn dòng chữ ký và ký tài liệu một cách an toàn.
type: docs
weight: 10
url: /vi/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Giới thiệu

Xin chào, những người đam mê công nghệ! Bạn đã bao giờ muốn tự động hóa việc đưa các dòng chữ ký vào tài liệu Word của mình chưa? Hôm nay, chúng ta sẽ tìm hiểu cách thực hiện điều này bằng Aspose.Words cho .NET. Hướng dẫn từng bước này sẽ hướng dẫn bạn cách tạo dòng chữ ký và thiết lập ID nhà cung cấp, giúp các tác vụ xử lý tài liệu của bạn hiệu quả và hợp lý hơn.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã thiết lập mọi thứ:

1.  Aspose.Words cho .NET: Nếu bạn chưa cài đặt, hãy tải xuống[đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Sử dụng Visual Studio hoặc bất kỳ thiết lập phát triển C# nào.
3. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy của mình.
4. Chứng chỉ PFX: Bạn sẽ cần chứng chỉ PFX để ký tài liệu, có thể lấy từ một cơ quan cấp chứng chỉ đáng tin cậy.

## Nhập các không gian tên cần thiết

Để bắt đầu, hãy nhập các không gian tên cần thiết vào dự án C# của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Bây giờ, chúng ta hãy đi sâu vào chi tiết về cách tạo dòng chữ ký mới và thiết lập ID nhà cung cấp.

## Bước 1: Tạo một tài liệu mới

Đầu tiên, chúng ta cần tạo một tài liệu Word mới, tài liệu này sẽ đóng vai trò là khung cho dòng chữ ký của chúng ta:

```csharp
// Chỉ định đường dẫn đến thư mục tài liệu của bạn.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ở đây, chúng ta khởi tạo một cái mới`Document` và một`DocumentBuilder`, cho phép chúng ta thêm các phần tử một cách dễ dàng.

## Bước 2: Xác định các tùy chọn dòng chữ ký

Tiếp theo, chúng ta sẽ xác định các tùy chọn cho dòng chữ ký, bao gồm tên, chức danh, email và các thông tin chi tiết liên quan khác của người ký:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Các tùy chọn này giúp cá nhân hóa dòng chữ ký, làm cho nó rõ ràng và chuyên nghiệp.

## Bước 3: Chèn Dòng chữ ký

Sau khi đã chuẩn bị xong các tùy chọn, chúng ta có thể chèn dòng chữ ký vào tài liệu:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Các`InsertSignatureLine` phương pháp này thêm dòng chữ ký và chúng tôi gán cho nó một ID nhà cung cấp duy nhất.

## Bước 4: Lưu tài liệu

Sau khi chèn dòng chữ ký, chúng ta hãy lưu tài liệu:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Thao tác này sẽ lưu tài liệu của bạn với dòng chữ ký mới được thêm vào.

## Bước 5: Thiết lập tùy chọn ký tên

Bây giờ, chúng ta sẽ cấu hình các tùy chọn ký, bao gồm ID dòng chữ ký, ID nhà cung cấp, bình luận và thời gian ký:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Những thiết lập này đảm bảo rằng tài liệu được ký với thông tin chính xác.

## Bước 6: Tạo chủ sở hữu chứng chỉ

Để ký tài liệu, chúng ta cần tạo người giữ chứng chỉ bằng chứng chỉ PFX:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Thay thế`"morzal.pfx"` với tên tệp chứng chỉ thực tế của bạn và`"aw"` bằng mật khẩu chứng chỉ của bạn.

## Bước 7: Ký vào tài liệu

Cuối cùng, chúng ta sẽ ký tài liệu bằng tiện ích chữ ký số:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Quá trình này sẽ ký tài liệu và lưu thành một tệp mới.

## Phần kết luận

Xin chúc mừng! Bạn đã tạo thành công dòng chữ ký và đặt ID nhà cung cấp trong tài liệu Word bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này đơn giản hóa các tác vụ xử lý tài liệu, giúp quy trình làm việc của bạn hiệu quả hơn. Hãy thử và xem nó có thể cải thiện dự án của bạn như thế nào!

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh giao diện của dòng chữ ký không?
 Chắc chắn rồi! Bạn có thể điều chỉnh nhiều tùy chọn khác nhau trong`SignatureLineOptions` phù hợp với phong cách và yêu cầu của bạn.

### Nếu tôi không có chứng chỉ PFX thì sao?
Bạn sẽ cần phải xin chứng chỉ từ một cơ quan cấp chứng chỉ đáng tin cậy vì nó rất cần thiết để ký tài liệu kỹ thuật số.

### Tôi có thể thêm nhiều dòng chữ ký vào một tài liệu không?
Có, bạn có thể thêm nhiều dòng chữ ký bằng cách lặp lại quy trình chèn với các tùy chọn khác nhau.

### Aspose.Words cho .NET có tương thích với .NET Core không?
Có, Aspose.Words for .NET hỗ trợ .NET Core, khiến nó trở nên linh hoạt cho nhiều môi trường phát triển khác nhau.

### Chữ ký số an toàn đến mức nào?
Chữ ký số được tạo bằng Aspose.Words có tính bảo mật cao, miễn là bạn sử dụng chứng chỉ hợp lệ và đáng tin cậy.