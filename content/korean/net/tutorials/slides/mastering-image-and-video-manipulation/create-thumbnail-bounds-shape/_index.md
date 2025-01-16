---
title: Aspose.Slides에서 모양에 대한 경계가 있는 썸네일 만들기
linktitle: Aspose.Slides에서 모양에 대한 경계가 있는 썸네일 만들기
second_title: Aspose.Slides .NET PowerPoint 처리 API
description: .NET용 Aspose.Slides를 사용하여 PowerPoint 프레젠테이션의 모양에 대한 정의된 경계가 있는 썸네일 이미지를 만드는 방법을 알아보세요. 이 포괄적인 가이드는 단계별 지침을 제공합니다.
type: docs
weight: 10
url: /ko/net/tutorials/slides/mastering-image-and-video-manipulation/create-thumbnail-bounds-shape/
---
## 소개

PowerPoint 프레젠테이션에서 모양에 대한 경계가 있는 썸네일 이미지를 생성하는 효율적인 방법을 찾고 있는 .NET 개발자라면 Aspose.Slides for .NET이 고려할 만한 훌륭한 도구입니다. 이 강력한 라이브러리는 PowerPoint 파일 조작을 간소화하여 귀중한 데이터를 원활하게 추출하고 작업할 수 있도록 합니다. 이 튜토리얼에서는 모양에 대한 경계가 있는 썸네일을 만드는 과정을 안내합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  .NET 라이브러리용 Aspose.Slides: 여기에서 다운로드하여 설치하세요.[Aspose 사이트](https://releases.aspose.com/slides/net/).
2.  파일 경로: 바꾸기`"Your Documents Directory"` 문서의 실제 경로를 코드에 넣습니다.

## 필요한 네임스페이스 가져오기

Aspose.Slides의 기능을 활용하려면 먼저 프로젝트 시작 시 필요한 네임스페이스를 가져옵니다.

```csharp
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Slides;
```

## 1단계: 프레젠테이션 클래스 인스턴스화

 먼저 초기화해야 합니다.`Presentation` PowerPoint 파일을 나타내는 클래스:

```csharp
string dataDir = "Your Documents Directory\\";
using (Presentation presentation = new Presentation(dataDir + "HelloWorld.pptx"))
{
    // 이제 프레젠테이션 객체를 조작할 준비가 되었습니다.
}
```

 사용하여`using` 여기에 명시된 내용은 작업이 끝난 후 리소스가 적절히 해제되도록 보장합니다.

## 2단계: 모양 경계가 있는 썸네일 이미지 만들기

다음으로, 지정된 경계를 사용하여 프레젠테이션의 도형의 축소판 이미지를 만듭니다.

```csharp
using (Bitmap bitmap = presentation.Slides[0].Shapes[0].GetThumbnail(ShapeThumbnailBounds.Appearance, 1, 1))
{
    // 이제 비트맵에는 정의된 범위 내의 썸네일 이미지가 포함됩니다.
}
```

 이 스니펫에서는`ShapeThumbnailBounds.Appearance` 모양의 모양 경계를 원한다는 것을 지정합니다. 출력 요구 사항에 따라 필요에 따라 너비와 높이에 대한 매개변수(1, 1)를 조정합니다.

## 3단계: 썸네일 이미지를 디스크에 저장

마지막으로 생성된 썸네일 이미지를 PNG와 같은 원하는 형식으로 저장합니다.

```csharp
bitmap.Save(dataDir + "Shape_thumbnail_Bound_Shape_out.png", ImageFormat.Png);
```

여기에서는 프로젝트 요구 사항에 맞게 파일 이름과 형식을 사용자 지정할 수 있습니다.

축하합니다! Aspose.Slides for .NET을 사용하여 모양에 대한 경계가 있는 썸네일을 성공적으로 만들었습니다. 이 프로세스는 간단하며 .NET 애플리케이션에 쉽게 통합할 수 있습니다.

## 결론

Aspose.Slides for .NET은 PowerPoint 프레젠테이션을 제작하고 관리하는 작업을 간소화하여 개발자에게 썸네일 등을 만드는 강력한 도구를 제공합니다. 이 가이드를 따르면 프로젝트에서 이 라이브러리를 효율적으로 사용하는 데 필요한 필수 단계를 알게 됩니다.

## 자주 묻는 질문

### Aspose.Slides는 최신 .NET 프레임워크와 호환됩니까?

네, Aspose.Slides는 .NET 프레임워크의 최신 버전을 지원하도록 자주 업데이트됩니다.

### Aspose.Slides를 상업 프로젝트에 사용할 수 있나요?

 물론입니다! Aspose.Slides는 개인 및 상업적 사용에 적합한 다양한 라이선스 옵션을 제공합니다. 확인[여기](https://purchase.aspose.com/buy) 자세한 내용은.

### 무료 체험판이 있나요?

 네! 무료 체험판을 통해 Aspose.Slides의 기능을 탐색할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Slides에 대한 지원은 어떻게 받을 수 있나요?

도움이 필요하면 다음을 방문하세요.[Aspose.Slides 포럼](https://forum.aspose.com/c/slides/11) 커뮤니티와 경험이 풍부한 개발자들과 소통하세요.

### Aspose.Slides에 대한 임시 라이선스를 얻을 수 있나요?

 네, 단기 프로젝트를 위한 임시 라이센스를 취득할 수 있습니다.[여기](https://purchase.aspose.com/temporary-license/).