---
title: Chuyển đổi HTML sang PNG bằng Aspose.HTML trong .NET
linktitle: Chuyển đổi HTML sang PNG bằng Aspose.HTML trong .NET
second_title: API thao tác HTML Aspose.HTML .NET
description: Tìm hiểu cách chuyển đổi tài liệu HTML thành hình ảnh PNG trong .NET bằng thư viện Aspose.HTML. Làm theo hướng dẫn từng bước của chúng tôi để đơn giản hóa việc chuyển đổi HTML sang hình ảnh.
type: docs
weight: 10
url: /vi/net/tutorials/html/converting-html-documents/convert-html-as-png/
---
## Giới thiệu

Bạn đang muốn chuyển đổi tài liệu HTML thành hình ảnh PNG một cách dễ dàng? Vâng, bạn đã đến đúng nơi rồi! Trong hướng dẫn này, chúng ta sẽ tìm hiểu cách sử dụng Aspose.HTML cho .NET để hiển thị HTML dưới dạng hình ảnh PNG. Thư viện mạnh mẽ này đơn giản hóa quy trình xử lý nội dung HTML trong các ứng dụng .NET, giúp bạn dễ dàng chuyển đổi các trang web hoặc mẫu tài liệu thành định dạng hình ảnh.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo rằng bạn đã thiết lập mọi thứ chính xác:

