---
title: Aspose.Cells를 사용하여 스레드 댓글의 생성 시간 읽기
linktitle: Aspose.Cells를 사용하여 스레드 댓글의 생성 시간 읽기
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 Excel 워크시트에서 스레드된 댓글의 생성 시간을 쉽게 읽는 방법을 알아보세요. 단계별 지침이 있는 자세한 가이드를 따르세요.
type: docs
weight: 21
url: /ko/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## 소개

Excel 파일을 작업할 때 주석 관리가 협업 및 피드백 추적에 필수적일 수 있습니다. 이 가이드에서는 Aspose.Cells for .NET을 사용하여 Excel 워크시트에서 스레드 주석의 생성 시간을 읽는 과정을 안내합니다. 이 강력한 도구는 Excel 파일과 상호 작용하는 효율적인 방법을 제공하여 개발자가 주석에서 자세한 정보를 추출할 수 있게 하며, 이는 협업 시나리오에서 피드백의 타이밍을 추적하는 데 특히 유용합니다.

## 필수 조건

시작하기 전에 Aspose.Cells for .NET을 사용하기 위해 개발 환경이 제대로 설정되어 있는지 확인하는 것이 중요합니다. 필요한 것은 다음과 같습니다.

1.  .NET용 Aspose.Cells: Aspose.Cells 라이브러리가 설치되어 있어야 합니다. 최신 버전은 다음에서 받을 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/cells/net/).
2. IDE: Visual Studio(또는 원하는 .NET IDE)를 사용하여 코드를 작성하고 실행합니다.
3. 기본 C# 지식: C# 프로그래밍에 익숙하면 예제를 더 쉽게 따라갈 수 있습니다.
4.  Excel 파일: 이 튜토리얼에서는 다음과 같은 이름의 Excel 파일을 사용합니다.`ThreadedCommentsSample.xlsx`, 여기에는 스레드 댓글이 포함됩니다. 따라갈 수 있도록 파일에 댓글이 포함되어 있는지 확인하세요.

## 필수 패키지 가져오기

우선 Aspose.Cells에서 작업하는 데 필요한 네임스페이스를 가져와야 합니다. C# 프로젝트를 열고 코드 파일 맨 위에 다음 using 지시문을 추가합니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

 그만큼`Aspose.Cells` 네임스페이스를 사용하면 Excel 파일을 조작하는 데 필요한 모든 클래스와 메서드에 액세스할 수 있습니다.`System` 출력이나 예외 처리 같은 일반적인 기능에 필요합니다.

## 1단계: Excel 파일의 디렉토리 지정

첫 번째 단계는 Excel 파일이 저장된 경로를 정의하는 것입니다. 이 경로는 프로그래밍 방식으로 파일을 찾는 데 사용됩니다.

```csharp
// Excel 파일의 디렉토리를 정의합니다
string sourceDir = "Your Document Directory";
```

 바꾸다`"C:\\YourDirectory\\"`파일의 실제 경로와 함께. 이렇게 하면 프로그램이 파일을 찾을 위치를 알 수 있습니다.`ThreadedCommentsSample.xlsx`.

## 2단계: 통합 문서 로드

 디렉토리가 설정되었으므로 이제 Excel 통합 문서를 로드할 수 있습니다. 이는 새 통합 문서를 만들어서 수행됩니다.`Workbook` 객체를 만들고 해당 객체의 파일 경로를 전달합니다.

