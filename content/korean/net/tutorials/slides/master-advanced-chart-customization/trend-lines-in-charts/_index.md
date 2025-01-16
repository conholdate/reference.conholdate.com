---
title: Aspose.Slides for .NET을 사용한 차트의 추세선
linktitle: Aspose.Slides for .NET을 사용한 차트의 추세선
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 차트에 추세선을 추가하고 사용자 지정하는 방법을 알아보세요. 이 포괄적인 가이드는 지수, 선형, 대수, 다항식 및 이동 평균 추세선을 다루어 데이터 시각화를 향상시킵니다.
type: docs
weight: 12
url: /ko/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## 소개  

차트에 추세선을 추가하는 것은 데이터 추세를 분석하고 미래 가치를 예측하는 데 중요한 기술입니다. Aspose.Slides for .NET을 사용하면 프레젠테이션 차트에 추세선을 원활하게 추가하고 사용자 지정하여 데이터 시각화를 향상시킬 수 있습니다. 이 가이드는 Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션에서 다양한 차트 유형에 추세선을 추가하는 방법에 대한 자세한 연습 과정을 제공합니다.  

## 필수 조건  

구현에 들어가기 전에 다음 설정이 있는지 확인하세요.  

1.  .NET용 Aspose.Slides: 라이브러리를 다운로드하여 설치하세요.[다운로드 페이지](https://releases.aspose.com/slides/net/).  
2. 개발 환경: Visual Studio와 같은 IDE를 사용하여 코딩하세요.  
3. 기본 C# 지식: 이 튜토리얼을 따르려면 C# 프로그래밍에 대한 지식이 필요합니다.  

## 필요한 네임스페이스 가져오기  

시작하려면 필수 네임스페이스를 프로젝트로 가져옵니다.  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## 1단계: 프레젠테이션 설정  

먼저, 빈 프레젠테이션을 초기화합니다. 이것은 차트의 컨테이너 역할을 할 것입니다.  

```csharp
string dataDir = "Your/Documents/Directory";

// 디렉토리가 존재하는지 확인하세요
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// 새로운 프레젠테이션 만들기
Presentation presentation = new Presentation();
```

## 2단계: 슬라이드에 차트 추가  

이제 슬라이드를 추가하고 클러스터형 막대형 차트를 포함하여 데이터를 시각화해 보세요.  

```csharp
// 빈 슬라이드 추가
ISlide slide = presentation.Slides[0];

// 클러스터형 막대형 차트 추가
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## 3단계: 차트 데이터 채우기  

차트에 샘플 데이터를 채웁니다.  

```csharp
// 기본 차트 데이터 통합 문서에 액세스
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// 기본 카테고리 및 시리즈 값 업데이트
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## 4단계: 추세선 추가  

### 지수 추세선  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### 선형 추세선  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### 대수 추세선  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### 이동 평균 추세선  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### 다항식 추세선  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### 전력 추세선  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## 5단계: 프레젠테이션 저장  

마지막으로 차트에 추가된 모든 추세선과 함께 프레젠테이션을 저장합니다.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## 결론  

Aspose.Slides for .NET을 사용하면 차트에 추세선을 추가하는 작업이 간단해집니다. 이 기능을 사용하면 데이터 추세를 효과적으로 표현하고 프레젠테이션에 전문적인 터치를 추가할 수 있습니다. 위의 단계에 따라 다양한 추세선 유형을 통합하고 데이터 시각화를 향상시킵니다.  

## 자주 묻는 질문  

### 추세선의 모양을 사용자 정의할 수 있나요?  
 예, 추세선의 색상, 두께 및 스타일을 사용자 정의할 수 있습니다.`Format.Line` 재산.  

### 다른 차트 유형도 지원되나요?  
네, .NET용 Aspose.Slides는 막대형, 원형, 선형 차트 등 다양한 차트 유형을 지원합니다.  

### 방정식과 R제곱 값을 어떻게 표시하나요?  
 할 수 있게 하다`DisplayEquation` 그리고`DisplayRSquaredValue` 차트에 이러한 값을 표시하기 위한 추세선 속성입니다.  

### Aspose.Slides for .NET을 다른 언어와 함께 사용할 수 있나요?  
네, 라이브러리는 VB.NET, F#을 포함하여 모든 .NET 지원 언어와 호환됩니다.  

### 추가 문서는 어디에서 확인할 수 있나요?  
 방문하세요[.NET 설명서용 Aspose.Slides](https://reference.aspose.com/slides/net/) 자세한 내용은.