---
title: Kết xuất chế độ xem toàn cảnh của cảnh 3D bằng Aspose.3D cho .NET
linktitle: Hiển thị chế độ xem toàn cảnh của một cảnh 3D
second_title: API Aspose.3D .NET
description: Tìm hiểu cách kết xuất chế độ xem toàn cảnh tuyệt đẹp của cảnh 3D trong ứng dụng .NET của bạn bằng Aspose.3D. Làm theo hướng dẫn từng bước của chúng tôi để kết xuất cảnh đắm chìm.
type: docs
weight: 13
url: /vi/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Giới thiệu

Tạo các cảnh 3D toàn cảnh, đắm chìm là một bước ngoặt đối với các nhà phát triển muốn nâng cao ứng dụng của họ bằng các hiệu ứng hình ảnh tuyệt đẹp. Cho dù bạn đang làm việc trên một công cụ chơi game, hình ảnh kiến trúc hay trải nghiệm web đắm chìm, việc kết xuất các cảnh 3D dưới dạng toàn cảnh cho phép người dùng trải nghiệm chế độ xem động từ mọi góc độ. Aspose.3D cho .NET là công cụ hoàn hảo để tích hợp liền mạch tính năng này vào các dự án .NET của bạn. Hướng dẫn toàn diện này sẽ hướng dẫn bạn quy trình kết xuất toàn cảnh từ một cảnh 3D bằng Aspose.3D cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu quá trình kết xuất, hãy đảm bảo rằng bạn đã chuẩn bị những điều sau:

