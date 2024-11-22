---
title: Aspose.CAD for .NET을 사용하여 CAD를 래스터 이미지로 변환하여 내보내기
linktitle: CAD를 래스터 이미지로 변환하여 내보내기
second_title: Aspose.CAD .NET - CAD 및 BIM 파일 형식
description: Aspose.CAD for .NET을 사용하여 CAD 레이아웃을 다양한 래스터 이미지 형식으로 효율적으로 변환하는 방법을 알아보세요. 이 포괄적인 가이드는 명확한 코드로 프로세스를 안내합니다.
type: docs
weight: 10
url: /ko/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## 소개

Aspose.CAD for .NET을 사용하여 CAD 레이아웃을 래스터 이미지 형식으로 손쉽게 변환하고 싶으신가요? 이 단계별 가이드는 프로세스를 탐색하는 데 도움이 되도록 설계되었으며, 원활한 경험을 위한 간결한 코드 조각이 포함되어 있습니다. 숙련된 개발자이든 방금 시작한 개발자이든, 이 튜토리얼은 모든 기술 수준에 대한 귀중한 통찰력을 제공합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET 라이브러리용 Aspose.CAD: 라이브러리를 다운로드하여 설치하세요.[Aspose.CAD 웹사이트](https://releases.aspose.com/cad/net/).
-  CAD 도면 파일: CAD 도면 파일(예:`conic_pyramid.dxf`) 변환 준비됨.

## 필요한 네임스페이스 가져오기

.NET 프로젝트에서 Aspose.CAD 함수를 활용하려면 필요한 네임스페이스를 가져와야 합니다. 코드 맨 위에 다음을 추가합니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## 1단계: CAD 도면 로드

먼저 디렉토리를 지정하고 CAD 파일을 이미지 인스턴스로 로드합니다.

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// CAD 도면을 로드합니다
using (var image = Image.Load(sourceFilePath))
{
    // 다음 단계로 진행하세요
}
```

## 2단계: 래스터화 옵션 생성

다음으로, 출력 이미지에 대한 원하는 크기를 정의하여 래스터화 옵션을 설정합니다.

```csharp
// CadRasterizationOptions 초기화
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## 3단계: 변환을 위한 레이어 지정

특정 레이어를 변환하려면 래스터화 옵션에 추가하세요.

```csharp
// 변환할 레이어를 지정하세요
rasterizationOptions.Layers = new [] { "LayerA" };
```

## 4단계: JPEG 내보내기 옵션 설정

이제 내보내고자 하는 이미지 형식(이 경우 JPEG)에 대한 옵션을 만듭니다.

```csharp
// 내보내기 위한 JpegOptions 생성
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## 5단계: JPEG 형식으로 내보내기

마지막으로 변환된 이미지를 저장합니다.

```csharp
// 출력 파일 경로를 정의하고 이미지를 저장합니다.
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## 추가 기능: 모든 레이어 변환

CAD 도면의 모든 레이어를 변환하려면 다음과 같은 방법을 구현할 수 있습니다.

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // 레이어를 반복하고 각각을 별도의 JPEG 파일로 저장합니다.
    // 여기에 구현 코드가 있습니다.
}
```

## 결론

축하합니다! Aspose.CAD for .NET을 사용하여 CAD 레이아웃을 래스터 이미지 형식으로 효과적으로 변환하는 방법을 배웠습니다. 이 가이드는 효율적인 CAD 변환을 목표로 하는 개발자에게 적합한 간단한 접근 방식을 제공합니다.

## 자주 묻는 질문

### 다양한 이미지 형식으로 내보낼 수 있나요?

 물론입니다! 간단히 바꾸세요`JpegOptions` 다른 형식 옵션과 함께, 예:`PngOptions` 또는`BmpOptions`, 귀하의 요구 사항에 따라 다릅니다.

### 체험판이 있나요?

 네, 다음 단계에 따라 평가판을 다운로드하여 기능을 탐색할 수 있습니다.[링크](https://releases.aspose.com/cad/net/).

### Aspose.CAD에 대한 지원은 어디에서 받을 수 있나요?

 커뮤니티 지원을 위해 Aspose.CAD를 확인하세요.[법정](https://forum.aspose.com/c/cad/19)또는 보다 전담적인 지원을 받으려면 라이선스를 구매하는 것을 고려해 보세요.

### 임시 면허가 가능합니까?

 예, 임시 라이센스를 이용할 수 있습니다. 라이센스를 요청할 수 있습니다.[여기](https://purchase.conholdate.com/temporary-license/).

### 자세한 문서는 어디서 볼 수 있나요?

 포괄적인 문서를 방문하세요[여기](https://reference.aspose.com/cad/net/) 자세한 내용은.