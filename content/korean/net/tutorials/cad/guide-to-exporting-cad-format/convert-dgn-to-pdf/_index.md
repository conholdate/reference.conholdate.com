---
title: .NET용 Aspose.CAD에서 DGN을 PDF로 변환
linktitle: .NET용 Aspose.CAD에서 DGN을 PDF로 변환
second_title: Aspose.CAD .NET - CAD 및 BIM 파일 형식
description: .NET용 강력한 Aspose.CAD 라이브러리를 사용하여 DGN 파일을 PDF로 손쉽게 변환하는 방법을 알아보세요. 이 단계별 가이드는 모든 레벨의 개발자를 위해 설계되었습니다.
type: docs
weight: 12
url: /ko/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## 소개

CAD 파일의 세계를 탐색하는 것은 어려울 수 있지만 Aspose.CAD for .NET을 사용하면 개발자는 다양한 CAD 형식을 쉽게 조작하고 변환할 수 있습니다. 일반적인 요구 사항 중 하나는 DGN 파일을 PDF로 변환하는 것이며, 이 튜토리얼에서는 단계별로 살펴보겠습니다.

## 필수 조건

따라오려면 다음 사항이 있는지 확인하세요.

- C# 및 .NET 프레임워크에 대한 기본 지식이 필요합니다.
-  Aspose.CAD for .NET 라이브러리가 설치되었습니다. 다운로드할 수 있습니다.[여기](https://releases.aspose.com/cad/net/).
- 샘플 DGN 파일(예: Nikon_D90_Camera.dgn) 

## 1단계: 필요한 네임스페이스 가져오기

먼저 C# 프로젝트에서 관련 네임스페이스를 가져옵니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## 2단계: DGN 파일 로드

DGN 파일에 대한 디렉토리를 지정하고 다음 코드를 사용하여 로드합니다.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // 추가 처리가 여기에 진행됩니다...
}
```

## 3단계: 래스터화 옵션 구성

다음으로, DGN이 PDF에서 렌더링되는 방식을 정의하기 위해 래스터화 옵션을 설정합니다.

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // 필요에 따라 너비를 조정하세요
    PageHeight = 300, // 필요에 따라 높이를 조정하세요
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## 4단계: PDF 옵션 만들기

이전에 구성한 래스터화 설정을 통합하여 PDF 옵션을 정의합니다.

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## 5단계: DGN을 PDF로 저장

마지막으로, 구성한 옵션을 사용하여 DGN 파일을 PDF로 저장합니다.

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## 결론

축하합니다! Aspose.CAD for .NET을 사용하여 DGN 파일을 PDF로 성공적으로 변환했습니다. 이 간단한 튜토리얼은 DGN 파일을 로드하고, 래스터화 옵션을 설정하고, 출력을 PDF로 저장하는 방법을 안내합니다.

## 자주 묻는 질문

### Aspose.CAD를 사용하려면 CAD에 대한 사전 지식이 필요한가요?  
물론입니다! Aspose.CAD는 복잡한 CAD 작업을 단순화하도록 설계되어 CAD 지식에 관계없이 모든 개발자가 사용할 수 있습니다.

### Aspose.CAD에 대한 추가 리소스와 문서는 어디에서 찾을 수 있나요?  
 포괄적인 가이드와 예를 탐색할 수 있습니다.[Aspose.CAD 설명서](https://reference.aspose.com/cad/net/).

### Aspose.CAD에 대한 무료 평가판이 있나요?  
 네, 무료 체험판을 받으실 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.CAD에 대한 임시 라이선스를 어떻게 받을 수 있나요?  
 임시 라이센스를 요청할 수 있습니다[여기](https://purchase.conholdate.com/temporary-license/).

### 도움이 필요하시거나 궁금한 점이 있으신가요?  
 대화에 참여하세요[Aspose.CAD 포럼](https://forum.aspose.com/c/cad/19) 커뮤니티 지원 및 문의사항은 여기를 클릭하세요.