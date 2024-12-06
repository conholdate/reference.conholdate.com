---
title: Phát hiện định dạng tệp tài liệu
linktitle: Phát hiện định dạng tệp tài liệu
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách phát hiện và quản lý nhiều định dạng tệp tài liệu khác nhau một cách liền mạch bằng Aspose.Words cho .NET. Làm theo hướng dẫn chi tiết của chúng tôi với các ví dụ thực tế, mẹo và câu hỏi thường gặp.
type: docs
weight: 10
url: /vi/net/tutorials/words/words-processing-with-file-format/document-file-format-detection/
---
## Giới thiệu

Quản lý và sắp xếp hiệu quả nhiều định dạng tài liệu khác nhau là rất quan trọng trong bối cảnh kỹ thuật số ngày nay. Aspose.Words for .NET cung cấp giải pháp mạnh mẽ để phát hiện và xử lý các loại tệp khác nhau. Trong hướng dẫn này, chúng tôi sẽ đi sâu vào quy trình từng bước để phát hiện các định dạng tài liệu, đảm bảo độ chính xác và tiết kiệm thời gian quý báu.

## Điều kiện tiên quyết để phát hiện tài liệu

Trước khi bắt đầu, hãy đảm bảo đáp ứng các yêu cầu sau:

1. Aspose.Words cho Thư viện .NET  
    Tải xuống thư viện từ[Aspose Words phát hành](https://releases.aspose.com/words/net/) và kích hoạt nó bằng giấy phép hợp lệ. Đối với giấy phép tạm thời, hãy truy cập[Giấy phép tạm thời Aspose](https://purchase.aspose.com/temporary-license/).

2. Môi trường phát triển  
   Sử dụng Visual Studio (bất kỳ phiên bản nào gần đây) đã cài đặt .NET Framework.

3. Thiết lập tập tin cơ bản  
   Sắp xếp các tập tin đầu vào và chuẩn bị các thư mục để phân loại các định dạng được phát hiện.

## Nhập không gian tên thiết yếu

Bao gồm các không gian tên này khi bắt đầu chương trình của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Các lệnh nhập này cung cấp quyền truy cập vào các lớp và phương thức cần thiết để phát hiện định dạng tệp.

## Bước 1: Khởi tạo thư mục để sắp xếp đầu ra

Tạo thư mục để lưu trữ tệp dựa trên định dạng được phát hiện của chúng.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
string supportedDir = Path.Combine(dataDir, "Supported");
string unknownDir = Path.Combine(dataDir, "Unknown");
string encryptedDir = Path.Combine(dataDir, "Encrypted");
string pre97Dir = Path.Combine(dataDir, "Pre97");

// Đảm bảo các thư mục tồn tại
Directory.CreateDirectory(supportedDir);
Directory.CreateDirectory(unknownDir);
Directory.CreateDirectory(encryptedDir);
Directory.CreateDirectory(pre97Dir);
```

Cấu trúc này giúp đơn giản hóa việc quản lý tập tin.

## Bước 2: Lấy danh sách tập tin

Lọc ra các tài liệu bị hỏng hoặc không được hỗ trợ để đơn giản hóa quá trình xử lý.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir)
    .Where(fileName => !fileName.EndsWith("Corrupted document.docx"));
```

Danh sách được lọc đảm bảo bạn chỉ làm việc với các tệp hợp lệ.

## Bước 3: Phát hiện và phân loại định dạng tệp

Lặp qua từng tệp để xác định định dạng của tệp và di chuyển tệp đến thư mục thích hợp.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);
    Console.WriteLine($"Processing file: {nameOnly}");

    FileFormatInfo fileInfo = FileFormatUtil.DetectFileFormat(fileName);

    // Định dạng đầu ra được phát hiện
    Console.WriteLine($"Detected Format: {fileInfo.LoadFormat}");
    if (fileInfo.IsEncrypted)
    {
        Console.WriteLine("This file is encrypted.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (fileInfo.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

 Các`FileFormatUtil.DetectFileFormat` Phương pháp này đóng vai trò trung tâm trong việc xác định đặc điểm của tài liệu.

## Phần kết luận

Bằng cách tận dụng Aspose.Words cho .NET, việc phát hiện các định dạng tệp tài liệu trở thành một nhiệm vụ dễ dàng. Khả năng xác định và phân loại các định dạng khác nhau đảm bảo quản lý tài liệu liền mạch, nâng cao năng suất và hiệu quả quy trình làm việc.

## Câu hỏi thường gặp

### Mục đích chính của việc phát hiện định dạng tài liệu là gì?  
Phát hiện định dạng giúp hợp lý hóa việc xử lý tài liệu bằng cách phân loại tệp cho các quy trình công việc hoặc ứng dụng cụ thể.

### Aspose.Words có hỗ trợ các tập tin được mã hóa không?  
Có, nó có thể phát hiện mã hóa và xử lý các tài liệu được mã hóa theo đúng yêu cầu.

### Tôi có thể mở rộng giải pháp này cho các loại tệp khác không?  
Có, bạn có thể sửa đổi mã để bao gồm các định dạng bổ sung hoặc tích hợp các thư viện Aspose khác.

### Tôi phải xử lý những định dạng không xác định như thế nào?  
Lưu trữ riêng các định dạng không xác định để kiểm tra thủ công hoặc xử lý thêm bằng các công cụ chuyên dụng.

### Tôi có thể tìm tài liệu bổ sung ở đâu?  
 Ghé thăm[Tài liệu Aspose.Words](https://reference.aspose.com/words/net/) để có hướng dẫn và ví dụ toàn diện.
