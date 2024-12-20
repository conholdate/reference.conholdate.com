---
title: .NET용 Aspose.PDF로 잉크 주석 추가
linktitle: .NET용 Aspose.PDF로 잉크 주석 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET을 사용하여 잉크 주석을 추가하여 PDF 문서를 보다 상호 작용적이고 매력적으로 만드는 방법을 알아보세요. 이 포괄적인 가이드는 전체 프로세스를 안내합니다.
type: docs
weight: 20
url: /ko/net/tutorials/pdf/mastering-annotations/adding-ink-annotations/
---
## 소개

Aspose.PDF for .NET으로 PDF 조작의 신나는 세계에 오신 것을 환영합니다! 전문적인 용도, 개인 프로젝트 또는 그 사이의 어떤 용도로든 문서를 개선하든, 여러분은 올바른 곳에 있습니다. 이 가이드에서는 Aspose.PDF의 실용적인 기능인 PDF 파일에 잉크 주석을 추가하는 것을 살펴보겠습니다. 이 기능은 손으로 쓴 메모나 서명을 통합하여 문서를 더욱 상호 작용적이고 매력적으로 만드는 데 적합합니다.

## 필수 조건

코드로 넘어가기 전에 모든 것이 설정되어 있는지 확인해 보겠습니다.

