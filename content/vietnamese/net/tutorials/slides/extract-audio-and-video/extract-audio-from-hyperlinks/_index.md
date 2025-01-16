---
title: Trích xuất âm thanh từ siêu liên kết trong PowerPoint bằng Aspose.Slides
linktitle: Trích xuất âm thanh từ siêu liên kết
second_title: API xử lý PowerPoint Aspose.Slides .NET
description: Tìm hiểu cách trích xuất âm thanh từ siêu liên kết trong bản trình bày PowerPoint bằng Aspose.Slides cho .NET. Hướng dẫn từng bước này cung cấp hướng dẫn rõ ràng.
type: docs
weight: 12
url: /vi/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## Giới thiệu

Trong các bài thuyết trình đa phương tiện, âm thanh làm tăng đáng kể tác động của các slide của bạn. Nếu bạn đã từng gặp một bài thuyết trình PowerPoint có siêu liên kết âm thanh và tự hỏi làm thế nào để trích xuất âm thanh đó cho các mục đích sử dụng khác, thì bạn đã đến đúng nơi rồi. Hướng dẫn này sẽ hướng dẫn bạn quy trình trích xuất âm thanh từ siêu liên kết trong bài thuyết trình PowerPoint bằng thư viện Aspose.Slides for .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

### Aspose.Slides cho Thư viện .NET

 Hãy đảm bảo bạn đã cài đặt thư viện Aspose.Slides for .NET. Nếu bạn chưa cài đặt, bạn có thể tải xuống từ[Aspose.Slides cho Tài liệu .NET](https://reference.aspose.com/slides/net/).

### Bài thuyết trình PowerPoint có siêu liên kết âm thanh

Bạn sẽ cần một bản trình bày PowerPoint (PPTX) có chứa siêu liên kết với âm thanh liên quan. Bản trình bày này sẽ là nguồn trích xuất âm thanh của bạn.

## Nhập không gian tên bắt buộc

Để sử dụng Aspose.Slides cho .NET một cách hiệu quả, bạn sẽ cần nhập các không gian tên sau vào dự án C# của mình:

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Bây giờ chúng ta đã có mọi thứ cần thiết, hãy chia nhỏ quá trình trích xuất thành các bước đơn giản.

## Bước 1: Xác định thư mục tài liệu

 Bắt đầu bằng cách chỉ định thư mục nơi lưu trữ bản trình bày PowerPoint của bạn. Thay thế`"Your Document Directory"` với đường dẫn thực tế.

```csharp
string dataDir = "Your Document Directory";
```

## Bước 2: Tải bản trình bày PowerPoint

 Tiếp theo, tải bản trình bày PowerPoint (PPTX) có chứa siêu liên kết âm thanh. Thay thế`"HyperlinkSound.pptx"` bằng tên tệp trình bày thực tế của bạn.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Tiếp tục bước tiếp theo.
}
```

## Bước 3: Truy cập vào Hyperlink Sound

Lấy siêu liên kết từ hình dạng đầu tiên trên trang chiếu đầu tiên. Nếu siêu liên kết này có âm thanh liên quan, chúng ta có thể tiến hành trích xuất nó.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Tiếp tục bước tiếp theo.
}
```

## Bước 4: Trích xuất âm thanh từ siêu liên kết

Nếu siêu liên kết chứa âm thanh, chúng ta có thể trích xuất nó thành một mảng byte và lưu dưới dạng tệp phương tiện.

```csharp
// Trích xuất âm thanh siêu liên kết dưới dạng một mảng byte
byte[] audioData = link.Sound.BinaryData;

// Chỉ định đường dẫn nơi bạn muốn lưu âm thanh đã trích xuất
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Lưu âm thanh đã trích xuất vào một tập tin phương tiện
File.WriteAllBytes(outMediaPath, audioData);
```

Xin chúc mừng! Bạn đã trích xuất thành công âm thanh từ siêu liên kết trong bản trình bày PowerPoint bằng Aspose.Slides for .NET. Bây giờ bạn có thể sử dụng âm thanh này trong các dự án đa phương tiện của mình.

## Phần kết luận

Aspose.Slides for .NET cung cấp một cách mạnh mẽ và thân thiện với người dùng để trích xuất âm thanh từ siêu liên kết trong các bài thuyết trình PowerPoint. Với các bước được nêu trong hướng dẫn này, bạn có thể dễ dàng sử dụng lại nội dung âm thanh từ các bài thuyết trình của mình để nâng cao các dự án của bạn.

## Câu hỏi thường gặp

### Aspose.Slides cho .NET có phải là thư viện miễn phí không?
 Không, Aspose.Slides cho .NET là một thư viện thương mại, nhưng bạn có thể tải xuống bản dùng thử miễn phí để khám phá các tính năng của nó từ[đây](https://releases.aspose.com/).

### Tôi có thể trích xuất âm thanh từ các định dạng PowerPoint cũ hơn như PPT không?
Có, Aspose.Slides for .NET hỗ trợ cả định dạng PPTX và PPT để trích xuất âm thanh.

### Có diễn đàn cộng đồng nào hỗ trợ Aspose.Slides không?
 Chắc chắn rồi! Bạn có thể nhận được sự hỗ trợ và chia sẻ kinh nghiệm trong[Diễn đàn cộng đồng Aspose.Slides](https://forum.aspose.com/).

### Tôi có thể mua giấy phép tạm thời cho Aspose.Slides cho một dự án ngắn hạn không?
Có, bạn có thể xin giấy phép tạm thời cho nhu cầu dự án ngắn hạn của mình bằng cách truy cập[liên kết này](https://purchase.aspose.com/temporary-license/).

### Có định dạng âm thanh nào khác được hỗ trợ để trích xuất ngoài MPG không?
Có, Aspose.Slides for .NET cho phép trích xuất ở nhiều định dạng âm thanh khác nhau. Bạn có thể chuyển đổi âm thanh sang định dạng ưa thích sau khi trích xuất.