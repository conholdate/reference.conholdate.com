---
title: Aspose.Slides를 사용하여 PowerPoint 슬라이드에서 비디오 추출
linktitle: PowerPoint 슬라이드에서 비디오 추출
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션에서 내장된 비디오 파일을 쉽게 추출하는 방법을 알아보세요. 이 포괄적인 단계별 가이드는 환경 설정부터 추출된 비디오 저장까지 모든 것을 다룹니다.
type: docs
weight: 14
url: /ko/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## 소개

Aspose.Slides for .NET은 개발자가 PowerPoint 프레젠테이션과 프로그래밍 방식으로 상호 작용할 수 있는 강력한 라이브러리입니다. 이 가이드에서는 Aspose.Slides for .NET을 사용하여 PowerPoint 슬라이드에 포함된 비디오를 추출하는 과정을 안내합니다. 

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.Slides: 라이브러리를 얻고 설치하세요.[Aspose 웹사이트](https://purchase.aspose.com/buy).
-  PowerPoint 프레젠테이션: PowerPoint 파일을 준비하세요(예:`Video.pptx`)을 추출하려는 비디오와 함께 사용합니다.

## 필요한 네임스페이스

.NET용 Aspose.Slides를 사용하려면 적절한 네임스페이스를 가져와야 합니다. 코드에 다음을 포함합니다.

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## 1단계: 문서 디렉토리 지정

먼저, PowerPoint 프레젠테이션의 경로를 정의하세요.

```csharp
string dataDir = "Your Document Directory";
```

 바꾸다`"Your Document Directory"` PowerPoint 파일이 들어 있는 디렉토리의 실제 경로를 입력합니다.

## 2단계: 프레젠테이션 로드

 PowerPoint 프레젠테이션을 로드합니다.`Presentation` 물체:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 이것은 초기화됩니다`Presentation` 지정한 PowerPoint 파일에 개체를 추가합니다.

## 3단계: 슬라이드 및 도형 반복

다음으로, 프레젠테이션의 각 슬라이드를 반복하여 비디오 프레임을 확인합니다.

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // 비디오 추출을 진행하세요
        }
    }
}
```

## 4단계: 비디오 데이터 추출

비디오 프레임을 찾으면 해당 속성과 바이너리 데이터를 추출합니다.

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // 모양을 비디오 프레임으로 저장
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// 파일 확장자를 얻으세요
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## 5단계: 비디오 저장

마지막으로 추출한 비디오 데이터를 파일에 씁니다.

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

이 코드는 지정된 디렉토리에 새 파일을 만들고 비디오 데이터를 그 안에 씁니다.

## 결론

Aspose.Slides for .NET을 사용하면 PowerPoint 슬라이드에서 비디오를 추출하는 것이 간단한 프로세스입니다. 이 가이드를 따르면 .NET 애플리케이션 내에서 멀티미디어 콘텐츠를 쉽게 관리하여 사용자 경험과 기능을 풍부하게 할 수 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.Slides란 무엇인가요?
.NET용 Aspose.Slides는 PowerPoint 프레젠테이션을 다루기 위해 설계된 라이브러리로, 사용자가 프로그래밍 방식으로 프레젠테이션 파일을 만들고, 편집하고, 조작할 수 있도록 해줍니다.

### .NET용 Aspose.Slides에 대한 설명서는 어디에서 찾을 수 있나요?
 전체 문서에 접근할 수 있습니다[여기](https://reference.aspose.com/slides/net/).

### .NET용 Aspose.Slides를 무료 평가판으로 이용할 수 있나요?
 네, 무료 평가판을 다운로드할 수 있습니다.[이 링크](https://releases.aspose.com/).

### Aspose.Slides for .NET에 대한 임시 라이선스를 어떻게 얻을 수 있나요?
 임시 면허 신청이 가능합니다.[여기](https://purchase.aspose.com/temporary-license/).

### .NET용 Aspose.Slides에 대한 지원은 어디에서 받을 수 있나요?
 지원은 다음을 통해 제공됩니다.[Aspose.Slides 포럼](https://forum.aspose.com/).