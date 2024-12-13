---
title: Thêm chữ ký số mới vào tệp Excel đã ký
linktitle: Thêm chữ ký số mới vào tệp Excel đã ký
second_title: API xử lý Excel Aspose.Cells .NET
description: Tìm hiểu cách thêm chữ ký số mới vào tệp Excel đã ký hiện có bằng Aspose.Cells cho .NET. Hướng dẫn toàn diện này bao gồm tất cả các điều kiện tiên quyết, hướng dẫn từng bước và ví dụ về mã.
type: docs
weight: 12
url: /vi/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Giới thiệu

Trong bối cảnh kỹ thuật số ngày nay, việc đảm bảo tính xác thực và toàn vẹn của tài liệu quan trọng hơn bao giờ hết. Chữ ký số cung cấp một cách đáng tin cậy để xác minh rằng tài liệu không bị thay đổi và có nguồn gốc từ một nguồn hợp pháp. Nếu bạn đang làm việc với các tệp Excel trong .NET và cần thêm chữ ký số mới vào một tệp đã được ký, hướng dẫn này dành cho bạn! Chúng tôi sẽ hướng dẫn quy trình thêm chữ ký số vào tệp Excel đã ký hiện có bằng Aspose.Cells cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu triển khai, hãy đảm bảo bạn có những điều sau:

1.  Aspose.Cells cho .NET: Tải xuống và cài đặt Aspose.Cells từ[trang phát hành](https://releases.aspose.com/cells/net/).
2. .NET Framework: Đảm bảo máy của bạn đã thiết lập .NET Framework và bạn đã quen thuộc với các khái niệm lập trình .NET cơ bản.
3. Chứng chỉ số: Nhận chứng chỉ số hợp lệ ở định dạng .pfx. Để thử nghiệm, bạn có thể tạo chứng chỉ tự ký.
4. Môi trường phát triển: Sử dụng IDE như Visual Studio để viết và thực thi mã C# của bạn.
5. Tệp Excel mẫu: Chuẩn bị một tệp Excel đã được ký kỹ thuật số, đây sẽ là mục tiêu để thêm chữ ký mới.

Với những điều kiện tiên quyết này, chúng ta hãy bắt đầu viết mã!

## Nhập các gói cần thiết

Ở đầu tệp C# của bạn, hãy bao gồm các không gian tên sau để truy cập các lớp và phương thức cần thiết:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Bước 1: Xác định thư mục của bạn

Chỉ định thư mục cho các tệp nguồn của bạn và nơi lưu tệp đầu ra:

```csharp
// Thư mục nguồn
string sourceDir = "Your Document Directory"; // Thay thế bằng thư mục thực tế của bạn
// Thư mục đầu ra
string outputDir = "Your Document Directory"; // Thay thế bằng thư mục thực tế của bạn
```

## Bước 2: Tải Workbook đã ký hiện có

Tải bảng tính Excel đã được ký:

```csharp
// Tải sổ làm việc đã được ký số
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Bước 3: Tạo Bộ sưu tập chữ ký số

Tạo bộ sưu tập để quản lý chữ ký số của bạn:

```csharp
//Tạo bộ sưu tập chữ ký số
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Bước 4: Tải chứng chỉ của bạn

Tải chứng chỉ số của bạn, chứng chỉ này sẽ được sử dụng để tạo chữ ký mới:

```csharp
// Tệp chứng chỉ và mật khẩu của nó
string certFileName = sourceDir + "AsposeDemo.pfx"; // Tệp chứng chỉ của bạn
string password = "aspose"; // Mật khẩu chứng chỉ của bạn

// Tạo chứng chỉ mới
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Bước 5: Tạo chữ ký số mới

Bây giờ, hãy tạo chữ ký số mới và thêm nó vào bộ sưu tập của bạn:

```csharp
// Tạo chữ ký số mới và thêm vào bộ sưu tập
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Bước 6: Thêm Bộ sưu tập chữ ký vào Sổ làm việc

Thêm bộ sưu tập chữ ký số vào sổ làm việc:

```csharp
// Thêm bộ sưu tập chữ ký số vào sổ làm việc
workbook.AddDigitalSignature(dsCollection);
```

## Bước 7: Lưu sổ làm việc

Lưu sổ làm việc có kèm chữ ký số mới:

```csharp
// Lưu sổ làm việc
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Bước 8: Xác nhận thành công

Cung cấp phản hồi sau khi thực hiện thành công:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Phần kết luận

Xin chúc mừng! Bạn đã thêm thành công chữ ký số mới vào tệp Excel đã ký bằng Aspose.Cells cho .NET. Quá trình này tăng cường tính bảo mật cho tài liệu của bạn và đảm bảo tính xác thực và toàn vẹn của chúng.

## Câu hỏi thường gặp

### Chữ ký số là gì?

Chữ ký số là một lược đồ toán học xác minh tính xác thực và toàn vẹn của tin nhắn hoặc tài liệu kỹ thuật số, đảm bảo chúng không bị thay đổi và xác nhận danh tính của người ký.

### Tôi có cần chứng chỉ đặc biệt để tạo chữ ký số không?

Có, cần phải có chứng chỉ số do cơ quan cấp chứng chỉ (CA) đáng tin cậy cấp để tạo chữ ký số hợp lệ.

### Tôi có thể sử dụng chứng chỉ tự ký để thử nghiệm không?

Hoàn toàn được! Bạn có thể sử dụng chứng chỉ tự ký cho mục đích phát triển và thử nghiệm, nhưng đối với sản xuất, bạn nên sử dụng chứng chỉ từ một CA đáng tin cậy.

### Điều gì xảy ra nếu tôi cố gắng thêm chữ ký vào một tài liệu chưa được ký?

Nếu bạn thử thêm chữ ký số vào một tài liệu chưa được ký, thao tác này sẽ không có vấn đề gì, nhưng chữ ký gốc sẽ không có.

### Tôi có thể tìm thêm thông tin về Aspose.Cells ở đâu?

 Để biết hướng dẫn chi tiết và tham chiếu API, hãy kiểm tra[Tài liệu Aspose.Cells](https://reference.aspose.com/cells/net/).