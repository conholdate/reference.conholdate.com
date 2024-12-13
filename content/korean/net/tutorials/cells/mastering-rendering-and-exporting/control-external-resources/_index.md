---
title: Aspose.Cells for .NET으로 외부 리소스 제어
linktitle: Aspose.Cells for .NET으로 외부 리소스 제어
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET으로 Excel에서 PDF로 변환하는 모든 잠재력을 활용하세요. 이 포괄적인 가이드에서는 이미지와 같은 외부 리소스를 관리하고 PDF가 정확한 서식 요구 사항을 반영하도록 하는 방법을 알아보세요.
type: docs
weight: 12
url: /ko/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## 소개

오늘날의 디지털 환경에서 Excel 스프레드시트를 PDF 문서로 변환하는 것은 일반적이고 필수적인 작업입니다. 보고서, 재무 데이터 또는 프레젠테이션 자료를 준비하든 PDF가 의도한 형식을 반영하는지 확인하는 것이 중요합니다. Aspose.Cells for .NET은 특히 이미지와 같은 외부 리소스를 처리할 때 이 변환 프로세스를 자세히 제어할 수 있는 강력한 라이브러리를 제공합니다. 이 가이드에서는 Aspose.Cells를 사용하여 Excel에서 PDF로 변환하는 동안 외부 리소스를 효과적으로 관리하는 방법을 살펴보겠습니다. 시작해 볼까요!

## 필수 조건

시작하기 전에 다음 사항을 준비하세요.

1. Visual Studio 또는 .NET 호환 IDE: 이것이 개발 환경이 됩니다.
2.  .NET용 Aspose.Cells: 아직 설치하지 않았다면 다음을 방문하세요.[Aspose 다운로드](https://releases.aspose.com/cells/net/) 최신 버전을 받으려면 페이지로 가세요.
3. C#에 대한 기본 지식: C#에 대한 지식이 유익할 것입니다. 개념에 대한 설명이 필요하면 자유롭게 찾아보세요.
4. 샘플 Excel 파일: 변환하려는 외부 리소스가 포함된 "samplePdfSaveOptions_StreamProvider.xlsx"와 같은 Excel 파일을 준비합니다.
5. 테스트를 위한 이미지 파일: 변환하는 동안 "newPdfSaveOptions_StreamProvider.png"와 같은 이미지 파일을 외부 리소스로 사용합니다.

## 필요한 패키지 가져오기

시작하려면 Aspose.Cells 라이브러리에서 필요한 네임스페이스를 가져와야 합니다. C# 파일의 맨 위에 다음 using 지시문을 추가합니다.

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

이러한 네임스페이스는 작업에 필수적인 클래스와 메서드를 제공합니다.

## 1단계: 스트림 공급자 클래스 생성

 먼저, 다음을 구현하는 스트림 공급자 클래스를 만듭니다.`IStreamProvider` 인터페이스. 이 클래스를 사용하면 외부 리소스가 로드되는 방식을 제어할 수 있습니다.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // 이미지를 메모리 스트림에 로드합니다.
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: 이 메서드는 스트림이 닫힐 때 호출되며 현재 디버그 메시지를 기록합니다.
- InitStream: 이 메서드는 외부 이미지 파일을 바이트 배열로 읽고 이를 메모리 스트림으로 변환하여 메모리에 할당합니다.`options.Stream` 재산.

## 2단계: 소스 및 출력 디렉토리 설정

다음으로, Excel 파일과 출력 PDF에 대한 디렉토리를 정의합니다.

```csharp
// 소스 디렉토리
string sourceDir = "Your Document Directory";
// 출력 디렉토리
string outputDir = "Your Document Directory";
```

 바꾸다`"Your Document Directory"` 파일이 위치한 시스템의 실제 경로를 말합니다.

## 3단계: Excel 파일 로드

이제 PDF를 만들려는 Excel 파일을 로드합니다.

```csharp
// 외부 이미지가 포함된 소스 Excel 파일을 로드합니다.
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 그만큼`Workbook` Aspose.Cells의 클래스는 이미지와 같은 다양한 외부 리소스를 포함할 수 있는 Excel 파일을 나타냅니다.

## 4단계: PDF 저장 옵션 설정

통합 문서를 PDF로 저장하기 전에 원하는 저장 옵션을 지정하세요.

```csharp
// PDF 저장 옵션 지정 - 스트림 제공자
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // 각 시트를 새 페이지에 저장하세요
};
```

 이것은 인스턴스를 생성합니다`PdfSaveOptions` PDF 형식을 사용자 정의할 수 있습니다.`OnePagePerSheet` 이 옵션을 사용하면 각 Excel 시트가 최종 PDF에서 별도의 페이지에 표시됩니다.

## 5단계: 스트림 공급자 지정

 연결하세요`Workbook` 인스턴스와 함께`MyStreamProvider` 이전에 만든 클래스입니다.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

이 라인은 변환 중에 외부 리소스가 발생할 때마다 사용자 지정 공급자가 이를 적절히 관리하도록 보장합니다.

## 6단계: 통합 문서를 PDF로 저장

이제 Excel 통합 문서를 PDF로 저장해 보세요.

```csharp
// 통합 문서를 PDF로 저장
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 전화를 걸어서`Save` 통합 문서 개체에서 메서드를 사용하고 PDF 옵션과 함께 출력 디렉터리를 전달하면 Excel 파일을 잘 포맷된 PDF로 변환할 수 있습니다.

## 7단계: 성공적인 실행 확인

마지막으로, 프로세스가 성공적으로 완료되었는지 확인하는 것이 좋습니다.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

이 메시지는 귀하의 작업 상태를 알려주고 유용한 피드백을 제공합니다.

## 결론

이제 Aspose.Cells를 사용하여 Excel에서 PDF로 변환하는 동안 외부 리소스를 제어하는 프로세스를 마스터했습니다! 이러한 단계를 따르면 문서에 이미지와 기타 외부 요소가 정확하게 포함되어 항상 세련된 최종 제품을 얻을 수 있습니다.

## 자주 묻는 질문

### Aspose.Cells란 무엇인가요?
Aspose.Cells는 다양한 형식의 Excel 파일을 생성, 조작, 변환, 렌더링할 수 있는 .NET 개발자를 위한 강력한 라이브러리입니다.

### Aspose.Cells를 어떻게 다운로드하나요?
 최신 버전은 다음에서 다운로드할 수 있습니다.[다운로드 링크](https://releases.aspose.com/cells/net/).

### Aspose.Cells를 무료로 사용할 수 있나요?
 네! 무료 체험판을 방문하면 이용할 수 있습니다.[무료 체험 페이지](https://releases.aspose.com/).

### Aspose.Cells에 대한 지원은 어디에서 찾을 수 있나요?
 지원 관련 문의 사항은 다음을 방문하세요.[Aspose 지원 포럼](https://forum.aspose.com/c/cells/9).

### Aspose.Cells에 대한 임시 라이선스를 어떻게 얻을 수 있나요?
 임시면허를 신청할 수 있습니다.[여기](https://purchase.aspose.com/temporary-license/).