1.  .NET Framework/ .NET Core: Đảm bảo bạn đã cài đặt .NET Framework hoặc .NET Core trên máy của mình. Bạn có thể tải xuống[.NET ở đây](https://dotnet.microsoft.com/download).

2.  Aspose.HTML cho Thư viện .NET: Bạn sẽ cần phải có thư viện Aspose.HTML. Bạn có thể tải xuống[đây](https://releases.aspose.com/html/net/)hoặc dùng thử miễn phí với[dùng thử miễn phí](https://releases.aspose.com/).

3. IDE: Nên sử dụng môi trường phát triển tích hợp (IDE) phù hợp như Visual Studio để viết và chạy mã của bạn.

4. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp bạn theo dõi dễ dàng, nhưng đừng lo, tôi sẽ giải thích mọi thứ khi chúng ta thực hành!

Khi bạn đã đáp ứng được những điều kiện tiên quyết này, chúng ta đã sẵn sàng để bắt đầu!

## Nhập gói

Để sử dụng các chức năng của Aspose.HTML, chúng ta cần nhập các không gian tên cần thiết. Sau đây là cách thêm tham chiếu vào dự án của bạn:

1. Mở dự án của bạn trong Visual Studio.
2. Nhấp chuột phải vào dự án của bạn trong Solution Explorer.
3. Chọn "Quản lý gói NuGet".
4.  Tìm kiếm`Aspose.HTML` và cài đặt nó.

Sau khi cài đặt gói, bạn có thể bắt đầu viết mã! Bước đầu tiên là chuẩn bị không gian làm việc và bao gồm các không gian tên có liên quan trong tệp C# của bạn.

```csharp
using Aspose.Html;
using Aspose.Html.Converters;
using Aspose.Html.Rendering;
using Aspose.Html.Rendering.Image;
```

Bây giờ chúng ta đã thiết lập xong bối cảnh, hãy chia nhỏ quá trình hiển thị HTML dưới dạng hình ảnh PNG thành các bước chi tiết, dễ làm theo.

## Bước 1: Thiết lập thư mục dữ liệu

Điều đầu tiên bạn muốn làm là thiết lập một thư mục nơi bạn sẽ lưu hình ảnh của mình. Thư mục này đóng vai trò là nơi lưu trữ các tệp PNG được tạo.

```csharp
string dataDir = "Your Data Directory"; // Chỉ định đường dẫn thư mục của bạn
```

-  Thay thế`"Your Data Directory"` với đường dẫn nơi bạn muốn lưu trữ các tệp PNG đầu ra của mình. Điều này có thể giống như`@"C:\work\"`.

## Bước 2: Tạo một đối tượng tài liệu HTML

Bây giờ chúng ta đã thiết lập thư mục, hãy tạo một đối tượng tài liệu HTML. Đây là nơi chúng ta sẽ xác định nội dung HTML mà chúng ta muốn chuyển đổi.

```csharp
using (var document = new Aspose.Html.HTMLDocument("<style>p { color: green; }</style><p>my first paragraph</p>", dataDir))
{
    // Các bước tiếp theo ở đây
}
```

-  Trong đoạn mã trên, chúng ta đang khởi tạo một`HTMLDocument` trong khi truyền vào một số nội dung HTML cơ bản định dạng một đoạn văn thành màu xanh lá cây. Tham số thứ hai là đường dẫn nơi bất kỳ tài nguyên nào (nếu cần) sẽ được lưu trữ.

## Bước 3: Tạo một trình kết xuất HTML

 Tiếp theo, chúng ta sẽ tạo một phiên bản của`HtmlRenderer` Lớp này có nhiệm vụ chuyển đổi tài liệu HTML của chúng ta thành định dạng hình ảnh mong muốn.

```csharp
using (HtmlRenderer renderer = new HtmlRenderer())
{
    // Tiến hành bước tiếp theo
}
```

-  Các`HtmlRenderer`là đối tượng bạn cần để chuyển đổi nội dung HTML thành hình ảnh. Nó xử lý quá trình kết xuất ẩn, vì vậy bạn có thể tập trung vào những gì bạn cần!

## Bước 4: Thiết lập thiết bị hình ảnh

 Bây giờ là lúc chuẩn bị`ImageDevice`. Đây là mục tiêu cho quá trình kết xuất của chúng tôi, nơi hình ảnh PNG cuối cùng sẽ được tạo ra.

```csharp
using (ImageDevice device = new ImageDevice(dataDir + @"document_out.png"))
{
    // Hiển thị tài liệu HTML
}
```

- `ImageDevice` lấy đường dẫn đầy đủ của tệp PNG cần tạo. Ở đây, chúng tôi chỉ định rằng tệp này sẽ được lưu dưới dạng`document_out.png` trong thư mục đã xác định trước đó của chúng tôi.

## Bước 5: Kết xuất tài liệu HTML thành PNG

Bây giờ đến phần thú vị—kết xuất tài liệu HTML của chúng ta thành hình ảnh PNG! Đây là nơi chúng ta gọi phương thức kết xuất để hoàn tất quá trình chuyển đổi.

```csharp
renderer.Render(device, document);
```

-  Sử dụng`Render` phương pháp của`HtmlRenderer` , bạn vượt qua`ImageDevice` và`HTMLDocument`. Hành động này chuyển đổi mã HTML đã chỉ định thành hình ảnh PNG và hình ảnh được lưu vào thư mục bạn đã chỉ định trước đó.

## Phần kết luận

Và bạn đã có nó! Bạn đã kết xuất thành công HTML dưới dạng hình ảnh PNG bằng Aspose.HTML trong .NET. Công cụ mạnh mẽ này cung cấp một cách trực tiếp để thao tác nội dung HTML theo chương trình, giúp việc tạo và trình bày tài liệu dễ dàng hơn bao giờ hết. Cho dù bạn đang làm việc trên các ứng dụng web hay tạo báo cáo, phương pháp này là một công cụ thay đổi cuộc chơi.

## Câu hỏi thường gặp

### Aspose.HTML dành cho .NET là gì?
Aspose.HTML for .NET là một thư viện cho phép các nhà phát triển làm việc với các tài liệu HTML trong các ứng dụng .NET, cung cấp các chức năng để kết xuất, chuyển đổi và chỉnh sửa.

### Tôi có thể sử dụng Aspose.HTML mà không cần giấy phép không?
Có, Aspose cung cấp phiên bản dùng thử miễn phí mà bạn có thể sử dụng để khám phá các tính năng trước khi mua.

### Aspose.HTML có thể chuyển đổi những loại tệp nào?
Aspose.HTML chủ yếu chuyển đổi các tài liệu HTML sang nhiều định dạng khác nhau, bao gồm PNG, JPEG, PDF và nhiều định dạng khác nữa.

### Tôi có thể nhận hỗ trợ cho Aspose.HTML ở đâu?
 Bạn có thể nhận được hỗ trợ thông qua diễn đàn Aspose[đây](https://forum.aspose.com/c/html/29).

### Aspose.HTML có tương thích với .NET Core không?
Có, Aspose.HTML tương thích với .NET Core và có thể sử dụng trong các ứng dụng .NET Core mà không gặp bất kỳ sự cố nào.