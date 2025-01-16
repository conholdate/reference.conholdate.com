---
title: Aspose.Slides를 사용하여 프레젠테이션의 요약 확대/축소 만들기
linktitle: Aspose.Slides를 사용하여 프레젠테이션의 요약 확대/축소 만들기
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 시각적으로 매력적인 요약 확대/축소를 만들어 프레젠테이션 기술을 향상시키는 방법을 알아보세요. 이 단계별 튜토리얼은 프레젠테이션 설정부터 슬라이드 사용자 지정 및 대화형 요소 추가까지 모든 것을 다룹니다.
type: docs
weight: 16
url: /ko/net/tutorials/slides/mastering-image-and-video-manipulation/create-summary-zoom/
---
## 소개

빠르게 움직이는 프레젠테이션 영역에서 Aspose.Slides for .NET은 슬라이드 제작 경험을 향상시키는 강력한 도구로 등장합니다. 두드러지는 기능 중 하나는 요약 확대/축소로, 슬라이드 모음을 시각적으로 매력적인 방식으로 제시합니다. 이 튜토리얼에서는 Aspose.Slides for .NET을 사용하여 프레젠테이션에서 요약 확대/축소를 만드는 과정을 안내합니다.

## 필수 조건

튜토리얼을 시작하기에 앞서 다음 사항이 설정되어 있는지 확인하세요.

-  .NET용 Aspose.Slides: 라이브러리를 다운로드하여 설치하세요.[릴리스 페이지](https://releases.aspose.com/slides/net/).
- 개발 환경: .NET 개발을 위해 Visual Studio나 선호하는 IDE를 사용하세요.
- C#에 대한 기본 지식: 이 튜토리얼을 이해하려면 C# 프로그래밍에 대한 지식이 필요합니다.

## 필요한 네임스페이스 가져오기

Aspose.Slides 기능에 액세스하려면 C# 프로젝트 시작 시 필요한 네임스페이스를 포함시켜 시작하세요.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## 1단계: 프레젠테이션 설정

먼저 새 프레젠테이션을 만듭니다.`using` 이 문장은 프레젠테이션이 닫힐 때 리소스가 제대로 해제되도록 보장합니다. 결과 파일의 경로와 파일 이름을 다음과 같이 지정합니다.`resultPath` 변하기 쉬운:

```csharp
string dataDir = "Your Documents Directory";
string resultPath = Path.Combine(dataDir, "SummaryZoomPresentation.pptx");

using (Presentation pres = new Presentation())
{
    // 여기에서 슬라이드와 섹션을 만들어 보세요.
    // ...
    
    // 프레젠테이션 저장
    pres.Save(resultPath, SaveFormat.Pptx);
}
```

## 2단계: 슬라이드 및 섹션 추가

 다음으로 개별 슬라이드를 만들고 섹션으로 구성합니다.`AddEmptySlide` 새로운 슬라이드를 추가하고 활용하는 방법`Sections.AddSection` 더 나은 조직을 위한 방법:

```csharp
ISlide slide = pres.Slides.AddEmptySlide(pres.Slides[0].LayoutSlide);
// 여기에서 슬라이드를 사용자 지정하세요
// ...
pres.Sections.AddSection("Section 1", slide);
// 추가 섹션(섹션 2, 섹션 3, 섹션 4)에 대해 반복합니다.
```

## 3단계: 슬라이드 배경 사용자 지정

배경을 사용자 지정하여 각 슬라이드의 시각적 매력을 향상시킵니다. 채우기 유형, 단색 채우기 색상 및 배경 유형을 설정합니다.

```csharp
slide.Background.FillFormat.FillType = FillType.Solid;
slide.Background.FillFormat.SolidFillColor.Color = Color.Brown; // 원하는 색상을 선택하세요
slide.Background.Type = BackgroundType.OwnBackground;
// 다른 색상을 사용하여 다른 슬라이드에 대한 사용자 정의를 반복합니다.
```

## 4단계: 요약 확대 프레임 추가

프레젠테이션의 섹션을 연결하는 시각적 요소 역할을 하는 요약 확대 프레임을 만듭니다.`AddSummaryZoomFrame` 지정된 슬라이드에 이 기능을 추가하는 방법:

```csharp
ISummaryZoomFrame summaryZoomFrame = pres.Slides[0].Shapes.AddSummaryZoomFrame(150, 50, 300, 200);
// 필요에 따라 좌표와 치수를 조정하세요
```

## 5단계: 프레젠테이션 저장

마지막으로, 프레젠테이션을 원하는 파일 경로에 저장합니다. 이 단계는 모든 변경 사항이 보존되도록 합니다.

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

이러한 단계를 거치면 Aspose.Slides for .NET을 사용하여 시각적으로 매력적인 요약 확대/축소 프레임을 특징으로 하는 깔끔하게 구성된 프레젠테이션을 만들 수 있습니다.

## 결론

Aspose.Slides for .NET은 프레젠테이션을 한 단계 업그레이드할 수 있는 기능을 제공하며, 요약 확대 기능은 전문성과 참여도를 더해줍니다. 설명된 단계를 따르면 최소한의 노력으로 슬라이드의 시각적 매력을 강화할 수 있습니다.

## 자주 묻는 질문

### 요약 확대 프레임의 모양을 사용자 지정할 수 있나요?
네, 디자인 요구 사항에 맞게 좌표와 치수를 조정할 수 있습니다.

### Aspose.Slides는 최신 .NET 버전과 호환됩니까?
네, Aspose.Slides는 최신 .NET 버전과의 호환성을 위해 정기적으로 업데이트됩니다.

### 요약 확대/축소 프레임에 하이퍼링크를 추가할 수 있나요?
물론입니다! 슬라이드에 추가된 하이퍼링크는 요약 줌 프레임 내에서 원활하게 작동합니다.

### 프레젠테이션의 섹션 수에 제한이 있습니까?
현재 프레젠테이션에 추가할 수 있는 섹션 수에 엄격한 제한은 없습니다.

### Aspose.Slides의 평가판이 있나요?
 예, Aspose.Slides 기능을 다운로드하면 탐색할 수 있습니다.[무료 체험판](https://releases.aspose.com/).
