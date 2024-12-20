---
title: PDF 주석 추가
linktitle: PDF 주석 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET을 사용하여 주석을 추가하는 방법을 알아보세요. 이 단계별 튜토리얼은 라이브러리 설치부터 주석 사용자 지정까지 모든 것을 다룹니다.
type: docs
weight: 10
url: /ko/net/tutorials/pdf/mastering-annotations/adding-pdf-annotation/
---
## 소개

주석은 PDF 문서를 풍부하게 만들어 대화형이고 유익한 문서로 만듭니다. 다른 사람과 협업하든 독자에게 추가적인 통찰력을 제공하든 주석은 필수적인 도구입니다. 이 튜토리얼에서는 Aspose.PDF for .NET을 사용하여 PDF 파일에 PDF 주석을 추가하는 방법을 살펴보고, 각 단계를 안내하여 이 프로세스에 능숙해지도록 합니다.

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.PDF: 라이브러리를 다음에서 다운로드하세요.[.NET용 Aspose.PDF 다운로드 페이지](https://releases.aspose.com/pdf/net/).
- 개발 환경: Visual Studio나 원하는 C# IDE를 사용하세요.
- C#에 대한 기본 지식: C# 프로그래밍에 익숙하다고 가정합니다.
- 샘플 PDF 문서: 주석을 추가할 PDF 파일입니다.

 아직 Aspose.PDF 라이브러리를 취득하지 못했다면 시작할 수 있습니다.[무료 체험](https://releases.aspose.com/) 또는 구매[특허](https://purchase.aspose.com/buy).

## 필요한 패키지 가져오기

코딩하기 전에 필요한 네임스페이스를 가져와야 합니다.

```csharp
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
```

이러한 네임스페이스는 PDF 조작 및 주석에 필요한 클래스와 메서드를 제공합니다.

## 1단계: PDF 문서 로드

PDF 주석을 추가하려는 PDF 문서를 로드하여 시작합니다.

```csharp
// 문서 디렉토리의 경로를 지정하세요.
string dataDir = "YOUR DATA DIRECTORY";
// PDF 문서를 로드합니다
Document pdfDocument = new Document(dataDir + "AddAnnotation.pdf");
```

 이 코드 조각은 PDF 파일의 디렉토리를 설정하고 이를 로드합니다.`Document` 객체를 생성하여 추가 수정이 가능합니다.

## 2단계: 주석 만들기

 다음으로, 우리는 다음을 만들 것입니다.`TextAnnotation`, 댓글이나 메모를 추가하는 데 적합합니다.

```csharp
// TextAnnotation 만들기
TextAnnotation textAnnotation = new TextAnnotation(pdfDocument.Pages[1], new Aspose.Pdf.Rectangle(200, 400, 400, 600))
{
    Title = "Sample Annotation Title",
    Subject = "Sample Subject",
    Contents = "Sample contents for the annotation",
    Open = true,
    Icon = TextIcon.Key
};
```

-  위치 및 크기:`Rectangle`클래스는 페이지에서 주석의 위치와 크기를 정의합니다.
-  속성: 주석의 제목, 주제 및 내용을 설정할 수 있습니다.`Open` 속성은 주석이 기본적으로 열린 상태로 표시될지 여부를 결정합니다.
-  아이콘 :`TextIcon.Key` 주석에 시각적 요소를 추가합니다.

## 3단계: 주석 모양 사용자 지정

주석의 모양을 사용자 지정하여 주석의 가시성을 높입니다.

```csharp
// 주석 테두리 사용자 지정
Border border = new Border(textAnnotation)
{
    Width = 5,
    Dash = new Dash(1, 1)
};
textAnnotation.Border = border;
textAnnotation.Rect = new Aspose.Pdf.Rectangle(200, 400, 400, 600);
```

-  테두리: 만들기`Border` 객체를 선택하고 너비와 스타일(이 경우 점선)을 설정하여 가시성을 높입니다.

## 4단계: PDF 페이지에 주석 추가

이제 PDF 페이지에 주석을 추가할 시간입니다.

```csharp
// 페이지의 주석 컬렉션에 주석을 추가합니다.
pdfDocument.Pages[1].Annotations.Add(textAnnotation);
```

이 줄은 새로 만든 주석을 PDF의 첫 페이지에 추가하여 문서에 통합합니다.

## 5단계: 업데이트된 PDF 문서 저장

마지막으로, 변경 사항을 유지하려면 문서를 저장하세요.

```csharp
// 업데이트된 PDF 문서를 저장합니다.
dataDir = dataDir + "AddAnnotation_out.pdf";
pdfDocument.Save(dataDir);
Console.WriteLine("\nAnnotation added successfully.\nFile saved at " + dataDir);
```

이 코드는 수정된 문서를 다음과 같이 저장합니다.`AddAnnotation_out.pdf`원본 파일을 보존하고 주석이 성공적으로 추가되었는지 확인합니다.

## 결론

PDF에 주석을 추가하는 것은 Aspose.PDF for .NET으로 쉽게 할 수 있는 강력한 기능입니다. 문서 검토든 개인 메모든, 이 가이드는 주석을 효과적으로 만들고 사용자 정의하는 방법을 알려줍니다. 이러한 단계를 따르면 PDF 문서의 상호 작용성과 유용성을 향상시킬 수 있습니다.

## 자주 묻는 질문

### Aspose.PDF for .NET을 사용하여 어떤 유형의 주석을 추가할 수 있습니까?
텍스트, 링크, 강조, 스탬프 주석 등 다양한 주석을 추가할 수 있습니다.

### 주석의 모양을 사용자 지정할 수 있나요?
물론입니다! 주석의 크기, 색상, 테두리, 아이콘을 수정할 수 있습니다.

### 한 페이지에 여러 개의 주석을 추가할 수 있나요?
네, PDF의 어느 페이지에나 여러 개의 주석을 추가할 수 있습니다.

### 주석을 추가한 후에 제거할 수 있나요?
 예, 주석은 다음을 사용하여 제거할 수 있습니다.`Annotations.Delete`Aspose.PDF에서 제공하는 방법입니다.

### Aspose.PDF for .NET을 사용하려면 라이선스가 필요합니까?
 예, 모든 기능을 잠금 해제하고 제한을 피하려면 라이센스가 필요합니다. 또한 다음을 얻을 수 있습니다.[임시 면허](https://purchase.aspose.com/temporary-license/) 평가 목적으로.