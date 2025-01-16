---
title: Tùy chỉnh biểu đồ nâng cao với Aspose.Slides cho .NET
linktitle: Tùy chỉnh biểu đồ nâng cao với Aspose.Slides cho .NET
second_title: API xử lý PowerPoint Aspose.Slides .NET
description: Mở khóa toàn bộ tiềm năng của Aspose.Slides cho .NET bằng cách thành thạo các kỹ thuật tùy chỉnh biểu đồ nâng cao. Hướng dẫn từng bước này bao gồm mọi thứ từ việc tạo biểu đồ cơ bản đến các chi tiết phức tạp như đường lưới, tiêu đề trục và màu tùy chỉnh.
type: docs
weight: 10
url: /vi/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Giới thiệu

Việc tạo biểu đồ hấp dẫn và nhiều thông tin là rất quan trọng để trình bày dữ liệu hiệu quả. Aspose.Slides for .NET cung cấp các công cụ mạnh mẽ để tùy chỉnh biểu đồ, cho phép bạn tùy chỉnh mọi khía cạnh của biểu đồ. Trong hướng dẫn này, chúng ta sẽ khám phá các kỹ thuật nâng cao để tùy chỉnh biểu đồ bằng Aspose.Slides for .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đáp ứng các điều kiện tiên quyết sau:

