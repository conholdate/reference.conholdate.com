---
title: PDF 문서에 목차 추가
linktitle: PDF 문서에 목차 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: 이 튜토리얼에서는 Aspose.Pdf for .NET을 사용하여 PDF 문서에 목차(TOC)를 추가하는 방법을 보여줍니다.
type: docs
weight: 40
url: /ko/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## 소개

PDF 문서에 목차(TOC)를 만들면 탐색 및 접근성이 크게 향상될 수 있습니다. 이 가이드에서는 Aspose.Pdf for .NET을 사용하여 PDF 파일에 TOC를 추가하는 방법을 보여드리겠습니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.   .NET용 Aspose.PDF: 최신 버전을 다운로드하여 설치하세요.[여기](https://releases.aspose.com/pdf/net/).
2.  개발 환경: Visual Studio와 같은 .NET 개발 환경을 설정합니다.
3.   라이센스: 필요한 경우 임시 라이센스를 요청하십시오. 방문하십시오.[Aspose.Pdf 라이센스 페이지](https://asposepdf.com/developers) 자세한 내용은.

필요한 라이브러리 가져오기

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## 1단계: PDF 문서 로드

TOC를 추가하려는 기존 PDF 파일을 로드합니다. 문서 디렉토리 경로를 지정합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## 2단계: TOC에 대한 새 페이지 삽입

PDF 문서의 시작 부분에 새 페이지를 삽입합니다. 이 페이지는 목차(TOC) 역할을 합니다.

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## 3단계: TOC 정보 개체 만들기

TOC 정보를 나타낼 객체를 만듭니다. 제목을 추가하고 링크를 추가하여 탐색을 개선합니다.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## 4단계: TOC 요소 정의

TOC에 표시될 요소(또는 제목)를 정의합니다. 이러한 요소는 독자가 문서의 특정 섹션으로 이동하는 데 도움이 될 수 있습니다.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## 5단계: TOC 제목 만들기

TOC의 처음 두 요소에 대한 제목을 만듭니다. 이 제목은 해당 페이지로 연결됩니다.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## 6단계: TOC를 포함한 PDF 저장

마지막으로 업데이트된 PDF 파일을 저장합니다.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## 확인 메시지

사용자에게 프로세스가 완료되었음을 알리는 확인 메시지를 표시합니다.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## 결론

Aspose.PDF for .NET을 사용하면 PDF에 목차를 추가하는 것이 쉬울 뿐만 아니라 사용자 정의도 가능합니다. 간단한 탐색 링크나 복잡한 구조를 만들어야 하든 이 도구가 해결해 드립니다. 따라서 다음에 긴 PDF 작업을 할 때는 전문적인 터치를 위해 목차를 추가하는 것을 잊지 마세요.

## 자주 묻는 질문

### Aspose.PDF에서 TOC의 모양을 사용자 정의할 수 있나요?

네, 글꼴 스타일, 크기, 정렬을 비롯하여 TOC의 모양을 완전히 사용자 지정할 수 있습니다.

### TOC에 부제목을 추가하려면 어떻게 해야 하나요?

 하위 제목을 추가하려면 다음을 조정하세요.`Heading` 수준(예:`Heading(2)`).

### 문서가 변경되면 TOC를 자동으로 업데이트할 수 있나요?

아니요, TOC는 자동으로 업데이트되지 않습니다. 문서 구조가 변경되면 다시 만들어야 합니다.

### TOC 항목을 외부 문서에 연결할 수 있나요?

네, 하이퍼링크를 사용하여 TOC 항목을 외부 PDF나 URL에 연결할 수 있습니다.

### Aspose.PDF는 다단계 목차를 지원합니까?

네, Aspose.PDF는 하위 섹션이 있는 복잡한 문서에 대해 다단계 TOC를 지원합니다.
