---
title: .NET용 Aspose.PDF를 사용하여 PDF 파일에 보이지 않는 주석 추가
linktitle: .NET용 Aspose.PDF를 사용하여 PDF 파일에 보이지 않는 주석 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: Aspose.PDF for .NET을 사용하여 보이지 않는 주석으로 PDF 문서를 강화하는 방법을 알아보세요. 이 포괄적인 튜토리얼은 PDF 내에서 효과적이면서도 신중한 노트를 만드는 과정을 안내합니다.
type: docs
weight: 100
url: /ko/net/tutorials/pdf/mastering-annotations/invisible-annotation-in-pdf-file/
---
## 소개

PDF 문서에 효과적이면서도 보이지 않는 메모를 포함하고 싶었던 적이 있나요? 숨겨진 메시지를 남기거나 인쇄를 위해 메모를 추가하는 것이든 보이지 않는 주석은 엄청나게 유용할 수 있습니다. 이 포괄적인 가이드에서는 .NET용 강력한 Aspose.PDF 라이브러리를 사용하여 PDF 파일에 보이지 않는 주석을 만드는 방법을 알아봅니다. 마지막에는 프로처럼 이러한 주석을 추가하는 데 능숙해질 것입니다!

## 필수 조건

다음 단계를 살펴보기 전에 다음 사항이 있는지 확인하세요.

-  .NET용 Aspose.PDF: Aspose.PDF 라이브러리를 다운로드하고 설치하세요[여기](https://releases.aspose.com/pdf/net/).
- .NET 개발 환경: Visual Studio나 선호하는 다른 .NET IDE를 사용하세요.
- C#에 대한 기본 지식: C# 구문과 프로그래밍 개념에 대한 지식이 필수적입니다.
-  유효한 라이센스 또는 무료 평가판: 라이센스가 없는 경우 임시 라이센스를 취득하세요.[여기](https://purchase.aspose.com/temporary-license/) 또는 무료 체험판을 이용해보세요.

## 필요한 네임스페이스 가져오기

필요한 네임스페이스를 가져오는 것으로 시작합니다. 이를 통해 Aspose.PDF for .NET에서 PDF 작업에 필요한 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
```

## 1단계: 문서 디렉토리 설정

입력 PDF 파일이 저장된 문서 디렉토리 경로를 지정합니다. 이 경로는 프로그램이 PDF 문서를 로드하는 데 도움이 됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 컴퓨터의 실제 경로와 일치합니다.

## 2단계: PDF 문서 로드

다음으로, Aspose.PDF 라이브러리를 사용하여 PDF 문서를 엽니다.

```csharp
// 문서를 로드합니다
Document doc = new Document(dataDir + "input.pdf");
```

 확인한다`input.pdf` 지정된 디렉토리에 있습니다.

## 3단계: 보이지 않는 주석 만들기

 이제 흥미로운 부분인 보이지 않는 주석 만들기에 대해 알아보겠습니다!`FreeTextAnnotation` PDF의 첫 페이지에 보이지 않는 자유 텍스트 주석을 추가하는 클래스입니다.

```csharp
FreeTextAnnotation annotation = new FreeTextAnnotation(doc.Pages[1], 
new Aspose.Pdf.Rectangle(50, 600, 250, 650), 
new DefaultAppearance("Helvetica", 16, System.Drawing.Color.Red));
annotation.Contents = "ABCDEFG"; // 숨겨진 메시지
annotation.Characteristics.Border = System.Drawing.Color.Red;
annotation.Flags = AnnotationFlags.Print | AnnotationFlags.NoView; // 화면에 보이지 않음
doc.Pages[1].Annotations.Add(annotation);
```

- `FreeTextAnnotation`새로운 자유 텍스트 주석을 만듭니다.
- `Rectangle`: 페이지에서 주석의 위치와 크기를 정의합니다.
- `DefaultAppearance`: 글꼴을 설정합니다(Helvetica, 크기 16, 빨간색).
- `Contents`: 이 속성은 숨겨진 메시지(이 경우 "ABCDEFG")를 보관합니다.
- `Characteristics.Border`: 주석의 테두리 색상을 정의합니다.
- `Flags` : 가시성 동작을 지정합니다.`Print` 인쇄 시 가시성을 허용합니다.`NoView` 화면에 숨겨져 있습니다.

## 4단계: 업데이트된 PDF 문서 저장

주석을 성공적으로 추가한 후 업데이트된 PDF 문서를 저장합니다.

```csharp
dataDir = dataDir + "InvisibleAnnotation_out.pdf";
// 수정된 파일을 저장하세요
doc.Save(dataDir);
```

 이 코드는 출력 파일 이름을 업데이트하고 저장합니다.`"InvisibleAnnotation_out.pdf"`.

## 5단계: 프로세스 완료 확인

마지막으로, 간단한 콘솔 출력을 통해 주석이 성공적으로 추가되었는지 확인하는 것이 좋습니다.

```csharp
Console.WriteLine("\nInvisible annotation added successfully.\nFile saved at " + dataDir);
```

이를 통해 사용자는 프로세스 완료에 대한 명확한 피드백을 받을 수 있습니다.

## 결론

축하합니다! 이제 Aspose.PDF for .NET을 사용하여 PDF 파일에 보이지 않는 주석을 추가하는 방법을 성공적으로 배웠습니다. 이 튜토리얼은 환경 설정부터 최종 문서 저장까지 안내해 드렸습니다. 인쇄 목적으로 숨겨진 메시지나 메모를 추가하는 기능은 문서 관리에 새로운 가능성을 열어줍니다.

## 자주 묻는 질문

### 주석을 다시 보이게 할 수 있나요?
 네! 제거할 수 있습니다.`AnnotationFlags.NoView` 일반적으로 볼 때 주석이 보이도록 하려면 플래그를 지정합니다.

### Aspose.PDF를 사용하여 어떤 유형의 주석을 추가할 수 있나요?
Aspose.PDF는 텍스트, 링크, 강조 표시, 스탬프 주석을 포함한 다양한 주석을 지원합니다.

### 주석을 추가한 후에 수정할 수 있나요?
물론입니다! 문서에 추가된 후에도 주석의 속성을 변경할 수 있습니다.

### 동일한 문서에 여러 개의 주석을 추가하려면 어떻게 해야 하나요?
추가하려는 각 주석에 대해 주석 생성 및 추가 과정을 반복하기만 하면 됩니다.

### PDF 문서가 여러 페이지인 경우는 어떻게 되나요?
 주석을 생성할 때 원하는 페이지 번호를 지정하기만 하면 됩니다.`doc.Pages[1]` 대상 페이지 인덱스로 이동합니다.