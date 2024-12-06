---
title: 1Bpp 색인 생성
linktitle: 1Bpp 색인 생성
second_title: Aspose.Words 문서 처리 API
description: 이 가이드에서는 보관, 인쇄 또는 공간 절약 목적으로 1Bpp 인덱스 이미지를 효율적으로 만드는 데 도움이 되는 단계별 지침과 샘플 코드를 제공합니다.
type: docs
weight: 10
url: /ko/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## 소개

Word 문서를 흑백 이미지로 변환해야 했던 적이 있나요? 디지털 보관, 인쇄 또는 단순히 공간 절약을 위해 문서를 1Bpp 인덱스 이미지로 변환하는 것은 매우 유용할 수 있습니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 이를 달성하는 간단한 방법을 살펴보겠습니다. 시작해 볼까요!

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.Words: 라이브러리를 다운로드하고 설치하세요.[여기](https://releases.aspose.com/words/net/).
- .NET 개발 환경: Visual Studio가 인기 있는 선택이기는 하지만 .NET을 지원하는 IDE라면 무엇이든 작동합니다.
- 기본 C# 지식: C#에 대해 알고 있으면 도움이 되지만, 여기서는 간단하게 설명하겠습니다.
- 샘플 Word 문서: 변환할 문서를 준비하세요.

## 1단계: 필요한 네임스페이스 가져오기

Aspose.Words를 사용하려면 관련 네임스페이스를 가져와야 합니다. 이는 문서 조작에 필요한 클래스와 메서드에 액세스하는 데 필수적입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 2단계: 문서 디렉토리 설정

Word 문서가 저장되어 있는 디렉토리 경로와 변환된 이미지를 저장할 디렉토리 경로를 지정하세요.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## 3단계: Word 문서 로드

Word 문서를 로드하세요`Aspose.Words.Document` 객체. 이 객체를 사용하면 문서를 프로그래밍 방식으로 조작할 수 있습니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 4단계: 이미지 저장 옵션 구성

 다음으로 설정하세요`ImageSaveOptions` 문서를 이미지로 저장하는 방법을 정의합니다. 1Bpp 인덱스 색상 모드로 PNG 형식으로 저장하도록 구성합니다.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // 첫 번째 페이지만 변환
    ImageColorMode = ImageColorMode.BlackAndWhite, // 흑백으로 설정
    PixelFormat = ImagePixelFormat.Format1bppIndexed // 1Bpp 인덱스 형식 사용
};
```

- SaveFormat.Png: 출력 형식이 PNG가 되도록 지정합니다.
- PageSet(1): 문서의 첫 페이지만 변환됨을 나타냅니다.
- ImageColorMode.BlackAndWhite: 이미지를 흑백으로 표시합니다.
- ImagePixelFormat.Format1bppIndexed: 픽셀 형식을 1Bpp 인덱스로 설정하여 공간을 최적화합니다.

## 5단계: 문서를 이미지로 저장

 마지막으로 다음을 사용합니다.`Save` 의 방법`Document` 변환된 이미지를 저장할 객체입니다.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서를 1Bpp 인덱스 이미지로 성공적으로 변환했습니다. 이 방법은 효율적일 뿐만 아니라 다양한 애플리케이션에 적합한 고대비 이미지를 만드는 데 도움이 됩니다. 이 기능을 프로젝트에 통합해도 좋습니다. 즐거운 코딩 되세요!

## 자주 묻는 질문

### 1Bpp 인덱스 이미지란 무엇인가요?
1Bpp(픽셀당 1비트) 인덱스 이미지는 각 픽셀이 0 또는 1의 단일 비트로 표현되는 흑백 이미지 형식입니다. 이 형식은 공간 효율성이 매우 높아 보관에 이상적입니다.

### 한 번에 Word 문서의 여러 페이지를 변환할 수 있나요?
 네! 간단히 수정하면 됩니다.`PageSet` 에 있는 재산`ImageSaveOptions` 여러 페이지를 포함하거나 전체 문서를 변환하도록 설정할 수 있습니다.

### Aspose.Words for .NET을 사용하려면 라이선스가 필요합니까?
 예, 모든 기능을 사용하려면 라이센스가 필요합니다.[여기 임시 면허증](https://purchase.aspose.com/temporary-license/).

### Word 문서를 어떤 다른 이미지 형식으로 변환할 수 있나요?
 Aspose.Words는 JPEG, BMP, TIFF를 포함한 다양한 형식을 지원합니다.`SaveFormat`에서`ImageSaveOptions` 원하는 형식으로.

### .NET용 Aspose.Words에 대한 추가 문서는 어디에서 찾을 수 있나요?
 포괄적인 문서는 다음을 방문하세요.[.NET 설명서 페이지용 Aspose.Words](https://reference.aspose.com/words/net/).