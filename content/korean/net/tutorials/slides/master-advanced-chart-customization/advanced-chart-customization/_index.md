---
title: .NET용 Aspose.Slides를 사용한 고급 차트 사용자 지정
linktitle: .NET용 Aspose.Slides를 사용한 고급 차트 사용자 지정
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: 고급 차트 사용자 지정 기술을 마스터하여 .NET용 Aspose.Slides의 모든 잠재력을 활용하세요. 이 단계별 가이드는 기본 차트 생성부터 그리드 선, 축 제목, 사용자 지정 색상과 같은 복잡한 세부 사항까지 모든 것을 다룹니다.
type: docs
weight: 10
url: /ko/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## 소개

시각적으로 매력적이고 유익한 차트를 만드는 것은 효과적인 데이터 프레젠테이션에 필수적입니다. Aspose.Slides for .NET은 차트 사용자 정의를 위한 강력한 도구를 제공하여 차트의 모든 측면을 맞춤 설정할 수 있습니다. 이 튜토리얼에서는 Aspose.Slides for .NET을 사용하여 차트 사용자 정의를 위한 고급 기술을 살펴보겠습니다.

## 필수 조건

시작하기에 앞서 다음과 같은 전제 조건이 충족되었는지 확인하세요.

1.  .NET 라이브러리용 Aspose.Slides: Aspose.Slides 라이브러리를 다운로드하여 설치하세요.[여기](https://releases.aspose.com/slides/net/).
2. .NET 개발 환경: Visual Studio와 같은 .NET 개발 환경을 설정합니다.
3. C#에 대한 기본 지식: C# 코드를 작성하게 되므로 C# 프로그래밍에 익숙하면 도움이 됩니다.

이제 고급 차트 사용자 지정 과정을 명확한 단계로 나누어 보겠습니다.

## 1단계: 새 프레젠테이션 만들기

차트를 보관할 새 프레젠테이션을 만드는 것부터 시작하세요.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "Your Document Directory";

// 디렉토리가 없으면 생성합니다.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// 프레젠테이션을 인스턴스화합니다
Presentation pres = new Presentation();
```

## 2단계: 첫 번째 슬라이드에 액세스

다음으로, 차트를 추가하려는 첫 번째 슬라이드에 액세스합니다.

```csharp
// 첫 번째 슬라이드에 접근하세요
ISlide slide = pres.Slides[0];
```

## 3단계: 샘플 차트 추가

이제 슬라이드에 마커가 있는 선형 차트를 추가해 보겠습니다.

```csharp
// 샘플 차트 추가
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## 4단계: 차트 제목 설정

차트에 제목을 설정하면 중요한 맥락을 제공할 수 있습니다.

```csharp
// 차트 제목을 설정하세요
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 5단계: 주요 그리드 선 사용자 지정

가독성을 높이기 위해 값 축의 격자선을 향상시킬 수 있습니다.

```csharp
// 값 축에 대한 주요 그리드 선 사용자 정의
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## 6단계: 보조 그리드 선 사용자 정의

마찬가지로 값 축의 보조 격자선을 사용자 지정합니다.

```csharp
// 값 축에 대한 보조 그리드 선 사용자 정의
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## 7단계: 값 축 숫자 형식 정의

값 축에 표시되는 숫자의 서식을 지정할 수 있습니다.

```csharp
// 값 축 번호 형식 설정
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## 8단계: 최대값 및 최소값 설정

차트의 최대값과 최소값을 정의합니다.

```csharp
// 차트 최대값 및 최소값 설정
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## 9단계: 값 축 텍스트 속성 사용자 정의

값 축의 텍스트 속성을 향상시키면 가독성이 향상됩니다.

```csharp
// 값 축 텍스트 속성 사용자 정의
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## 10단계: 값 축 제목 추가

값 축에 제목을 추가하면 데이터가 나타내는 내용을 명확하게 알 수 있습니다.

```csharp
// 값 축 제목 설정
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 11단계: 카테고리 축에 대한 주요 그리드 선 사용자 정의

이제 카테고리 축의 주요 격자선을 강화해 보겠습니다.

```csharp
// 카테고리 축에 대한 주요 격자선 사용자 정의
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## 12단계: 카테고리 축에 대한 보조 그리드 선 사용자 정의

마찬가지로, 카테고리 축에 대한 보조 격자선을 사용자 정의합니다.

```csharp
// 카테고리 축에 대한 보조 그리드 선 사용자 정의
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## 13단계: 범주 축 텍스트 속성 사용자 정의

카테고리 축 라벨의 글꼴 스타일과 모양을 개선합니다.

```csharp
// 카테고리 축 텍스트 속성 사용자 정의
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## 14단계: 카테고리 축 제목 추가

필요한 경우 카테고리 축에 제목을 추가할 수도 있습니다.

```csharp
// 카테고리 축 제목 설정
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## 15단계: 추가 사용자 정의

범례, 벽 색상, 플롯 영역 설정 등의 추가 사용자 정의로 차트를 더욱 향상시켜 보세요.

```csharp
// 추가 사용자 정의(선택 사항)

// 범례 텍스트 속성 사용자 정의
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// 차트가 겹치지 않게 차트 범례 표시
chart.Legend.Overlay = true;

// 차트 뒷벽 색상 설정
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// 차트 바닥 색상 설정
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// 플롯 영역 색상 설정
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// 프레젠테이션 저장
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## 결론

이 포괄적인 가이드에서는 Aspose.Slides for .NET을 사용하여 고급 차트 사용자 지정 기술을 다루었습니다. 프레젠테이션을 만들고, 차트를 추가하고, 모양을 다듬고, 격자선, 축 레이블, 범례와 같은 다양한 차트 요소를 사용자 지정하는 방법을 배웠습니다. 

## 자주 묻는 질문

### Aspose.Slides for .NET에서는 어떤 버전의 .NET이 지원되나요?
Aspose.Slides for .NET은 .NET Framework 및 .NET Core를 포함한 다양한 .NET 버전을 지원합니다. 지원되는 버전의 전체 목록은 설명서를 참조하세요.

### Excel 파일과 같은 데이터 소스에서 차트를 만들 수 있나요?
네, Aspose.Slides를 사용하면 Excel 스프레드시트와 같은 외부 데이터 소스에서 차트를 만들 수 있습니다. 자세한 예는 설명서를 참조하세요.

### 차트 시리즈에 사용자 정의 데이터 레이블을 추가하려면 어떻게 해야 하나요?
 사용자 정의 데이터 레이블을 추가하려면`DataLabels` 시리즈의 속성을 조정하고 필요에 따라 레이블을 조정합니다. 설명서에서 코드 샘플을 찾을 수 있습니다.

### 차트를 PDF나 이미지 등 다른 형식으로 내보낼 수 있나요?
물론입니다! Aspose.Slides를 사용하면 차트가 있는 프레젠테이션을 PDF 및 이미지 형식을 포함한 다양한 형식으로 내보낼 수 있습니다.

### Aspose.Slides for .NET에 대한 더 많은 튜토리얼과 예제는 어디에서 찾을 수 있나요?
 Aspose.Slides를 방문하세요[웹사이트](https://reference.aspose.com/slides/net/) 광범위한 튜토리얼, 코드 예제 및 설명서를 제공합니다.