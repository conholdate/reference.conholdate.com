---
title: PowerPoint에서 오디오 및 비디오 추출
linktitle: PowerPoint에서 오디오 및 비디오 추출
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션에서 오디오 및 비디오 요소를 손쉽게 추출하는 방법을 알아보세요. 이 자세한 가이드는 단계별 접근 방식을 제공합니다.
type: docs
weight: 10
url: /ko/net/tutorials/slides/extract-audio-and-video/extracting-audio-and-video/
---
## 소개

오늘날의 디지털 환경에서 멀티미디어 프레젠테이션은 커뮤니케이션, 교육 및 엔터테인먼트에서 중요한 역할을 합니다. PowerPoint 슬라이드는 종종 오디오 및 비디오 요소를 통합하여 정보를 효과적으로 전달하는 데 필수적입니다. 보관, 콘텐츠 재활용 또는 프레젠테이션 향상을 위해 이러한 멀티미디어 구성 요소를 추출하는 것이 종종 필요합니다.

이 가이드에서는 Aspose.Slides for .NET을 사용하여 PowerPoint 슬라이드에서 오디오 및 비디오를 추출하는 과정을 안내합니다. Aspose.Slides는 .NET 개발자가 PowerPoint 프레젠테이션을 프로그래밍 방식으로 조작하여 멀티미디어 추출 작업을 간소화할 수 있는 강력한 라이브러리입니다.

## 필수 조건

시작하기 전에 다음 사항이 설정되어 있는지 확인하세요.

1. Visual Studio: .NET 개발을 위해 Visual Studio가 설치되어 있는지 확인하세요.
2.  .NET용 Aspose.Slides: Aspose.Slides for .NET을 다운로드하여 설치하세요.[Aspose 웹사이트](https://releases.aspose.com/slides/net/).
3. PowerPoint 프레젠테이션: 연습을 위해 오디오 및 비디오 요소가 포함된 PowerPoint 프레젠테이션을 준비하세요.

이러한 전제 조건을 갖추었으니 추출 과정을 시작해 보겠습니다.

## PowerPoint 슬라이드에서 오디오 추출

### 1단계: 프로젝트 설정

Visual Studio에서 새 프로젝트를 만들고 필요한 Aspose.Slides 네임스페이스를 가져옵니다.

```csharp
using Aspose.Slides;
using Aspose.Slides.SlideShow;
```

### 2단계: 프레젠테이션 로드

추출하려는 오디오가 포함된 PowerPoint 프레젠테이션을 로드합니다.

```csharp
string dataDir = "Your Document Directory";
string presName = dataDir + "AudioSlide.ppt";
Presentation pres = new Presentation(presName);
```

### 3단계: 원하는 슬라이드에 액세스

 사용하세요`ISlide` 특정 슬라이드에 접근하기 위한 인터페이스:

```csharp
ISlide slide = pres.Slides[0]; // 첫 번째 슬라이드에 접근하세요
```

### 4단계: 오디오 추출

슬라이드의 전환 효과에서 오디오 데이터를 검색합니다.

```csharp
ISlideShowTransition transition = slide.SlideShowTransition;
byte[] audio = transition.Sound.BinaryData;
System.Console.WriteLine("Audio Length: " + audio.Length);
```

## PowerPoint 슬라이드에서 비디오 추출

### 1단계: 프로젝트 설정

오디오 추출과 마찬가지로 새 프로젝트를 만들고 필요한 네임스페이스를 가져오는 것으로 시작합니다.

### 2단계: 프레젠테이션 로드

추출하려는 비디오가 포함된 PowerPoint 프레젠테이션을 로드합니다.

```csharp
string dataDir = "Your Document Directory";
string presName = dataDir + "Video.pptx";
Presentation pres = new Presentation(presName);
```

### 3단계: 슬라이드 및 도형 반복

슬라이드와 모양을 반복하여 비디오 프레임을 식별합니다.

```csharp
foreach (ISlide slide in pres.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is IVideoFrame videoFrame)
        {
            // 비디오 프레임 정보 추출
            string contentType = videoFrame.EmbeddedVideo.ContentType;
            string fileType = contentType.Substring(contentType.LastIndexOf('/') + 1);
            
            // 비디오 데이터를 바이트 배열로 가져오기
            byte[] buffer = videoFrame.EmbeddedVideo.BinaryData;
            
            // 비디오를 파일로 저장
            using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileType, FileMode.Create, FileAccess.Write, FileShare.Read))
            {
                stream.Write(buffer, 0, buffer.Length);
            }
        }
    }
}
```

## 결론

Aspose.Slides for .NET을 사용하면 PowerPoint 프레젠테이션에서 오디오와 비디오를 쉽게 추출할 수 있습니다. 콘텐츠를 보관하든, 멀티미디어를 재활용하든, 프레젠테이션을 분석하든, 이 라이브러리는 프로세스를 간소화하는 데 필요한 도구를 제공합니다.

## 자주 묻는 질문

### .NET용 Aspose.Slides가 최신 PowerPoint 형식과 호환됩니까?
예, Aspose.Slides for .NET은 PPTX를 포함한 최신 PowerPoint 형식을 지원합니다.

### 한 번에 여러 슬라이드에서 오디오와 비디오를 추출할 수 있나요?
물론입니다! 여러 슬라이드를 반복하고 각각에서 멀티미디어를 추출하도록 코드를 수정할 수 있습니다.

### Aspose.Slides for .NET에 대한 라이선스 옵션은 있나요?
 Aspose는 무료 평가판 및 임시 라이선스를 포함하여 다양한 라이선스 옵션을 제공합니다. 방문하세요[웹사이트](https://purchase.aspose.com/buy) 자세한 내용은.

### .NET용 Aspose.Slides에 대한 지원을 어떻게 받을 수 있나요?
 기술 지원 및 커뮤니티 토론을 위해 Aspose.Slides를 확인하세요.[법정](https://forum.aspose.com/).

### Aspose.Slides for .NET으로 어떤 다른 작업을 수행할 수 있나요?
 Aspose.Slides for .NET은 PowerPoint 프레젠테이션을 만들고, 수정하고, 변환하는 것을 포함한 광범위한 기능을 제공합니다. 자세한 내용은 설명서를 살펴보세요.[.NET용 Aspose.Slides 설명서](https://reference.aspose.com/slides/net/).