```csharp
// Excel 통합 문서 로드
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

지정된 경로에서 파일을 찾을 수 없는 경우 예외가 발생하므로 계속 진행하기 전에 파일 경로가 올바른지 확인하세요.

## 3단계: 원하는 워크시트에 액세스

워크북이 로드되면 스레드된 댓글이 포함된 워크시트에 액세스해야 합니다. 이 예에서는 워크북의 첫 번째 워크시트를 검색합니다.

```csharp
// 통합 문서의 첫 번째 워크시트에 액세스하세요
Worksheet worksheet = workbook.Worksheets[0];
```

 귀하의 의견이 다른 워크시트에 있는 경우 인덱스를 그에 맞게 수정하기만 하면 됩니다. 예를 들어, 다음을 사용합니다.`Worksheets[1]` 두 번째 워크시트에 대해서도 마찬가지입니다.

## 4단계: 스레드 댓글 검색

스레드된 댓글을 검색하려면 댓글이 포함된 셀을 지정해야 합니다. 이 경우 셀에 초점을 맞춥니다.`A1` . 방법`GetThreadedComments` 특정 셀과 관련된 모든 주석을 가져오는 데 사용됩니다.

```csharp
// 셀 A1에서 스레드된 댓글 가져오기
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

이렇게 하면 셀 A1에 대한 스레드된 댓글 모음이 반환됩니다. 지정된 셀에 댓글이 없으면 모음이 비어 있게 됩니다.

## 5단계: 주석을 반복하고 생성된 시간 추출

 스레드된 댓글을 검색한 다음 단계는 컬렉션을 반복하고 각 댓글에 대해 생성된 시간을 포함하여 관련 세부 정보를 추출하는 것입니다. 이를 쉽게 달성할 수 있습니다.`ThreadedCommentCollection`.

```csharp
// 각 스레드 댓글을 반복하고 세부 정보를 표시합니다.
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

 이 코드는 댓글의 내용, 작성자 이름, 댓글이 작성된 시간을 출력합니다.`CreatedTime` 해당 속성은 댓글이 원래 작성된 타임스탬프를 반환합니다.

## 6단계: 확인 메시지 표시

스레드 댓글을 성공적으로 읽고 정보를 표시한 후에는 항상 코드에 확인 메시지를 포함하는 것이 좋습니다. 이렇게 하면 프로세스가 올바르게 실행되었는지 확인하는 데 도움이 됩니다.

```csharp
// 확인 메시지
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

이 메시지는 코드 실행이 완료되면 콘솔에 인쇄되어 프로세스가 오류 없이 실행되었음을 확인합니다.

## 결론

이제 Aspose.Cells for .NET을 사용하여 Excel 워크시트에서 스레드된 댓글의 생성 시간을 쉽게 읽는 방법을 배웠습니다. 이 기능은 협업 환경에서 댓글과 피드백을 추적하고 문서 검토 프로세스에 필수적인 타임스탬프를 제공하는 데 매우 중요합니다. 이 가이드를 따르면 .NET 애플리케이션에서 댓글 데이터를 효율적으로 추출하고 활용하여 워크플로를 개선하고 팀원과의 협업을 개선할 수 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.Cells란 무엇인가요?

Aspose.Cells for .NET은 개발자가 .NET 애플리케이션에서 Excel 파일을 만들고, 조작하고, 관리할 수 있는 포괄적인 라이브러리입니다. Excel 파일을 프로그래밍 방식으로 읽고, 쓰고, 수정하기 위한 강력한 도구를 제공합니다.

### Aspose.Cells for .NET을 어떻게 다운로드할 수 있나요?

 .NET용 Aspose.Cells의 최신 버전은 다음에서 다운로드할 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/cells/net/).

### 무료 체험판이 있나요?

 네, Aspose는 Aspose.Cells for .NET에 대한 무료 평가판을 제공합니다. 평가판은 다음에서 다운로드할 수 있습니다.[무료 체험 페이지](https://releases.aspose.com/).

### 다른 셀에서 주석에 접근할 수 있나요?

 예, 워크시트의 모든 셀에서 셀 참조를 수정하여 스레드된 주석에 액세스할 수 있습니다.`GetThreadedComments` 방법. 간단히 변경하세요`"A1"` 원하는 셀의 참조로.

### Aspose.Cells에 대한 지원은 어디서 받을 수 있나요?

 지원이 필요하거나 질문이 있는 경우 다음을 방문하세요.[Aspose 포럼](https://forum.aspose.com/c/cells/9), 커뮤니티에서 답변을 찾거나 도움을 요청할 수 있습니다.