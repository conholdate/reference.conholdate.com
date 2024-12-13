---
title: 워크북에서 압축 수준 조정
linktitle: 워크북에서 압축 수준 조정
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 압축 수준을 조정하여 대용량 Excel 파일을 효율적으로 관리하는 방법을 알아보세요. 이 단계별 가이드는 디렉터리 설정부터 압축 시간 측정까지 모든 것을 다루며, 파일 크기를 최적화하고 성능을 향상시키는 데 도움이 됩니다.
type: docs
weight: 14
url: /ko/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## 소개

대용량 Excel 파일을 관리하는 것은 어려울 수 있으며, 특히 저장 및 전송 효율성과 관련된 경우 더욱 그렇습니다. 다행히도 파일 압축을 통해 이러한 파일의 크기를 크게 줄여 처리하기 쉽게 만들 수 있습니다. Aspose.Cells for .NET을 사용하는 경우 통합 문서의 압축 수준을 쉽게 조정할 수 있습니다. 이 가이드에서는 각 코드 부분에 대한 명확한 설명을 제공하면서 단계별로 프로세스를 안내합니다.

## 필수 조건

코드를 살펴보기 전에 다음과 같은 전제 조건이 충족되었는지 확인하세요.

1. C#에 대한 기본 지식: C# 프로그래밍에 익숙하면 코드 조각을 더 잘 이해하는 데 도움이 됩니다.
2.  Aspose.Cells 라이브러리: Aspose.Cells 라이브러리를 다운로드하여 설치하세요.[여기](https://releases.aspose.com/cells/net/).
3. Visual Studio: 코드를 실행하려면 Visual Studio와 같은 개발 환경이 필요합니다.
4. .NET Framework: 프로젝트가 호환되는 .NET Framework 버전으로 설정되었는지 확인하세요.

## 필요한 패키지 가져오기

시작하려면 C# 프로젝트에서 필요한 패키지를 가져와야 합니다. 코드 파일 맨 위에 다음 줄을 추가합니다.

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 이러한 패키지는 Aspose.Cells 라이브러리를 사용하여 Excel 파일을 작업하는 데 필수적입니다.`Aspose.Cells` 네임스페이스에는 Excel 파일을 조작하는 데 필요한 모든 클래스가 포함되어 있습니다.`Aspose.Cells.Xlsb` XLSB 형식으로 파일을 저장하기 위한 옵션을 제공합니다.

## 1단계: 소스 및 출력 디렉토리 정의

먼저, 소스 파일이 있는 디렉토리와 출력 파일을 저장할 디렉토리를 설정합니다.

```csharp
// 소스 및 출력 디렉토리 정의
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 교체를 꼭 해주세요`"Your Document Directory\\"` 디렉토리의 실제 경로와 함께. 이렇게 하면 프로그램이 작업하는 데 필요한 파일을 찾을 수 있습니다.

## 2단계: 통합 문서 로드

다음으로, 압축하려는 통합 문서를 로드합니다.

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 여기서 우리는 새로운 인스턴스를 생성합니다`Workbook` 클래스와 기존 Excel 파일을 로드합니다. 파일 이름이 소스 디렉토리의 파일 이름과 일치하는지 확인합니다.

## 3단계: 저장 옵션 설정

이제 통합 문서의 저장 옵션을 구성하세요.

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 그만큼`XlsbSaveOptions`클래스를 사용하면 XLSB 형식으로 통합 문서를 저장할 때 압축 수준을 포함한 다양한 옵션을 지정할 수 있습니다.

## 4단계: 레벨 1의 압축 시간 측정

첫 번째 압축 수준에서 시작하여 통합 문서를 저장하는 데 걸리는 시간을 측정합니다.

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

이 스니펫은 압축 유형을 수준 1로 설정하고, 통합 문서를 저장하고, 경과 시간을 측정합니다.

## 5단계: 레벨 6에 대한 압축 시간 측정

다음으로, 레벨 6 압축으로 성능을 테스트합니다.

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

이 단계는 이전 단계와 비슷하지만 압축 수준이 더 높습니다.

## 6단계: 레벨 9에 대한 압축 시간 측정

마지막으로 가장 높은 압축 수준으로 성능을 평가합니다.

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

이 단계에서는 압축 수준을 수준 9로 설정합니다. 이 수준에서는 파일 크기가 가장 크게 줄어드는 것을 볼 수 있지만 처리하는 데 시간이 더 걸릴 수 있습니다.

## 7단계: 최종 출력

모든 압축 수준을 완료한 후 프로세스가 성공적으로 완료되었음을 나타내는 메시지를 출력합니다.

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

이 간단한 문장은 프로그램이 문제없이 실행되었다는 것을 확인해 줍니다.

## 결론

Aspose.Cells for .NET을 사용하여 통합 문서의 압축 수준을 조정하는 것은 파일 크기와 성능을 크게 개선할 수 있는 간단한 프로세스입니다. 이 가이드에 설명된 단계를 따르면 응용 프로그램에서 압축을 효율적으로 구현하여 Excel 파일 관리 기능을 향상시킬 수 있습니다.

## 자주 묻는 질문

### Aspose.Cells란 무엇인가요?  
Aspose.Cells는 개발자가 Microsoft Excel이 없어도 Excel 파일을 만들고, 조작하고, 변환할 수 있는 강력한 .NET용 라이브러리입니다.

### Aspose.Cells를 어떻게 설치하나요?  
 Aspose.Cells를 다음에서 다운로드하여 설치할 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/cells/net/).

### 어떤 압축 수준을 사용할 수 있나요?  
Aspose.Cells는 레벨 1(가장 낮은 압축)부터 레벨 9(가장 높은 압축)까지 다양한 압축 레벨을 지원합니다.

### Aspose.Cells를 무료로 테스트해 볼 수 있나요?  
 네! Aspose.Cells의 무료 체험판을 받으실 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Cells에 대한 지원은 어디에서 찾을 수 있나요?  
 문의사항이나 지원이 필요하면 Aspose 지원 포럼을 방문하세요.[여기](https://forum.aspose.com/c/cells/9).