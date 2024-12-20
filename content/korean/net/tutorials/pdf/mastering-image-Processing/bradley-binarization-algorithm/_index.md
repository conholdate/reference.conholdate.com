---
title: 브래들리 이진화 알고리즘
linktitle: 브래들리 이진화 알고리즘
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET에서 Bradley 이진화 알고리즘을 사용하여 PDF 페이지를 고품질 이진 TIFF 이미지로 변환하는 방법을 알아보세요. 이 단계별 가이드에는 코드 예제가 포함되어 있습니다.
type: docs
weight: 30
url: /ko/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## 소개

이 튜토리얼에서는 Bradley Binarization Algorithm을 사용하여 PDF 페이지를 TIFF 이미지로 변환하는 과정을 안내합니다. Aspose.PDF for .NET은 이 작업을 간소화하여 문서 워크플로를 쉽게 자동화하고 간소화할 수 있도록 합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.PDF: 라이브러리를 여기에서 다운로드하세요.[여기](https://releases.aspose.com/pdf/net/).
- Visual Studio(또는 C# IDE).
- C#에 대한 기본 지식.
-  유효한 면허증 또는[임시 면허](https://purchase.aspose.com/temporary-license/) Aspose에서.

## 1단계: 프로젝트 설정

먼저 IDE에서 새 C# 프로젝트를 만들고 필요한 네임스페이스를 가져옵니다.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## 2단계: 문서 디렉토리 정의

PDF 문서가 있는 디렉토리 경로와 TIFF 이미지의 출력 경로를 지정하세요.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // PDF 파일 경로
```

이 디렉토리에는 원본 PDF와 변환된 TIFF 파일이 모두 저장됩니다.

## 3단계: PDF 문서 로드

변환하려는 PDF 문서를 엽니다.

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 바꾸다`PageToTIFF.pdf` PDF 파일의 이름을 입력합니다.

## 4단계: 출력 경로 지정

생성된 TIFF 파일에 대한 출력 경로를 정의합니다.

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## 5단계: 이미지 해상도 설정

TIFF 이미지의 해상도를 설정합니다. DPI가 높을수록 이미지 품질이 더 좋아집니다.

```csharp
Resolution resolution = new Resolution(300);
```

## 6단계: TIFF 설정 구성

압축 및 색상 깊이를 포함하여 TIFF 이미지에 대한 설정을 구성합니다.

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

1bpp(픽셀당 1비트)를 사용하면 이미지를 이진 출력으로 준비할 수 있습니다.

## 7단계: TIFF 장치 생성

변환을 처리할 TIFF 장치를 만듭니다.

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## 8단계: PDF 페이지를 TIFF로 변환

PDF의 첫 번째 페이지를 TIFF 이미지로 변환:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## 9단계: Bradley 이진화 알고리즘 적용

이제 Bradley 알고리즘을 적용하여 회색조 TIFF 이미지를 이진 이미지로 변환합니다.

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 그만큼`BinarizeBradley` 이 방법은 두 개의 파일 스트림(입력 및 출력)과 임계값을 사용합니다. 최적의 결과를 위해 필요에 따라 임계값을 조정합니다.

## 10단계: 성공적인 전환 확인

마지막으로 변환이 성공적으로 완료되었는지 확인하세요.

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## 결론

축하합니다! PDF 페이지를 TIFF 이미지로 성공적으로 변환하고 Aspose.PDF for .NET을 사용하여 Bradley Binarization Algorithm을 적용했습니다. 이 프로세스는 문서 보관, OCR 및 기타 전문 응용 프로그램에 필수적입니다. 고품질 해상도와 효율적인 압축으로 문서 이미지가 선명하고 크기가 관리하기 쉽습니다.

## 자주 묻는 질문

### 브래들리 알고리즘이란?
브래들리 알고리즘은 주변 환경에 따라 각 픽셀에 대한 적응적 임계값을 결정하여 회색조 이미지를 이진 이미지로 변환하는 이진화 기술입니다.

### 이 방법을 사용하여 여러 개의 PDF 페이지를 TIFF로 변환할 수 있나요?
 네, 수정할 수 있습니다.`Process` 문서의 모든 페이지를 반복하여 변환하는 방법입니다.

### PDF를 TIFF로 변환할 때 최적의 해상도는 무엇입니까?
일반적으로 고품질 이미지에는 300 DPI의 해상도가 권장되지만, 특정 요구 사항에 맞게 이를 조정할 수 있습니다.

### 색상 심도에서 1bpp는 무엇을 의미합니까?
1bpp(픽셀당 1비트)는 이미지가 흑백임을 나타내며, 각 픽셀은 완전히 검은색이거나 완전히 흰색입니다.

### Bradley 알고리즘은 OCR에 적합합니까?
네, 브래들리 알고리즘은 OCR 전처리에 자주 사용되는데, 스캔한 문서의 텍스트 대비를 높여 인식 정확도를 높이기 때문입니다.