---
title: Gọi lại trang lưu trong tài liệu Word
linktitle: Gọi lại trang lưu trong tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách dễ dàng chuyển đổi từng trang của tài liệu Word thành từng hình ảnh PNG riêng lẻ bằng Aspose.Words cho .NET. Hướng dẫn này cung cấp hướng dẫn từng bước, bao gồm các ví dụ về mã.
type: docs
weight: 10
url: /vi/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Giới thiệu

Bạn đã bao giờ cần chuyển đổi từng trang của một tài liệu Word thành từng hình ảnh riêng lẻ chưa? Cho dù bạn đang muốn tạo hình thu nhỏ để xem trước hay chia nhỏ một báo cáo dài thành hình ảnh dễ hiểu, Aspose.Words for .NET giúp bạn thực hiện nhiệm vụ này một cách đơn giản và hiệu quả. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thiết lập lệnh gọi lại lưu trang để lưu từng trang của tài liệu dưới dạng hình ảnh PNG. Hãy bắt đầu nào!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những thứ sau:

1.  Aspose.Words cho .NET: Tải xuống và cài đặt từ[đây](https://releases.aspose.com/words/net/).
2. Visual Studio: Có thể sử dụng bất kỳ phiên bản nào, nhưng chúng tôi sẽ sử dụng Visual Studio 2019 cho hướng dẫn này.
3. Kiến thức cơ bản về C#: Sự quen thuộc với C# sẽ giúp bạn theo dõi dễ dàng hơn.

## Bước 1: Nhập các không gian tên cần thiết

Đầu tiên, chúng ta cần nhập các không gian tên cần thiết. Điều này cho phép chúng ta truy cập các lớp và phương thức cần thiết mà không cần nhập toàn bộ không gian tên mỗi lần.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 2: Xác định thư mục tài liệu của bạn

Tiếp theo, hãy đặt đường dẫn đến thư mục tài liệu của bạn. Đây là nơi tài liệu Word đầu vào của bạn nằm và nơi hình ảnh đầu ra sẽ được lưu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 3: Tải tài liệu của bạn

Bây giờ, hãy tải tài liệu bạn muốn xử lý. Đảm bảo rằng tài liệu của bạn có tên "Rendering.docx" nằm trong thư mục đã chỉ định.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Bước 4: Cấu hình tùy chọn lưu hình ảnh

Chúng tôi sẽ thiết lập các tùy chọn để lưu hình ảnh, chỉ rõ rằng chúng tôi muốn lưu các trang dưới dạng tệp PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Đây,`PageSet` xác định phạm vi các trang cần lưu và`PageSavingCallback` trỏ tới lớp gọi lại tùy chỉnh của chúng tôi.

## Bước 5: Triển khai lệnh gọi lại lưu trang

Bây giờ, chúng ta cần triển khai lớp gọi lại để xử lý cách lưu từng trang.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Lớp này thực hiện`IPageSavingCallback` giao diện. Trong`PageSaving` phương pháp này, chúng tôi chỉ định mẫu đặt tên cho mỗi trang đã lưu.

## Bước 6: Lưu tài liệu dưới dạng hình ảnh

Cuối cùng, chúng ta lưu tài liệu bằng các tùy chọn đã cấu hình.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Phần kết luận

Xin chúc mừng! Bạn đã thiết lập thành công lệnh gọi lại lưu trang để lưu từng trang của tài liệu Word dưới dạng hình ảnh PNG riêng biệt bằng Aspose.Words cho .NET. Kỹ thuật này cực kỳ hữu ích cho nhiều ứng dụng khác nhau, từ tạo bản xem trước trang đến tạo hình ảnh trang riêng lẻ cho báo cáo.

## Câu hỏi thường gặp

### Tôi có thể lưu các trang ở định dạng khác ngoài PNG không?
 Có! Bạn có thể lưu các trang ở các định dạng như JPEG, BMP và TIFF bằng cách thay đổi`SaveFormat` TRONG`ImageSaveOptions`.

### Làm thế nào để tôi có thể chỉ lưu những trang cụ thể?
 Để lưu các trang cụ thể, hãy điều chỉnh`PageSet` tham số trong`ImageSaveOptions` để chỉ bao gồm những trang mong muốn.

### Có thể tùy chỉnh chất lượng hình ảnh không?
 Chắc chắn rồi! Bạn có thể kiểm soát chất lượng hình ảnh đầu ra bằng cách thiết lập các thuộc tính như`ImageSaveOptions.JpegQuality`.

### Làm sao tôi có thể xử lý hiệu quả các tài liệu lớn?
Đối với các tài liệu lớn, hãy cân nhắc xử lý các trang theo từng đợt để quản lý việc sử dụng bộ nhớ hiệu quả.

### Tôi có thể tìm thêm thông tin về Aspose.Words cho .NET ở đâu?
 Để có hướng dẫn và ví dụ toàn diện, hãy xem[Tài liệu Aspose.Words](https://reference.aspose.com/words/net/).