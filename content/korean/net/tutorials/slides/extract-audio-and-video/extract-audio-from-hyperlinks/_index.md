---
title: Aspose.Slides를 사용하여 PowerPoint에서 하이퍼링크에서 오디오 추출
linktitle: 하이퍼링크에서 오디오 추출
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션의 하이퍼링크에서 오디오를 추출하는 방법을 알아보세요. 이 단계별 가이드는 명확한 지침을 제공합니다.
type: docs
weight: 12
url: /ko/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## 소개

멀티미디어 프레젠테이션에서 오디오는 슬라이드의 효과를 크게 향상시킵니다. 오디오 하이퍼링크가 있는 PowerPoint 프레젠테이션을 접하고 다른 용도로 오디오를 추출하는 방법을 궁금해 했다면, 당신은 올바른 곳에 있습니다. 이 가이드는 Aspose.Slides for .NET 라이브러리를 사용하여 PowerPoint 프레젠테이션의 하이퍼링크에서 오디오를 추출하는 과정을 안내합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

### .NET 라이브러리용 Aspose.Slides

 .NET 라이브러리용 Aspose.Slides가 설치되어 있는지 확인하세요. 아직 설치하지 않았다면 다음에서 다운로드할 수 있습니다.[.NET용 Aspose.Slides 설명서](https://reference.aspose.com/slides/net/).

### 오디오 하이퍼링크가 있는 PowerPoint 프레젠테이션

관련 오디오가 있는 하이퍼링크가 포함된 PowerPoint 프레젠테이션(PPTX)이 필요합니다. 이 프레젠테이션은 오디오 추출을 위한 소스가 될 것입니다.

## 필요한 네임스페이스 가져오기

.NET용 Aspose.Slides를 효과적으로 사용하려면 다음 네임스페이스를 C# 프로젝트로 가져와야 합니다.

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

이제 모든 것이 준비되었으니 추출 과정을 간단한 단계로 나누어 보겠습니다.

## 1단계: 문서 디렉토리 정의

 PowerPoint 프레젠테이션이 있는 디렉토리를 지정하여 시작하세요. 바꾸기`"Your Document Directory"` 실제 경로와 함께.

```csharp
string dataDir = "Your Document Directory";
```

## 2단계: PowerPoint 프레젠테이션 로드

 다음으로 오디오 하이퍼링크가 포함된 PowerPoint 프레젠테이션(PPTX)을 로드합니다. 바꾸기`"HyperlinkSound.pptx"` 실제 프레젠테이션 파일 이름을 사용하세요.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // 다음 단계로 넘어가세요.
}
```

## 3단계: 하이퍼링크 사운드에 액세스

첫 번째 슬라이드의 첫 번째 모양에서 하이퍼링크를 검색합니다. 이 하이퍼링크에 연관된 사운드가 있는 경우 추출을 진행할 수 있습니다.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // 다음 단계로 넘어가세요.
}
```

## 4단계: 하이퍼링크에서 오디오 추출

하이퍼링크에 사운드가 포함되어 있으면 이를 바이트 배열로 추출해서 미디어 파일로 저장할 수 있습니다.

```csharp
// 하이퍼링크 사운드를 바이트 배열로 추출합니다.
byte[] audioData = link.Sound.BinaryData;

// 추출된 오디오를 저장할 경로를 지정하세요
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// 추출된 오디오를 미디어 파일에 저장합니다.
File.WriteAllBytes(outMediaPath, audioData);
```

축하합니다! Aspose.Slides for .NET을 사용하여 PowerPoint 프레젠테이션의 하이퍼링크에서 오디오를 성공적으로 추출했습니다. 이제 이 오디오를 멀티미디어 프로젝트에서 사용할 수 있습니다.

## 결론

Aspose.Slides for .NET은 PowerPoint 프레젠테이션의 하이퍼링크에서 오디오를 추출하는 강력하고 사용자 친화적인 방법을 제공합니다. 이 가이드에 설명된 단계를 사용하면 프레젠테이션의 오디오 콘텐츠를 쉽게 재사용하여 프로젝트를 향상시킬 수 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.Slides는 무료 라이브러리입니까?
 아니요, Aspose.Slides for .NET은 상용 라이브러리이지만 무료 평가판을 다운로드하여 기능을 탐색할 수 있습니다.[여기](https://releases.aspose.com/).

### PPT와 같은 오래된 PowerPoint 형식에서 오디오를 추출할 수 있나요?
네, Aspose.Slides for .NET은 오디오 추출을 위해 PPTX와 PPT 형식을 모두 지원합니다.

### Aspose.Slides 지원을 위한 커뮤니티 포럼이 있나요?
 물론입니다! 도움을 받고 경험을 공유할 수 있습니다.[Aspose.Slides 커뮤니티 포럼](https://forum.aspose.com/).

### 단기 프로젝트를 위해 Aspose.Slides의 임시 라이선스를 구매할 수 있나요?
네, 단기 프로젝트에 필요한 임시 라이센스를 다음 사이트를 방문하여 얻을 수 있습니다.[이 링크](https://purchase.aspose.com/temporary-license/).

### MPG 외에 추출이 지원되는 다른 오디오 포맷이 있습니까?
네, Aspose.Slides for .NET은 다양한 오디오 포맷으로 추출할 수 있습니다. 추출 후 오디오를 원하는 포맷으로 변환할 수 있습니다.