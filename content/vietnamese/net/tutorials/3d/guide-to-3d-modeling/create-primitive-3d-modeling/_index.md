---
title: Tạo mô hình 3D nguyên thủy
linktitle: Tạo mô hình 3D nguyên thủy
second_title: API Aspose.3D .NET
description: Tìm hiểu cách tạo và tùy chỉnh các mô hình 3D nguyên thủy, bao gồm hộp và hình trụ, và lưu chúng ở định dạng FBX một cách dễ dàng.
type: docs
weight: 10
url: /vi/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Giới thiệu

Chào mừng đến với thế giới nhập vai của mô hình 3D sử dụng Aspose.3D cho .NET! Trong hướng dẫn toàn diện này, chúng tôi sẽ hướng dẫn bạn từng bước trong quy trình tạo mô hình 3D nguyên thủy. Cho dù bạn là nhà phát triển có kinh nghiệm hay người mới bắt đầu háo hức học hỏi, hướng dẫn này sẽ giúp bạn tạo ra các thành phần 3D tuyệt đẹp cho các dự án của mình.

## Điều kiện tiên quyết

Trước khi bắt đầu tạo mô hình 3D, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

-  Aspose.3D cho .NET: Tải xuống và cài đặt thư viện Aspose.3D cho .NET từ[trang tải xuống](https://releases.aspose.com/3d/net/).
  
- Môi trường phát triển .NET: Thiết lập môi trường tương thích với Aspose.3D, chẳng hạn như Visual Studio.

Khi đã chuẩn bị mọi thứ xong, chúng ta hãy bắt đầu cuộc phiêu lưu tạo mô hình 3D nhé!

## Nhập không gian tên bắt buộc

Bắt đầu bằng cách nhập các không gian tên cần thiết để truy cập các chức năng của Aspose.3D:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Các không gian tên này sẽ cung cấp cho bạn các công cụ cần thiết để thao tác với các mô hình 3D và lưu các sáng tạo của bạn.

## Bước 1: Khởi tạo đối tượng Scene

Tạo một đối tượng cảnh mới đóng vai trò như khung vẽ cho mô hình 3D của bạn:

```csharp
// Khởi tạo một đối tượng Scene
Scene scene = new Scene();
```

Cảnh này sẽ chứa các hình dạng nguyên thủy mà bạn sắp tạo.

## Bước 2: Tạo mô hình hộp

Tiếp theo, hãy thêm mô hình hộp vào cảnh của bạn:

```csharp
// Tạo mô hình hộp
scene.RootNode.CreateChildNode("box", new Box());
```

Bạn có thể tùy chỉnh kích thước và đặc tính của hộp cho phù hợp với tầm nhìn sáng tạo của mình.

## Bước 3: Tạo mô hình hình trụ

Bây giờ, hãy tăng cường cảnh của bạn bằng cách thêm một hình trụ:

```csharp
// Tạo mô hình hình trụ
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Giống như hộp, bạn có thể thoải mái điều chỉnh các thông số của xi lanh để đạt được hình dáng mong muốn.

## Bước 4: Lưu cảnh ở định dạng FBX

Để bảo quản mô hình 3D của bạn, hãy lưu nó ở định dạng FBX:

```csharp
// Lưu bản vẽ ở định dạng FBX
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Hãy đảm bảo chọn thư mục đầu ra và tên tệp phù hợp cho mô hình của bạn.

## Bước 5: Hiển thị thông báo thành công

Cuối cùng, hãy ăn mừng thành công của bạn bằng cách hiển thị thông báo:

```csharp
// Hiển thị thông báo thành công
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Cảnh 3D gồm các mô hình nguyên thủy của bạn hiện đã hoàn tất và được lưu!

## Phần kết luận

 Xin chúc mừng vì đã tạo ra các mô hình 3D tuyệt đẹp bằng Aspose.3D cho .NET! Hướng dẫn này đề cập đến những điều cơ bản về mô hình hóa nguyên thủy, nhưng khả năng là vô tận. Khám phá thêm về các tính năng và kỹ thuật nâng cao trong[tài liệu](https://reference.aspose.com/3d/net/).

## Câu hỏi thường gặp

### Tôi có thể sử dụng Aspose.3D cho .NET với các ngôn ngữ lập trình khác ngoài .NET không?

Aspose.3D chủ yếu hỗ trợ .NET, nhưng cũng có phiên bản dành cho Java và các nền tảng khác.

### Có bản dùng thử miễn phí không?

 Có, bạn có thể dùng thử khả năng của Aspose.3D với[dùng thử miễn phí](https://releases.aspose.com/).

### Tôi có thể tìm thấy hỗ trợ cho Aspose.3D cho .NET ở đâu?

Để được cộng đồng hỗ trợ, hãy truy cập[Diễn đàn Aspose.3D](https://forum.aspose.com/c/3d/18).

### Tôi có thể xin giấy phép tạm thời bằng cách nào?

 Bạn có thể yêu cầu giấy phép tạm thời[đây](https://purchase.conholdate.com/temporary-license/).

### Có hướng dẫn bổ sung nào không?

 Có! Khám phá thêm các hướng dẫn và ví dụ trong[tài liệu](https://reference.aspose.com/3d/net/).