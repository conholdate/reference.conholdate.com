---
title: 채워진 사각형 만들기
linktitle: 채워진 사각형 만들기
second_title: .NET API 참조를 위한 Aspose.PDF
description: 이 단계별 튜토리얼에서 Aspose.PDF for .NET으로 PDF 조작의 힘을 잠금 해제하세요. 채워진 사각형을 그려 시각적으로 매력적인 PDF 문서를 프로그래밍 방식으로 만드는 방법을 알아보세요.
type: docs
weight: 50
url: /ko/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## 소개

시각적으로 멋진 PDF를 프로그래밍 방식으로 만들고 싶었던 적이 있나요? 그렇다면, 당신은 올바른 곳에 있습니다! 이 튜토리얼에서는 PDF 문서 조작을 간소화하는 강력한 라이브러리인 Aspose.PDF for .NET을 살펴보겠습니다. 오늘은 PDF 파일 내에서 채워진 사각형을 만드는 데 집중하겠습니다. 노련한 개발자이든 초보자이든, 이 가이드는 친절하고 매력적인 방식으로 각 단계를 안내합니다. 그러니 코딩 모자를 쓰고 시작해 봅시다!

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

1. Visual Studio: .NET 개발을 위한 훌륭한 IDE인 Visual Studio를 컴퓨터에 설치하세요.
2. .NET용 Aspose.PDF: Aspose.PDF 라이브러리를 다운로드하여 설치하세요.[여기](https://releases.aspose.com/pdf/net/).
3. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 코드 조각을 더 잘 이해하는 데 도움이 됩니다.

## 1단계: 새 프로젝트 만들기

1. Visual Studio를 열고 새 콘솔 애플리케이션 프로젝트를 만듭니다.
2. 프로젝트 이름을 적절하게 지정하세요.

## 2단계: Aspose.PDF 참조 추가

1. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 버튼으로 클릭합니다.
2. NuGet 패키지 관리를 선택합니다.
3. Aspose.PDF를 검색하여 최신 버전을 설치하세요.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

이제 모든 것이 설정되었으니, 코드를 살펴보겠습니다!

## 3단계: 문서 디렉토리 설정

PDF가 저장될 경로를 지정하세요:

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` PDF를 저장하려는 컴퓨터의 실제 경로를 입력하세요.

## 4단계: 문서 인스턴스 생성

새 PDF 문서 초기화:

```csharp
// 문서 인스턴스 생성
Document doc = new Document();
```

## 5단계: 문서에 페이지 추가

모든 PDF에는 최소한 한 페이지가 필요합니다. 하나를 추가해 보겠습니다.

```csharp
// PDF 파일의 페이지 컬렉션에 페이지 추가
Page page = doc.Pages.Add();
```

## 6단계: 그래프 인스턴스 생성

 에이`Graph` 인스턴스는 모양을 그리기 위한 캔버스 역할을 합니다.

```csharp
// 그래프 인스턴스 생성
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## 7단계: 페이지에 그래프 추가

그래프를 페이지에 첨부하세요.

```csharp
// 페이지 인스턴스의 문단 컬렉션에 그래프 객체 추가
page.Paragraphs.Add(graph);
```

## 8단계: 사각형 인스턴스 생성

사각형의 위치와 크기를 정의합니다.

```csharp
// Rectangle 인스턴스 생성
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## 9단계: 채우기 색상 지정

사각형의 색상을 선택하세요. 이 예에서는 빨간색을 사용하겠습니다.

```csharp
// 그래프 객체에 대한 채우기 색상 지정
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## 10단계: 그래프에 사각형 추가

그래프에 사각형을 추가합니다.

```csharp
// Graph 객체의 모양 컬렉션에 사각형 객체 추가
graph.Shapes.Add(rect);
```

## 11단계: PDF 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// PDF 파일 저장
doc.Save(dataDir);
```

## 12단계: 확인 메시지

성공을 나타내는 확인 메시지를 인쇄합니다.

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## 결론

축하합니다! Aspose.PDF for .NET을 사용하여 PDF 문서에 채워진 사각형을 성공적으로 만들었습니다. 이 강력한 라이브러리는 PDF 조작에 대한 가능성의 세계를 열어주어 프로그래밍 방식으로 멋진 문서를 생성할 수 있습니다. 보고서, 송장 또는 다른 유형의 PDF를 만들든 Aspose.PDF가 해결해 드립니다.

## 자주 묻는 질문

### .NET용 Aspose.PDF란 무엇인가요?
.NET용 Aspose.PDF는 개발자가 프로그래밍 방식으로 PDF 문서를 만들고, 조작하고, 변환할 수 있는 라이브러리입니다.

### Aspose.PDF를 무료로 사용할 수 있나요?
 네, Aspose는 라이브러리의 기능을 탐색하는 데 사용할 수 있는 무료 평가판 버전을 제공합니다. 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.PDF에 대한 지원을 받을 수 있는 방법이 있나요?
 물론입니다! Aspose 포럼을 통해 지원을 받을 수 있습니다.[여기](https://forum.aspose.com/c/pdf/10).

### Aspose.PDF를 어떻게 구매할 수 있나요?
 구매 페이지를 방문하여 Aspose.PDF를 구매하실 수 있습니다.[여기](https://purchase.aspose.com/buy).

### Aspose.PDF로 어떤 유형의 모양을 만들 수 있나요?
Aspose.PDF 라이브러리를 사용하면 사각형, 원, 선 등 다양한 모양을 만들 수 있습니다.