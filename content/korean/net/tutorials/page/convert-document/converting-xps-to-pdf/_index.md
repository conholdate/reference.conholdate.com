---
title: Aspose.Page for .NET을 사용하여 XPS를 PDF로 변환
linktitle: XPS를 PDF로 변환
second_title: Aspose.Page .NET API
description: 강력한 Aspose.Page for .NET 라이브러리를 사용하여 XPS(XML Paper Specification) 문서를 PDF(Portable Document Format)로 원활하게 변환하는 방법을 알아보세요.
type: docs
weight: 11
url: /ko/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## 소개

이 튜토리얼에서는 다재다능한 Aspose.Page for .NET 라이브러리를 사용하여 XPS(XML Paper Specification) 문서를 PDF(Portable Document Format)로 변환하는 방법을 살펴보겠습니다. 이 강력한 라이브러리는 문서 변환을 간소화하고 다양한 사용자 지정 옵션을 제공하므로 개발자에게 탁월한 선택입니다.

## 필수 조건

시작하기 전에 다음 사항이 준비되었는지 확인하세요.

-  .NET 라이브러리용 Aspose.Page: .NET 라이브러리용 Aspose.Page를 다운로드하여 설치하세요.[Aspose.Page 문서](https://reference.aspose.com/page/net/).
  
- 개발 환경: Visual Studio나 다른 호환 IDE를 사용하여 .NET 개발 환경을 설정합니다.

- XPS 문서: 변환하려는 XPS 파일을 준비하고 지정된 디렉토리에 저장해 둡니다.

## 1단계: 필요한 네임스페이스 가져오기

Aspose.Page 기능에 액세스하는 데 필요한 네임스페이스를 가져오는 것으로 시작합니다.

```csharp
using Aspose.Page.XPS;
```

## 2단계: 문서 디렉토리 초기화

문서가 저장된 디렉토리 경로를 정의하세요.

```csharp
string dataDir = "Your Document Directory";
```

 교체를 꼭 해주세요`"Your Document Directory"` XPS 문서가 들어 있는 디렉토리의 실제 경로를 포함합니다.

### 3단계: PDF 및 XPS 스트림 열기

다음으로, 입력 XPS 파일과 출력 PDF 파일 모두에 대한 스트림을 초기화합니다.

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

파일에 올바른 경로가 설정되어 있는지 확인하세요.

### 4단계: XPS 문서 로드

이제 Aspose.Page 라이브러리를 사용하여 XPS 문서를 로드합니다.

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### 5단계: PDF 저장 옵션 구성

이미지 품질 및 압축 매개변수를 포함하여 PDF에 대한 저장 옵션을 설정합니다.

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // JPEG 품질 수준 설정
    ImageCompression = PdfImageCompression.Jpeg, // 이미지에 JPEG 압축을 사용하세요
    TextCompression = PdfTextCompression.Flate, // 텍스트에 Flate 압축 적용
    PageNumbers = new int[] { 1, 2, 6 } // 포함할 페이지 번호를 지정하세요
};
```

귀하의 요구 사항에 맞게 이러한 매개변수를 자유롭게 조정하세요.

### 6단계: PDF 렌더링 장치 생성

PDF 형식에 대한 렌더링 장치를 만듭니다.

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### 7단계: 문서를 PDF로 저장

마지막으로 지정된 장치와 옵션을 사용하여 XPS 문서를 PDF로 저장합니다.

```csharp
document.Save(device, options);
```

## 결론

축하합니다! Aspose.Page for .NET을 사용하여 XPS 문서를 PDF로 성공적으로 변환했습니다. 이 라이브러리는 문서 변환을 간소화할 뿐만 아니라 다양한 형식을 처리하기 위한 광범위한 기능을 제공합니다.

## 자주 묻는 질문

### 여러 XPS 파일을 하나의 PDF로 변환할 수 있나요?

물론입니다! 여러 XPS 파일을 반복하고 동일한 변환 단계에 따라 단일 PDF 문서로 병합할 수 있습니다.

### Aspose.Page for .NET은 어떤 다른 출력 형식을 지원합니까?

PDF 외에도 Aspose.Page for .NET은 TIFF, JPEG, PNG 등 다양한 형식을 지원합니다.

### 변환된 PDF의 모양을 어떻게 사용자 지정할 수 있나요?

 매개변수를 조정할 수 있습니다`PdfSaveOptions` JPEG 품질과 압축 설정 등을 조정하여 원하는 모습을 얻을 수 있습니다.

### Aspose.Page for .NET의 평가판이 있나요?

 네, 무료 평가판을 통해 Aspose.Page for .NET을 사용해 볼 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Page for .NET에 대한 커뮤니티 지원은 어디에서 찾을 수 있나요?

커뮤니티 토론 및 지원을 위해 다음을 방문하세요.[Aspose.Page 포럼](https://forum.aspose.com/c/page/39).