---
title: Aspose.Cells for .NET을 사용하여 Excel 통합 문서 내에서 데이터 복사
linktitle: Aspose.Cells for .NET을 사용하여 Excel 통합 문서 내에서 데이터 복사
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 Excel 통합 문서 내에서 데이터를 효율적으로 복사하는 방법을 알아보세요. 이 단계별 가이드를 따라 시트를 쉽게 복제하고, 데이터를 전송하고, Excel 파일을 쉽게 관리하세요.
type: docs
weight: 12
url: /ko/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## 소개

이 자세한 가이드에서는 Aspose.Cells for .NET을 사용하여 동일한 통합 문서 내에서 데이터를 복사하는 방법을 보여드립니다. 아래에 설명된 단계별 지침을 따르면 시트를 프로그래밍 방식으로 복제하고 내용과 서식을 유지하는 방법을 배울 수 있습니다.

## Aspose.Cells를 사용하여 Excel에서 데이터를 복사하기 위한 전제 조건

코딩 과정을 시작하기 전에 모든 것이 제대로 되어 있는지 확인해 보겠습니다.

1. Aspose.Cells for .NET 라이브러리: Aspose.Cells for .NET 라이브러리가 설치되어 있어야 합니다. 최신 버전은 다음에서 다운로드할 수 있습니다.[.NET용 Aspose.Cells 다운로드 페이지](https://releases.aspose.com/cells/net/).
2. 개발 환경: 코드를 작성하고 실행하려면 Visual Studio와 같은 .NET 호환 IDE가 필요합니다.
3.  Aspose 라이선스: 무료 평가판이나 구매한 라이선스를 사용할 수 있습니다. 자세한 내용은 다음을 방문하세요.[여기](https://purchase.aspose.com/temporary-license/).

필수 조건이 설정되면 라이브러리 작업을 시작할 준비가 된 것입니다.

## 필수 패키지 가져오기

시작하려면 Aspose.Cells에서 관련 네임스페이스를 가져와야 합니다. 이렇게 하면 Aspose.Cells에서 제공하는 클래스와 메서드를 사용하여 Excel 파일을 작업할 수 있습니다.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 이러한 네임스페이스를 사용하면 다음에 액세스할 수 있습니다.`Workbook` 클래스(Excel 파일 작업용) 및`WorksheetCollection` (통합 문서 내의 여러 시트에 액세스하기 위해).

## 1단계: 통합 문서의 파일 경로 초기화

코드를 정리하려면 통합 문서가 있는 파일 경로와 수정된 파일을 저장할 위치를 정의하는 것이 필수적입니다. 경로를 지정하는 방법은 다음과 같습니다.

```csharp
// Excel 파일이 있는 디렉토리 경로를 정의합니다.
string dataDir = "Your Directory Path";

// 입력 통합 문서의 전체 경로를 정의합니다.
string inputPath = dataDir + "book1.xls";
```

 바꾸다`"Your Directory Path"` 통합 문서가 들어 있는 디렉토리의 실제 경로와 함께. 이렇게 하면 코드가 유연하고 경로를 효과적으로 관리할 수 있습니다.

## 2단계: 통합 문서를 열어 데이터 액세스

 이제 파일 경로가 설정되었으므로 다음 단계는 Excel 통합 문서를 로드하는 것입니다.`Workbook` 객체. 이를 통해 조작을 위해 콘텐츠에 액세스할 수 있습니다.

```csharp
// Excel 파일을 Workbook 개체에 로드합니다.
Workbook wb = new Workbook(inputPath);
```

 이 줄을 사용하면 성공적으로 로드되었습니다.`book1.xls` 에`wb` 객체를 만들어 데이터에 접근할 수 있게 합니다.

## 3단계: 워크시트 컬렉션에 액세스

 통합 문서가 로드되면 통합 문서에 포함된 시트에 액세스할 수 있습니다. Aspose.Cells는 다음을 제공합니다.`Worksheets`통합 문서의 각 워크시트와 상호 작용할 수 있는 컬렉션입니다.

```csharp
// 통합 문서에서 워크시트 컬렉션을 검색합니다.
WorksheetCollection sheets = wb.Worksheets;
```

 그만큼`sheets` 이제 객체를 사용하면 해당 워크시트에 대한 모든 액세스 권한이 부여됩니다.`book1.xls`, 다양한 작업을 수행할 수 있습니다. 예를 들어 한 시트에서 다른 시트로 데이터를 복사하는 작업이 포함됩니다.

## 4단계: 한 시트에서 다른 시트로 데이터 복사

 동일한 통합 문서 내의 한 워크시트에서 다른 워크시트로 데이터를 복사하기 위해 Aspose.Cells는 다음과 같은 사용하기 쉬운 방법을 제공합니다.`AddCopy`. 이 방법은 지정된 워크시트의 복제본을 만들어 통합 문서에 추가합니다.

```csharp
// 통합 문서 내의 새 시트에 "Sheet1"의 데이터를 복사합니다.
sheets.AddCopy("Sheet1");
```

 이 예에서 우리는 "Sheet1"에서 새 시트로 데이터를 복사하고 있습니다.`AddCopy` 이 방법을 사용하면 수식, 서식, 값을 포함한 모든 내용을 보존하면서 전체 시트를 복제할 수 있습니다.

## 5단계: 수정된 통합 문서 저장

 데이터를 복사한 후 수정된 통합 문서를 새 이름이나 위치로 저장할 수 있습니다. 이는 다음을 호출하여 수행됩니다.`Save`방법에 대한`Workbook` 물체.

```csharp
//수정된 통합 문서를 새 이름으로 저장합니다.
wb.Save(dataDir + "book1_copy.xls");
```

 이렇게 하면 복사된 시트가 있는 통합 문서가 저장됩니다.`book1_copy.xls` 지정된 디렉토리에 있습니다. 필요에 따라 파일 이름과 경로를 변경할 수 있습니다.

## 결론

Aspose.Cells for .NET을 사용하여 Excel 통합 문서 내에서 데이터를 복사하는 것은 쉬운 작업이며, 이 가이드는 효율적으로 수행하는 데 필요한 단계를 제공합니다. 전체 시트를 복제하든 특정 데이터 범위를 복제하든 Aspose.Cells는 Excel 자동화를 간단하고 효과적으로 만드는 강력하고 유연한 API를 제공합니다.

## 자주 묻는 질문

### 한 번에 여러 장을 복사할 수 있나요?

Aspose.Cells는 단일 호출에서 여러 시트를 복사하는 것을 지원하지 않습니다. 그러나 복사하려는 시트를 반복하여 개별적으로 복사할 수 있습니다.

### 복사한 시트의 이름을 바꾸려면 어떻게 해야 하나요?

시트를 복사한 후 다음과 같이 이름을 바꿀 수 있습니다.

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Aspose.Cells는 .NET Core와 호환됩니까?

네, Aspose.Cells는 .NET Framework와 .NET Core 환경 모두와 완벽하게 호환됩니다.

### Aspose.Cells는 복사하는 동안 서식을 어떻게 처리하나요?

 그만큼`AddCopy`이 방법을 사용하면 시트를 복사할 때 모든 내용과 서식이 보존되므로 복사된 데이터가 원본과 동일하게 표시됩니다.

### 시트를 다른 통합 문서에 복사할 수 있나요?

 예, 다음을 사용하여 시트를 다른 통합 문서로 복사할 수 있습니다.`Copy` 대상 통합 문서를 참조하는 메서드.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```