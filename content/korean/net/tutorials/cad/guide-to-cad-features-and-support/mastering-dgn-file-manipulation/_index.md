---
title: .NET에서 Aspose.CAD를 사용하여 DGN 파일 조작 마스터링
linktitle: DGN 파일 조작 마스터링
second_title: Aspose.CAD .NET - CAD 및 BIM 파일 형식
description: DGN 파일을 로드하고, 해당 요소를 반복하고, 2D 및 3D 엔터티를 관리하고, 이를 래스터 이미지로 내보내는 방법을 알아보세요. 이 모든 작업을 Aspose.CAD 라이브러리의 강력한 기능을 활용하는 동시에 수행할 수 있습니다.
type: docs
weight: 18
url: /ko/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## 소개

DGN 파일을 애플리케이션에 통합하고 싶은 .NET 개발자이신가요? Aspose.CAD for .NET은 DGN 파일 형식으로 작업하기 위해 특별히 설계된 강력한 라이브러리를 제공합니다. 이 튜토리얼에서는 지원되는 요소를 포함하여 DGN 파일을 효율적으로 처리하는 방법과 .NET 프로젝트에서 이를 조작하는 방법을 살펴보겠습니다.

## 필수 조건

시작하기 전에 다음 설정이 있는지 확인하세요.

- .NET 프로그래밍에 대한 기본 지식: C# 또는 VB.NET에 대한 지식이 있으면 좋습니다.
- Visual Studio: 프로젝트 개발을 위해 컴퓨터에 설치합니다.
-  .NET 라이브러리용 애스포즈.캐드: 여기에서 다운로드하세요.[Aspose.CAD](https://releases.aspose.com/cad/net/).

## 1단계: 필요한 네임스페이스 가져오기

Aspose.CAD의 기능을 활용하려면 먼저 필요한 네임스페이스를 프로젝트로 가져옵니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## 2단계: DGN 파일 로드

 기존 DGN 파일을 애플리케이션에 로드하여 시작합니다. 이는 다음을 인스턴스화하여 수행됩니다.`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // 여기에서 논리를 진행하세요
}
```

## 3단계: DGN 요소 반복

DGN 파일이 로드되면 해당 요소를 반복할 수 있습니다. Aspose.CAD는 조작을 위한 다양한 DGN 요소 유형을 제공합니다.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // 각 요소를 처리합니다
}
```

## 4단계: 2D 및 3D 엔터티 처리

2D와 3D DGN 요소를 구별할 수 있습니다. 다음은 이를 효율적으로 처리하는 방법입니다.

### 2D 엔티티 처리

이전에 지원되었던 2D 엔터티를 switch-case 블록을 사용하여 관리할 수 있습니다.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // 여기에 처리 로직을 추가하세요
        break;
}
```

### 3D 엔티티 처리

마찬가지로 3D 엔터티를 다음과 같이 처리합니다.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // 여기에 처리 로직을 추가하세요
        break;
}
```

## 5단계: DGN 파일 내보내기

DGN 요소를 조작한 후 파일을 래스터 이미지로 내보내고 싶을 수 있습니다. 이는 Aspose.CAD로 쉽게 수행할 수 있습니다.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // 출력 경로를 정의하세요
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## 결론

이 튜토리얼에서는 Aspose.CAD for .NET을 사용하여 DGN 파일을 효과적으로 관리하는 방법을 알아보았습니다. 설명된 단계를 따르면 2D 및 3D DGN 요소를 손쉽게 처리하고 래스터 이미지로 내보낼 수 있습니다. 이 강력한 라이브러리를 사용하면 DGN 처리를 .NET 애플리케이션에 원활하게 통합하여 프로젝트 기능을 향상시킬 수 있습니다.

## 자주 묻는 질문

### Aspose.CAD for .NET에 대한 설명서는 어디에서 찾을 수 있나요?

 포괄적인 문서를 사용할 수 있습니다[여기](https://reference.aspose.com/cad/net/).

### .NET용 Aspose.CAD를 어떻게 다운로드하나요?

 최신 버전의 라이브러리를 다운로드할 수 있습니다.[여기](https://releases.aspose.com/cad/net/).

### Aspose.CAD for .NET의 무료 평가판이 있나요?

 네, 무료 체험판을 이용하실 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.CAD for .NET에 대한 임시 라이선스를 어떻게 얻을 수 있나요?

 임시 라이센스를 요청할 수 있습니다[여기](https://purchase.conholdate.com/temporary-license/).

### 도움이 필요하시거나 궁금한 점이 있으신가요?

 지원이나 질문이 있으시면 Aspose.CAD 커뮤니티를 방문하세요.[지원 포럼](https://forum.aspose.com/c/cad/19).