---
title: Chuyển biểu mẫu người dùng VBA và macro giữa các sổ làm việc Excel
linktitle: Chuyển biểu mẫu người dùng VBA và macro giữa các sổ làm việc Excel
second_title: API xử lý Excel Aspose.Cells .NET
description: Mở khóa sức mạnh của tự động hóa Excel với hướng dẫn toàn diện này về cách chuyển Biểu mẫu người dùng VBA và macro giữa các sổ làm việc bằng Aspose.Cells cho .NET. Hoàn hảo cho cả người mới bắt đầu và nhà phát triển có kinh nghiệm.
type: docs
weight: 11
url: /vi/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Giới thiệu

Chào mừng bạn đến với hướng dẫn tối ưu để nâng cao trải nghiệm Excel của bạn bằng cách sử dụng macro VBA và biểu mẫu người dùng! Trong hướng dẫn này, chúng ta sẽ khám phá cách chuyển Macro VBA UserForm Designer từ sổ làm việc này sang sổ làm việc khác bằng cách sử dụng thư viện Aspose.Cells for .NET mạnh mẽ. Cho dù bạn là nhà phát triển có kinh nghiệm hay mới bắt đầu, hướng dẫn từng bước này sẽ trang bị cho bạn kiến thức để xử lý các tệp Excel theo chương trình. Sẵn sàng để bắt đầu chưa? Hãy bắt đầu thôi!

## Điều kiện tiên quyết
Trước khi bắt đầu viết mã, hãy đảm bảo bạn có mọi thứ cần thiết:

