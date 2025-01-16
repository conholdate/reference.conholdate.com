---
title: .NET 프레젠테이션에 내장된 비디오 프레임 추가
linktitle: .NET 프레젠테이션에 내장된 비디오 프레임 추가
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 비디오를 임베드하는 방법을 배우면 프레젠테이션의 잠재력을 끌어낼 수 있습니다. 이 포괄적인 튜토리얼은 멀티미디어 요소를 통합하는 단계별 프로세스를 안내합니다.
type: docs
weight: 19
url: /ko/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## 소개

오늘날의 빠르게 움직이는 프레젠테이션 환경에서 멀티미디어 요소를 통합하면 참여도와 청중 유지도를 크게 높일 수 있습니다. Aspose.Slides for .NET은 슬라이드에 비디오 프레임을 임베드하기 위한 강력한 솔루션을 제공합니다. 이 튜토리얼은 처음부터 끝까지 원활한 경험을 보장하면서 단계별로 프로세스를 안내합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET 라이브러리용 Aspose.Slides: 라이브러리를 다운로드하여 설치하세요.[릴리스 페이지](https://releases.aspose.com/slides/net/).
- 미디어 콘텐츠: 프레젠테이션에 포함하려는 비디오 파일(예: "Wildlife.mp4")입니다.

## 필요한 네임스페이스 가져오기

.NET 프로젝트에 필요한 네임스페이스를 가져오는 것으로 시작합니다.

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## 1단계: 디렉토리 설정

프로젝트에 문서 및 미디어 파일에 필요한 디렉토리가 포함되어 있는지 확인하세요.

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

// 디렉토리가 없으면 생성합니다.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## 2단계: 프레젠테이션 클래스 인스턴스화

 인스턴스를 생성합니다`Presentation` PPTX 파일을 나타내는 클래스:

```csharp
using (Presentation pres = new Presentation())
{
    // 첫 번째 슬라이드를 받으세요
    ISlide sld = pres.Slides[0];
```

## 3단계: 비디오 삽입

다음 코드를 사용하여 비디오를 프레젠테이션에 삽입하세요.

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## 4단계: 비디오 프레임 추가

다음으로, 슬라이드에 비디오 프레임을 추가합니다.

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## 5단계: 비디오 속성 구성

재생 모드 및 볼륨을 포함한 비디오 속성을 설정합니다.

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; // 비디오를 자동으로 재생합니다
vf.Volume = AudioVolumeMode.Loud; // 볼륨 레벨 설정
```

## 6단계: 프레젠테이션 저장

마지막으로 수정된 PPTX 파일을 디스크에 저장합니다.

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

프레젠테이션에 포함하려는 각 비디오에 대해 이 단계를 반복할 수 있습니다.

## 결론

축하합니다! Aspose.Slides for .NET을 사용하여 프레젠테이션에 비디오 프레임을 성공적으로 임베드했습니다. 이 역동적인 기능은 프레젠테이션을 한 단계 업그레이드하여 완벽하게 통합된 멀티미디어로 청중을 사로잡을 수 있습니다.

## 자주 묻는 질문

### 프레젠테이션의 모든 슬라이드에 비디오를 삽입할 수 있나요?

 네, 인덱스를 조정하여 원하는 슬라이드를 선택할 수 있습니다.`pres.Slides[index]`.

### 어떤 비디오 형식이 지원되나요?

Aspose.Slides는 MP4, AVI, WMV 등 다양한 비디오 형식을 지원합니다.

### 비디오 프레임의 크기와 위치를 사용자 지정할 수 있나요?

 물론입니다! 매개변수를 수정할 수 있습니다.`AddVideoFrame(x, y, width, height, video)` 귀하의 필요에 맞게.

### 삽입할 수 있는 비디오 수에 제한이 있나요?

내장된 비디오의 제한은 일반적으로 프레젠테이션 소프트웨어의 용량에 따라 달라집니다.

### 더 많은 도움을 구하거나, 내 경험을 공유할 수 있는 곳은 어디인가요?

 자유롭게 방문하세요[Aspose.Slides 포럼](https://forum.aspose.com/c/slides/11) 지역사회의 지원과 토론을 위해.