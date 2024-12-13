---
title: Excel 파일에서 PDF에 지정된 목적지가 있는 북마크 추가
linktitle: Excel 파일에서 PDF에 지정된 목적지가 있는 북마크 추가
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 Excel 파일에서 대화형 PDF를 쉽게 만드는 방법을 알아보세요. 이 튜토리얼에서는 PDF 탐색을 향상시키기 위해 명명된 대상을 사용하여 북마크를 추가하는 방법을 다룹니다.
type: docs
weight: 10
url: /ko/net/tutorials/cells/mastering-rendering-and-exporting/add-bookmarks-with-named-destinations/
---
## 소개

큰 PDF 파일을 탐색하는 것은 종종 건초더미에서 바늘을 찾는 것과 같을 수 있습니다. 특히 방대한 Excel 스프레드시트에서 생성된 경우 더욱 그렇습니다. PDF 문서의 북마크는 파일의 관련 섹션 사이를 원활하게 이동할 수 있는 방법을 제공하여 사용자 경험을 향상시킵니다. 이 자세한 가이드에서는 Aspose.Cells for .NET을 사용하여 Excel 파일에서 생성된 PDF에 명명된 대상을 가진 북마크를 추가하는 과정을 안내합니다.

## .NET용 Aspose.Cells 작업을 위한 전제 조건

코드에 들어가기 전에 성공적인 구현을 위한 모든 도구가 설정되어 있는지 확인하는 것이 필수적입니다. 전제 조건은 다음과 같습니다.

