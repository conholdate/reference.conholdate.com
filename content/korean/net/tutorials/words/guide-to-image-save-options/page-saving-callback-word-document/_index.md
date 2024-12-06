---
title: Word 문서에서 페이지 저장 콜백
linktitle: Word 문서에서 페이지 저장 콜백
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서의 각 페이지를 개별 PNG 이미지로 쉽게 변환하는 방법을 알아보세요. 이 가이드는 코드 예제를 포함한 단계별 지침을 제공합니다.
type: docs
weight: 10
url: /ko/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## 소개

Word 문서의 각 페이지를 개별 이미지로 변환해야 했던 적이 있나요? 미리보기용 썸네일을 만들거나 긴 보고서를 소화 가능한 비주얼로 분할하려는 경우 Aspose.Words for .NET이 이 작업을 간단하고 효율적으로 만들어줍니다. 이 가이드에서는 문서의 각 페이지를 PNG 이미지로 저장하기 위한 페이지 저장 콜백을 설정하는 과정을 안내해드리겠습니다. 시작해 볼까요!

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  Aspose.Words for .NET: 여기에서 다운로드하고 설치하세요.[여기](https://releases.aspose.com/words/net/).
2. Visual Studio: 어떤 버전이든 괜찮지만 이 가이드에서는 Visual Studio 2019를 사용하겠습니다.
3. 기본 C# 지식: C#에 익숙하면 원활하게 따라갈 수 있습니다.

## 1단계: 필요한 네임스페이스 가져오기

먼저, 필요한 네임스페이스를 가져와야 합니다. 이렇게 하면 매번 전체 네임스페이스를 입력하지 않고도 필요한 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 2단계: 문서 디렉토리 정의

다음으로, 문서 디렉토리 경로를 설정합니다. 여기에 입력 Word 문서가 있고 출력 이미지가 저장되는 곳입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 3단계: 문서 로드

이제 처리하려는 문서를 로드해 보겠습니다. "Rendering.docx"라는 이름의 문서가 지정된 디렉토리에 있는지 확인하세요.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 4단계: 이미지 저장 옵션 구성

페이지를 PNG 파일로 저장하도록 지정하여 이미지 저장 옵션을 설정합니다.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 여기,`PageSet` 저장할 페이지 범위를 정의하고`PageSavingCallback` 사용자 정의 콜백 클래스를 가리킵니다.

## 5단계: 페이지 저장 콜백 구현

이제 각 페이지가 어떻게 저장되는지 처리하는 콜백 클래스를 구현해야 합니다.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 이 클래스는 다음을 구현합니다.`IPageSavingCallback` 인터페이스.`PageSaving` 이 방법을 사용하면 저장된 각 페이지에 대한 명명 패턴을 지정할 수 있습니다.

## 6단계: 문서를 이미지로 저장

마지막으로 구성된 옵션을 사용하여 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서의 각 페이지를 별도의 PNG 이미지로 저장하는 페이지 저장 콜백을 성공적으로 설정했습니다. 이 기술은 페이지 미리보기 만들기부터 보고서의 개별 페이지 이미지 생성까지 다양한 애플리케이션에 매우 유용합니다.

## 자주 묻는 질문

### PNG 이외의 형식으로 페이지를 저장할 수 있나요?
 네! JPEG, BMP, TIFF와 같은 형식으로 페이지를 저장할 수 있습니다.`SaveFormat` ~에`ImageSaveOptions`.

### 특정 페이지만 저장하려면 어떻게 해야 하나요?
 특정 페이지를 저장하려면 다음을 조정하세요.`PageSet` 매개변수`ImageSaveOptions` 원하는 페이지만 포함시킵니다.

### 이미지 품질을 사용자 정의할 수 있나요?
 물론입니다! 다음과 같은 속성을 설정하여 출력 이미지 품질을 제어할 수 있습니다.`ImageSaveOptions.JpegQuality`.

### 대용량 문서를 효율적으로 처리하려면 어떻게 해야 하나요?
대용량 문서의 경우 메모리 사용량을 효과적으로 관리하기 위해 페이지를 일괄적으로 처리하는 것이 좋습니다.

### Aspose.Words for .NET에 대한 자세한 정보는 어디에서 찾을 수 있나요?
 포괄적인 가이드와 예를 보려면 다음을 확인하세요.[Aspose.Words 문서](https://reference.aspose.com/words/net/).