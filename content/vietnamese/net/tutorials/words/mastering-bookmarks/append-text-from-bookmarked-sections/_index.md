---
title: Thêm văn bản từ các phần được đánh dấu trong tài liệu Word
linktitle: Thêm văn bản từ các phần được đánh dấu trong tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thêm văn bản liền mạch từ các phần được đánh dấu của tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn từng bước này.
type: docs
weight: 10
url: /vi/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## Giới thiệu

Bạn đã bao giờ thấy khó khăn khi thêm văn bản từ một phần được đánh dấu trong tài liệu Word chưa? Bạn đã đến đúng nơi rồi! Hướng dẫn này sẽ hướng dẫn bạn từng bước thực hiện quy trình bằng cách sử dụng Aspose.Words cho .NET. Đến cuối, bạn sẽ có thể thêm văn bản được đánh dấu như một chuyên gia. Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Aspose.Words cho .NET: Nếu bạn chưa cài đặt nó, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Môi trường phát triển .NET như Visual Studio.
- Kiến thức cơ bản về C#: Sự quen thuộc với các khái niệm lập trình C# cơ bản sẽ có lợi.
- Tài liệu Word có dấu trang: Tài liệu Word có dấu trang mà chúng ta sẽ sử dụng để thêm văn bản.

## Nhập các không gian tên cần thiết

Đầu tiên, chúng ta cần nhập các không gian tên cần thiết để truy cập các chức năng của Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## Bước 1: Tải Tài liệu và Khởi tạo Biến

Chúng ta hãy bắt đầu bằng cách tải các tài liệu Word nguồn và đích và khởi tạo các biến cần thiết.

```csharp
//Tải tài liệu nguồn và tài liệu đích.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Khởi tạo trình nhập tài liệu.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Tìm dấu trang trong tài liệu nguồn.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Bước 2: Xác định đoạn văn bắt đầu và kết thúc

Tiếp theo, chúng ta cần xác định vị trí các đoạn văn mà dấu trang bắt đầu và kết thúc. Điều này rất cần thiết để trích xuất văn bản chính xác.

```csharp
// Xác định các đoạn văn ở đầu và cuối của dấu trang.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Xác thực các đoạn văn.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## Bước 3: Xác thực đoạn văn cha

Chúng ta cần đảm bảo rằng cả đoạn mở đầu và kết thúc đều có chung một nút cha. Đây là cách tiếp cận đơn giản để tránh phức tạp.

```csharp
// Kiểm tra xem đoạn mở đầu và đoạn kết có cùng phần tử cha hay không.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## Bước 4: Xác định nút cần dừng

Bây giờ, chúng ta cần xác định vị trí dừng sao chép văn bản, đó sẽ là nút ngay sau đoạn văn kết thúc.

```csharp
// Xác định nút ngay sau đoạn văn kết thúc.
Node endNode = endPara.NextSibling;
```

## Bước 5: Thêm Văn bản được Đánh dấu vào Tài liệu Đích

Cuối cùng, chúng ta sẽ lặp qua các nút từ đoạn văn bắt đầu đến nút sau đoạn văn kết thúc và thêm chúng vào tài liệu đích.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Nhập nút hiện tại vào tài liệu đích.
    Node newNode = importer.ImportNode(curNode, true);

    // Thêm nút đã nhập vào tài liệu đích.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Lưu tài liệu đích đã cập nhật.
dstDoc.Save("appended_document.docx");
```

## Phần kết luận

Xin chúc mừng! Bạn đã thêm thành công văn bản từ một phần được đánh dấu trong tài liệu Word bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này giúp thao tác tài liệu trở nên đơn giản và giờ đây bạn có thêm một kỹ năng tiện dụng trong bộ công cụ của mình. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể thêm văn bản từ nhiều dấu trang cùng một lúc không?
Có, bạn có thể lặp lại quy trình này cho từng dấu trang và thêm văn bản nếu cần.

### Nếu đoạn mở đầu và đoạn kết thúc có phần cha khác nhau thì sao?
Ví dụ hiện tại giả định chúng có cùng cha mẹ. Nếu không, bạn sẽ cần triển khai xử lý phức tạp hơn.

### Định dạng gốc của văn bản được thêm vào có được giữ nguyên không?
 Chắc chắn rồi! Sử dụng`ImportFormatMode.KeepSourceFormatting`đảm bảo định dạng ban đầu được duy trì.

### Có thể thêm văn bản vào vị trí cụ thể trong tài liệu đích không?
Có, bạn có thể thêm văn bản vào bất kỳ vị trí mong muốn nào bằng cách điều hướng đến nút thích hợp trong tài liệu đích.

### Tôi có thể thêm văn bản từ dấu trang vào phần mới không?
Có, bạn có thể tạo một phần mới trong tài liệu đích và thêm văn bản vào đó.