1. .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요. Aspose.PDF는 .NET Core를 포함한 다양한 버전과 원활하게 작동합니다.
2.  Aspose.PDF 라이브러리: 프로젝트에서 .NET용 Aspose.PDF 라이브러리를 다운로드하여 참조하세요. 최신 버전은 다음에서 가져올 수 있습니다.[다운로드 링크](https://releases.aspose.com/pdf/net/).
3. 코드 편집기: 어떤 코드 편집기든 사용할 수 있지만, Visual Studio는 .NET 애플리케이션에서 사용하기 편리한 인터페이스를 갖추고 있어 적극 권장됩니다.
4. 기본 C# 지식: C#에 익숙하면 코딩 예제를 원활하게 탐색하는 데 도움이 됩니다.
5. 개발 환경 설정: IDE가 .NET 프로젝트에 맞게 구성되어 있고 Aspose.PDF 라이브러리를 올바르게 참조했는지 확인하세요.

이러한 필수 구성 요소를 갖추면 PDF에 잉크 주석을 추가할 준비가 된 것입니다!

## 필요한 패키지 가져오기

코딩에 들어가기 전에 필요한 패키지를 임포트해 보겠습니다. C# 파일의 맨 위에 다음 using 문을 추가합니다.

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
using System.Collections.Generic;
```

이러한 문장은 PDF 주석 작업에 필요한 모든 클래스와 메서드에 대한 접근을 제공합니다.

PDF 문서에 잉크 주석을 추가하는 과정을 명확한 단계로 나누어 보겠습니다.

## 1단계: 문서 및 디렉토리 설정

먼저, 문서와 출력 파일을 저장할 경로를 설정합니다.

```csharp
string dataDir = "YOUR DATA DIRECTORY";
Document doc = new Document();
```

 여기,`dataDir` 결과 PDF가 저장될 디렉토리를 가리키고 새 인스턴스를 생성합니다.`Document` 편집할 개체입니다.

## 2단계: 문서에 페이지 추가

다음으로, 새로 만든 문서에 페이지를 추가합니다.

```csharp
Page pdfPage = doc.Pages.Add();
```

모든 PDF에는 최소한 한 페이지가 필요하므로 이 단계는 필수입니다.

## 3단계: 도면 사각형 정의

이제 페이지의 어느 위치에 잉크 주석을 넣을지 정의하세요.

```csharp
System.Drawing.Rectangle drect = new System.Drawing.Rectangle
{
    Height = (int)pdfPage.Rect.Height,
    Width = (int)pdfPage.Rect.Width,
    X = 0,
    Y = 0
};
Aspose.Pdf.Rectangle arect = Aspose.Pdf.Rectangle.FromRect(drect);
```

 이 코드는 다음을 생성합니다.`Rectangle` 잉크 주석에 대한 페이지의 영역을 지정하여 전체 페이지에 맞게 조정하는 개체입니다.

## 4단계: 잉크 포인트 준비

다음으로, 잉크 주석을 구성할 포인트를 정의합니다.

```csharp
IList<Point[]> inkList = new List<Point[]>();
Aspose.Pdf.Point[] arrpt = new Aspose.Pdf.Point[3];
inkList.Add(arrpt);
arrpt[0] = new Aspose.Pdf.Point(100, 800);
arrpt[1] = new Aspose.Pdf.Point(200, 800);
arrpt[2] = new Aspose.Pdf.Point(200, 700);
```

이 블록은 Point 배열 목록을 생성하는데, 각 배열은 잉크 스트로크에 대한 점 집합을 나타냅니다. 여기서는 삼각형을 형성하는 세 점을 정의하지만, 디자인에 맞게 좌표를 자유롭게 조정하세요.

## 5단계: 잉크 주석 만들기

포인트를 정의한 후 잉크 주석을 만듭니다.

```csharp
InkAnnotation ia = new InkAnnotation(pdfPage, arect, inkList)
{
    Title = "Your Title",
    Color = Aspose.Pdf.Color.LightBlue,
    CapStyle = CapStyle.Rounded
};
```

 우리는 인스턴스화합니다`InkAnnotation` 객체, 페이지, 사각형 및 잉크 포인트를 전달합니다. 다음과 같은 속성을 사용자 정의합니다.`Title`, `Color` , 그리고`CapStyle` 귀하의 필요에 맞게!

## 6단계: 테두리 및 불투명도 설정

주석을 돋보이게 하려면 다음과 같이 스타일을 지정해 보세요.

```csharp
Border border = new Border(ia)
{
    Width = 25
};
ia.Border = border;
ia.Opacity = 0.5;
```

이 코드는 특정 너비의 테두리를 추가하고 주석의 불투명도를 설정하여 반투명하게 만듭니다.

## 7단계: 페이지에 주석 추가

이제 PDF 페이지에 주석을 추가하세요.

```csharp
pdfPage.Annotations.Add(ia);
```

이 줄은 페이지의 주석 컬렉션에 잉크 주석을 추가합니다.

## 8단계: 문서 저장

마지막으로 수정된 문서를 저장합니다.

```csharp
dataDir = dataDir + "AddInkAnnotation_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nInk annotation added successfully.\nFile saved at " + dataDir);
```

 여기서 우리는 수정합니다`dataDir` 출력 파일 이름을 포함하고 문서를 저장합니다. 확인 메시지가 모든 것이 순조롭게 진행되었음을 알려줍니다.

## 결론

축하합니다! Aspose.PDF for .NET을 사용하여 PDF 문서에 잉크 주석을 성공적으로 추가했습니다. 이 간단하면서도 강력한 기능은 문서를 향상시키고 대화형으로 만들 수 있습니다. 서명, 메모 또는 낙서를 추가하든 잉크 주석은 콘텐츠를 풍부하게 하는 독특한 방법을 제공합니다.

## 자주 묻는 질문

### Aspose.PDF란 무엇인가요?
Aspose.PDF는 .NET 애플리케이션에서 PDF 문서를 만들고, 조작하고, 변환하기 위한 라이브러리입니다.

### Aspose.PDF를 무료로 사용할 수 있나요?
네! Aspose는 자사 제품을 평가하기 위한 무료 체험판을 제공합니다. 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### 여러 개의 잉크 주석을 추가할 수 있나요?
 물론입니다! 여러 개를 만들 수 있습니다.`InkAnnotation` 개체를 선택하여 문서 페이지에 추가합니다.

### 더 많은 예를 어디서 볼 수 있나요?
 확인해보세요[선적 서류 비치](https://reference.aspose.com/pdf/net/) 자세한 튜토리얼과 샘플을 확인하세요.

### 지원이 필요하면 어떻게 해야 하나요?
 문제가 발생하면 다음에서 도움을 요청할 수 있습니다.[지원 포럼](https://forum.aspose.com/c/pdf/10).