1. Visual Studio: .NET 개발을 위한 권장 IDE입니다. 시스템에 설치되고 올바르게 구성되었는지 확인하세요.
2.  .NET용 Aspose.Cells: Excel 파일을 프로그래밍 방식으로 조작하는 데 필요한 핵심 라이브러리입니다.[여기서 다운로드하세요](https://releases.aspose.com/cells/net/) Aspose를 처음 사용하는 경우 다음부터 시작할 수 있습니다.[무료 체험](https://releases.aspose.com/).
3. .NET Framework: 호환되는 버전의 .NET Framework를 사용하고 있는지 확인하세요. Aspose.Cells는 여러 버전을 지원합니다.
4. 기본 C# 지식: C#에 대한 기본적인 이해는 코드를 따라가는 데 도움이 됩니다.

이러한 구성 요소가 준비되면 북마크가 포함된 PDF 문서를 만들 준비가 되었습니다!

## 프로젝트 설정

개발 환경이 준비되면 Visual Studio에서 새 C# 프로젝트를 만들 수 있습니다. Aspose.Cells 기능을 사용하려면 필요한 네임스페이스를 가져와야 합니다.

## 필요한 네임스페이스 가져오기

C# 파일의 맨 위에 다음을 추가하세요.`using` 프로젝트에서 .NET용 Aspose.Cells에 액세스할 수 있도록 하는 명령문:

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

이러한 네임스페이스는 Excel 데이터를 조작하고 PDF로 변환하는 데 도움이 되는 필수 클래스에 대한 액세스를 제공합니다.

## 1단계: 입력 및 출력 파일을 위한 디렉토리 설정

첫 번째 단계는 입력 및 출력 파일 디렉토리를 정의하는 것입니다. 이렇게 하면 원본 Excel 파일과 결과 PDF 파일이 제대로 배치됩니다.

```csharp
string sourceDir = "Your Document Directory";  // Excel 파일에 대한 경로
string outputDir = "Your Document Directory"; // 출력 PDF가 저장될 경로
```

이는 프로젝트를 시작하기 전에 작업 공간을 구성하는 것과 비슷합니다.

## 2단계: Excel 통합 문서 로드

 다음 단계는 소스 Excel 파일을 로드하는 것입니다. Aspose.Cells를 사용하면 Excel 파일을 쉽게 로드할 수 있습니다.`Workbook` 시트, 셀, 콘텐츠 모두에 대한 액세스를 제공하는 객체입니다.

```csharp
Workbook wb = new Workbook(sourceDir + "sampleExcelFile.xlsx");
```

이렇게 하면 통합 문서가 열리고 조작을 준비합니다. 이제 데이터를 추출하고 PDF에 맞게 서식을 지정할 수 있습니다.

## 3단계: 워크시트 액세스

이제 통합 문서가 로드되었으므로 북마크에 대한 관련 셀이 있는 워크시트에 액세스할 차례입니다. 이 예에서는 첫 번째 워크시트로 작업합니다.

```csharp
Worksheet ws = wb.Worksheets[0]; // 첫 번째 워크시트에 접근하기
```

이 단계에서는 북마크의 캔버스를 설정합니다. 북마크를 위해 참조할 각 셀은 이 워크시트에서 가져옵니다.

## 4단계: 목적지가 지정된 북마크 만들기

이 시점에서 북마크를 만들기 시작할 수 있습니다. 북마크는 본질적으로 문서의 특정 영역에 대한 빠른 액세스를 제공하는 링크입니다. 이 예에서 우리는 셀 "C5"에 대한 북마크를 만들 것입니다.

### 단일 셀에 대한 북마크 만들기

 북마크를 만들려면 먼저 연결하려는 셀에 액세스해야 합니다. 그런 다음 북마크를 만듭니다.`PdfBookmarkEntry` 그것을 세포의 위치와 연관시킵니다.

```csharp
Cell cell = ws.Cells["C5"];
PdfBookmarkEntry bookmarkEntry = new PdfBookmarkEntry();
bookmarkEntry.Text = "Bookmark for C5"; // 북마크에 대한 텍스트
bookmarkEntry.Destination = cell;  // 북마크를 셀에 연결하기
bookmarkEntry.DestinationName = "AsposeCells--" + cell.Name; // 고유한 목적지 이름
```

이것을 한 번의 클릭으로 돌아갈 수 있는 문서의 지점을 표시하는 것으로 생각하세요. 책갈피에 모든 텍스트를 할당하고(예: "C5에 대한 책갈피") 특정 셀에 연결할 수 있습니다.

### 향상된 탐색을 위한 하위 북마크 추가

메인 북마크에서 분기되는 하위 북마크를 추가하여 사용자 경험을 향상시킬 수 있습니다. 이러한 하위 북마크는 같은 워크시트 내의 다른 영역이나 다른 시트를 가리킬 수 있습니다.

```csharp
cell = ws.Cells["G56"];
PdfBookmarkEntry subbookmarkEntry1 = new PdfBookmarkEntry();
subbookmarkEntry1.Text = "Sub-Bookmark 1"; // 첫 번째 하위 북마크에 대한 텍스트
subbookmarkEntry1.Destination = cell;
subbookmarkEntry1.DestinationName = "AsposeCells--" + cell.Name;

cell = ws.Cells["L4"];
PdfBookmarkEntry subbookmarkEntry2 = new PdfBookmarkEntry();
subbookmarkEntry2.Text = "Sub-Bookmark 2"; // 두 번째 하위 북마크에 대한 텍스트
subbookmarkEntry2.Destination = cell;
subbookmarkEntry2.DestinationName = "AsposeCells--" + cell.Name;
```

이러한 하위 책갈피는 책의 장과 마찬가지로 문서 탐색을 위한 추가 안내 표지판 역할을 합니다.

### 주요 북마크 아래에 하위 북마크 그룹화

계층적 구조를 만들려면 이러한 하위 북마크를 기본 북마크 아래에 추가할 수 있습니다. 이렇게 하면 사용자가 다른 섹션으로 이동하기가 더 쉬워집니다.

```csharp
ArrayList list = new ArrayList();
list.Add(subbookmarkEntry1);
list.Add(subbookmarkEntry2);
bookmarkEntry.SubEntry = list; // 메인 북마크에 하위 북마크 추가
```

이렇게 하면 각 책갈피가 여러 개의 하위 책갈피를 가질 수 있는 트리 구조가 생성됩니다.

## 5단계: 북마크를 사용하여 PDF 저장

### PDF 저장 옵션 설정

 문서를 PDF로 저장하기 전에 저장 옵션을 지정하고 북마크가 포함되어 있는지 확인해야 합니다. 다음을 사용합니다.`PdfSaveOptions` 이러한 목적을 위해서.

```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = bookmarkEntry;  // PDF에 북마크 지정
```

이렇게 하면 Aspose.Cells에 방금 만든 북마크를 포함하는 PDF를 생성하게 됩니다.

### 문서 저장

이제 책갈피가 설정되었으므로 통합 문서를 PDF로 저장할 수 있습니다.

```csharp
wb.Save(outputDir + "outputWithBookmarks.pdf", opts);
```

이렇게 하면 클릭 가능한 책갈피가 포함된 최종 PDF가 생성되어 사용자가 문서의 특정 섹션으로 빠르게 이동할 수 있습니다.

## 결론

이러한 간단한 단계를 따르면 Aspose.Cells for .NET을 사용하여 Excel 파일에서 북마크와 명명된 목적지가 있는 PDF를 성공적으로 만들 수 있습니다. 북마크를 추가하는 기능은 사용자 경험을 향상시킬 뿐만 아니라 큰 문서 내에서 탐색을 훨씬 더 효율적으로 만듭니다. 보고서, 가이드 또는 프레젠테이션을 작업하든 주요 섹션을 북마크하면 독자가 문서를 최대한 활용하는 데 도움이 됩니다.

## 자주 묻는 질문

### .NET용 Aspose.Cells란 무엇인가요?
Aspose.Cells for .NET은 Excel 파일을 작업하기 위한 강력한 API로, Excel 문서를 프로그래밍 방식으로 만들고, 편집하고, 변환할 수 있습니다. 이 도구로 데이터, 차트, 서식을 쉽게 조작할 수 있습니다.

### Aspose.Cells for .NET의 무료 평가판을 어떻게 받을 수 있나요?
 Aspose.Cells for .NET의 무료 평가판 버전을 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Cells는 어떤 파일 형식과 호환되나요?
Aspose.Cells는 XLSX, XLS, CSV, PDF 등 다양한 파일 형식을 지원합니다.

### PDF에 북마크를 만드는 과정을 자동화할 수 있나요?
네! Aspose.Cells를 애플리케이션에 통합하면 프로세스를 완전히 자동화할 수 있으며, 워크플로의 일부로 북마크가 포함된 Excel 기반 PDF를 동적으로 생성할 수 있습니다.

### .NET용 Aspose.Cells에 대한 지원은 어디에서 받을 수 있나요?
 방문할 수 있습니다[Aspose 포럼](https://forum.aspose.com/c/cells/9) 질문을 하거나 문제를 보고합니다.