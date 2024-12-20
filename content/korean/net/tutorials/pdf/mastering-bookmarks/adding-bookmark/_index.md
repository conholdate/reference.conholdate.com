---
title: PDF 파일에 북마크 추가
linktitle: PDF 파일에 북마크 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET을 사용하여 PDF 문서에 북마크를 프로그래밍 방식으로 추가하는 방법을 알아보세요. 이 단계별 가이드는 필요한 패키지를 가져오는 것부터 수정된 문서를 저장하는 것까지 모든 것을 다룹니다.
type: docs
weight: 10
url: /ko/net/tutorials/pdf/mastering-bookmarks/adding-bookmark/
---
## 소개

큰 PDF 문서를 탐색하는 것은 어려운 작업일 수 있습니다. 여러 페이지 문서에서 특정 정보를 찾을 때 끝없이 스크롤하면 소중한 시간을 낭비할 수 있습니다. 북마크는 이 문제에 대한 간단한 해결책을 제공하여 PDF에서 관련 섹션으로 빠르게 이동할 수 있는 방법을 제공합니다. 이 튜토리얼은 .NET 애플리케이션에서 PDF 파일을 사용하도록 설계된 강력한 라이브러리인 Aspose.PDF for .NET을 사용하여 PDF 파일에 북마크를 추가하는 방법을 단계별로 안내합니다.

## 필수 조건

코드를 살펴보기 전에 먼저 따라갈 수 있는 필수 도구와 지식이 있는지 확인해 보겠습니다.

