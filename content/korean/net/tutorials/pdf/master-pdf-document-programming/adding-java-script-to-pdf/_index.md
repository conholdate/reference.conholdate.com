---
title: PDF 파일에 자바 스크립트 추가
linktitle: 자바스크립트 PDF 파일 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: 이 문서에서는 Aspose.PDF for .NET을 사용하여 팝업 알림이나 자동 인쇄 기능과 같은 대화형 요소를 PDF 문서에 추가하는 방법에 대한 포괄적인 가이드를 제공합니다.
type: docs
weight: 10
url: /ko/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## 소개
이 문서는 Aspose.PDF for .NET을 사용하여 팝업 알림이나 자동 인쇄 기능과 같은 대화형 요소를 PDF 문서에 추가하는 방법에 대한 포괄적인 가이드를 제공합니다. 이 라이브러리의 기능을 활용하면 다양한 사용자 요구 사항을 충족하는 동적이고 매력적인 PDF를 만들 수 있습니다.

## 필수 조건
 진행하기 전에 .NET용 Aspose.PDF의 최신 버전을 다운로드했는지 확인하십시오.[Aspose 릴리스](https://릴리스.aspose.com/pdf/net/) 또는 웹사이트를 통해 무료 체험판을 받으세요:[releases.aspose.com](http://releases.aspose.com).

또한 C#에 대한 기본적인 이해가 있어야 하며 사용하는 개발 환경에 익숙해야 합니다. 또한 개발 프로세스 중에 제한을 피해야 하는 경우 Aspose에서 임시 라이선스를 취득하는 것을 고려하세요.

## 필요한 패키지 가져오기
코드 작성을 시작하려면 Aspose.PDF 라이브러리에서 필요한 네임스페이스를 가져옵니다.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## 1단계: 기존 PDF 로드
대화형 요소를 추가하려는 기존 PDF 문서를 로드합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` PDF 파일의 실제 경로를 포함합니다.

## 2단계: 문서 수준에서 JavaScript 추가

 문서가 열릴 때 트리거되는 스크립트를 적용하려면 다음을 인스턴스화합니다.`JavascriptAction` 물체:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## 3단계: 페이지 수준에서 JavaScript 추가

 페이지 열기 또는 닫기에 따라 특정 작업을 트리거하려면 다음을 인스턴스화합니다.`JavascriptAction` 각 페이지의 객체:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## 4단계: PDF 문서 저장

수정된 PDF 문서를 저장하려면 출력 파일 경로를 지정하세요.

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## 결론
이 가이드를 따르고 Aspose.PDF for .NET을 활용하면 대화형 요소로 PDF를 효과적으로 향상시킬 수 있습니다. 이 라이브러리는 다양한 사용자 요구 사항을 충족하는 동적이고 매력적인 문서를 만드는 포괄적인 솔루션을 제공합니다.

## 자주 묻는 질문

### PDF의 여러 페이지에 여러 개의 JavaScript 동작을 추가할 수 있나요?
네, 개별 페이지나 전체 문서에 다른 JavaScript 동작을 할당할 수 있습니다.

### PDF를 추가한 후 JavaScript를 제거할 수 있나요?
 예, 기존 JavaScript 작업을 지우면 제거하거나 수정할 수 있습니다.`Actions` 문서나 페이지의 속성.

### PDF에서 어떤 종류의 JavaScript 함수를 사용할 수 있나요?
인쇄, 알림, 양식 조작 등 Adobe Acrobat의 JavaScript 엔진이 지원하는 모든 JavaScript를 사용할 수 있습니다.

### JavaScript는 모든 PDF 뷰어에서 작동합니까?
대부분 JavaScript 동작은 Adobe Acrobat과 같이 대화형 PDF를 지원하는 PDF 뷰어에서 작동합니다. 그러나 일부 기본 PDF 리더는 JavaScript를 지원하지 않을 수 있습니다.