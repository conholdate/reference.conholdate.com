---
title: PowerPoint 타임라인에서 오디오 추출
linktitle: 타임라인에서 오디오 추출
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션에서 오디오 파일을 손쉽게 추출하는 방법을 알아보세요. 이 단계별 가이드는 명확한 지침을 제공합니다.
type: docs
weight: 13
url: /ko/net/tutorials/slides/extract-audio-and-video/extracting-audio-from-timeline/
---
## 소개

멀티미디어 프레젠테이션의 영역에서 사운드는 시청자의 경험을 향상시키고 메시지를 효과적으로 전달하는 데 중요한 역할을 합니다. PowerPoint 프레젠테이션에서 오디오를 추출하려는 경우 Aspose.Slides for .NET이 간단한 솔루션을 제공합니다. 이 단계별 가이드는 이 강력한 라이브러리를 사용하여 PowerPoint 프레젠테이션에서 오디오를 추출하는 과정을 안내합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  .NET 라이브러리용 Aspose.Slides: .NET 라이브러리용 Aspose.Slides를 다운로드하여 설치하세요.[여기](https://releases.aspose.com/slides/net/).

2. PowerPoint 프레젠테이션: 오디오를 추출할 PowerPoint 프레젠테이션(PPTX) 파일을 준비하세요. 편리한 디렉토리에 저장하세요.

3. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 코드 예제를 따라가는 데 도움이 됩니다.

모든 것이 준비되었으니, 추출 과정을 시작해볼까요!

## 1단계: 필요한 네임스페이스 가져오기

먼저, C# 프로젝트에 필요한 네임스페이스를 포함해야 합니다. 파일 맨 위에 다음 코드를 추가합니다.

```csharp
using Aspose.Slides;
using System.IO;
```

## 2단계: PowerPoint 프레젠테이션 로드

추출 프로세스의 첫 번째 단계는 PowerPoint 파일을 로드하는 것입니다. 방법은 다음과 같습니다.

```csharp
string dataDir = "Your Document Directory";
string pptxFile = Path.Combine(dataDir, "AnimationAudio.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // 오디오 추출을 진행하세요
}
```

 교체를 꼭 해주세요`"Your Document Directory"` 프레젠테이션이 저장된 실제 경로를 사용합니다.

## 3단계: 슬라이드 및 타임라인 액세스

다음으로, 오디오를 추출하려는 특정 슬라이드에 액세스해야 합니다.

```csharp
ISlide slide = pres.Slides[0]; // 첫 번째 슬라이드에 접근하세요
```

필요한 경우 다른 슬라이드를 대상으로 인덱스를 변경할 수 있습니다.

## 4단계: 효과 시퀀스 추출

이제 슬라이드에 액세스할 수 있으므로 오디오 트랙이 포함된 효과 시퀀스를 검색할 수 있습니다.

```csharp
ISequence effectsSequence = slide.Timeline.MainSequence;
```

## 5단계: 오디오를 바이트 배열로 추출

추출하려는 오디오가 시퀀스의 첫 번째 효과라고 가정하면 다음과 같이 추출할 수 있습니다.

```csharp
byte[] audio = effectsSequence[0].Sound.BinaryData;
```

오디오가 다른 위치에 있는 경우 인덱스도 이에 맞게 조정하세요.

## 6단계: 추출된 오디오 저장

마지막으로 추출된 오디오를 파일에 저장합니다. 방법은 다음과 같습니다.

```csharp
string outMediaPath = Path.Combine(RunExamples.OutPath, "MediaTimeline.mpg");
File.WriteAllBytes(outMediaPath, audio);
```

 이 코드는 오디오를 다음과 같이 저장합니다.`MediaTimeline.mpg` 지정한 출력 디렉토리에.

## 결론

Aspose.Slides for .NET을 사용하면 PowerPoint 프레젠테이션에서 오디오를 추출하는 과정이 매끄럽습니다. 이 가이드에서는 몇 줄의 C# 코드를 사용하여 효율적으로 오디오를 추출하는 방법을 보여주었습니다. 이 기능을 활용하면 매력적인 멀티미디어 콘텐츠로 프레젠테이션을 향상시킬 수 있습니다.

## 자주 묻는 질문

### PowerPoint 프레젠테이션의 특정 슬라이드에서 오디오를 추출할 수 있나요?

네, 코드에서 슬라이드 인덱스를 수정하면 모든 슬라이드에서 오디오를 추출할 수 있습니다.

### 추출한 오디오는 어떤 오디오 형식으로 저장할 수 있나요?

.NET용 Aspose.Slides를 사용하면 추출된 오디오를 MP3, WAV 등 다양한 형식으로 저장할 수 있습니다.

### .NET용 Aspose.Slides가 최신 버전의 PowerPoint와 호환됩니까?

네, Aspose.Slides for .NET은 최신 릴리스를 포함한 다양한 버전의 PowerPoint와 호환되도록 설계되었습니다.

### Aspose.Slides를 사용하여 추출한 오디오를 조작하고 편집할 수 있나요?

물론입니다! Aspose.Slides는 오디오가 추출되면 오디오 조작 및 편집을 위한 광범위한 기능을 제공합니다.

### Aspose.Slides for .NET에 대한 포괄적인 문서는 어디에서 찾을 수 있나요?

 Aspose.Slides for .NET에 대한 자세한 설명서와 예제에 액세스할 수 있습니다.[여기](https://reference.aspose.com/slides/net/).
