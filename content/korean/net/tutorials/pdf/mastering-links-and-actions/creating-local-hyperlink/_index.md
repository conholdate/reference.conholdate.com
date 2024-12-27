---
title: PDF 파일에서 로컬 하이퍼링크 만들기
linktitle: PDF 파일에서 로컬 하이퍼링크 만들기
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET을 사용하여 로컬 하이퍼링크를 만들어 PDF 문서의 탐색을 개선하는 방법을 알아보세요. 이 단계별 튜토리얼은 전체 프로세스를 안내합니다.
type: docs
weight: 40
url: /ko/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## 소개

이 가이드에서는 Aspose.PDF for .NET을 사용하여 PDF 파일에 로컬 하이퍼링크를 만드는 과정을 안내합니다. 각 단계를 명확하게 나누어 PDF 조작을 처음 접하는 사람이라도 손쉽게 따라할 수 있도록 합니다.

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

1.  Visual Studio: 여기에서 다운로드하세요[Visual Studio 웹사이트](https://visualstudio.microsoft.com/).
2.  .NET용 Aspose.PDF: 라이브러리를 다음을 통해 다운로드하세요.[Aspose 웹사이트](https://releases.aspose.com/pdf/net/)이 라이브러리는 PDF 조작을 위한 풍부한 기능 세트를 제공합니다.
3. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 도움이 되지만 걱정하지 마세요. 코드를 줄별로 설명해 드리겠습니다.
4. .NET Framework: 컴퓨터에 .NET framework가 설치되어 있는지 확인하세요. Aspose.PDF에서 요구 사항을 확인하세요.[선적 서류 비치](https://reference.aspose.com/pdf/net/).

이러한 전제 조건을 갖추면 PDF 문서에서 로컬 하이퍼링크를 만드는 방법을 배울 준비가 된 것입니다!

## 필수 패키지 가져오기

이제 모든 설정이 끝났으니, C# 프로젝트로 필요한 패키지를 가져올 차례입니다.

### 프로젝트 열기

기존 .NET 프로젝트를 열거나 Visual Studio에서 새 프로젝트를 만듭니다. 새로 시작하는 경우 시작 화면에서 "새 프로젝트 만들기"를 선택합니다.

### Aspose.PDF에 참조 추가

 솔루션 탐색기에서 프로젝트 폴더의 "종속성"을 마우스 오른쪽 버튼으로 클릭합니다. "NuGet 패키지 관리"를 선택하고 다음을 검색합니다.`Aspose.PDF`, 그리고 사용 가능한 최신 버전을 설치합니다. 이렇게 하면 PDF를 만들고 조작하는 데 필요한 모든 도구가 제공됩니다.

### 네임스페이스 가져오기

.cs 파일의 맨 위에 다음 using 지침을 추가합니다.

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

이러한 지침을 사용하면 라이브러리 기능에 원활하게 접근할 수 있습니다.

로컬 하이퍼링크를 만드는 과정을 간단한 단계로 나누어 보겠습니다.

## 1단계: 문서 인스턴스 설정

 새 인스턴스를 만듭니다.`Document` 클래스는 작업할 PDF 파일을 나타냅니다.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // 문서 디렉토리 설정
Document doc = new Document(); // 문서 인스턴스 생성
```

 바꾸다`"YOUR_DOCUMENT_DIRECTORY"` PDF가 저장될 시스템의 실제 경로를 입력합니다.

## 2단계: 문서에 페이지 추가

다음으로, PDF 문서에 페이지를 추가합니다.

```csharp
Page page = doc.Pages.Add(); // 새로운 페이지 추가
```

이 줄은 문서에 새 페이지를 추가하며, 여기에 모든 콘텐츠가 배치됩니다.

## 3단계: 텍스트 조각 만들기

이제 클릭할 수 있는 링크 역할을 하는 텍스트를 만들어 보겠습니다.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // 텍스트 조각 만들기
```

 이것`TextFragment` 사용자가 클릭할 수 있는 텍스트를 표시합니다.

## 4단계: 로컬 하이퍼링크 만들기

이제 7페이지를 가리키는 로컬 하이퍼링크를 만듭니다.

```csharp
LocalHyperlink link = new LocalHyperlink(); // 로컬 하이퍼링크 만들기
link.TargetPageNumber = 7; // 링크의 대상 페이지를 설정하세요
text.Hyperlink = link; // 텍스트 조각에 대한 하이퍼링크를 설정합니다.
```

 그만큼`LocalHyperlink` 클래스를 사용하면 하이퍼링크의 대상 페이지 번호를 지정할 수 있습니다.

## 5단계: 페이지에 텍스트 조각 추가

만든 페이지에 클릭 가능한 텍스트를 추가합니다.

```csharp
page.Paragraphs.Add(text); // 페이지에 텍스트 조각을 추가합니다.
```

이 줄은 해당 페이지의 문단 모음에 텍스트를 추가합니다.

## 6단계: 다른 텍스트 조각 만들기(선택 사항)

1페이지로 돌아갈 수 있는 하이퍼링크를 하나 더 추가해 보겠습니다.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // 새로운 텍스트 조각 만들기
textBack.IsInNewPage = true; // 새 페이지에 있어야 한다고 표시하세요
```

## 7단계: 두 번째 로컬 하이퍼링크 설정

1페이지에 대한 다른 로컬 하이퍼링크를 만듭니다.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // 다른 로컬 하이퍼링크를 만듭니다
linkBack.TargetPageNumber = 1; // 두 번째 하이퍼링크에 대한 대상 페이지 설정
textBack.Hyperlink = linkBack; // 두 번째 텍스트 조각에 대한 하이퍼링크를 설정합니다.
```

## 8단계: 새 페이지에 두 번째 텍스트 조각 추가

두 번째 텍스트 조각을 해당 페이지에 추가합니다.

```csharp
Page newPage = doc.Pages.Add(); // 두 번째 링크에 대한 새 페이지를 추가합니다.
newPage.Paragraphs.Add(textBack); // 새 페이지에 텍스트 조각을 추가합니다.
```

## 9단계: 문서 저장

마지막으로 문서를 저장합니다.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // 출력 파일 이름을 지정하세요
doc.Save(dataDir); // 업데이트된 문서를 저장합니다
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 이 줄은 디렉토리 경로와 파일 이름을 결합합니다.`Save()` 이 방법으로 문서를 저장합니다.

## 결론

Aspose.PDF for .NET을 사용하여 PDF 파일에 로컬 하이퍼링크를 만드는 것은 탐색 및 사용자 경험을 향상시키는 실용적인 기능입니다. 이제 독자를 필요한 정보로 직접 안내하여 PDF를 보다 상호 작용적이고 사용자 친화적으로 만들 수 있는 지식이 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.PDF란 무엇인가요?
.NET용 Aspose.PDF는 개발자가 .NET 프레임워크를 사용하여 프로그래밍 방식으로 PDF 문서를 만들고, 조작하고, 변환할 수 있는 라이브러리입니다.

### 외부 웹 페이지에 하이퍼링크를 만들 수 있나요?
네, Aspose.PDF는 PDF 내의 로컬 하이퍼링크뿐만 아니라 외부 URL에 대한 하이퍼링크 생성도 지원합니다.

### Aspose.PDF 무료 평가판이 있나요?
 물론입니다! 무료 체험판을 다음에서 이용할 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/).

### Aspose는 어떤 프로그래밍 언어를 지원하나요?
Aspose는 Java, C를 포함한 다양한 프로그래밍 언어에 대한 라이브러리를 제공합니다.++, Python 등이 있습니다.

### Aspose 제품에 대한 지원은 어떻게 받을 수 있나요?
 지원을 요청할 수 있습니다.[Aspose 포럼](https://forum.aspose.com/c/pdf/10).