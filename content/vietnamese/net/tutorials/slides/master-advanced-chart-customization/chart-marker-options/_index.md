---
title: Tùy chọn đánh dấu biểu đồ trên điểm dữ liệu trong Aspose.Slides .NET
linktitle: Tùy chọn đánh dấu biểu đồ trên điểm dữ liệu trong Aspose.Slides .NET
second_title: API xử lý PowerPoint Aspose.Slides .NET
description: Tìm hiểu cách cải thiện biểu đồ PowerPoint của bạn bằng các tùy chọn đánh dấu tùy chỉnh bằng Aspose.Slides cho .NET. Hướng dẫn từng bước này bao gồm các điều kiện tiên quyết, tạo biểu đồ, định dạng điểm dữ liệu và nhiều hơn nữa.
type: docs
weight: 11
url: /vi/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Giới thiệu

Việc kết hợp các phương tiện hỗ trợ trực quan vào bài thuyết trình là điều cần thiết để giao tiếp có tác động. Aspose.Slides for .NET cung cấp các công cụ mạnh mẽ để tạo và tùy chỉnh biểu đồ, cho phép các nhà phát triển cải thiện bài thuyết trình dữ liệu của họ. Một trong những tính năng nổi bật là khả năng sử dụng các tùy chọn đánh dấu biểu đồ trên các điểm dữ liệu, cho phép tùy chỉnh chính xác để có biểu đồ trông chuyên nghiệp. Bài viết này sẽ hướng dẫn bạn từng bước cần thiết để đạt được điều này.

## Điều kiện tiên quyết

Trước khi tiếp tục, hãy đảm bảo những điều sau:

-  Aspose.Slides cho .NET đã cài đặt: Tải xuống từ[đây](https://releases.aspose.com/slides/net/).
- Thiết lập cơ bản: Một tệp trình bày, chẳng hạn như "Test.pptx," trong thư mục làm việc của bạn.
- Môi trường phát triển: Visual Studio hoặc tương đương, được cấu hình cho .NET.

## Nhập không gian tên bắt buộc

Thêm các không gian tên cần thiết vào dự án của bạn để phát triển liền mạch:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Bước 1: Tạo biểu đồ trong bài thuyết trình của bạn

Bắt đầu bằng cách tạo biểu đồ mặc định trên trang chiếu đầu tiên của bài thuyết trình:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Điều này thêm một`LineWithMarkers` biểu đồ vào trang chiếu của bạn với các kích thước được chỉ định.

## Bước 2: Lấy chỉ mục bảng dữ liệu biểu đồ

Chỉ mục bảng tính dữ liệu biểu đồ mặc định rất cần thiết để tùy chỉnh thêm:

```csharp
int defaultWorksheetIndex = 0;
```

## Bước 3: Truy cập vào Sổ làm việc dữ liệu biểu đồ

Để thao tác dữ liệu biểu đồ, hãy lấy sổ làm việc liên quan:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Bước 4: Cấu hình Chuỗi biểu đồ và Thêm Điểm dữ liệu

Xóa chuỗi mặc định và thêm điểm dữ liệu mới cho chuỗi của bạn:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Thêm điểm dữ liệu vào chuỗi
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Bước 5: Áp dụng Tô hình ảnh vào Điểm đánh dấu dữ liệu

Hình ảnh tùy chỉnh có thể làm cho các điểm đánh dấu dữ liệu trở nên hấp dẫn về mặt thị giác:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Đặt hình ảnh tùy chỉnh cho các điểm đánh dấu
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Bước 6: Tùy chỉnh kích thước điểm đánh dấu

Thay đổi kích thước của điểm đánh dấu để tăng khả năng hiển thị:

```csharp
series.Marker.Size = 20;
```

## Bước 7: Lưu bản trình bày đã cập nhật

Lưu bản trình bày tùy chỉnh vào vị trí mong muốn của bạn:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Phần kết luận

Aspose.Slides for .NET trang bị cho các nhà phát triển các công cụ để tạo biểu đồ chuyên nghiệp với nhiều tùy chọn tùy chỉnh. Bằng cách tận dụng các tùy chọn đánh dấu biểu đồ, bạn có thể cải thiện đáng kể sức hấp dẫn trực quan và độ rõ nét của bài thuyết trình. Hướng dẫn từng bước này đảm bảo rằng ngay cả các tùy chỉnh phức tạp cũng dễ thực hiện.

## Câu hỏi thường gặp

### Tôi có thể sử dụng bất kỳ định dạng hình ảnh nào để tùy chỉnh điểm đánh dấu không?
Có, Aspose.Slides hỗ trợ nhiều định dạng hình ảnh, bao gồm JPEG, PNG và BMP để tùy chỉnh điểm đánh dấu.

### Làm thế nào để thay đổi loại biểu đồ sau khi tạo?
 Để thay đổi loại biểu đồ, hãy truy cập`chart.Type` tài sản và chỉ định một khác nhau`ChartType`.

### Aspose.Slides for .NET có tương thích với các phiên bản PowerPoint cũ hơn không?
Có, nó hỗ trợ khả năng tương thích ngược với các định dạng PowerPoint cũ hơn, đảm bảo tính linh hoạt.

### Tôi có thể cập nhật dữ liệu biểu đồ một cách động không?
 Hoàn toàn. Sử dụng`IChartDataWorkbook` để cập nhật dữ liệu biểu đồ theo chương trình.

### Tôi có thể tìm thêm tài nguyên ở đâu?
 Khám phá[Tài liệu Aspose.Slides](https://reference.aspose.com/slides/net/)hoặc tham gia[diễn đàn cộng đồng](https://forum.aspose.com/) để được hỗ trợ.