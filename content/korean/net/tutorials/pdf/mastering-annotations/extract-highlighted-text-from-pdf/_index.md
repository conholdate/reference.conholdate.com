---
title: Aspose.PDF for .NET을 사용하여 PDF에서 강조된 텍스트 추출
linktitle: Aspose.PDF for .NET을 사용하여 PDF에서 강조된 텍스트 추출
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET으로 강조된 텍스트를 추출하는 방법을 배우면 PDF 문서의 잠재력을 끌어낼 수 있습니다. 이 포괄적인 가이드는 설정부터 구현까지 각 단계를 안내합니다.
type: docs
weight: 60
url: /ko/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## 소개

PDF 파일을 작업할 때 강조된 텍스트를 추출하는 것은 데이터 분석, 콘텐츠 검토 또는 메모 정리에 필수적일 수 있습니다. Aspose.PDF for .NET을 사용 중이라면 운이 좋습니다. 이 튜토리얼은 PDF 문서에서 강조된 텍스트를 효율적으로 추출하는 방법에 대한 명확하고 단계별 지침을 제공합니다.

## 필수 조건

시작하기 전에 다음 사항이 준비되었는지 확인하세요.

-  .NET 라이브러리용 Aspose.PDF: 라이브러리를 다음에서 다운로드하세요.[릴리스 페이지](https://releases.aspose.com/pdf/net/).
- 개발 환경: Visual Studio와 같은 작업 환경.
- C#에 대한 기본 지식: C# 및 객체 지향 프로그래밍에 대한 지식이 필요합니다.
-  Aspose 라이센스: 무료 평가판으로 시작할 수 있지만[임시 면허](https://purchase.aspose.com/temporary-license/) 또는 다음으로부터의 전체 라이센스[여기](https://purchase.aspose.com/buy) 제한 없는 접근이 제공됩니다.

## 필요한 네임스페이스 가져오기

먼저 C# 프로젝트에 필요한 네임스페이스를 가져옵니다.

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

이러한 네임스페이스는 PDF 문서와 주석을 처리하는 데 필요한 클래스와 메서드에 대한 액세스를 제공합니다.

## 1단계: 프로젝트 디렉토리 설정

PDF 파일이 있는 디렉토리를 지정하세요:

```csharp
// 문서 디렉토리 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

경로를 PDF 파일의 실제 디렉토리로 바꿔야 합니다.

## 2단계: PDF 문서 로드

다음 코드로 PDF 문서를 로드합니다.

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

지정된 파일이 주어진 디렉토리에 있는지 확인하세요.

## 3단계: 페이지에서 주석에 액세스

주석에 액세스하려면 원하는 페이지(이 경우 첫 번째 페이지)에서 주석을 반복합니다.

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 이 코드는 다음을 필터링합니다.`TextMarkupAnnotation` 하이라이트를 나타내는 유형입니다.

## 4단계: 강조된 텍스트 추출

이제 강조된 주석에서 텍스트를 추출하여 표시합니다.

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

이 명령은 강조 표시된 부분과 연관된 모든 텍스트 조각을 검색하여 콘솔에 출력합니다.

## 결론

Aspose.PDF for .NET을 사용하여 PDF에서 강조 표시된 텍스트를 추출하는 것은 간단하며 문서 처리 프로세스를 크게 향상시킬 수 있습니다. 위에 설명된 단계를 따르면 보고서 준비 또는 데이터 분석과 같은 다양한 응용 프로그램을 위해 강조 표시된 텍스트를 효율적으로 수집할 수 있습니다.

## 자주 묻는 질문

### 다른 유형의 주석을 추출할 수 있나요?
 네, 간단히 조정하세요`if` 다양한 주석 유형을 포함하는 조건`TextAnnotation` 또는`StampAnnotation`.

### 모든 PDF 페이지에서 강조된 텍스트를 추출하려면 어떻게 해야 하나요?
다음을 사용하여 모든 페이지를 반복할 수 있습니다.
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Aspose.PDF for .NET에 라이선스가 필요합니까?
 무료 체험판을 이용할 수 있지만 다음을 고려하세요.[임시 면허](https://purchase.aspose.com/temporary-license/) 또는 전체 액세스를 위한 전체 라이센스입니다.

### 추출된 텍스트를 파일로 저장할 수 있나요?
물론입니다! 추출된 텍스트를 텍스트 파일에 쓰도록 코드를 수정할 수 있습니다.

### Aspose.PDF는 다른 플랫폼을 지원합니까?
네, Aspose.PDF는 Java 및 기타 플랫폼도 지원하여 비슷한 기능을 제공합니다.