1. Môi trường phát triển C#: Môi trường làm việc để phát triển C#, trong đó Visual Studio được khuyến khích sử dụng.
2.  Aspose.Cells cho Thư viện .NET: Đảm bảo tích hợp thư viện Aspose.Cells vào dự án của bạn. Bạn có thể dễ dàng[tải xuống ở đây](https://releases.aspose.com/cells/net/).
3. Kiến thức cơ bản về VBA và Macro Excel: Sự quen thuộc với VBA và cách thức hoạt động của macro Excel sẽ giúp bạn hiểu rõ hơn về hướng dẫn này.
4. Tệp Excel có Biểu mẫu Người dùng: Tạo hoặc lấy sổ làm việc Excel có chứa Biểu mẫu Người dùng (tốt nhất là có bật macro, như`.xlsm` tập tin).

## Nhập các gói cần thiết
Để sử dụng các chức năng do Aspose.Cells cung cấp, hãy thêm các không gian tên sau vào đầu tệp C# của bạn:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Các không gian tên này sẽ cung cấp cho bạn quyền truy cập vào các công cụ mạnh mẽ được nhúng trong thư viện Aspose.Cells.

## Bước 1: Xác định thư mục nguồn và thư mục đầu ra của bạn
Đầu tiên, hãy xác định vị trí lưu trữ các tập tin của bạn:

```csharp
// Xác định thư mục nguồn và thư mục đầu ra
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Thay thế đường dẫn giữ chỗ bằng các thư mục thực tế nơi lưu trữ tệp của bạn.

## Bước 2: Tạo một Workbook mục tiêu trống
Tiếp theo, tạo một bảng tính mới nơi bạn sẽ sao chép biểu mẫu người dùng và macro:

```csharp
// Tạo một bảng tính mục tiêu trống
Workbook target = new Workbook();
```

Thao tác này sẽ khởi tạo một bảng tính trống, đóng vai trò như nền tảng cho quá trình truyền dữ liệu sắp tới.

## Bước 3: Tải Sổ làm việc mẫu của bạn
Tải sổ làm việc chứa biểu mẫu người dùng và macro của bạn:

```csharp
// Tải tệp Excel có chứa VBA-Macro Designer User Form
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Điều chỉnh`"sampleDesignerForm.xlsm"` vào tên tập tin thực tế của bạn.

## Bước 4: Sao chép các trang tính vào Sổ làm việc đích
Bây giờ, hãy sao chép các bảng tính từ mẫu sang bảng tính đích:

```csharp
// Sao chép tất cả các bảng tính mẫu vào bảng tính đích
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Thêm một thông báo vào ô A2 của bảng tính mục tiêu
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Mã này lặp qua từng bảng tính trong mẫu và sao chép vào bảng tính đích, đảm bảo mọi dữ liệu của bạn được truyền tải liền mạch.

## Bước 5: Sao chép Macro VBA từ Mẫu
Tiếp theo, chúng ta sẽ sao chép các macro VBA, bao gồm các mô-đun UserForm Designer, vào bảng tính mới:

```csharp
// Sao chép VBA-Macro Designer UserForm từ Mẫu đến Mục tiêu
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Sao chép mã mô-đun Workbook này
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Sao chép mã và dữ liệu của các mô-đun khác
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Nhận bộ lưu trữ thiết kế biểu mẫu người dùng
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Thêm bộ lưu trữ thiết kế vào Dự án Vba mục tiêu
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Mã này đảm bảo rằng không chỉ mã mà cả thiết kế biểu mẫu người dùng đều được sao chép, giúp duy trì chức năng của macro.

## Bước 6: Lưu Workbook mục tiêu
Sau khi hoàn tất quá trình sao chép, hãy lưu bảng tính mới của bạn:

```csharp
// Lưu sổ làm việc mục tiêu
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Sửa đổi tên tệp đầu ra nếu cần. Bước này tạo sổ làm việc tùy chỉnh của bạn chứa đầy macro và biểu mẫu người dùng.

## Bước 7: Xác nhận thành công
Cuối cùng, in thông báo thành công ra bảng điều khiển:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Dòng đơn giản này đảm bảo với bạn rằng quá trình của bạn diễn ra suôn sẻ—một sự xác nhận thiết yếu cho sự chăm chỉ của bạn!

## Phần kết luận
Xin chúc mừng! Bạn đã học thành công cách sao chép VBA Macro User Form Designer từ sổ làm việc này sang sổ làm việc khác bằng Aspose.Cells for .NET. Mặc dù thoạt đầu có vẻ khó khăn, nhưng thực hành sẽ giúp bạn thành thạo trong việc thao tác sổ làm việc. Hãy nhớ rằng, mã hóa là về thử nghiệm, vì vậy đừng ngần ngại khám phá các chức năng khác nhau trong các tệp Excel của bạn. Nếu bạn có bất kỳ câu hỏi nào hoặc cần trợ giúp, diễn đàn và tài liệu Aspose là những nguồn hỗ trợ tuyệt vời.

## Câu hỏi thường gặp

### Aspose.Cells hỗ trợ những phiên bản Excel nào?
Aspose.Cells hỗ trợ nhiều định dạng Excel, bao gồm XLSX, XLSM, CSV, v.v.

### Tôi có thể sử dụng Aspose.Cells miễn phí không?
 Có! Bạn có thể bắt đầu dùng thử miễn phí để đánh giá thư viện:[Dùng thử miễn phí](https://releases.aspose.com/).

### Tôi có cần Visual Studio để chạy mã này không?
Mặc dù Visual Studio được khuyến khích sử dụng vì các tính năng thân thiện với người dùng, nhưng bất kỳ IDE C# nào hỗ trợ phát triển .NET đều có thể dùng được.

### Tôi có thể tìm thêm ví dụ và tài liệu ở đâu?
 Bạn có thể khám phá[Tài liệu Aspose.Cells](https://reference.aspose.com/cells/net/) để biết thêm ví dụ và giải thích chi tiết.

### Làm thế nào để giải quyết vấn đề khi sử dụng Aspose.Cells?
 Bạn nên ghé thăm[Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/cells/9) để được cộng đồng và đội ngũ hỗ trợ của Aspose giúp đỡ.