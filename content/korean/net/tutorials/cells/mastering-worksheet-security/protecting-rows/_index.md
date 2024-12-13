---
title: Aspose.Cells를 사용하여 워크시트의 행 보호
linktitle: Aspose.Cells를 사용하여 워크시트의 행 보호
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 특정 행을 보호하여 Excel 워크시트에서 민감한 정보를 보호하는 방법을 알아보세요. 이 포괄적인 튜토리얼은 환경 설정부터 모든 것을 다룹니다.
type: docs
weight: 18
url: /ko/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## 소개

Excel 파일을 프로그래밍 방식으로 작업하려면 데이터 조작뿐만 아니라 데이터 보호도 필요한 경우가 많습니다. 워크시트의 특정 행을 보호하는 것은 민감한 정보를 보호하거나 실수로 편집하는 것을 방지하는 데 중요할 수 있습니다. 이 튜토리얼에서는 Aspose.Cells for .NET을 사용하여 Excel 워크시트의 행을 보호하는 방법을 살펴보겠습니다. 환경을 설정하는 것부터 행 보호 기능을 간단한 방식으로 구현하는 것까지 필요한 단계를 안내해 드리겠습니다.

## 필수 조건
시작하기 전에 다음 사항이 준비되었는지 확인하세요.

1.  .NET용 Aspose.Cells: 여기에서 다운로드하여 설치하세요.[Aspose Cells 다운로드 페이지](https://releases.aspose.com/cells/net/).
2. Visual Studio 또는 .NET IDE: 개발 환경이 필요합니다. Visual Studio가 권장되지만 .NET 호환 IDE라면 무엇이든 충분합니다.
3. 기본 C# 지식: C# 프로그래밍에 익숙하면 예제 코드를 따라가고 필요에 따라 수정하는 데 도움이 됩니다.
4.  Aspose.Cells API 문서: 검토[.NET용 Aspose.Cells 설명서](https://reference.aspose.com/cells/net/) 클래스 구조와 메서드에 대한 개요는 다음과 같습니다.

필수 구성 요소가 준비되면 구현으로 넘어갈 수 있습니다.

## 필요한 패키지 가져오기
C# 프로젝트에서 필요한 패키지를 가져오는 것으로 시작합니다. 이러한 라이브러리는 Excel 파일과 상호 작용하는 데 필수적입니다.

```csharp
using System.IO;
using Aspose.Cells;
```

## 1단계: 새 통합 문서 및 워크시트 만들기
보호 설정을 적용하기 전에 새 통합 문서를 만들고 작업할 워크시트를 선택합니다.

```csharp
// 문서 디렉토리의 경로를 정의합니다.
string dataDir = "Your Document Directory";
// 디렉토리가 없으면 만듭니다.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// 새 통합 문서를 만들고 첫 번째 워크시트를 선택합니다.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## 2단계: Style 및 StyleFlag 객체 정의
셀 속성(예: 잠금 또는 잠금 해제)을 수정할 수 있는 스타일 및 스타일 플래그 개체를 정의합니다.

```csharp
// 스타일과 스타일 플래그 객체를 정의합니다.
Style style;
StyleFlag flag;
```

## 3단계: 워크시트의 모든 열 잠금 해제
기본적으로 Excel 워크시트의 모든 셀은 잠겨 있습니다. 특정 행만 보호하려면 먼저 모든 열을 잠금 해제합니다.

```csharp
// 모든 열을 반복하여 잠금을 해제합니다.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## 4단계: 특정 행 잠금
이제 보호하려는 행을 잠급니다. 이 예에서는 첫 번째 행을 잠급니다.

```csharp
// 첫 번째 행을 잠급니다.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

잠그려는 추가 행에 대해 이 단계를 반복할 수 있습니다.

## 5단계: 시트 보호
필요한 행이 잠기면 워크시트를 보호할 차례입니다. 이렇게 하면 보호가 해제되지 않는 한 잠긴 행을 수정할 수 없습니다.

```csharp
// 시트를 보호하세요.
sheet.Protect(ProtectionType.All);
```

## 6단계: 통합 문서 저장
마지막으로, 적용된 변경 사항으로 통합 문서를 저장합니다. Excel 97-2003 또는 최신 버전과 같은 다양한 형식 중에서 선택할 수 있습니다.

```csharp
// Excel 파일을 저장합니다.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## 결론
축하합니다! Aspose.Cells for .NET을 사용하여 Excel 워크시트에서 행을 보호하는 방법을 성공적으로 배웠습니다. 이러한 단계를 따르면 필요에 따라 행이나 열을 잠금 해제하거나 잠그고 보호를 적용하여 데이터 무결성을 유지할 수 있습니다.

## 자주 묻는 질문
### 한 번에 여러 행을 보호하려면 어떻게 해야 하나요?
여러 행 인덱스를 반복하고 각 인덱스에 잠금 스타일을 개별적으로 적용할 수 있습니다.

### 시트 보호에 비밀번호를 설정할 수 있나요?
 네, 비밀번호를 전달할 수 있습니다.`sheet.Protect()` 비밀번호 보호를 강제하는 방법입니다.

### 전체 열 대신 특정 셀만 잠금 해제할 수 있나요?
네, 열 전체의 잠금을 해제하는 대신, 스타일 속성을 수정하여 개별 셀의 잠금을 해제할 수 있습니다.

### 보호된 행을 편집하려고 하면 어떻게 되나요?
행이 보호되면 Excel에서는 시트가 보호 해제되지 않는 한 잠긴 셀을 편집할 수 없습니다.

### 행 내의 특정 범위를 보호할 수 있나요?
 네! 개별 범위를 행으로 잠글 수 있습니다.`IsLocked` 해당 범위 내의 특정 셀에 대한 속성입니다.