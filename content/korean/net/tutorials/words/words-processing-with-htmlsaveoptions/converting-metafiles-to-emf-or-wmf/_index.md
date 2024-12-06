---
title: 메타파일을 Emf 또는 Wmf로 변환
linktitle: 메타파일을 Emf 또는 Wmf로 변환
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에서 SVG 이미지를 EMF 또는 WMF 형식으로 원활하게 변환하는 방법을 알아보세요. 정확하고 호환되는 결과를 위한 코드 예제가 포함된 단계별 가이드.
type: docs
weight: 10
url: /ko/net/tutorials/words/words-processing-with-htmlsaveoptions/converting-metafiles-to-emf-or-wmf/
---
## 소개

이미지 형식을 효율적으로 관리하고 변환하는 것은 전문적인 Word 문서를 만드는 데 중요한 부분입니다. 이 가이드에서는 Aspose.Words for .NET을 사용하여 SVG 이미지를 EMF(Enhanced Metafile) 또는 WMF(Windows Metafile) 형식으로 변환하여 원활하게 통합하는 방법을 살펴봅니다. 이 튜토리얼은 개발자가 변환을 쉽게 구현할 수 있도록 명확하고 단계별 지침을 제공합니다.

## SVG를 EMF 또는 WMF로 변환하기 위한 전제 조건

원활한 개발 환경을 보장하려면 다음 전제 조건이 충족되는지 확인하세요.

- .NET용 Aspose.Words: 다음에서 최신 버전을 얻으세요.[Aspose 릴리스 페이지](https://releases.aspose.com/words/net/).
- .NET Framework: .NET Framework(또는 사용자 환경에 따라 .NET Core/5/6)가 설치되어 있는지 확인하세요.
- 개발 환경: Visual Studio는 강력한 기능을 갖추고 있어 권장됩니다.
- C# 능숙도: C# 프로그래밍에 대한 기본적인 지식이 필수입니다.

## 필요한 네임스페이스 가져오기

프로젝트에서 Aspose.Words 기능에 액세스하는 데 필요한 네임스페이스를 가져옵니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: 문서 디렉토리 정의

Word 문서가 저장될 디렉토리 경로를 설정합니다. 이는 출력 파일을 효과적으로 관리하는 데 필수적입니다.

```csharp
string dataDir = @"C:\MyDocuments\";
```

 바꾸다`@"C:\MyDocuments\"` 당신이 원하는 경로로.

## 2단계: SVG를 포함하는 HTML 문자열 준비

SVG 콘텐츠를 임베드하는 HTML 문자열을 작성합니다. 이를 통해 Aspose.Words가 SVG를 렌더링하고 처리할 수 있습니다.

```csharp
string htmlContent = 
    @"<html>
        <body>
            <svg xmlns='http://www.w3.org/2000/svg' 너비='300' 높이='100' viewBox='0 0 300 100'>
                <rect x='10' y='10' width='280' height='80' fill='blue' stroke='black' stroke-width='2'/>
                <text x='20' y='60' fill='white' font-size='20'>Aspose SVG Example</text>
            </svg>
        </body>
    </html>";
```

## 3단계: HTML 로드 옵션 구성

 SVG 변환을 적절히 처리하려면 다음을 구성하세요.`HtmlLoadOptions` ~와 함께`ConvertSvgToEmf`.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    ConvertSvgToEmf = true
};
```

## 4단계: Word 문서에 HTML 로드

구성된 로드 옵션을 사용하여 다음을 생성합니다.`Document` HTML 문자열에서 객체를 가져옵니다.

```csharp
using (MemoryStream htmlStream = new MemoryStream(Encoding.UTF8.GetBytes(htmlContent)))
{
    Document document = new Document(htmlStream, loadOptions);
}
```

## 5단계: EMF/WMF에 대한 저장 옵션 구성

 원하는 메타파일 형식을 정의하기 위해 저장 옵션을 사용자 정의합니다. 여기서 우리는 선택합니다.`HtmlMetafileFormat.Emf`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Emf
};
```

## 6단계: 문서 저장

지정된 저장 옵션을 사용하여 문서를 저장합니다.

```csharp
document.Save(dataDir + "ConvertedDocument.emf", saveOptions);
```

결과 파일에는 EMF 형식으로 변환된 SVG 콘텐츠가 포함됩니다.

## 결론

이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 SVG 이미지를 EMF 또는 WMF 형식으로 변환하는 방법을 보여주었습니다. 이러한 단계를 따르면 Word 문서의 호환성과 시각적 충실도를 향상시킬 수 있습니다. 문서 생성을 자동화하든 고품질 보고서를 준비하든 이 방법은 원활한 결과를 보장합니다.

## 자주 묻는 질문

### 이 방법을 사용하여 여러 SVG를 일괄 처리할 수 있나요?
네, SVG가 포함된 여러 HTML 파일을 반복하여 동일한 프로세스를 루프로 적용할 수 있습니다.

### EMF와 WMF의 차이점은 무엇인가요?
EMF는 WMF의 향상된 버전으로 복잡한 그래픽과 더 큰 데이터 크기에 대한 더 나은 지원을 제공합니다.

### Aspose.Words는 .NET Core와 호환됩니까?
네, Aspose.Words for .NET은 .NET Core와 .NET 5/6을 지원하므로 최신 크로스 플랫폼 애플리케이션에 적합합니다.

### 출력에서 원본 SVG 형식을 유지할 수 있나요?
아니요, 이 방법은 SVG를 EMF/WMF로 특별히 변환합니다. 그러나 변환하지 않고 문서에 직접 임베드하여 원본 SVG를 유지할 수 있습니다.

### Aspose.Words 무료 평가판은 어디에서 다운로드할 수 있나요?
 무료 평가판을 다운로드할 수 있습니다.[Aspose 릴리스 페이지](https://releases.aspose.com/).