- Visual Studio: 이 통합 개발 환경(IDE)은 .NET 개발에 필수적입니다.
-  .NET용 Aspose.PDF: Aspose.PDF 라이브러리를 다운로드하고 설치하여 프로젝트에서 PDF 파일을 조작합니다. 방문[다운로드 페이지](https://releases.aspose.com/pdf/net/) 시작하려면 클릭하세요.
- C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 이 가이드의 예제를 원활하게 따라갈 수 있습니다.

### 새 콘솔 애플리케이션 만들기

1. Visual Studio를 열고 새로운 C# 콘솔 애플리케이션 프로젝트를 만듭니다.
2. "PDFBookmarkingDemo"와 같이 프로젝트에 적절한 이름을 지정합니다.

### 프로젝트에 Aspose.PDF 라이브러리 추가

프로젝트에서 Aspose.PDF for .NET을 사용하려면:

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 버튼으로 클릭합니다.
2. NuGet 패키지 관리를 선택합니다.
3. Aspose.PDF를 검색하고 설치를 클릭하여 프로젝트에 라이브러리를 추가합니다.

### 필요한 네임스페이스 가져오기

 당신의 맨 위에`Program.cs` 파일에서 다음 네임스페이스를 가져옵니다.

```csharp
using System;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
```

이러한 네임스페이스는 PDF 문서 및 책갈피와 같은 주석 작업에 필수적인 클래스에 대한 액세스를 제공합니다.

## 1단계: PDF 문서 디렉토리 정의

시작하려면 PDF 파일이 있는 디렉토리를 지정하세요. 이 디렉토리는 PDF 파일을 로드하고 저장하는 데 사용됩니다. 다음은 예입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"C:\\YourDirectory\\"` PDF 파일이 들어 있는 폴더의 실제 경로를 입력합니다.

## 2단계: PDF 문서 열기

 다음으로 북마크를 추가할 기존 PDF 문서를 엽니다.`Document` PDF 파일을 로드하는 클래스:

```csharp
Document pdfDocument = new Document(dataDir + "YourFile.pdf");
```

이 코드는 지정된 디렉토리에서 PDF를 로드합니다.

## 3단계: 북마크 개체 만들기

이제 북마크를 만들고 속성을 구성해 보겠습니다. 각 북마크는 PDF 내의 특정 섹션이나 페이지에 대한 링크를 나타냅니다. 다음 코드는 "Chapter 1"이라는 제목의 북마크를 만듭니다.

```csharp
OutlineItemCollection pdfOutline = new OutlineItemCollection(pdfDocument.Outlines);
pdfOutline.Title = "Chapter 1";
pdfOutline.Italic = true;
pdfOutline.Bold = true;
```

북마크의 제목과 모양을 수정할 수 있습니다. 이 경우 제목 "챕터 1"은 강조를 위해 굵게 기울임체로 표시됩니다.

## 4단계: 북마크 대상 정의

각 북마크에는 목적지가 필요합니다. 이 목적지는 북마크가 링크할 PDF의 특정 페이지입니다. 예를 들어, 북마크를 첫 번째 페이지에 링크하려면:

```csharp
pdfOutline.Action = new GoToAction(pdfDocument.Pages[1]);
```

이 코드는 북마크의 동작을 PDF 문서의 첫 페이지로 이동하도록 설정합니다. 북마크가 가리키고 싶은 위치에 따라 페이지 번호를 조정합니다.

## 5단계: 문서에 북마크 추가

북마크가 설정되면 PDF의 개요 컬렉션에 추가할 차례입니다. 이렇게 하면 북마크가 문서의 대화형 목차에 포함됩니다.

```csharp
pdfDocument.Outlines.Add(pdfOutline);
```

이 코드 줄은 새로 만든 책갈피를 PDF 파일의 개요 컬렉션에 추가합니다.

## 6단계: 북마크로 PDF 저장

마지막으로 책갈피를 추가한 후 새 책갈피를 포함하여 수정된 PDF 파일을 저장합니다.

```csharp
dataDir = dataDir + "YourFile_with_Bookmark.pdf";
pdfDocument.Save(dataDir);
Console.WriteLine("\nBookmark added successfully.\nFile saved at " + dataDir);
```

이 코드는 추가된 책갈피가 포함된 PDF를 지정된 디렉토리에 "YourFile_with_Bookmark.pdf"라는 이름으로 저장합니다.

## 결론

PDF 파일에 북마크를 추가하는 것은 문서의 탐색 및 사용성을 개선하는 간단하면서도 효과적인 방법입니다. Aspose.PDF for .NET을 사용하면 사용자가 특정 페이지나 섹션으로 이동할 수 있는 북마크를 빠르게 구현하여 전반적인 사용자 경험을 향상시킬 수 있습니다. 이 가이드를 따르면 몇 줄의 코드만으로 PDF 파일에 북마크를 만들고, 사용자 지정하고, 추가하는 방법을 배웠습니다.

## 자주 묻는 질문

### PDF에 여러 개의 책갈피를 추가할 수 있나요?

 네, Aspose.PDF for .NET을 사용하면 필요한 만큼 북마크를 추가할 수 있습니다. 여러 개의 북마크를 만들기만 하면 됩니다.`OutlineItemCollection` 개체를 선택하여 문서의 개요 컬렉션에 추가합니다.

### 북마크의 모양을 어떻게 바꾸나요?

 다음과 같은 속성을 사용하여 북마크의 모양을 수정할 수 있습니다.`Italic`, `Bold` , 그리고`Color` 에`OutlineItemCollection` 객체. 사용자 정의 아이콘이나 스타일을 추가할 수도 있습니다.

### Aspose.PDF는 무료로 사용할 수 있나요?

 Aspose.PDF는 기능을 탐색할 수 있는 무료 평가판을 제공합니다. 그러나 모든 기능을 사용하려면 라이선스를 구매해야 합니다. 확인[구매 페이지](https://purchase.aspose.com/buy) 자세한 내용은.

### 더 많은 문서는 어디서 찾을 수 있나요?

 .NET용 Aspose.PDF에 대한 자세한 설명서는 다음을 방문하세요.[선적 서류 비치](https://reference.aspose.com/pdf/net/).

### Aspose.PDF에 대한 지원은 어떻게 받을 수 있나요?

 도움이나 지원이 필요하면 다음을 방문하세요.[Aspose 지원 포럼](https://forum.aspose.com/c/pdf/10).