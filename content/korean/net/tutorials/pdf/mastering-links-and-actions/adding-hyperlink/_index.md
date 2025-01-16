---
title: PDF 파일에 하이퍼링크 추가
linktitle: PDF 파일에 하이퍼링크 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET을 사용하여 대화형 하이퍼링크를 추가하여 PDF 문서의 기능을 향상시키는 방법을 알아보세요. 이 포괄적인 가이드는 단계별 튜토리얼을 제공합니다.
type: docs
weight: 10
url: /ko/net/tutorials/pdf/mastering-links-and-actions/adding-hyperlink/
---
## 소개

PDF 문서의 상호 작용성과 탐색성을 강화하면 사용자 경험이 크게 향상될 수 있습니다. 결제 포털에 대한 링크가 있는 송장을 만들든 독자를 온라인 리소스로 안내하는 보고서를 만들든, 하이퍼링크를 추가하면 PDF를 보다 사용자 친화적으로 만들 수 있는 강력한 방법입니다. 이 가이드에서는 .NET용 Aspose.PDF 라이브러리를 사용하여 PDF 파일에 하이퍼링크를 추가하는 과정을 살펴보겠습니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1. .NET Framework: 컴퓨터에 설치된 .NET Framework와 호환되는 버전입니다.
2.  .NET 라이브러리용 Aspose.PDF: 라이브러리를 다음에서 다운로드하세요.[Aspose 웹사이트](https://releases.aspose.com/pdf/net/).
3. 기본 C# 지식: C# 프로그래밍에 익숙하면 원활하게 따라갈 수 있습니다.
4. 개발 환경: 코딩과 테스트를 위해 설정된 Visual Studio와 같은 IDE.

이러한 전제 조건을 갖추면 이제 시작할 준비가 된 것입니다!

## 1단계: 문서 디렉토리 설정

PDF 파일을 저장할 디렉토리를 정의하는 것으로 시작합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`YOUR_DOCUMENT_DIRECTORY` PDF를 저장하려는 실제 경로를 선택하세요.

## 2단계: 기존 PDF 문서 열기

 기존 PDF를 수정하려면 다음을 사용하십시오.`Document`Aspose.PDF 라이브러리의 클래스:

```csharp
Document document = new Document(dataDir + "AddHyperlink.pdf");
```

 파일을 확인하세요`"AddHyperlink.pdf"` 지정한 디렉토리에 존재합니다.

## 3단계: PDF 페이지에 액세스

하이퍼링크를 추가할 페이지를 선택합니다. 예를 들어, 첫 번째 페이지에 추가하려면 다음과 같이 합니다.

```csharp
Page page = document.Pages[1]; // 페이지 인덱스는 1부터 시작합니다
```

## 4단계: 링크 주석 만들기

사각형을 사용하여 하이퍼링크의 클릭 가능한 영역을 정의합니다.

```csharp
LinkAnnotation link = new LinkAnnotation(page, new Aspose.Pdf.Rectangle(100, 100, 300, 300));
```

 사각형 좌표 조정`(100, 100)` 에게`(300, 300)` 귀하의 디자인 요구에 맞게.

## 5단계: 링크 테두리 구성

링크의 테두리를 사용자 지정할 수 있습니다. 여기서는 테두리를 보이지 않게 설정하겠습니다.

```csharp
Border border = new Border(link) { Width = 0 };
link.Border = border;
```

## 6단계: 하이퍼링크 동작 지정

하이퍼링크에 대한 작업을 설정합니다. 이 예에서는 Aspose 웹사이트에 링크합니다.

```csharp
link.Action = new GoToURIAction("http://www.aspose.com");
```

## 7단계: 페이지에 링크 주석 추가

페이지의 주석 컬렉션에 하이퍼링크를 추가합니다.

```csharp
page.Annotations.Add(link);
```

## 8단계: 자유 텍스트 주석 만들기

텍스트 주석을 추가하면 하이퍼링크에 대한 컨텍스트를 제공하는 데 도움이 됩니다.

```csharp
FreeTextAnnotation textAnnotation = new FreeTextAnnotation(
    document.Pages[1], 
    new Aspose.Pdf.Rectangle(100, 100, 300, 300), 
    new DefaultAppearance(FontRepository.FindFont("TimesNewRoman"), 10, Color.Blue)
)
{
    Contents = "Link to Aspose website",
    Border = border
};

document.Pages[1].Annotations.Add(textAnnotation);
```

## 9단계: 문서 저장

마지막으로, 하이퍼링크와 함께 업데이트된 PDF를 저장합니다.

```csharp
dataDir = dataDir + "AddHyperlink_out.pdf";
document.Save(dataDir);
```

## 결론

Aspose.PDF for .NET을 사용하여 PDF 문서에 하이퍼링크를 추가하면 전문성이 향상될 뿐만 아니라 사용자 참여도 향상됩니다. 이 가이드에 설명된 단계를 사용하면 만들거나 수정하는 모든 PDF에 하이퍼링크를 쉽게 추가할 수 있습니다.

## 자주 묻는 질문

### 하이퍼링크의 스타일을 다르게 지정할 수 있나요?  
네, 글꼴, 색상, 테두리 스타일 등 하이퍼링크의 모양을 사용자 지정할 수 있습니다.

### 내부 페이지에 링크를 걸려면 어떻게 해야 하나요?  
 사용`GoToAction` 대신에`GoToURIAction` 동일한 PDF 내의 다른 페이지에 링크합니다.

### Aspose.PDF는 다른 파일 형식을 지원합니까?  
네, Aspose.PDF는 다양한 파일 형식을 조작하고 변환할 수 있도록 지원합니다.

### 개발을 위한 임시 라이선스는 어떻게 받을 수 있나요?  
 임시 면허증은 다음 사이트를 방문하여 취득할 수 있습니다.[이 링크](https://purchase.aspose.com/temporary-license/).

### Aspose.PDF에 대한 더 많은 튜토리얼은 어디에서 찾을 수 있나요?  
 더 많은 튜토리얼을 탐색해보세요[Aspose 문서](https://reference.aspose.com/pdf/net/).