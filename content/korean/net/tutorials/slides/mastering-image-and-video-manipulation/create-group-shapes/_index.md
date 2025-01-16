---
title: Aspose.Slides for .NET을 사용하여 PowerPoint에서 그룹 모양 만들기
linktitle: Aspose.Slides for .NET을 사용하여 PowerPoint에서 그룹 모양 만들기
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 그룹 모양을 만들고 관리하는 방법을 알아보세요. 이 포괄적인 가이드는 명확하고 단계별 지침을 제공합니다.
type: docs
weight: 11
url: /ko/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## 소개

PowerPoint 프레젠테이션의 시각적 매력과 구성을 강화하면 청중의 참여에 상당한 영향을 미칠 수 있습니다. 이를 달성하는 효과적인 방법 중 하나는 그룹 모양을 사용하는 것입니다. 이 튜토리얼에서는 Aspose.Slides for .NET을 활용하여 프레젠테이션에서 그룹 모양을 만들고 조작하는 방법을 살펴보겠습니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.Slides: Aspose.Slides 라이브러리의 최신 버전을 다운로드하여 설치하세요.[Aspose 웹사이트](https://releases.aspose.com/slides/net/).
- 개발 환경: Visual Studio와 같은 .NET 호환 IDE를 설정하여 프로젝트 작업을 진행하세요.
- 기본 C# 지식: 기본 C# 개념에 익숙해지세요.


## 필요한 네임스페이스 가져오기

C# 프로젝트에서 다음 네임스페이스를 포함하여 시작합니다.

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## 1단계: 프레젠테이션 클래스 인스턴스화

 인스턴스를 생성합니다`Presentation`슬라이드 작업을 할 클래스입니다. 문서가 저장된 디렉토리를 지정하세요:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // 모양을 만들고 조작하는 단계는 여기에 있습니다.
}
```

## 2단계: 첫 번째 슬라이드에 액세스

새로 만든 프레젠테이션의 첫 번째 슬라이드를 검색합니다.

```csharp
ISlide slide = pres.Slides[0];
```

## 3단계: Shape 컬렉션에 액세스

슬라이드에서 모양 모음을 가져오세요:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## 4단계: 그룹 모양 추가

이제 슬라이드에 그룹 모양을 추가할 시간입니다.

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## 5단계: 그룹 내부에 모양 추가

사각형과 같은 개별 모양으로 그룹 모양을 채울 수 있습니다.

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // 모양 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // 모양 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // 모양 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // 모양 4
```

## 6단계: 그룹 모양의 프레임 정의

그룹 모양에 대한 프레임을 설정하면 정의된 경계가 지정됩니다.

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## 7단계: 프레젠테이션 저장

마지막으로 수정된 프레젠테이션을 지정된 디렉토리에 저장합니다.

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## 결론

축하합니다! Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션에서 그룹 모양을 성공적으로 만들었습니다. 이런 방식으로 모양을 구성하면 콘텐츠의 시각적 레이아웃과 명확성을 크게 개선하여 프레젠테이션을 더욱 강렬하게 만들 수 있습니다.

## 자주 묻는 질문

### Aspose.Slides는 최신 버전의 .NET과 호환됩니까?

 네, Aspose.Slides는 최신 .NET 버전과의 호환성을 위해 정기적으로 업데이트됩니다.[선적 서류 비치](https://reference.aspose.com/slides/net/) 최신 호환성 세부 정보를 확인하세요.

### 구매하기 전에 Aspose.Slides를 사용해볼 수 있나요?

 물론입니다! 무료 체험판을 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Slides 관련 쿼리에 대한 지원은 어디에서 찾을 수 있나요?

 Aspose.Slides를 방문하세요[법정](https://forum.aspose.com/c/slides/11) 지역사회의 지원과 토론을 위해.

### Aspose.Slides에 대한 임시 라이선스를 어떻게 얻을 수 있나요?

 임시 면허를 요청할 수 있습니다.[여기](https://purchase.aspose.com/temporary-license/).

### Aspose.Slides의 전체 라이선스는 어디에서 구매할 수 있나요?

 라이센스는 다음에서 구매할 수 있습니다.[구매 페이지](https://purchase.aspose.com/buy).