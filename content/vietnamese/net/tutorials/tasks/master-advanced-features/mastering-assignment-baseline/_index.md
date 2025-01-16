---
title: Làm chủ các đường cơ sở bài tập với Aspose.Tasks cho .NET
linktitle: Quản lý đường cơ sở nhiệm vụ trong Aspose.Tasks
second_title: API Aspose.Tasks .NET
description: Tìm hiểu cách quản lý đường cơ sở phân công hiệu quả bằng Aspose.Tasks cho .NET. Hướng dẫn từng bước này bao gồm tải dự án, thiết lập đường cơ sở, truy xuất dữ liệu, so sánh đường cơ sở và nhiều hơn nữa để tối ưu hóa quy trình quản lý dự án.
type: docs
weight: 14
url: /vi/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## Giới thiệu

Quản lý dự án hiệu quả phụ thuộc vào việc theo dõi và quản lý chính xác các đường cơ sở phân công. Với Aspose.Tasks for .NET, bạn có được một bộ công cụ mạnh mẽ để hợp lý hóa việc xử lý các đường cơ sở phân công để có cái nhìn sâu sắc hơn về dự án. Trong bài viết này, chúng tôi sẽ hướng dẫn bạn quy trình quản lý các đường cơ sở phân công, đảm bảo các dự án của bạn vẫn đi đúng hướng.

## Điều kiện tiên quyết

Trước khi bắt đầu triển khai, hãy đảm bảo bạn có những điều sau:

- Kinh nghiệm lập trình: Có kiến thức cơ bản về C#.
- Môi trường phát triển: Cài đặt và cấu hình Visual Studio.
-  Aspose.Tasks cho Thư viện .NET: Tải xuống từ[Aspose.Tasks phát hành](https://releases.aspose.com/tasks/net/).
- Tệp dự án: Truy cập vào tệp dự án ở định dạng MPP.

## Nhập không gian tên bắt buộc

Để sử dụng chức năng của Aspose.Tasks, hãy bao gồm các không gian tên sau vào tệp dự án của bạn:

```csharp
using Aspose.Tasks;
using System;
```

## Bước 1: Tải một dự án và thiết lập đường cơ sở

Tải một dự án và thiết lập đường cơ sở là nền tảng để quản lý đường cơ sở phân công. Mã sau đây minh họa cách tải một dự án và thiết lập đường cơ sở của nó.

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// Thiết lập đường cơ sở của dự án
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## Bước 2: Lấy dữ liệu cơ sở của bài tập

Bạn có thể trích xuất thông tin cơ sở chi tiết cho từng nhiệm vụ tài nguyên. Sau đây là cách thực hiện:

```csharp
foreach (var assignment in project.ResourceAssignments)
{
    foreach (var baseline in assignment.Baselines)
    {
        Console.WriteLine("Baseline Start: " + baseline.Start);
        Console.WriteLine("Baseline Finish: " + baseline.Finish);
        Console.WriteLine("Baseline Cost: " + baseline.Cost);
        Console.WriteLine("Baseline Work: " + baseline.Work);
    }
}
```

## Bước 3: So sánh các đường cơ sở giữa các nhiệm vụ

Aspose.Tasks cho phép bạn so sánh các đường cơ sở theo chương trình để đánh giá sự khác biệt giữa các phân công tài nguyên.

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## Bước 4: Sửa đổi Chi tiết Đường cơ sở theo Chương trình

Bạn có thể lập trình để sửa đổi dữ liệu cơ sở để đáp ứng nhu cầu phát triển của dự án:

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // Điều chỉnh chi phí cơ sở
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // Thêm giờ làm việc

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## Phần kết luận

Quản lý đường cơ sở phân công hiệu quả là một phần không thể thiếu để duy trì quyền kiểm soát đối với lịch trình và ngân sách của dự án. Aspose.Tasks for .NET trang bị cho bạn các công cụ cần thiết để xử lý đường cơ sở một cách chính xác, cho phép đưa ra quyết định dựa trên dữ liệu.

## Câu hỏi thường gặp

### Aspose.Tasks có thể xử lý nhiều đường cơ sở cho một dự án không?  
Có, Aspose.Tasks hỗ trợ nhiều đường cơ sở, mang lại sự linh hoạt trong việc theo dõi nhiều phiên bản dự án khác nhau.

### Aspose.Tasks có tương thích với các tệp dự án không phải MPP không?  
Hoàn toàn đúng. Aspose.Tasks hỗ trợ các định dạng như XML, MPX, v.v.

### Tôi có thể tự động cập nhật cơ sở không?  
Có, API cho phép sửa đổi đường cơ sở tự động và động theo chương trình.

### Aspose.Tasks có cung cấp dữ liệu cơ sở theo giai đoạn thời gian không?  
Có, dữ liệu cơ sở theo từng giai đoạn thời gian chi tiết có thể được truy xuất và phân tích.

### Tôi có thể truy cập hỗ trợ và tài liệu ở đâu?  
 Thăm nom[Tài liệu Aspose.Tasks](https://reference.aspose.com/words/net/)hoặc tham gia[Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/words/8) để được hỗ trợ. 