1.  Aspose.Slides cho Thư viện .NET: Tải xuống và cài đặt thư viện Aspose.Slides từ[đây](https://releases.aspose.com/slides/net/).
2. Môi trường phát triển .NET: Thiết lập môi trường phát triển .NET, chẳng hạn như Visual Studio.
3. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ có lợi vì chúng ta sẽ viết mã C#.

Bây giờ, chúng ta hãy chia nhỏ quy trình tùy chỉnh biểu đồ nâng cao thành các bước rõ ràng.

## Bước 1: Tạo một bài thuyết trình mới

Bắt đầu bằng cách tạo một bản trình bày mới để lưu biểu đồ của bạn.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "Your Document Directory";

// Tạo thư mục nếu nó không tồn tại.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Khởi tạo bài thuyết trình
Presentation pres = new Presentation();
```

## Bước 2: Truy cập vào Slide đầu tiên

Tiếp theo, hãy truy cập vào trang chiếu đầu tiên mà bạn muốn thêm biểu đồ.

```csharp
// Truy cập trang chiếu đầu tiên
ISlide slide = pres.Slides[0];
```

## Bước 3: Thêm biểu đồ mẫu

Bây giờ, chúng ta hãy thêm biểu đồ đường có đánh dấu vào trang chiếu.

```csharp
// Thêm một biểu đồ mẫu
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Bước 4: Đặt tiêu đề biểu đồ

Đặt tiêu đề cho biểu đồ sẽ cung cấp bối cảnh cần thiết.

```csharp
// Đặt tiêu đề biểu đồ
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Bước 5: Tùy chỉnh các đường lưới chính

Bạn có thể tăng cường các đường lưới cho trục giá trị để dễ đọc hơn.

```csharp
// Tùy chỉnh các đường lưới chính cho trục giá trị
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Bước 6: Tùy chỉnh các đường lưới nhỏ

Tương tự như vậy, tùy chỉnh các đường lưới nhỏ cho trục giá trị.

```csharp
// Tùy chỉnh các đường lưới nhỏ cho trục giá trị
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Bước 7: Xác định Định dạng Số Trục Giá trị

Bạn có thể định dạng các số hiển thị trên trục giá trị.

```csharp
// Đặt định dạng số trục giá trị
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Bước 8: Đặt giá trị tối đa và tối thiểu

Xác định giá trị tối đa và tối thiểu cho biểu đồ.

```csharp
// Đặt giá trị biểu đồ tối đa và tối thiểu
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Bước 9: Tùy chỉnh Thuộc tính Văn bản Trục Giá trị

Việc cải thiện các thuộc tính văn bản của trục giá trị sẽ cải thiện khả năng đọc.

```csharp
// Tùy chỉnh Thuộc tính Văn bản Trục Giá trị
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Bước 10: Thêm Tiêu đề Trục Giá trị

Việc thêm tiêu đề vào trục giá trị có thể làm rõ dữ liệu thể hiện nội dung gì.

```csharp
// Đặt tiêu đề trục giá trị
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Bước 11: Tùy chỉnh các Đường lưới chính cho Trục danh mục

Bây giờ, chúng ta hãy cải thiện các đường lưới chính cho trục danh mục.

```csharp
// Tùy chỉnh các Đường lưới chính cho trục Danh mục
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Bước 12: Tùy chỉnh các đường lưới phụ cho trục danh mục

Tương tự như vậy, tùy chỉnh các đường lưới nhỏ cho trục danh mục.

```csharp
// Tùy chỉnh các Đường lưới nhỏ cho trục Danh mục
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Bước 13: Tùy chỉnh Thuộc tính Văn bản Trục Danh mục

Cải thiện kiểu phông chữ và giao diện của nhãn trục danh mục.

```csharp
// Tùy chỉnh Thuộc tính Văn bản Trục Danh mục
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Bước 14: Thêm Tiêu đề Trục Danh mục

Nếu cần, bạn cũng có thể thêm tiêu đề cho trục danh mục.

```csharp
// Đặt Tiêu đề Trục Danh mục
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Bước 15: Tùy chỉnh bổ sung

Cải thiện biểu đồ của bạn hơn nữa bằng các tùy chỉnh bổ sung, chẳng hạn như chú thích, màu tường và cài đặt vùng biểu đồ.

```csharp
// Tùy chỉnh bổ sung (Tùy chọn)

// Tùy chỉnh Thuộc tính Văn bản Huyền thoại
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Hiển thị chú giải biểu đồ mà không chồng chéo biểu đồ
chart.Legend.Overlay = true;

// Thiết lập biểu đồ màu tường phía sau
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Đặt biểu đồ màu sàn
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Đặt màu vùng vẽ
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Lưu bài thuyết trình
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Phần kết luận

Trong hướng dẫn toàn diện này, chúng tôi đã đề cập đến các kỹ thuật tùy chỉnh biểu đồ nâng cao bằng Aspose.Slides cho .NET. Bạn đã học cách tạo bản trình bày, thêm biểu đồ, tinh chỉnh giao diện và tùy chỉnh nhiều thành phần biểu đồ khác nhau như đường lưới, nhãn trục và chú giải. 

## Câu hỏi thường gặp

### Aspose.Slides hỗ trợ những phiên bản .NET nào cho .NET?
Aspose.Slides for .NET hỗ trợ nhiều phiên bản .NET khác nhau, bao gồm .NET Framework và .NET Core. Tham khảo tài liệu để biết danh sách đầy đủ các phiên bản được hỗ trợ.

### Tôi có thể tạo biểu đồ từ nguồn dữ liệu như tệp Excel không?
Có, Aspose.Slides cho phép bạn tạo biểu đồ từ các nguồn dữ liệu bên ngoài như bảng tính Excel. Tham khảo tài liệu để biết ví dụ chi tiết.

### Làm thế nào để tôi có thể thêm nhãn dữ liệu tùy chỉnh vào chuỗi biểu đồ của mình?
 Để thêm nhãn dữ liệu tùy chỉnh, hãy truy cập`DataLabels` thuộc tính của chuỗi và tùy chỉnh nhãn khi cần. Bạn có thể tìm thấy các mẫu mã trong tài liệu.

### Có thể xuất biểu đồ sang các định dạng khác nhau như PDF hoặc hình ảnh không?
Chắc chắn rồi! Aspose.Slides cho phép bạn xuất bản bài thuyết trình có biểu đồ sang nhiều định dạng khác nhau, bao gồm định dạng PDF và hình ảnh.

### Tôi có thể tìm thêm hướng dẫn và ví dụ về Aspose.Slides cho .NET ở đâu?
 Truy cập Aspose.Slides[trang web](https://reference.aspose.com/slides/net/) để có hướng dẫn chi tiết, ví dụ mã và tài liệu.