-  Aspose.3D cho .NET: Để bắt đầu, bạn cần cài đặt Aspose.3D, cung cấp tất cả các công cụ cần thiết để xử lý nội dung 3D và kết xuất.[Tải xuống Aspose.3D cho .NET](https://releases.aspose.com/3d/net/) để bắt đầu.
- Môi trường phát triển .NET: Yêu cầu môi trường phát triển .NET được cấu hình đầy đủ. Đảm bảo bạn có Visual Studio hoặc bất kỳ IDE tương thích nào khác.
- Tệp cảnh 3D mẫu: Bạn có thể sử dụng bất kỳ cảnh 3D nào ở các định dạng như`.glb`, `.fbx` , hoặc`.obj`. Đối với hướng dẫn này, chúng tôi sẽ sử dụng tệp "VirtualCity.glb" đơn giản.

Khi bạn đã đáp ứng được những điều kiện tiên quyết này, chúng ta có thể chuyển sang thiết lập bối cảnh.

## Nhập các không gian tên cần thiết

Để làm việc với Aspose.3D, chúng ta cần nhập một số không gian tên vào dự án của mình. Các không gian tên này cho phép bạn thao tác các đối tượng 3D, cài đặt camera và tùy chọn kết xuất một cách hiệu quả.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Các không gian tên này rất cần thiết để tải cảnh 3D, cấu hình camera, ánh sáng và thiết lập kết cấu dựng hình tạo nên chế độ xem toàn cảnh.

## Bước 1: Tải Cảnh 3D vào Ứng dụng của bạn

 Bước đầu tiên là tải cảnh 3D vào ứng dụng của bạn. Điều này có thể đạt được bằng cách sử dụng`Scene` lớp được cung cấp bởi Aspose.3D. Thay thế`"VirtualCity.glb"` với đường dẫn đến tệp cảnh 3D của bạn.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 Các`Scene` Đối tượng tải cảnh 3D vào bộ nhớ, cho phép bạn tương tác với đối tượng và áp dụng các kỹ thuật kết xuất.

## Bước 2: Thiết lập máy ảnh và đèn

Để đảm bảo cảnh 3D của bạn được chụp chính xác, bạn sẽ cần thiết lập máy ảnh và ánh sáng phù hợp. Máy ảnh cho phép bạn kiểm soát góc nhìn của cảnh, trong khi đèn giúp chiếu sáng các vật thể.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Thiết lập camera: Các mặt phẳng gần và xa của camera được thiết lập để xác định phạm vi có thể nhìn thấy trong cảnh 3D.
- Thiết lập ánh sáng: Thêm hai đèn—một đèn điểm và một đèn có màu cụ thể để tăng thêm chiều sâu và tính chân thực cho cảnh.

## Bước 3: Thiết lập Renderer và Xác định Mục tiêu Render

Bây giờ cảnh, máy quay và đèn của bạn đã được thiết lập, bước tiếp theo là tạo trình kết xuất và xác định mục tiêu kết xuất. Trình kết xuất chịu trách nhiệm tạo hình ảnh 3D và mục tiêu kết xuất xác định nơi lưu trữ đầu ra cuối cùng.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Cube Render Texture: Được sử dụng để render bản đồ khối cho chế độ xem toàn cảnh. Chúng tôi định nghĩa một texture 512x512 tại đây.
- Kết cấu kết xuất cuối cùng: Đây là kết cấu sẽ giữ chế độ xem toàn cảnh hình chữ nhật cuối cùng.

## Bước 4: Cấu hình Viewport và Render Scene

Sau khi tạo kết cấu kết xuất, chúng ta cần cấu hình khung nhìn để xác định vùng cảnh 3D mà camera sẽ chụp.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Mã này thiết lập chế độ xem cho bản đồ khối và hiển thị cảnh vào`rt` kết xuất kết cấu.

## Bước 5: Áp dụng Hậu xử lý cho Phép chiếu hình chữ nhật đều

Tại thời điểm này, chúng ta cần áp dụng hậu xử lý để chuyển đổi bản đồ khối thành chế độ xem toàn cảnh hình chữ nhật. Sự chuyển đổi này đảm bảo rằng hình ảnh cuối cùng sẽ là một bức tranh toàn cảnh thích hợp.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Phép chiếu hình chữ nhật: Hiệu ứng hậu xử lý này sẽ lấy bản đồ hình khối và biến đổi nó thành phép chiếu toàn cảnh hình chữ nhật, mang đến góc nhìn 360 độ liền mạch.

## Bước 6: Lưu ảnh toàn cảnh đã kết xuất

Sau khi quá trình dựng hình và xử lý hậu kỳ hoàn tất, bước cuối cùng là lưu ảnh toàn cảnh vào một tệp hình ảnh, chẳng hạn như PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Thao tác này sẽ lưu hình ảnh toàn cảnh vào thư mục đã chỉ định, cho phép bạn tích hợp hình ảnh đó vào ứng dụng hoặc hiển thị trên trang web.

## Phần kết luận

Việc dựng hình ảnh toàn cảnh của các cảnh 3D chưa bao giờ dễ dàng đến thế với Aspose.3D for .NET. Bằng cách làm theo các bước nêu trên, bạn có thể dễ dàng tải một cảnh 3D, cấu hình camera và đèn, dựng hình cảnh và áp dụng các hiệu ứng hậu xử lý để tạo ra hình ảnh toàn cảnh sống động. Aspose.3D for .NET cung cấp sức mạnh và tính linh hoạt để đưa hình ảnh trực quan 3D của bạn vào cuộc sống và tích hợp chúng một cách liền mạch vào các ứng dụng của bạn.

## Câu hỏi thường gặp

### Tôi có thể sử dụng cảnh 3D của riêng mình để dựng ảnh toàn cảnh không?
Hoàn toàn đúng. Chỉ cần thay thế đường dẫn tệp cảnh mẫu bằng vị trí cảnh 3D tùy chỉnh của bạn.

### Có bất kỳ hiệu ứng hậu xử lý bổ sung nào không?
Có, Aspose.3D cung cấp nhiều hiệu ứng hậu xử lý như độ sâu trường ảnh, hiệu ứng nở hoa, v.v. có thể được áp dụng để nâng cao hình ảnh được kết xuất của bạn.

### Làm thế nào để tối ưu hóa hiệu suất kết xuất?
Hiệu suất kết xuất có thể được tối ưu hóa bằng cách điều chỉnh các thông số như kích thước và độ phân giải kết cấu kết xuất, cũng như tinh chỉnh các mặt phẳng gần và xa của máy ảnh.

### Tôi có thể tích hợp tính năng này vào ứng dụng web không?
Có, Aspose.3D cho .NET có thể được tích hợp vào các ứng dụng web .NET của bạn để hiển thị toàn cảnh 3D một cách động.

### Có diễn đàn cộng đồng nào hỗ trợ Aspose.3D không?
 Vâng, bạn có thể ghé thăm[Diễn đàn Aspose.3D](https://forum.aspose.com/c/3d/18) để hỗ trợ và thảo luận cộng đồng.